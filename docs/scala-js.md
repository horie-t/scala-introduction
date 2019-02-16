# Scala.js

本章ではScala.jsを使っていきます。

## 開発ツールのインストール

Scala.jsを動かすには、node.jsがあると便利なのでインストールします。

```bash
curl -sL https://deb.nodesource.com/setup_10.x | sudo -E bash -
sudo apt-get install -y nodejs
```

node.jsとnode.jsのパッケージ・マネージャのnpmがインストールされます。

追加で、yarnと言う最近の流行りのnode.jsのパッケージ・マネージャもインストールしておきます。

```bash
curl -sL https://dl.yarnpkg.com/debian/pubkey.gpg | sudo apt-key add -
echo "deb https://dl.yarnpkg.com/debian/ stable main" | sudo tee /etc/apt/sources.list.d/yarn.list
sudo apt-get update && sudo apt-get install yarn
```

## Scala.jsでHello, world!

Scalaで、プロジェクトを作成します。

```
sbt new sbt/scala-seed.g8
# (中略)
name [Scala Seed Project]: Scalajs_hello_world
```

`scalajs_hello_world` のディレクトリの `project/plugins.sbt` に以下の内容を追記します。

```
addSbtPlugin("org.scala-js" % "sbt-scalajs" % "0.6.26")
```

`build.sbt` を以下のように修正します。

```scala
// (前略)
lazy val root = (project in file("."))
  .enablePlugins(ScalaJSPlugin)
  .settings(
    name := "Scalajs_hello_world",
    scalaJSUseMainModuleInitializer := true,
    libraryDependencies += scalaTest % Test
  )
// (後略)
```

`sbt` を実行して `run` を呼び出し、コンパイル、実行します。

```bash
cd scalajs_hello_world
sbt
(中略)
> run
(中略)
[info] Fast optimizing /home/horie-t/workspace/scala-introduction/scalajs_hello_world/target/scala-2.12/scalajs_hello_world-fastopt.js
[info] Running example.Hello
hello
[success] Total time: 1 s, completed 2019/02/16 20:30:11
```

プロジェクトのディレクトリに　`index.html` ファイルを作成し、以下の内容を記述します。

```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="UTF-8">
    <title>Scala.js Hello</title>
  </head>
  <body>
    <!-- Include Scala.js compiled code -->
    <script type="text/javascript" src="./target/scala-2.12/scalajs_hello_world-fastopt.js"></script>
  </body>
</html>
```

ブラウザで index.html ファイルを開きます。

```
# Chromeでの例
google-chrome index.html
# Firefoxでの例
firefox index.html
```

空白の画面が表示されますが、ブラウザのコンソールには、helloと表示されています。

* *Chromeの場合:* `Ctrl+Shift+I` を押下して、[console]タブを選択します。
* *Firefoxの場合:* `Ctrl+Shift+K` を押下します。
