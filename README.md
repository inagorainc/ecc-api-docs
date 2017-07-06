# Supplier APIドキュメント
APIドキュメントです。

## 概要
サプライヤー管理システム内の連携用API資料です。

## 仕様
### ホスト
* staging環境

  https://supplier.stg.wonderfull.jp/

* 本番環境

  https://supplier.wonderfull.jp/

### 認証
サプライヤーAPIの呼び出しには、API KEY認証が必要になります。弊社がお知らせしたAPI KEYとAPI SECRETを使用します。API KEYとAPI SECRETは、外部に公開しないでください。

APIを呼び出す際、HTTP Headerに下記3点を含めてリクエストしてください。

1) ACCESS-KEY: API KEY
2) ACCESS-TIMESTAMP: UNIXタイムスタンプ
3) ACCESS-SIGNATURE: ACCESS-TIMESTAMP, API KEY, HTTP-METHODを文字列にし連結したものを、API SECRETでHMAC-SHA256で署名

e.g.
```
<PHP CODE>
$intTimeStamp = time(); *
$strAccessKey = "API_KEY"; *
$strAccessSecret = "API_SECRET";
$srtHttpMethod = "POST";
$strMessage = $intTimeStamp . $strAccessKey. $srtHttpMethod;
$strSignature = hash_hmac("sha256", $strMessage, $strAccessSecret); *

$header = [
    'ACCESS-KEY: '.$strAccessKey,
    'ACCESS-TIMESTAMP: '.intTimeStamp,
    'ACCESS-SIGNATURE: '.strSignature,
];
```

*は、Headerに含めてリクエストするもの。
### データ形式
すべてJSON形式を利用します。
POSTのリクエストに対しては、Content-Typeヘッダに「application/json」を指定してください。

正常時、以下のHTTPステータスコードを返します。

* 200 OK - 返すべきレスポンスがある場合
* 204 No Content - 特に返すレスポンスがない場合

異常時、HTTPステータスコード400と、エラーメッセージを返します。
```json
400 Bad Request

{
  "errors": [
    {
      "code": 3001,
      "order_code": "ECN000110189822",
      "message": "存在しない注文番号です"
    }
  ]
}
```

### エラーコード
* [エラーコード一覧](error_code.md)

### タイムゾーン
すべてJST（UTC+9）となっております。

## API

## 注文
* [GET /api/v1/orders](v1_orders.md) - 注文情報一覧を取得
* [POST /api/v1/orders/confirm](v1_orders_confirm.md) - 注文受領を通知

## 出荷
* [POST /api/v1/shipping](v1_shipping.md) - 出荷情報を通知

## 在庫
* [POST /api/v1/stock](v1_stock.md) - 在庫更新
