# 2. Git の基本

## 3つの場所

```mermaid
flowchart LR
    W["ワークツリー"] -->|git add| S["ステージ"]
    S -->|git commit| R["リポジトリ"]
```

| 場所 | 意味 |
| --- | --- |
| ワークツリー | 編集中のファイル |
| ステージ | 次のコミットに入れる変更を置く場所 |
| リポジトリ | コミットの履歴(`.git` フォルダに保存される) |

## 基本操作

```console
$ mkdir git-practice
$ cd git-practice
$ git init                       # このフォルダをリポジトリにする
（profile.md を作って保存）
$ git status                     # 状態を確認
$ git add profile.md             # ステージに追加
$ git commit -m "自己紹介を追加"   # コミット
```

ファイルを編集したら、また **`add` → `commit`** です。

```console
$ git diff                       # 何を変えたか確認
$ git add profile.md
$ git commit -m "趣味を追加"
$ git log --oneline              # 履歴を見る
8c7d6e5 (HEAD -> main) 趣味を追加
3f2a1b9 自己紹介を追加
```

- 迷ったら `git status`
- コミットメッセージには **何をしたか** を書く
- `git log` から抜けるときは `q`

## 🧪 やってみよう

`profile.md` を2回編集して、それぞれコミットする。`git log --oneline` でコミットが並んでいることを確認する。

---

[← 前へ: 1. 準備](01-setup.md) | [次へ: 3. GitHub とつなぐ →](03-remote.md)
