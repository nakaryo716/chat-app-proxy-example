## Chat App Proxy Server
チャットアプリケーションでTLS通信をするためのプロキシサーバーのExample  
本番環境では使えません  
[チャットアプリケーションのクライアントサイド実装](https://github.com/nakaryo716/chat-app)  
[チャットアプリケーションのサーバーサイド実装](https://github.com/nakaryo716/chat-app-server)  
## アプリケーションの全体の実行
### 1.サーバーサイドのセットアップ
リポジトリのクローン
```bash
git clone https://github.com/nakaryo716/chat-app
```
```.env```ファイルのALLOW_ORIGINのIPアドレスを自身のコンピュータのIPアドレスに修正  
```env
ALLOW_ORIGIN=https://192.168.0.1
                    #+++++++++++Fix 
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
 ```src/api/api.ts```のサーバーサイドのURLを自身のコンピュータのIPアドレスに修正(ポート番号はそのまま)
```typescript
export const HostApi = "https://192.168.1.0:1443";
                             //++++++++++++Fix
export const HostWsApi = "wss://192.168.1.0:1443";
                             //++++++++++++Fix
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
### 4.完了
```https://{あなたが指定したipアドレス}/```でアクセス可能です！

