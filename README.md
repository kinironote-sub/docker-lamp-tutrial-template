Docker LAMP Template
==
Docker上でのLAMP(Linux,Apache,MySQL,PHP)のテンプレート
  
***あくまでLAMPの開発練習用です．必要最低限のものしか入っていません***

初期設定済みのバージョン
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
- https://www.docker.com/products/docker-toolbox からDocker ToolBoxをダウンロードします。
- Docker ToolBoxをインストールします。このとき，Windows10の場合は途中の「Select Additional Tasks」で「Install VirtualBox with NDIS5 driver[default NDIS6]」にチェックを入れる必要があります。([参考:Failed to open/create the internal network Vagrant on Windows10](http://stackoverflow.com/questions/33725779/failed-to-open-create-the-internal-network-vagrant-on-windows10))
- ショートカットが２つ生成されますが，Docker Quickstart Terminalの方を起動します。最初の起動時には初期化が行われます．暫く待ち，クジラが表示されたら初期化完了です。
- ※ちなみに，もう一方のショートカットはKitematicというGUIで簡単にDockerを扱えるアプリケーションです。いろいろなサーバーのイメージが簡単に使用できて，楽しいです。

### LAMPの起動
- Docker Quickstart Terminalを起動します。このとき「default machine with IP \*\*\*」の\*\*\*の部分をメモしておきましょう。(VirtualBoxでDockerに割り当てられたIPアドレスです。Webアプリケーションが動作するIPアドレスになります。)
- プロジェクトを置きたいフォルダに移動します。なお，C:\\Users\\\*\*\*\がルートに設定されていますが，VirtualBoxの都合上，***ルートより下の階層***にフォルダを作ってください。
- このリポジトリをクローンします。
```
git clone https://github.com/kinironote-sub/docker-lamp-tutrial-template.git
```
- 「docker-compose up -d」によりDocker Composeを起動させます。初回はOSを３つ持ってきてapt updateとかするので少し時間がかかりますが，2回目以降は一瞬で起動できます。
```
cd docker-lamp-tutrial-template/
docker-compose up -d
```
- これで終了です。メモしておいたIPアドレスにブラウザからアクセスすると/webが見れます。phpMyAdmin(mysqlをGUIから操作するもの)は，IPアドレス:8080から見れます。停止する場合は以下のコマンドを実行して下さい。
```
docker-compose stop
```

##使い方
1. /webに動かしたいphpファイルを入れます。
1. 見れます。

##設定変更
###バージョン変更
#####MYSQL
/docker-compose.ymlの4行目を変更。([mysqlバージョン一覧](https://hub.docker.com/_/mysql/))
#####PHP
/bin/php/DockerFileの1行目を変更。([phpバージョン一覧](https://hub.docker.com/_/php/))
###ポート変更
/docker-compose.ymlの各「pots:」を変更。（左の数字がホストのポート，右の数字がコンテナのポート。）
###mysqlのユーザー名、パスワード変更
/docker-compose.ymlの「mysql: environment:」の中身を適宜変更。
