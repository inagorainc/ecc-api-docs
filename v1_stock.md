# PUT /api/v1/stock
商品の在庫に変動があった場合に叩いていただくAPI。

## リクエストパラメータ

| Name          | Required     | Description                                                 |
|---------------|--------------|-------------------------------------------------------------|
| jancode | jancode/sku_codeとどちらか必須 | JAN CODE |
| sku_code | jancode/sku_codeとどちらか必須 | 商品SKUコード |
| stock | 必須 | 在庫数 |

## リクエスト例
```json
Content-Type: application/json

[
  {
    "jancode": "6853856647891",
    "stock": 30
  },
  {
    "sku_code": "sku5567",
    "stock": 25
  },
  {
    "jancode": "6853856647708",
    "stock": 10
  }
]
```

## レスポンス例
```json
204 No Content
```

## エラーレスポンス例
```json
{
  "errors":[
    {
      "jancode": "6853856647891",
      "message": "存在しない商品です"
    },
    {
      "sku_code": "sku5567",
      "message": "存在しないSKUコードです"
    }
  ]
}
```
