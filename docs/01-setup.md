# 1. 準備

## アカウントを作る

<https://github.com/signup> から作成します。

## Git をインストールする

| OS | 方法 |
| --- | --- |
| Windows | <https://git-scm.com/downloads/win> からインストール。コマンドは **Git Bash** で打つ |
| macOS | ターミナルで `xcode-select --install` |
| Linux | `sudo apt install git` |

`git --version` でバージョンが出れば OK です。

## 初期設定(最初に1回だけ)

```console
$ git config --global user.name "Taro Yamada"
$ git config --global user.email "taro@example.com"
$ git config --global init.defaultBranch main
$ git config --global pull.rebase false
```

上から、名前・メールアドレス(コミットに記録される)、最初のブランチ名を `main` にする、`pull` のときはマージでまとめる、という設定です。

## GitHub にログインする

push するにはログインが必要です(GitHub のパスワードでは push できません)。[GitHub CLI](https://cli.github.com/) をインストールして、次を実行します。

```console
$ gh auth login
```

選択肢は **GitHub.com → HTTPS → Yes → Login with a web browser** を選び、表示されたコードをブラウザに貼り付ければ完了です。

## 🧪 やってみよう

`git config --global --list` で4つの設定が入っていること、`gh auth status` でログインできていることを確認する。

---

[← 前へ: 0. Git と GitHub](00-introduction.md) | [次へ: 2. Git の基本 →](02-git-basics.md)
