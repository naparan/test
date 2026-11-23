# 7. 困ったときは

Git は「ほぼ何でも元に戻せる」ツールです。焦って変なコマンドを打つ前に、まず `git status` と `git log --oneline` で今の状態を確認しましょう。

## 7-1. 取り消したい・やり直したい

まずは「どこまで進んでしまったか」で探してください。

```mermaid
flowchart TD
    A{"どこまで進んだ?"} -->|編集しただけ| B["git restore ファイル名"]
    A -->|add した| C["git restore --staged ファイル名"]
    A -->|commit した<br/>(push はまだ)| D["git reset --soft HEAD~1<br/>git commit --amend"]
    A -->|push した| E["git revert コミットID"]
```

### 編集を取り消して、最後のコミットの状態に戻したい(add 前)

```console
$ git restore profile.md
```

⚠️ **注意**: 編集内容は完全に消えます。元に戻せないので気をつけてください。

### add を取り消したい(ファイルの編集内容は残す)

```console
$ git restore --staged profile.md
```

### 直前のコミットメッセージを直したい(push 前)

```console
$ git commit --amend -m "正しいメッセージ"
```

### 直前のコミットにファイルを入れ忘れた(push 前)

```console
$ git add 忘れたファイル
$ git commit --amend --no-edit
```

### 直前のコミットを取り消したい(push 前)

```console
$ git reset --soft HEAD~1
```

コミットだけが取り消され、変更内容はステージに残ります。`HEAD~1` は「今の1つ前のコミット」という意味です。

### push したコミットを取り消したい

push したコミットは、他の人がすでに取り込んでいるかもしれないので **履歴を書き換えてはいけません**。代わりに「打ち消すコミット」を新しく作ります。

```console
$ git log --oneline
a1b2c3d 間違えた変更
8c7d6e5 その前の変更
$ git revert a1b2c3d
$ git push
```

⚠️ **注意**: `--amend` や `reset` は履歴を書き換えます。**push 済みのコミットには使わない** と覚えておきましょう。

### 消してしまったコミットを取り戻したい

`git reflog` には、HEAD(今いる場所)が動いた記録が残っています。

```console
$ git reflog
3f2a1b9 HEAD@{0}: reset: moving to HEAD~1
8c7d6e5 HEAD@{1}: commit: 消してしまったコミット
$ git reset --hard 8c7d6e5
```

`reset --hard` はワークツリーの未コミットの変更も消すので、実行前に `git status` で確認してください。

## 7-2. 作業を一時的に退避したい: `git stash`

作業の途中で「先に別のブランチで急ぎの修正をしたい」というときに使います。

```console
$ git stash              # 変更を一時的にしまう
$ git switch main        # 別の作業をする
（作業）
$ git switch 元のブランチ
$ git stash pop          # しまった変更を戻す
```

## 7-3. Git で管理したくないファイル: `.gitignore`

リポジトリのいちばん上に `.gitignore` というファイルを作ると、そこに書いたファイルは Git に無視されます。

```gitignore
# パスワードや API キー
.env

# OS が勝手に作るファイル
.DS_Store
Thumbs.db

# 自動生成されるもの
node_modules/
__pycache__/
*.log
```

GitHub でリポジトリを作るときに **Add .gitignore** で言語を選ぶと、テンプレートが入ります。[github/gitignore](https://github.com/github/gitignore) にも言語ごとのテンプレートがあります。

⚠️ **注意**: すでにコミットしたファイルは、あとから `.gitignore` に書いても無視されません。いったん管理対象から外す必要があります(ファイル自体は消えません)。

```console
$ git rm --cached .env
$ git commit -m ".env を管理対象から外す"
```

### パスワードや API キーを push してしまったら

**すぐにそのパスワードやキーを無効化(再発行)してください。** 公開リポジトリに push された秘密情報は、数分で自動的に収集されることがあります。履歴から消すのはそのあとです。消したから安全、ではありません。

## 7-4. よくあるエラー

### `fatal: not a git repository`

```
fatal: not a git repository (or any of the parent directories): .git
```

Git のリポジトリではないフォルダでコマンドを打っています。`pwd` で今いる場所を確認して、`cd` でリポジトリのフォルダに移動してください。

### push が拒否される

```
 ! [rejected]        main -> main (fetch first)
error: failed to push some refs to 'https://github.com/...'
hint: Updates were rejected because the remote contains work that you do not
hint: have locally.
```

GitHub 側に、手元にない新しいコミットがあります。先に取り込んでから push します。

```console
$ git pull
$ git push
```

### pull で「divergent branches」と言われる

```
hint: You have divergent branches and need to specify how to reconcile them.
fatal: Need to specify how to reconcile divergent branches.
```

手元と GitHub の両方に新しいコミットがあり、どうまとめるかを Git が聞いています。初心者のうちは「マージでまとめる」設定にしておけば OK です(1回だけ設定すれば済みます)。

```console
$ git config --global pull.rebase false
$ git pull
```

### パスワードで push できない

```
remote: Support for password authentication was removed on August 13, 2021.
```

GitHub はパスワードでの push に対応していません。[第1章 1-4](01-setup.md#1-4-github-にログインできるようにする) の手順で `gh auth login` してください。

### `refusing to merge unrelated histories`

GitHub でリポジトリを作るときに README などを作ってしまい、手元の履歴とつながっていないときに出ます。

```console
$ git pull origin main --allow-unrelated-histories
```

コンフリクトが出たら第4章の手順で解決し、そのあと push します。

### 切り替えや pull で「would be overwritten」と言われる

```
error: Your local changes to the following files would be overwritten by checkout:
	profile.md
Please commit your changes or stash them before you switch branches.
```

まだコミットしていない変更があります。コミットするか、`git stash` で退避してから実行してください。

### 変な画面が出て抜けられない(Vim)

`-m` をつけずに `git commit` したり、`git merge` でマージコミットを作ったりすると、**Vim** というエディタが開くことがあります。

- メッセージを書いて保存して閉じる: `i` で入力モード → 書く → `Esc` → `:wq` → `Enter`
- そのまま閉じる(マージのときなど): `Esc` → `:wq` → `Enter`
- 何もせずに中止する: `Esc` → `:q!` → `Enter`

VS Code を使っているなら、Git のエディタを VS Code にしておくと安心です。

```console
$ git config --global core.editor "code --wait"
```

## 7-5. それでも困ったら

- エラーメッセージを **そのまま** 検索する(英語のままの方がよく見つかります)
- `git status` の出力には、次に打つべきコマンドのヒント(`use "git ..."`)が書いてあることが多い
- 公式ドキュメント: [Pro Git(日本語版)](https://git-scm.com/book/ja/v2)、[GitHub Docs](https://docs.github.com/ja)
- 最終手段: 大事なファイルを別の場所にコピーしてから、GitHub から clone し直す

---

[← 前へ: 6. チームで開発する](06-team.md) | [次へ: 8. 次のステップ →](08-next-steps.md)
