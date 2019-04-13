# ScalaでAndroidアプリケーションを作成する。

## Android SDKのインストール

Android Studioをインストールし、Androidアプリ開発用のSDKをインストールする必要があります。

1. [Android Studioのダウンロード・ページ](https://developer.android.com/studio?hl=ja)にアクセスし、Android Studioをダウンロードします。
2. ダウンロードしたzipファイルを、インストール先ディレクトリに展開します。  
```bash
cd ~/ダウンロード
sudo unzip android-studio-ide-182.5314842-linux.zip -d /opt
```
3. `~/.bashrc` ファイルにPATHの記述を追加します。  
```bash
echo "export PATH=$PATH:/opt/android-studio/bin" >> ~/.bashrc
source ~/.bashrc
```
4. Adnroid Studioの依存ライブラリをインストールします。  
```bash
sudo apt-get install lib32z1 lib32ncurses5 lib32bz2-1.0 lib32stdc++6
```
5. Android Studioを起動して、セットアップを開始します。セットアップ・ウィザードの中で、[Verify Setting]の画面での、[SDK Folder:]のディレクトリをメモしておきます。  
```bash
studio.sh
```
7. セットアップを行って、Androidのプロジェクトを作成して、実機でPCに接続して動作するか確認します。
8. `ANDROID_HOME` 環境変数と、SDKツールへのPATHを設定します。  
```bash
export ANDROID_HOME=$HOME/Android/Sdk
export PATH=$PATH:$ANDROID_HOME/tools/bin:$ANDROID_HOME/platform-tools
```
## Androidのプロジェクトを作成する

1. Androidアプリのプロジェクトのディレクトリを作成します。  
```bash
mkdir hello_android
```

2. プロジェクトのディレクトリに移動して、sbtの設定をします。  
```bash
cd hello_android/
mkdir project
echo 'addSbtPlugin("org.scala-android" % "sbt-android" % "1.7.6")' >project/build.sbt
echo 'sbt.version=0.13.16' >project/build.properties
```

3. Androidのプロジェクトを作成して、動作させます。  
```bash
sbt "gen-android com.example.hello HelloWorld" android:run
```

以下のような画面が、Android端末に表示されます。

<img src="./images/HelloAndroid.png" width="480px">
