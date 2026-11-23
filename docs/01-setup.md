# 1. 準備

この章では、GitHub アカウントを作り、Git をインストールして初期設定をします。

## 1-1. GitHub アカウントを作る

1. <https://github.com/signup> を開く
2. メールアドレス、パスワード、ユーザー名を入力する
3. 届いたメールのコードで認証する

⚠️ **注意**: ユーザー名は URL(`https://github.com/ユーザー名`)になり、ポートフォリオや就活で人に見せることもあります。あとから変えられますが、リンク切れの原因になるので最初から落ち着いた名前にしておくのがおすすめです。

💡 **ポイント**: 学生なら [GitHub Education](https://education.github.com/) に申請すると、有料機能や開発ツールの特典を無料で使えます。

## 1-2. Git をインストールする

まず、すでに入っていないか確認します。ターミナル(Windows は「PowerShell」や「Git Bash」、macOS は「ターミナル」)を開いて次を入力します。

```console
$ git --version
```

`git version 2.xx.x` のように表示されればインストール済みです。1-3 に進んでください。

### Windows

1. <https://git-scm.com/downloads/win> からインストーラーをダウンロード
2. 基本的にはすべて「Next」で OK
   - 途中の「Adjusting the name of the initial branch」では **Override the default branch name for new repositories** を選び、`main` にしておくと後の手順と一致します
3. インストール後、**Git Bash** というアプリが使えるようになります。この教材のコマンドは Git Bash で入力するのがおすすめです

### macOS

ターミナルで次を実行すると、インストールするか聞かれます。「インストール」を選びます。

```console
$ xcode-select --install
```

Homebrew を使っている人は `brew install git` でも構いません。

### Linux (Ubuntu など)

```console
$ sudo apt update
$ sudo apt install git
```

## 1-3. 初期設定

Git は、コミットに「誰が記録したか」を残します。そのための名前とメールアドレスを設定します。**最初に1回だけ**やれば OK です。

```console
$ git config --global user.name "Taro Yamada"
$ git config --global user.email "taro@example.com"
```

新しいリポジトリの最初のブランチ名を `main` にする設定もしておきます。

```console
$ git config --global init.defaultBranch main
```

設定を確認します。

```console
$ git config --global --list
user.name=Taro Yamada
user.email=taro@example.com
init.defaultbranch=main
```

⚠️ **注意**: ここで設定したメールアドレスは、公開リポジトリのコミット履歴から誰でも見られます。公開したくない場合は、GitHub の [Settings → Emails](https://github.com/settings/emails) にある `xxxx+ユーザー名@users.noreply.github.com` という形式のアドレスを使いましょう。

## 1-4. GitHub にログインできるようにする

GitHub に push するときは本人確認が必要です。**GitHub のパスワードをそのまま使うことはできません**。いちばん簡単なのは **GitHub CLI**(`gh` コマンド)を使う方法です。

### GitHub CLI をインストールする

- Windows: <https://cli.github.com/> からインストーラーをダウンロード、または `winget install --id GitHub.cli`
- macOS: `brew install gh`
- Linux: <https://github.com/cli/cli/blob/trunk/docs/install_linux.md> を参照

### ログインする

```console
$ gh auth login
```

質問には次のように答えます(矢印キーで選んで Enter)。

| 質問 | 答え |
| --- | --- |
| Where do you use GitHub? | GitHub.com |
| What is your preferred protocol for Git operations? | HTTPS |
| Authenticate Git with your GitHub credentials? | Yes |
| How would you like to authenticate GitHub CLI? | Login with a web browser |

画面に出る 8 桁のコードをコピーし、開いたブラウザに貼り付けて承認すれば完了です。

```console
$ gh auth status
github.com
  ✓ Logged in to github.com account taro-yamada
```

💡 **ポイント**: Windows で Git をインストールした場合、「Git Credential Manager」が一緒に入っているので、GitHub CLI がなくても初回 push 時にブラウザでログインする画面が出ます。どちらの方法でも構いません。

## 🧪 やってみよう

1. `git --version` でバージョンが表示されることを確認する
2. `git config --global --list` で名前とメールアドレスが設定されていることを確認する
3. `gh auth status` でログインできていることを確認する(GitHub CLI を入れた人)

ここまでできたら準備完了です!

---

[← 前へ: 0. Git と GitHub ってなに?](00-introduction.md) | [次へ: 2. Git の基本 →](02-git-basics.md)
