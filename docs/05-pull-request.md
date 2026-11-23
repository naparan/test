# 5. プルリクエスト

| 用語 | 意味 |
| --- | --- |
| プルリクエスト (PR) | ブランチの変更を `main` に取り込んでもらうための提案 |
| レビュー | PR の内容を他の人が確認すること |
| Approve / Request changes | レビューの結果。「OK」/「修正してほしい」 |

## 流れ

```console
$ git switch main
$ git pull
$ git switch -c feature/add-goals
（編集して add / commit）
$ git push -u origin feature/add-goals
```

1. GitHub で **Compare & pull request** をクリック
2. **base: `main` ← compare: `feature/add-goals`** になっていることを確認し、タイトルと説明を書いて **Create pull request**
3. レビューしてもらう(**Files changed** タブで行ごとにコメントできる)
   - 修正を頼まれたら、同じブランチでコミットして `git push` するだけで PR が更新される
4. **Merge pull request** → **Confirm merge** でマージし、**Delete branch** でブランチを消す

マージしたら、手元も更新します。

```console
$ git switch main
$ git pull
$ git branch -d feature/add-goals
```

## 🧪 やってみよう

ブランチで変更して PR を作り、マージする。手元で `git pull` して反映を確認する。

---

[← 前へ: 4. ブランチ](04-branch.md) | [次へ: 6. Issue →](06-issue.md)
