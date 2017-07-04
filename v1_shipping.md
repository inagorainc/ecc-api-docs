# POST /api/v1/shipping
発送情報を通知

## リクエストパラメータ

| Name          | Description                                                 |
|---------------|-------------------------------------------------------------|
| order_code | 弊社が付与するオーダーをユニークにするID（必須） |
| jancode |1つのOrder_id内に含まれる商品のJancode(jancode/sku_codeどちらか必須) |
| sku_code | 1つのOrder_id内に含まれる商品のSKUコード(jancode/sku_codeどちらか必須) |
| quantity | 商品ごとの数量（必須） |
| shipping_number | 発送時追跡番号(伝票番号)（必須） |
| note | 備考（任意） |

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
正常時HTTPコード201を返します

## エラーレスポンス例
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
