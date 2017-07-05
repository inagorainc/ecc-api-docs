# POST /api/v1/orders/confirm
注文受領したことを通知。通知されたものはステータスが変更され、注文取得API`/api/v1/orders`を実行しても取得されなくなります。

## リクエストパラメータ
| Name          | Required      | Description                                                 |
|---------------|---------------|-------------------------------------------------------------|
| order_code    | 必須           | 弊社が付与するオーダーをユニークにするID                   |

## リクエスト例
```json
Content-Type: application/json

{
  "order_code": ["ECN000110189822", "ECN000110189823"]
}
```

## レスポンスの例
```json
201 Created
```
※bodyは返しません

## エラーレスポンスの例
複数の注文を送った場合、処理が成功したものはそのまま反映されます。
```json
400 Bad Request

{
  "errors":[
    {
      "code": 3001,
      "order_code": "ECN000110189822",
      "message": "存在しない注文番号です"
    }
  ]
}
```
```json
400 Bad Request

{
  "errors":[
    {
      "code": 3002,
      "order_code": "ECN000110189822",
      "message": "既に受領された注文番号です"
    }
  ]
}
```
