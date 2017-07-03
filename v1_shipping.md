# POST /api/v1/shipping
発送情報を通知

## リクエストパラメータ

| Name          | Description                                                 |
|---------------|-------------------------------------------------------------|
| order_code | 弊社が付与するオーダーをユニークにするID（必須） |
| jancode |1つのOrder_id内に含まれる商品のJancode(jancode/sku_codeどちらか必須) |
| sku_code | 1つのOrder_id内に含まれる商品のSKUコード(jancode/sku_codeどちらか必須) |
| quantity | 商品ごとの数量（必須） |
| shipping_date | 発送時刻 yyyy-mm-dd hh:mm:ss　（必須） |
| shipping_number | 発送時追跡番号(伝票番号)（任意） |

## レスポンス例
正常時HTTPコード201を返します

## エラーレスポンス例
