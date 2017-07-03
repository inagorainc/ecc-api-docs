# ECC APIドキュメント
APIドキュメントです。

## 概要
サプライヤー管理システム内の連携用API資料です。

## 仕様
### エンドポイント
+ stg環境

  http://supplier.stg.wonderfull.jp/

+ 本番環境

  https://supplier.wonderfull.jp/

### 認証

### データ形式
すべてJSON形式を利用します。
POSTのリクエストに対しては、Content-Typeヘッダに「application/json」を指定してください。

正常時、HTTPステータスコード200を返します。

異常時、HTTPステータスコード400を返します。

## API

## 注文
* [GET /v1/orders](v1_orders.md) - 注文情報一覧を取得

## 発送

## 在庫
