# GET /api/v1/orders
未確認の注文情報一覧取得
> 未確認とは - orders/confirmで確認されていないものを取得

## リクエストパラメータ

| Name          | Description                                                 |
|---------------|-------------------------------------------------------------|
| start_ordered | 注文日時指定開始　yyyy-mm-dd または yyyy-mm-dd hh:mm:ss（任意） |
| end_ordered | 注文日時指定終了yyyy-mm-dd または yyyy-mm-dd hh:mm:ss（任意） |

## リクエスト例
```json
GET /api/v1/orders?start_ordered=2017-06-01&end_ordered=2017-06-30 23:59:59
```

## レスポンス例
```json
{
"data":[
  {
    "order_code":"ECN000110189822",
    "orders":[
      {
        "jancode":"6853856647891",
        "sku_code":"smc123",
        "price":530,
        "quantity":1
      }
    ],
    "order_date":"2017-06-21 11:55:50"
  },
  {
    "order_code":"ECN000110189823",
    "orders":[
      {
        "jancode":"6853856647891",
        "sku_code":"smc123",
        "price":530,
        "quantity":1
      },
      {
        "jancode":"6853856645555",
        "sku_code":"smc567",
        "price":1000,
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
* order_code
  弊社が付与するオーダーをユニークにするID
* orders
  注文内容
  * jancode
  JAN CODE
  * sku_code
  SKUコード
  * price
  単価（税抜）
  * quantity
  商品ごとの数量
* order_date
  注文日時（yyyy-mm-dd hh:mm:ss+0900）
