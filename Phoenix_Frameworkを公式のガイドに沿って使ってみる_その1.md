Phoenix Frameworkを公式のガイドに沿って使ってみる その1

Phoenixが最近来ているようなので、僕も触ってみたいと思いました。
並列性、安全性、速度面、チャンネルがフレームワークの中に入っていて、無理矢理感が無い...などというメリットがあるようです。
APIサーバを立てるのには最良の選択肢であるとも聞きました。

それでは公式ページの内容に沿って初めていきます。
今回は新規ページを追加するところまでやろうと思います。
まずはもろもろのインストールから。

# インストール
公式ページでは[こちら](http://www.phoenixframework.org/v0.14.0/docs/installation)
僕は既にelixirが入っていました。
入っていない人は[こちら](http://elixir-lang.org/install.html)から。

次にHexをインストールします。以下のコマンドで。

```
$ mix local.hex
```

Phoenixをインストールします。以下のコマンドで。

```
$ mix archive.install https://github.com/phoenixframework/phoenix/releases/download/v0.14.0/phoenix_new-0.14.0.ez
```

# Up And Running
公式ページでは[こちら](http://www.phoenixframework.org/v0.14.0/docs/up-and-running)

まず、アプリケーションを作成します。以下のコマンドで。
ディレクトリは適宜変更してください。

また、アプリケーションの名前は `hello_phoenix ` にします。

```
$ mix phoenix.new /Users/me/work/elixir-stuff/hello_phoenix
```

```
$ mix phoenix.new hello_phoenix
```

これで、先ほど指定したディレクトリに、アプリケーションのひな型ができたと思います。

ではサーバを動かしてみましょう。
```
$ cd hello_phoenix
$ mix phoenix.server
```

ブラウザで `http://localhost:4000/` にアクセスしてみると、公式ページのように表示されました！

# Adding Pages
公式ページでは[こちら](http://www.phoenixframework.org/v0.14.0/docs/adding-pages)

次に `/hello` にアクセスできるよう、ページを追加します。

## ルータの追加

`web/router.ex` を以下のように変更します。

```
get "/hello", HelloController, :index
```
を追加します。

```
defmodule HelloPhoenix.Router do
  use HelloPhoenix.Web, :router

  pipeline :browser do
    plug :accepts, ["html"]
    plug :fetch_session
    plug :fetch_flash
    plug :protect_from_forgery
  end

  pipeline :api do
    plug :accepts, ["json"]
  end

  scope "/", HelloPhoenix do
    pipe_through :browser # Use the default browser stack

    get "/", PageController, :index
    get "/hello", HelloController, :index
  end

  # Other scopes may use custom stacks.
  # scope "/api", HelloPhoenix do
  #   pipe_through :api
  # end
end
```

## コントローラの追加
`web/controllers/hello_controller.ex` ファイルを作成してください。
内容は以下の通りです。

```
defmodule HelloPhoenix.HelloController do
  use HelloPhoenix.Web, :controller

  def index(conn, _params) do
    render conn, "index.html"
  end
end
```

## ビューの追加
`web/views/hello_view.ex` ファイルを作成してください。
内容は以下の通りです。

```
defmodule HelloPhoenix.HelloView do
  use HelloPhoenix.Web, :view
end
```

## テンプレートの追加
最後に、テンプレートを追加します。
`web/templates/hello/index.html.eex` ファイルを作成してください。
内容は以下の通りです。

```
<div class="jumbotron">
  <h2>Hello World, from Phoenix!</h2>
</div>
```

## 表示
`http://localhost:4000/hello` にアクセスしてみると、公式ページのように表示がされました！
エラーページに遷移する方は、一度サーバを再起動するといいかもしれません。あと、カンマを忘れていないか確認してみてください。


