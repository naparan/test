# コマンド早見表

## 最初に1回だけ

| コマンド | 意味 |
| --- | --- |
| `git config --global user.name "名前"` | 名前を設定 |
| `git config --global user.email "メール"` | メールアドレスを設定 |
| `git config --global init.defaultBranch main` | 最初のブランチ名を `main` にする |
| `git config --global pull.rebase false` | pull のときはマージでまとめる |
| `gh auth login` | GitHub にログイン |

## リポジトリを始める

| コマンド | 意味 |
| --- | --- |
| `git init` | 今のフォルダをリポジトリにする |
| `git clone URL` | GitHub のリポジトリをまるごとコピー |
| `git remote add origin URL` | リモートを登録 |
| `git remote -v` | 登録されているリモートを確認 |

## 毎日使う

| コマンド | 意味 |
| --- | --- |
| `git status` | 状態を確認(迷ったらこれ) |
| `git diff` | まだ add していない変更を見る |
| `git diff --staged` | add 済みの変更を見る |
| `git add ファイル名` | ステージに追加 |
| `git add .` | 今のフォルダ以下の変更をすべて追加 |
| `git commit -m "メッセージ"` | コミット |
| `git log --oneline` | 履歴を1行ずつ表示 |
| `git log --oneline --graph --all` | ブランチの分かれ方も図で表示 |
| `git pull` | リモートの変更を取り込む |
| `git push` | リモートに送る |
| `git push -u origin ブランチ名` | 新しいブランチを初めて送る |

## ブランチ

| コマンド | 意味 |
| --- | --- |
| `git branch` | ブランチ一覧 |
| `git switch -c ブランチ名` | 作って切り替える |
| `git switch ブランチ名` | 切り替える |
| `git merge ブランチ名` | 今のブランチに取り込む |
| `git merge --abort` | マージを中止 |
| `git branch -d ブランチ名` | 削除 |

## 取り消す

| 状況 | コマンド |
| --- | --- |
| 編集を取り消す(add 前) | `git restore ファイル名` |
| add を取り消す | `git restore --staged ファイル名` |
| 直前のコミットメッセージを直す(push 前) | `git commit --amend -m "メッセージ"` |
| 直前のコミットを取り消す(push 前) | `git reset --soft HEAD~1` |
| push したコミットを打ち消す | `git revert コミットID` |
| 作業を一時退避 / 戻す | `git stash` / `git stash pop` |
| 過去の操作履歴を見る | `git reflog` |

## いつもの流れ

```console
$ git switch main
$ git pull
$ git switch -c feature/やること
（編集）
$ git add .
$ git commit -m "何をしたか"
$ git push -u origin feature/やること
（GitHub で PR を作る → レビュー → マージ）
$ git switch main
$ git pull
$ git branch -d feature/やること
```
