## Chat App Proxy Server
チャットアプリケーションでTLS通信をするためのプロキシサーバーのExample  
本番環境では使えません  
[チャットアプリケーションのクライアントサイド実装](https://github.com/nakaryo716/chat-app)  
[チャットアプリケーションのサーバーサイド実装](https://github.com/nakaryo716/chat-app-server)  
## RUN
1. SSL証明書の作成
ここではexampleの為にオレオレ証明書を発行します  
```ssl/README.md```に従って証明書を発行してください  
```bash
cd ssl
```
2. Nginxコンテナの立ち上げ  
```compose.yaml```ファイルがあるディレクトリでコンテナを起動させてください  
```
docker compose up
```
## アプリケーションの全体の実行
### 1.サーバーサイドのセットアップ
リポジトリのクローン
```bash
git clone https://github.com/nakaryo716/chat-app
```
コンテナ起動
```
docker compose up
```
### 2.クライアントサイドのセットアップ
リポジトリのクローン
```bash
git clone https://github.com/nakaryo716/chat-app-server
```
ライブラリのインストール
```bash
npm i
```
コンテナ起動
```
docker compose up
```
### 3.プロキシサーバー(Example)のセットアップ
リポジトリのクローン
```bash
git clone https://github.com/nakaryo716/chat-app-proxy-example.git
```
SSL証明書の発行(詳しくは```ssl/README.md```を参照)
```bash
cd ssl
openssl ...
```
コンテナ起動
```bash
docker compose up
```
