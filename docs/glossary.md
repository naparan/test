# 用語集

| 用語 | 意味 | 出てくる章 |
| --- | --- | --- |
| リポジトリ (repository) | 履歴つきのプロジェクトフォルダ | [0](00-introduction.md) |
| ローカルリポジトリ | 自分のパソコンにあるリポジトリ | [3](03-remote.md) |
| リモートリポジトリ | GitHub などネットワーク上にあるリポジトリ | [3](03-remote.md) |
| ワークツリー (working tree) | 実際に編集しているファイル | [2](02-git-basics.md) |
| ステージ / インデックス (staging area / index) | 次のコミットに入れる変更を置いておく場所 | [2](02-git-basics.md) |
| コミット (commit) | 変更を記録したセーブポイント | [2](02-git-basics.md) |
| コミット ID / ハッシュ | コミットごとにつく固有の英数字 | [2](02-git-basics.md) |
| HEAD | 今いる場所(今のブランチの最新コミット)を指す目印 | [7](07-troubleshooting.md) |
| origin | リモートリポジトリにつける名前の慣習 | [3](03-remote.md) |
| upstream | Fork 元のリポジトリにつける名前の慣習 | [6](06-team.md) |
| push | 手元の履歴をリモートに送る | [3](03-remote.md) |
| pull | リモートの履歴を手元に取り込む | [3](03-remote.md) |
| fetch | リモートの履歴をダウンロードするだけ(取り込まない) | — |
| clone | リモートリポジトリをまるごとコピーする | [3](03-remote.md) |
| ブランチ (branch) | 履歴の分かれ道 | [4](04-branch.md) |
| main | 基本となるブランチ。昔は `master` と呼ばれることが多かった | [4](04-branch.md) |
| マージ (merge) | ブランチを合流させる | [4](04-branch.md) |
| コンフリクト (conflict) | 同じ箇所が別々に変更されていて、自動でマージできない状態 | [4](04-branch.md) |
| プルリクエスト (pull request, PR) | 変更を取り込んでもらうための提案 | [5](05-pull-request.md) |
| レビュー (review) | PR の内容を他の人が確認すること | [5](05-pull-request.md) |
| Approve | レビューで「問題なし」と承認すること | [5](05-pull-request.md) |
| Issue | やること・バグ・アイデアを書き込む掲示板 | [6](06-team.md) |
| Fork | 他人のリポジトリを自分のアカウントにコピーする | [6](06-team.md) |
| コラボレーター (collaborator) | リポジトリに直接 push できるよう招待された人 | [6](06-team.md) |
| Organization | 複数人でリポジトリを管理するためのグループアカウント | [6](06-team.md) |
| GitHub Flow | main から作ったブランチを PR でマージする開発の進め方 | [6](06-team.md) |
| revert | 過去のコミットを打ち消すコミットを作る | [7](07-troubleshooting.md) |
| reset | ブランチの位置を過去のコミットに戻す(履歴を書き換える) | [7](07-troubleshooting.md) |
| stash | 作業中の変更を一時的に退避する | [7](07-troubleshooting.md) |
| .gitignore | Git に無視させるファイルを書いておくファイル | [7](07-troubleshooting.md) |
| GitHub Pages | リポジトリを Web サイトとして公開する機能 | [8](08-next-steps.md) |
| GitHub Actions | push などをきっかけに処理を自動実行する機能 | [8](08-next-steps.md) |
