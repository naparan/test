# 3. GitHub とつなぐ

| 用語 | 意味 |
| --- | --- |
| ローカル / リモート | 自分の PC のリポジトリ / GitHub 上のリポジトリ |
| origin | リモートにつける名前(慣習) |

## GitHub にリポジトリを作る

右上の **+ → New repository** で `git-practice` を作ります。README などは **作らずに空のまま** にします。

## push する

```console
$ git remote add origin https://github.com/ユーザー名/git-practice.git
$ git push -u origin main     # 最初の1回だけ -u をつける
```

2回目からは **編集 → `add` → `commit` → `push`** です。

```console
$ git push
```

## pull / clone

```console
$ git pull                    # GitHub の変更を手元に取り込む
$ git clone URL               # GitHub のリポジトリをまるごとコピー
```

作業を始める前に `git pull` する癖をつけましょう。

## 🧪 やってみよう

1. `git-practice` を push して、GitHub で表示されることを確認する
2. GitHub 上でファイルを編集(鉛筆アイコン)してコミットし、手元で `git pull` する

---

[← 前へ: 2. Git の基本](02-git-basics.md) | [次へ: 4. ブランチ →](04-branch.md)
