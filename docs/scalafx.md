# ScalaでGUIアプリケーションを作成する

ScalaでGUIアプリケーションを作成するには、ScalaFXを使います。

まず、sbtプロジェクトを作成します。

```bash
$ sbt new sbt/scala-seed.g8
(中略)
name [Scala Seed Project]: hello_scalafx
```

build.sbtに以下を追記します。

```scala
libraryDependencies += "org.scalafx" %% "scalafx" % "8.0.144-R12"
```

追記した結果は以下のようになります。

```
import Dependencies._

ThisBuild / scalaVersion     := "2.12.8"
ThisBuild / version          := "0.1.0-SNAPSHOT"
ThisBuild / organization     := "com.example"
ThisBuild / organizationName := "example"

lazy val root = (project in file("."))
  .settings(
    name := "hello_scalafx",
    libraryDependencies ++= Seq(
      "org.scalafx" %% "scalafx" % "8.0.144-R12",
      scalaTest % Test
    )
  )
```
