# 開発ツールのインストール

Scalaのプロブラムの開発には、JDK(Java Development Kit)と、sbt(Scala、Java向けのビルド・ツール)をインストールする必要があります。(Scala自体は、作成するプロジェクト単位にインストールされます)

## JDKのインストール

JDKをインストールします。ここでは、[AdoptOpenJDK](https://adoptopenjdk.net/)の[Ubuntu向けのインストーラ・パッケージ](https://github.com/rpardini/adoptopenjdk-deb-installer)を使ってインストールします。

```bash
sudo add-apt-repository --yes ppa:rpardini/adoptopenjdk
sudo apt-get update
sudo apt-get install adoptopenjdk-8-jdk-hotspot-set-default
```

## sbtのインストール

```
echo "deb https://dl.bintray.com/sbt/debian /" | sudo tee -a /etc/apt/sources.list.d/sbt.list
sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv 2EE0EA64E40A89B84B2DF73499E82A75642AC823
sudo apt-get update
sudo apt-get install sbt
```
