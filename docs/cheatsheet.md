# コマンド早見表

| コマンド | 意味 |
| --- | --- |
| `git init` | 今のフォルダをリポジトリにする |
| `git status` | 状態を確認(迷ったらこれ) |
| `git diff` | 変更内容を見る |
| `git add ファイル名` | ステージに追加(`.` で全部) |
| `git commit -m "メッセージ"` | コミット |
| `git log --oneline` | 履歴を見る |
| `git remote add origin URL` | リモートを登録 |
| `git push -u origin ブランチ名` | 新しいブランチを初めて push |
| `git push` | push |
| `git pull` | GitHub の変更を取り込む |
| `git clone URL` | リポジトリをまるごとコピー |
| `git branch` | ブランチ一覧 |
| `git switch -c ブランチ名` | ブランチを作って切り替える |
| `git switch ブランチ名` | ブランチを切り替える |
| `git merge ブランチ名` | 今のブランチに取り込む |
| `git merge --abort` | マージを中止 |
| `git branch -d ブランチ名` | ブランチを削除 |

## いつもの流れ

```console
（GitHub で Issue を立てる）
$ git switch main
$ git pull
$ git switch -c feature/やること
（編集）
$ git add .
$ git commit -m "何をしたか"
$ git push -u origin feature/やること
（GitHub で PR を作る[説明に Closes #番号] → レビュー → マージ）
$ git switch main
$ git pull
$ git branch -d feature/やること
```
