FOAM Frameworkのチュートリアルをやる その0

これはFOAM Frameworkについて、公式ページを翻訳しながら学んでいこうという記事です。

前回の記事は[こちら](http://qiita.com/tako-black/items/6e5613867135215a67f2)。

今回からはいよいよチュートリアルを翻訳しながらやっていきたいと思います。
もし何か間違いやおかしい点などありましたら、コメントを頂けると幸いです。 
原文は[github.io](http://foam-framework.github.io/foam/tutorial/0-intro/)で、 
ライセンスは[こちら](https://github.com/foam-framework/foam/blob/master/COPYRIGHT)に準拠します。

以下翻訳

---

チュートリアル パート0 
## はじめに

### 概要 
FOAMはJavaScriptのライブラリです。コンセプトによっていくつかのパートに分かれますが、一般的には相互にインポートしています。 

* 先進的なクラスのシステム。Javaの原理に似ていますが、さらにパワフルです。 
* データソースを抽象化するものやキャッシュのためのヘルパーやログのためのライブラリ 
* ウェブアプリを作成するために使われるビューのライブラリ

FOAMは抽象的な概念や生産性やパフォーマンスの点でハイレベルな働きをします。[Aboutページ](http://foam-framework.github.io/foam/about/)([翻訳したものはこちら](http://qiita.com/tako-black/items/6e5613867135215a67f2))にこの原理について更に記述してあります。または、このチュートリアルに従うことで、すぐに始められます。

このチュートリアルはいくつかのパートに分かれます。 

* はじめに（以下） 
* [中心となる概念](http://foam-framework.github.io/foam/tutorial/1-concepts/) 
* [`電話`モデル](http://foam-framework.github.io/foam/tutorial/2-model/) 
* [コントローラー](http://foam-framework.github.io/foam/tutorial/3-dao/) 
* [カスタムテンプレート](http://foam-framework.github.io/foam/tutorial/4-templates) 
* [ナビゲーション](http://foam-framework.github.io/foam/tutorial/5-navigation) 
* [`詳細なビュー`や他のテンプレート](http://foam-framework.github.io/foam/tutorial/6-detailview)

### 対象者 
このチュートリアルの対象者はJavaScriptやウェブアプリには詳しいけれども、FOAMの概念や使い方を知らない人々です。 
このチュートリアルは手短な概念の説明と、電話のカタログを表示するアプリをFOAMでコードを書いて作成する詳細なチュートリアルを織り交ぜて提供します。

### 必要なツール 
このチュートリアルには2つだけ、必要なツールがあります。
 
* `git`
* ローカルウェブサーバー。Pythonの組み込みのサーバーモジュールをお勧めします。

### はじめに 
では始めましょう。プロジェクトの新しいディレクトリを作成して、そこに移動して、FOAMをダウンロードしてください。

```
mkdir $PROJECT 
cd $PROJECT 
git clone https://github.com/foam-framework/foam.git
```

いま、 `foam/` というサブディレクトリができました。それは、FOAMのすべてのコードと、たくさんのデモとテストページを持っています。 
このライブラリはたくさんのファイルに分割されていますが、HTMLドキュメントにインクルードする必要があるのは `core/bootFOAM.js` 1つだけです。 
`core/foam.css` も同様に正しくビューが表示されるためにはインクルードしておくべきです。

以下の内容で `$PROJECT/index.html` を作成してください。 

```
<html>
  <head>
    <script src="foam/core/bootFOAM.js"></script>
    <link rel="stylesheet" href="foam/core/foam.css" />
  </head>
  <body>
    <script>
      document.write(FOAM_POWERED);
    </script>
  </body>
</html>
```

ウェブサーバーを立ち上げて、このファイルに直でアクセスしてください。Pythonを使う場合、以下のようになります。 

```
python -m SimpleHTTPServer    # Python 2
python -m http.server         # Python 3
```

上記は、8000番ポートでカレントディレクトリのファイルを表示します:[http://localhost:8000/](http://localhost:8000/).

ページがローディングされると「FOAM Powered」のロゴが表示され、JSコンソールにはエラーは表示されません。

もし上記のように表示されたなら、おめでとうございます！FOAMが動き、次のチュートリアルである[パート1:中心となる概念](http://foam-framework.github.io/foam/tutorial/1-concepts/)を正しく行う準備が出来ました。

---

以上翻訳

上記の通りやってみると、確かにロゴが表示され、コンソールにエラーは見られませんでした。
Hello World的な扱いでしょうか。
次回はパート1をやってみたいと思います。
