# POST /api/v1/stock
商品の在庫に変動があった場合に叩いていただくAPI。

## リクエストパラメータ

| Name          | Required     | Description                                                 |
|---------------|--------------|-------------------------------------------------------------|
| jancode | jancode/sku_codeとどちらか必須 | JAN CODE |
| sku_code | jancode/sku_codeとどちらか必須 | 商品SKUコード |
| quantity | 必須 | 在庫数　（負数を含まない、整数値） |

jancodeとsku_code、どちらも指定していた場合、**jancodeを優先します**

## リクエスト例
```json
Content-Type: application/json

[
  {
    "jancode": "6853856647891",
    "quantity": 30
  },
  {
    "sku_code": "sku5567",
    "quantity": 25
  },
  {
    "jancode": "6853856647708",
    "quantity": 10
  }
]
```

## レスポンス例
```json
204 No Content
```

## エラーレスポンス例
```json
400 Bad Request

{
  "errors":[
    {
      "code": 3004,
      "jancode": "6853856647891",
      "message": "存在しないJANCODEです"
    },
    {
      "code": 3005,
      "sku_code": "sku5567",
      "message": "存在しないSKUコードです"
    }
  ]
}
```
```json
400 Bad Request

{
  "errors":[
    {
      "code": 3006,
      "sku_code": "sku5567",
      "message": "在庫数量が正しくありません"
    }
  ]
}
```
