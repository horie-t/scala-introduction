# 開発ツールのインストール

Scalaのプロブラムの開発には、JDK(Java Development Kit)と、sbt(Scala、Java向けのビルド・ツール)をインストールする必要があります。(Scala自体は、作成するプロジェクト単位にインストールされます)

## JDKのインストール

Scala関連では、いまだにJava 8でないと動かないものが多いので、JDK 8をインストールします。

OracleのJDK 8はサポートが切れてしまったので、2023年6月までサポートがあるAmazon Corretto 8(https://aws.amazon.com/jp/corretto/)をインストールします。

まず、[ダウンロードページ](https://docs.aws.amazon.com/ja_jp/corretto/latest/corretto-8-ug/downloads-list.html)から、.deb ファイルをダウンロードします。

そして、JDKをインストールする前に、java-commonをインストールします。

```bash
sudo apt-get update && sudo apt-get install java-common
```

JDKをインストールします。

```
cd ~/ダウンロード
sudo dpkg --install java-1.8.0-amazon-corretto-jdk_8.202.08-2_amd64.deb
```

既に、Ocacle JDK等をインストールしている場合には、以下の2つのコマンドを実行して、Amazon Correttoに切り替えます。

```
sudo update-alternatives --config java
sudo update-alternatives --config javac
```

## sbtのインストール

```
echo "deb https://dl.bintray.com/sbt/debian /" | sudo tee -a /etc/apt/sources.list.d/sbt.list
sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv 2EE0EA64E40A89B84B2DF73499E82A75642AC823
sudo apt-get update
sudo apt-get install sbt
```
