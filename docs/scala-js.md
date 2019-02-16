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
