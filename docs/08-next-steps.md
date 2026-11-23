# 8. 次のステップ

ここまでで、Git と GitHub を使った基本的な開発の流れはひととおりできるようになりました。ここからは、知っておくと便利な機能を紹介します。

## 8-1. README を書く

リポジトリのトップページに表示されるのが `README.md` です。初めて見た人が「これは何で、どう使うのか」を理解できるように書きましょう。

```markdown
# プロジェクト名

1〜2行で、これは何かを説明する。

## スクリーンショット
![画面](images/screenshot.png)

## 使い方
1. ...
2. ...

## 必要なもの
- Python 3.12 以上

## 作者
- 山田太郎 (@taro-yamada)
```

README は [Markdown](https://docs.github.com/ja/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax) という書式で書きます。この教材もすべて Markdown です。

💡 **ポイント**: ユーザー名と同じ名前のリポジトリ(例: `taro-yamada/taro-yamada`)を作って README を書くと、自分のプロフィールページのトップに表示されます。自己紹介やスキルを書いておくと、就活でポートフォリオとして見せるときにも役立ちます。

## 8-2. GitHub Pages: Web サイトを公開する

HTML ファイルを置いたリポジトリを、そのまま Web サイトとして無料で公開できます。

1. `index.html` を含むリポジトリを用意する
2. **Settings → Pages** を開く
3. **Source** を **Deploy from a branch**、**Branch** を `main`、フォルダを `/ (root)` にして **Save**
4. 数分待つと `https://ユーザー名.github.io/リポジトリ名/` で公開される

⚠️ **注意**: 無料プランでは、Pages を使えるのは Public リポジトリだけです(GitHub Education の特典があれば Private でも可)。

## 8-3. GitHub Actions: 自動化する

push や PR をきっかけに、テストやビルドを自動で実行できる仕組みです。`.github/workflows/` フォルダに YAML ファイルを置くだけで動きます。

```yaml
# .github/workflows/hello.yml
name: Hello
on: [push]
jobs:
  greet:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - run: echo "Hello, GitHub Actions!"
      - run: ls
```

push すると、リポジトリの **Actions** タブで実行結果を見られます。PR に自動テストを組み合わせると、「テストが通らない変更はマージできない」ようにできます。

## 8-4. GUI ツール

コマンドに慣れたら、GUI ツールも併用すると便利です。

- **VS Code**: 左のソース管理アイコンから add / commit / push、差分の確認、コンフリクトの解決ができる
- **GitHub Desktop**: GitHub 公式のアプリ。操作が直感的
- **github.dev**: GitHub でリポジトリを開いて `.`(ピリオド)キーを押すと、ブラウザ上で VS Code が開く

💡 **ポイント**: GUI はとても便利ですが、裏でやっていることはこの教材のコマンドと同じです。仕組みがわかっていれば、困ったときにも対処できます。

## 8-5. もっと学ぶには

- [Pro Git(日本語版)](https://git-scm.com/book/ja/v2): Git の公式解説書。無料で読める
- [GitHub Docs](https://docs.github.com/ja): GitHub の公式ドキュメント
- [GitHub Skills](https://skills.github.com/): GitHub 上で実際に手を動かしながら学べる公式の練習コース
- [Learn Git Branching](https://learngitbranching.js.org/?locale=ja): ブランチの動きをブラウザ上で図解しながら学べる

## 最後に

Git は、使えば使うほど手になじみます。授業の課題、個人開発、サークルの活動など、普段の作業でどんどん使ってみてください。

---

[← 前へ: 7. 困ったときは](07-troubleshooting.md) | [目次に戻る](../README.md)
