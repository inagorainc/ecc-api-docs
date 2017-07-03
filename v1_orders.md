# GET /v1/orders
注文情報一覧取得

## リクエストパラメータ

| Name          | Description                                                 |
|---------------|-------------------------------------------------------------|
| id | 弊社が付与するオーダーをユニークにするID（任意） |
| start_ordered | 注文日時指定開始　yyyy-mm-dd hh:mm:ss（任意） |
| end_ordered | 注文日時指定終了　yyyy-mm-dd hh:mm:ss（任意） |
| limit | 取得上限(任意 デフォルト: 10, MAX: 100) |
| offset | オフセット(任意 デフォルト: 0)|


## レスポンス例
```json
{
"data":[
  {
    "id":"ECN000110189822",
    "orders":[
      {
        "jancode":"6853856647891",
        "sku_code":"smc123",
        "quantity":1
      }
    ],
    "order_date":"2017-06-21 11:55:50"
  },
  {
    "id":"ECN000110189823",
    "orders":[
      {
        "jancode":"6853856647891",
        "sku_code":"smc123",
        "quantity":1
      },
      {
        "jancode":"6853856645555",
        "sku_code":"smc567",
        "quantity":2
      }
    ],
    "order_date":"2017-06-21 12:05:55"
  }
]
}
```

## レスポンス内容説明
* data
  すべてのデータ内容
* id
  弊社が付与するオーダーをユニークにするID
* orderes
  注文内容
  * jancode
  JAN CODE
  * sku_code
  SKUコード
  * quantity
  商品ごとの数量
* order_date
  注文日時（yyyy-mm-dd hh:mm:ss+0900）
