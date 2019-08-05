---
description: 上海支付寶
---

# 上海英特拉支付寶對接API

##  提交地址

* 測試機提交地址:[https://o2o-t.scsb.com.t](https://o2o-t.scsb.com.tw/alipay/api%20)w/[alipay/api ](https://o2o-t.scsb.com.tw/alipay/api%20)
* 正式機提交地址:[https://o2o.scsb.com.tw/alipay/api ](https://o2o-t.scsb.com.tw/alipay/api%20)

## 正掃

{% hint style="info" %}
發起支付寶正掃交易
{% endhint %}

#### Request

| 參數 | 型態 | 必填 | 備註 |
| :--- | :--- | :--- | :--- |
| service | String | Y | preCreate 固定值 |
| mchId | String  | Y | 支付寶付款帳號 ex:000123456780002 |
| createTime | String | Y | 提交時間 ex:20181226093032 |
| request | String | Y |  |
| outTradeNo | String | Y | 訂單號 |
| subject | String | Y | 商品描述 |
| totalFee | String  | Y | 金額 單位分 |
| currency | String | Y | 幣別 ex:TWD 台幣 |
| transCurrency | String  | Y | 交易幣別 ex:TWD |
| extendParams | String | Y | 拓展參數\(以下參數詳細說明請見支付寶官網說明\) |
| secondary\_merchant\_name | String | Y | 二級商家名 |
| secondary\_merchant\_id | String | Y | 二級商家編號 |
| secondary\_merchant\_industry | String | Y | 行業方類 由支付寶指定 |
| store\_id | String | Y | 商家id |
| store\_name | String | Y | 商家名 |
| terminal\_id | String | Y | 裝置id |

```text
{
"service":"preCreate",
"mchId":"000123456780002",
"createTime":"20181226093032",
"request":
    {
    "outTradeNo":"010001101",
    "subject":"金額100",
    "totalFee":"500",
    "currency":"TWD",
    "transCurrency":"TWD",
    "extendParams":{
        "secondary_merchant_name":"Lotte",
        "secondary_merchant_id":"123",
        "secondary_merchant_industry":"5812",
        "store_id":"A101",
        "store_name":"McDonald in 966 3rdAve, NewYork",
        "terminal_id":"212133131"
        }
    }
}
```

Response

| 參數 | 型態 | 必填 | 備註 |
| :--- | :--- | :--- | :--- |
| statusCode | String | Y | 0000 成功 |
| statusDesc | String  | Y | SUCCESS 成功 |
| service | String | Y | 提交時間 ex:20181226093032 |
| mchId | String | Y |  |
| sign | String | Y | 簽名 |
| responseTime | String | Y | 回應時間 |
| response | String  | Y |  |
| resultCode | String | Y | SUCCESS 成功 |
| outTradeNo | String  | Y | 交易訂單號 |
| voucherType | String | Y | 支付類型 |
| qrCode | String | Y | 支付連結 |
| bigPicUrl | String | Y | 大張圖片地址 |
| picUrl | String | Y | 圖片地址 |
| smallPicUrl | String | Y | 小張圖片地址 |

```text

String parseJS eval
{
"statusCode":"0000",
"statusDesc":"SUCCESS",
"service":"preCreate",
"mchId":"000123456780002",
"sign":"Y4UjDMTUbCGXGLMh4Uj8xqKV5rxBwwaRzS9K5aKFrPkHDY6hAVNaAClYcs6T6x8GrB+xytgHR1/MLyuAvKHW5VeeeXjN6bBObh3oiQ+cYQei+ndHul/nqbePEE2P35LrLHWE9c5uZ7+61aWxdWVJtAUgzXsMpObqayYP+S4qa78=",
"responseTime":"20181226093038",
"response":
    {
    "resultCode":"SUCCESS",
    "outTradeNo":"010001101",
    "voucherType":"qrcode",
    "qrCode":"https://qr.alipay.com/bax03823fcsbfzxcdbvq00fa",
    "bigPicUrl":"http://mobilecodec.alipaydev.com/show.htm?code=bax03823fcsbfzxcdbvq00fa&picSize=L",
    "picUrl":"http://mobilecodec.alipaydev.com/show.htm?code=bax03823fcsbfzxcdbvq00fa&picSize=M",
    "smallPicUrl":"http://mobilecodec.alipaydev.com/show.htm?code=bax03823fcsbfzxcdbvq00fa&picSize=S"
    }
}
```

## 條型碼/反掃

{% hint style="info" %}
發起條紋碼/反掃交易
{% endhint %}

Request

| 參數 | 型態 | 必填 | 備註 |
| :--- | :--- | :--- | :--- |
| service | String | Y | spotPay固定值 |
| mchId | String  | Y | 支付寶付款帳號 ex:000123456780002 |
| createTime | String | Y | 提交時間 ex:20181226093032 |
| request | String | Y |  |
| outTradeNo | String | Y | 訂單號 |
| transName | String | Y | 商品描述 |
| totalFee | String  | Y | 金額 單位分 |
| currency | String | Y | 幣別 ex:TWD 台幣 |
| buyerIdentityCode | String  | Y | 付款人條紋辨識碼 18位 |
| identityCodeType | String | Y | barcode 固定值 |
| extendParams | String | Y |  |
| secondary\_merchant\_name | String | Y | 二級商家名 |
| secondary\_merchant\_id | String | Y | 二級商家編號 |
| secondary\_merchant\_industry | String | Y | 行業方類 由支付寶指定 |
| store\_id | String | Y | 商家id |
| store\_name | String | Y | 商家名 |
| terminal\_id | String | Y | 裝置id |

```text
{
"service":"spotPay",
"mchId":"000123456780002",
"createTime":"20181226093233",
"request":{
        "transName":"金額300",
        "outTradeNo":"0000603",
        "currency":"TWD",
        "totalFee":"1",
        "buyerIdentityCode":"28570016633604203",
        "identityCodeType":"barcode",
        "extendParams":{
                "secondary_merchant_name":"Lotte",
                "secondary_merchant_id":"123",
                "secondary_merchant_industry":"5812",
                "store_id":"A101",
                "store_name":"McDonald in 966 3rdAve, NewYork",
                "terminal_id":"212133131"
        }
    }
}
```

Response

| 參數 | 型態 | 必填 | 備註 |
| :--- | :--- | :--- | :--- |
| statusCode | String | Y | 0000 成功 |
| statusDesc | String  | Y | SUCCESS 成功 |
| service | String | Y | spotPay |
| sign | String | Y | 簽名 |
| responseTime | String | Y | 回應時間 |
| response | String  | Y |  |
| resultCode | String | Y | SUCCESS 成功 |
| outTradeNo | String  | Y | 交易訂單號 |
| alipayBuyerLoginId | String | Y | 支付寶買家登入帳號 |
| alipayBuyerUserId | String | Y | 支付寶買家帳號 |
| alipayPayTime | String | Y | 支付寶交易時間 |
| alipayTransId | String | Y | 交易單號 |
| currency | String | Y | 結算幣別 |
| transAmount | String | Y | 標價幣別對應的訂單金額 |
| exchangeRate | String | Y | 匯率 |
| transAmountCny | String | Y | 標價幣別 |

```text
{
"statusCode":"0000",
"statusDesc":"SUCCESS",
"service":"spotPay",
"mchId":"000123456780002",
"sign":"IHQzdIiM1V9mGdNrtGTpMZFdUx+K/xsxVf1hE7ZxB8aMPLS50AXJcV/9CN7I7TVWuk7kI+e9QuyZ32xpCAKWeEqHn+cPVrV9pHp2TKOVhl0NaMLf7cfuSTgSs+0Ww1VXel+HpzXL73Nnt2HA3+fQbf/ECHn67iXGCeSCse8J6eY=",
"responseTime":"20181226092838",
"response":
    {
    "resultCode":"SUCCESS",
    "alipayBuyerLoginId":"cnb*@alitest.*",
    "alipayBuyerUserId":"2088622905305572",
    "outTradeNo":"0000603",
    "alipayPayTime":"20181226093346",
    "alipayTransId":"2018122622001405570500694711",
    "currency":"USD",
    "transAmount":"1.00",
    "exchangeRate":"6.64640000",
    "transAmountCny":"0.20"
    }
}
```



## 查詢

{% hint style="info" %}
發起查詢
{% endhint %}

Request

| 參數 | 型態 | 必填 | 備註 |
| :--- | :--- | :--- | :--- |
| service | String | Y | query固定值 |
| mchId | String  | Y | 支付寶付款帳號 ex:000123456780002 |
| createTime | String | Y | 提交時間 ex:20181226093032 |
| request | String | Y |  |
| outTradeNo | String | Y | 訂單號  |

```text
{
"service":"query",
"mchId":"000123456780002",
"createTime":"20181226093117",
    "request":{
    "outTradeNo":"'0000151'"
    }
}
```

Response

| 參數 | 型態 | 必填 | 備註 |
| :--- | :--- | :--- | :--- |
| statusCode | String | Y | 0000 成功 |
| statusDesc | String  | Y | SUCCESS 成功 |
| service | String | Y | query |
| mchId | String | Y | 支付寶付款帳號 |
| sign | String | Y | 簽名 |
| responseTime | String | Y | 回應時間 |
| response | String  | Y |  |
| resultCode | String | Y | SUCCESS 成功 |
| outTradeNo | String  | Y | 交易訂單號 |
| alipayTransStatus | String | Y | TRADE\_CLOSED |
| alipayBuyerLoginId | String | Y | cnb_@alitest._ |
| alipayBuyerUserId | String | Y | 支付寶買家帳號 |
| alipayPayTime | String | Y | 支付寶交易時間 |
| alipayTransId | String | Y | 交易單號 ex:2018092621001004570500321157 |
| currency | String | Y | 結算幣別 ex:USD |
| transAmount | String | Y | 標價幣別對應的訂單金額 |
| exchangeRate | String | Y | 匯率 |
| transAmountCny | String | Y | 標價幣別 |

```text
{
"statusCode":"0000",
"statusDesc":"SUCCESS",
"service":"query",
"mchId":"000123456780002",
"sign":"lDYP6c22wGtx+A7aMYQtxwkoNBmQz0hrKFcK3yAkhaJLlmyVSLm7XJDwUvTBtDoOsaczOFEAiJTA5Dwbfe+V5/dwl+wwjFNh3bSltyIpPoIbxdZ1KcSQXbzzjVKB7QpGNM+l4IUKaFq7b1ULi+uWUwMbJ9+bnVBoDAMmuuePqYc=",
"responseTime":"20181226093118",
"response":{
    "resultCode":"SUCCESS",
    "alipayTransStatus":"TRADE_CLOSED",
    "alipayBuyerLoginId":"cnb*@alitest.*",
    "alipayBuyerUserId":"2088622905305572",
    "outTradeNo":"0000151",
    "alipayTransId":"2018092621001004570500321157",
    "alipayPayTime":"20180926154107",
    "currency":"USD",
    "transAmount":"3.35",
    "exchangeRate":"6.64640000",
    "transAmountCny":"22.27"
    }
}
```

## 退款

{% hint style="info" %}
發起退款
{% endhint %}

Request

| 參數 | 型態 | 必填 | 備註 |
| :--- | :--- | :--- | :--- |
| service | String | Y | refund固定值 |
| mchId | String  | Y | 支付寶付款帳號 ex:000123456780002 |
| createTime | String | Y | 提交時間 ex:20181226093032 |
| request | String | Y |  |
| outTradeNo | String | Y | 訂單號  |
| partnerRefundId | String | Y | 退款商戶 r2221111901 |
| refundAmount | String | Y | 退款金額 單位分 |
| currency | String | Y | 退款幣別 |

```text
{
"service":"refund",
"mchId":"222111444990001",
"createTime":"20180710120000",
"request":{
    "outTradeNo":"'2221111901'",
    "partnerRefundId":"r2221111901",
    "refundAmount":"3000",
    "currency":"TWD"
    }
}
```

Response

| 參數 | 型態 | 必填 | 備註 |
| :--- | :--- | :--- | :--- |
| statusCode | String | Y | 0000 成功 |
| statusDesc | String  | Y | SUCCESS 成功 |
| service | String | Y | refund |
| mchId | String | Y | 支付寶付款帳號 |
| sign | String | Y | 簽名 |
| responseTime | String | Y | 回應時間 |
| response | String  | Y |  |
| resultCode | String | Y | SUCCESS 成功 |
| outTradeNo | String  | Y | 交易訂單號 |
| partnerRefundId | String | Y | 退款商戶號 |
| alipayTransId | String | Y | 交易單號 ex:2018092621001004570500321157 |
| currency | String | Y | 結算幣別 ex:USD |
| refundAmount | String | Y | 標價幣別對應的訂單金額 |
| exchangeRate | String | Y | 匯率 |
| refundAmountCny | String | Y | 標價幣別 |

```text
{
"statusCode":"0000",
"statusDesc":"SUCCESS",
"service":"refund",
"mchId":"222111444990001",
"sign":"QeT+P7UbdJxmlIculN7ouqIsql1wh6cVl/KhkvbbjkNmspbJozeu4FNawdp1hIs6MfBZIKGPIeUv0EQNPLgts4BvANksm+NCR6yhIMEgoRR4T3Q7qbfPYhKH0Z7XPGFEeYPDTFH+wDRl8WF62BdE/QbFBcbiQKXZ1CTn13FkiuI=",
"responseTime":"20190108151303",
"response":{
    "resultCode":"SUCCESS",
    "outTradeNo":"2221111901",
    "alipayTransId":"2018111922001405570500529427",
    "partnerRefundId":"r2221111901",
    "refundAmount":"3000",
    "currency":"USD",
    "exchangeRate":"6.64640000",
    "refundAmountCny":"667.76"
    }
}
```

支付寶相關參數詳細說明,請查官方正式文件說明

























