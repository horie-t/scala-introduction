# Hello, world!

ここでは、Hello, world!のアプリケーションを作ってみて、Scalaでのプログラミングの概略を説明します。

## プロジェクトの作成

sbtを使って、プロジェクトを作成します。

```bash
sbt new sbt/scala-seed.g8
# (中略)
name [Scala Seed Project]: hello_world
```

hello_worldと言うディレクトリが作成され、以下のように、ファイルが作成されます。

```bash
$ tree hello_world/
hello_world/
├── build.sbt                   # プロジェクトの設定ファイル
├── project                     # プロジェクトでのsbtが依存する設定
│   ├── Dependencies.scala
│   └── build.properties
└── src
    ├── main
    │   └── scala
    │       └── example
    │           └── Hello.scala # デフォルトのコード
    └── test
        └── scala
            └── example
                └── HelloSpec.scala # 自動テストコード

8 directories, 5 files
```

Hello.scalaファイルは以下の内容になっています。

```bash
$ cat hello_world/src/main/scala/example/Hello.scala 
package example

object Hello extends Greeting with App {
  println(greeting)
}

trait Greeting {
  lazy val greeting: String = "hello"
}
```

## プログラムの実行

### プロジェクトのコードをビルドして実行

作成されたプロジェクトのプログラムを実行するには、以下のようにします。

```bash
cd hello_world
sbt run
(中略)
[info] Running example.Hello 
hello     # この部分が実行結果
[success] Total time: 3 s, completed 2019/04/07 19:16:11
```

### jarファイルを作成して実行

[sbt-assembly](https://github.com/sbt/sbt-assembly)プラグインを使えるようにします。

```bash
echo 'addSbtPlugin("com.eed3si9n" % "sbt-assembly" % "0.14.9")' > project/assembly.sbt
```

```bash
sbt assembly
```

プロジェクト内の以下に、jarファイルが作成されます。

```
target/scala-2.12/hello_world-assembly-0.1.0-SNAPSHOT.jar
```

javaコマンドを使って、以下のように実行できます。

```bash
$ java -jar target/scala-2.12/hello_world-assembly-0.1.0-SNAPSHOT.jar 
hello
```
