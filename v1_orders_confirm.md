# POST /api/v1/orders/confirm
注文処理が終了したことを通知する

## リクエストパラメータ
| Name          | Description                                                 |
|---------------|-------------------------------------------------------------|
| order_code    | 弊社が付与するオーダーをユニークにするID（必須）                   |

## リクエスト例
```json
Content-Type: application/json

[
  {
    "order_code": "ECN000110189822"
  },
  {
    "order_code": "ECN000110189823"
  }
]
```

## レスポンスの例
```json
201 Created
```

## エラーレスポンスの例
```json
{
  "errors":[
    {
      "order_code": "ECN000110189822",
      "message": "存在しない注文番号です"
    }
  ]
}
```
