# PUT /api/v1/stock
商品の在庫に変動があった場合に叩いていただくAPI。

## リクエストパラメータ

| Name          | Description                                                 |
|---------------|-------------------------------------------------------------|
| jancode | JAN CODE（jancode/sku_codeとどちらか必須） |
| sku_code | 商品SKUコード（jancode/sku_codeとどちらか必須） |
| stock | 在庫数（必須） |

## レスポンス例
正常時HTTPコード204を返します

## エラーレスポンス例
