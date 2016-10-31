Docker LAMP Template
==
Docker上でのLAMP(Linux,Apache,MySQL,PHP)のテンプレート

***セキュリティについて現時点では保障できません***

- mysql:5.7.16
- php:7.0.12-apache

##目次
- 環境構築(Winsows)
- 使い方
- 設定変更
    - バージョン変更
    - ポート変更
    - mysqlのユーザー名、パスワード変更
    
##環境構築(Windows)

### Dockerを入れる
- https://www.docker.com/products/docker-toolbox からDocker ToolBoxをダウンロード．
- Docker ToolBoxをインストール．Win10の場合は途中の「Select Additional Tasks」で「Install VirtualBox with NDIS5 driver[default NDIS6]」にチェックを入れる必要があるらしい(僕はwin8)([参考:Failed to open/create the internal network Vagrant on Windows10](http://stackoverflow.com/questions/33725779/failed-to-open-create-the-internal-network-vagrant-on-windows10))
- ショートカットが二つ生成される．Docker Quickstart Terminalのほうを起動する．初回起動時に初期セットアップが行われる．クジラが表示されたら完了．
- もう一方のKitematicはGUIで簡単にDockerを使えるツール．色んなサーバーやMinecraftサーバーのイメージとかも転がってるので遊べる．

### LAMPの起動
- Docker Quickstart Terminalを起動．「default machine with IP \*\*\*」の\*\*\*のところをメモっておく．(VirtualBoxでDockerに割り当てられたIPアドレス．たぶん．)
- C:\User\\\<my user name>\がルートになっているので，***ルート以下***の，プロジェクトを置きたい好きなフォルダに移動
- こいつをクローン.
```
git clone https://github.com/kinironote-sub/docker-lamp-tutrial-template.git
```
- 「docker-compose up -d」で起動.初回はOSを３つ持ってきてapt updateとかするので少し時間がかかります．紅茶を飲みましょう．（2回目以降は秒で終わります）
- おしまい(メモったIPアドレスにブラウザからアクセスすると/webが見れます．phpMyAdmin(mysqlをGUIから操作するもの)は:8080から見れます．)
```
cd docker-lamp-tutrial-template/
docker-compose up -d
```

##使い方
1. /webに動かしたいphpファイルを入れます
1. 見れます

##設定変更
###バージョン変更
#####MYSQL
/docker-compose.ymlの4行目を変更([バージョン一覧](https://hub.docker.com/_/mysql/))
#####PHP
/bin/php/DockerFileの1行目を変更([バージョン一覧](https://hub.docker.com/_/php/))
###ポート変更
/docker-compose.ymlの各「pots:」を変更（左がホストのポート，右がコンテナのポート）
###mysqlのユーザー名、パスワード変更
/docker-compose.ymlの「mysql: environment:」の中身を適宜変更
