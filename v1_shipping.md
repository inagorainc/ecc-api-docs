# POST /api/v1/shipping
出荷情報を通知

## リクエストパラメータ

| Name          | Required    | Description                                                 |
|---------------|-------------|-------------------------------------------------------------|
| order_code | 必須 | 弊社が付与するオーダーをユニークにするID |
| shipping_number | 必須 | 発送時追跡番号(伝票番号) |

## リクエスト例
```json
Content-Type: application/json

[
  {
    "order_code": "ECN000110189822",
    "shipping_number": "678439575486"
  },
  {
    "order_code": "ECN000110189823",
    "shipping_number": "678439565098"
  }
]
```

## レスポンス例
```json
201 Created
```
※bodyは返しません

## エラーレスポンス例
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
      "code": 3003,
      "order_code": "ECN000110189822",
      "message": "既に出荷した注文番号です"
    }
  ]
}
```
