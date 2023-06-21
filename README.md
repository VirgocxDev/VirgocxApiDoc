# Virgocx API DOCS

### Get API Authorization

Please contact us to get your apiKey and apiSecret.
Note: Pay attention that these two keys are related to your account security. So keep them securely.
> Public interfaces do not need signatures. Request parameters of all interfaces which need signature must contain sign parameters.

> apiKey: private api key provided by VirgoCX.

> apiSecret: private api secret provided by VirgoCX.

```
Signature rules, as example of placing order interface:
original parameters list ==>{apiKey sign symbol category type price qty}
update parameters list ==>{apiKey apiSecret symbol category type price qty},remove sign and add apiSecret into this list

step-1:Sort the update parameters list by initial. 
{
    "apiKey":"AAAAA",
    "apiSecret":"BBBBB",
    "category":1,
    "price":9000.1,
    "qty":1.2,
    "symbol":"BTC/CAD",
    "type":1
}

step-2:Generate the character string by putting them together. 
Get: AAAAABBBBB19000.11.2BTC/CAD1

step-3:Execute MD5 algorithm. 
md5(AAAAABBBBB19000.11.2BTC/CAD1)
Get: b60743ad70bad7d1fc47777c0d58604e

step-4:Final parameters list used to call https://virgocx.ca/api/member/addOrder.
{
    "symbol":"BTC/CAD",
    "category":1,
    "type":1,
    "price":9000.1,
    "qty":1.2,
    "apiKey":"AAAAA",
    "sign":"b60743ad70bad7d1fc47777c0d58604e"
}
```


### 1. K-line Data (candlestick chart)

<br>

#### URL:

> https://virgocx.ca/api/market/history/kline

#### Request Method:

> GET

<br>

#### Request Parameters:

| Parameter Name | Required | Type    | Description                                                                                                                      |
|----------------|----------|---------|----------------------------------------------------------------------------------------------------------------------------------|
| symbol         | Yes      | String  | Trading pairs,for example: ETH/CAD                                                                                               |
| period         | Yes      | Integer | K-Line Type (1 minutes-1, 5 minutes-5,10 minutes-10,30 minutes-30,1hr-60,4hrs-240,1day-1440,5days-7200,1week-10080,1month-43200) |

<br>


### Request Example:
> https://virgocx.ca/api/market/history/kline?symbol=ETH/CAD&period=43200

### Response Example:
```

{
    "code": 0,
    "msg": "success",
    "data": [
        {
            "id": 85665,
            "country": 1,
            "marketId": 25,
            "open": 401.0,
            "high": 475.95,
            "low": 360.65,
            "close": 388.3,
            "createTime": 1559318400000
        },
        {
            "id": 408678,
            "country": 1,
            "marketId": 25,
            "open": 387.06,
            "high": 416.59,
            "low": 252.5,
            "close": 285.49,
            "createTime": 1561910400000
        },
        {
            "id": 806012,
            "country": 1,
            "marketId": 25,
            "open": 285.72,
            "high": 315.69,
            "low": 219.61,
            "close": 223.87,
            "createTime": 1564588800000
        },
        {
            "id": 1345976,
            "country": 1,
            "marketId": 25,
            "open": 223.89,
            "high": 418.8,
            "low": 202.23,
            "close": 237.32,
            "createTime": 1567267200000
        },
        {
            "id": 1960838,
            "country": 1,
            "marketId": 25,
            "open": 237.13,
            "high": 259.89,
            "low": 208.99,
            "close": 239.54,
            "createTime": 1569859200000
        },
        {
            "id": 2641817,
            "country": 1,
            "marketId": 25,
            "open": 239.61,
            "high": 255.87,
            "low": 175.78,
            "close": 201.8,
            "createTime": 1572537600000
        },
        {
            "id": 3369813,
            "country": 1,
            "marketId": 25,
            "open": 201.56,
            "high": 202.98,
            "low": 152.79,
            "close": 167.82,
            "createTime": 1575129600000
        },
        {
            "id": 3848988,
            "country": 1,
            "marketId": 25,
            "open": 167.91,
            "high": 246.32,
            "low": 162.72,
            "close": 237.77,
            "createTime": 1577808000000
        },
        {
            "id": 4070825,
            "country": 1,
            "marketId": 25,
            "open": 237.82,
            "high": 382.72,
            "low": 234.92,
            "close": 301.2,
            "createTime": 1580486400000
        },
        {
            "id": 4284913,
            "country": 1,
            "marketId": 25,
            "open": 300.04,
            "high": 309.66,
            "low": 145.0,
            "close": 187.84,
            "createTime": 1582992000000
        },
        {
            "id": 4633451,
            "country": 1,
            "marketId": 25,
            "open": 187.92,
            "high": 315.15,
            "low": 183.41,
            "close": 289.99,
            "createTime": 1585670400000
        },
        {
            "id": 4996227,
            "country": 1,
            "marketId": 25,
            "open": 289.49,
            "high": 339.67,
            "low": 247.86,
            "close": 321.68,
            "createTime": 1588262400000
        },
        {
            "id": 5347054,
            "country": 1,
            "marketId": 25,
            "open": 321.04,
            "high": 342.42,
            "low": 296.0,
            "close": 307.68,
            "createTime": 1590940800000
        },
        {
            "id": 5709609,
            "country": 1,
            "marketId": 25,
            "open": 307.92,
            "high": 466.95,
            "low": 303.03,
            "close": 461.41,
            "createTime": 1593532800000
        },
        {
            "id": 6063986,
            "country": 1,
            "marketId": 25,
            "open": 496.65,
            "high": 588.86,
            "low": 487.03,
            "close": 520.19,
            "createTime": 1596214800000
        },
        {
            "id": 6531682,
            "country": 1,
            "marketId": 25,
            "open": 461.7,
            "high": 527.43,
            "low": 426.45,
            "close": 471.06,
            "createTime": 1598893200000
        },
        {
            "id": 7073396,
            "country": 1,
            "marketId": 25,
            "open": 470.08,
            "high": 552.09,
            "low": 443.9,
            "close": 543.83,
            "createTime": 1601485200000
        },
        {
            "id": 7568326,
            "country": 1,
            "marketId": 25,
            "open": 518.81,
            "high": 810.71,
            "low": 493.82,
            "close": 688.33,
            "createTime": 1604163600000
        },
        {
            "id": 8100966,
            "country": 1,
            "marketId": 25,
            "open": 762.37,
            "high": 848.59,
            "low": 687.3,
            "close": 808.68,
            "createTime": 1606755600000
        },
        {
            "id": 8711518,
            "country": 1,
            "marketId": 25,
            "open": 1169.55,
            "high": 1828.36,
            "low": 1169.55,
            "close": 1566.82,
            "createTime": 1609434000000
        },
        {
            "id": 9318087,
            "country": 1,
            "marketId": 25,
            "open": 1674.46,
            "high": 2572.31,
            "low": 1640.68,
            "close": 2572.31,
            "createTime": 1612112400000
        }
    ],
    "success": true
}
```

#### Response Parameters:

| Parameter Name | Type    | Description          |
|----------------|---------|----------------------|
| id             | Integer | K-Line record id     |
| country        | Integer | Country id, Canada:1 |
| marketId       | Integer | Market id            |
| open           | Decimal | Market open price    |
| high           | Decimal | Highest market price |
| low            | Decimal | Lowest market price  |
| close          | Decimal | Market close price   |
| createTime     | Date    | K-Line create Time   |

---

### 2. Ticker Matching

<br>

#### URL:

> https://virgocx.ca/api/market/detail/merged

#### Request Method:

> GET

<br>

#### Request Parameters:

| Parameter Name | Required | Type   | Description                                                               |
|----------------|----------|--------|---------------------------------------------------------------------------|
| symbol         | Yes      | String | "/" needs to be added between the Market name and the Coin name (ETH/CAD) |

<br>

#### Request Example:
> https://virgocx.ca/api/market/detail/merged?symbol=ETH/CAD


### Response Example:
```
{
    "code": 0,
    "msg": "success",
    "data": {
        "symbol": "ETH/CAD",
        "last": "2400.24",
        "minTotal": 5.00000000,
        "volume": "0",
        "high": "2401.78",
        "low": "2389.47",
        "Ask": 2438.75,
        "priceDecimals": 2,
        "qtyDecimals": 3,
        "id": 25,
        "Bid": 2361.73,
        "changeRate": "+0.26%",
        "open": "2393.82",
        "minQty": 0.00200000
    },
    "success": true
}
```
#### Response Parameters:

| Parameter Name | Type    | Description                          |
|----------------|---------|--------------------------------------|
| volume         | String  | Volume                               |
| symbol         | String  | Trading pairs                        |
| high           | String  | Highest market price                 |
| last           | String  | Market close price                   |
| low            | String  | Lowest market price                  |
| bid            | Decimal | Virgocx bid price                    |
| ask            | Decimal | Virgocx ask price                    |
| id             | Integer | Market id                            |
| changeRate     | String  | Change rate in last 24 hours         |
| open           | String  | Market open price                    |
| minQty         | Decimal | Minimum order quantity               |
| priceDecimals  | Integer | The maximum accuracy of the price    |
| qtyDecimals    | Integer | The maximum accuracy of the quantity |
| minTotal       | Decimal | Minimum order amount                 |
---

### 3. The latest tickers of all trading pairs

<br>

#### URL:

> https://virgocx.ca/api/market/tickers

#### Request method:

> GET

<br>

#### Request Parameters: NO

<br>

#### Response example
```
{
    "code": 0,
    "msg": "success",
    "data": [
        {
            "symbol": "BTC/CAD",
            "last": "38128.13",
            "minTotal": 5.00000000,
            "volume": "0",
            "high": "38128.27",
            "low": "37897.79",
            "Ask": 38740.83,
            "priceDecimals": 2,
            "qtyDecimals": 4,
            "id": 24,
            "Bid": 37515.44,
            "changeRate": "+0.49%",
            "open": "37938.54",
            "minQty": 0.00018000
        },
        {
            "symbol": "ETH/CAD",
            "last": "2401.28",
            "minTotal": 5.00000000,
            "volume": "0",
            "high": "2401.78",
            "low": "2389.47",
            "Ask": 2439.75,
            "priceDecimals": 2,
            "qtyDecimals": 3,
            "id": 25,
            "Bid": 2362.81,
            "changeRate": "+0.31%",
            "open": "2393.82",
            "minQty": 0.00200000
        },
        {
            "symbol": "USDC/CAD",
            "last": "1.3214",
            "minTotal": 5.00000000,
            "volume": "0",
            "high": "1.3220",
            "low": "1.3210",
            "Ask": 1.3426,
            "priceDecimals": 4,
            "qtyDecimals": 4,
            "id": 55,
            "Bid": 1.3002,
            "changeRate": "-0.04%",
            "open": "1.3220",
            "minQty": 4.00000000
        },
        {
            "symbol": "ADA/CAD",
            "last": "0.368348",
            "minTotal": 5.00000000,
            "volume": "0",
            "high": "0.371880",
            "low": "0.367125",
            "Ask": 0.374329,
            "priceDecimals": 6,
            "qtyDecimals": 2,
            "id": 68,
            "Bid": 0.362368,
            "changeRate": "-0.77%",
            "open": "0.371239",
            "minQty": 7.50000000
        },
        {
            "symbol": "SOL/CAD",
            "last": "22.24",
            "minTotal": 5.00000000,
            "volume": "0",
            "high": "22.24",
            "low": "22.07",
            "Ask": 22.60,
            "priceDecimals": 2,
            "qtyDecimals": 6,
            "id": 75,
            "Bid": 21.88,
            "changeRate": "+0.49%",
            "open": "22.13",
            "minQty": 0.12000000
        },
        {
            "symbol": "XLM/CAD",
            "last": "0.110742",
            "minTotal": 5.00000000,
            "volume": "0",
            "high": "0.110756",
            "low": "0.110328",
            "Ask": 0.112551,
            "priceDecimals": 6,
            "qtyDecimals": 4,
            "id": 56,
            "Bid": 0.108933,
            "changeRate": "+0.06%",
            "open": "0.110667",
            "minQty": 30.00000000
        },
        {
            "symbol": "MANA/CAD",
            "last": "0.48484",
            "minTotal": 5.00000000,
            "volume": "0",
            "high": "0.48698",
            "low": "0.47754",
            "Ask": 0.49375,
            "priceDecimals": 5,
            "qtyDecimals": 5,
            "id": 73,
            "Bid": 0.47594,
            "changeRate": "+1.52%",
            "open": "0.47756",
            "minQty": 4.70000000
        },
        {
            "symbol": "ETC/CAD",
            "last": "21.190",
            "minTotal": 5.00000000,
            "volume": "0",
            "high": "21.219",
            "low": "21.150",
            "Ask": 21.578,
            "priceDecimals": 3,
            "qtyDecimals": 6,
            "id": 81,
            "Bid": 20.802,
            "changeRate": "-0.01%",
            "open": "21.194",
            "minQty": 0.18000000
        },
        {
            "symbol": "HBAR/CAD",
            "last": "0.06588",
            "minTotal": 5.00000000,
            "volume": "0",
            "high": "0.06593",
            "low": "0.06559",
            "Ask": 0.06715,
            "priceDecimals": 5,
            "qtyDecimals": 1,
            "id": 115,
            "Bid": 0.06462,
            "changeRate": "-0.01%",
            "open": "0.06589",
            "minQty": 54.00000000
        },
        {
            "symbol": "ICP/CAD",
            "last": "5.522",
            "minTotal": 5.00000000,
            "volume": "0",
            "high": "5.554",
            "low": "5.508",
            "Ask": 5.631,
            "priceDecimals": 3,
            "qtyDecimals": 6,
            "id": 131,
            "Bid": 5.414,
            "changeRate": "-0.55%",
            "open": "5.553",
            "minQty": 0.52000000
        },
        {
            "symbol": "SAND/CAD",
            "last": "0.5474",
            "minTotal": 5.00000000,
            "volume": "0",
            "high": "0.5475",
            "low": "0.5428",
            "Ask": 0.5575,
            "priceDecimals": 4,
            "qtyDecimals": 5,
            "id": 94,
            "Bid": 0.5373,
            "changeRate": "+0.23%",
            "open": "0.5461",
            "minQty": 3.90000000
        }
    ],
    "success": true
}
```

#### Response Parameters:

| Parameter Name | Type    | Description                          |
|----------------|---------|--------------------------------------|
| volume         | String  | Volume                               |
| symbol         | String  | Trading pairs                        |
| high           | String  | Highest market price                 |
| last           | String  | Market close price                   |
| low            | String  | Lowest market price                  |
| bid            | Decimal | Virgocx bid price                    |
| ask            | Decimal | Virgocx ask price                    |
| id             | Integer | Market Id                            |
| changeRate     | String  | Change rate in last 24 hours         |
| open           | String  | Market open price                    |
| minQty         | Decimal | Minimum order quantity               |
| priceDecimals  | Integer | The maximum accuracy of the price    |
| qtyDecimals    | Integer | The maximum accuracy of the quantity |
| minTotal       | Decimal | Minimum order amount                 |

---
### 4. Account information

<br>

#### URL:

> https://virgocx.ca/api/member/accounts

#### Request Method:

> GET

<br>

#### Request Parameters:

| Parameter Name | Required | Type   | Description         |
|----------------|----------|--------|---------------------|
| apiKey         | Yes      | String | Api Key             |
| sign           | Yes      | String | Parameter signature |

#### Request Example:
> https://virgocx.ca/api/member/accounts?apiKey=AAA&sign=BBB
<br>

>AAA: Your API key
 
>BBB: Sign calculated by MD5,for example:b60743ad70bad7d1fc47777c0d58604e

#### Response example:
```
{
    "code": 0,
    "msg": "success",
    "data": [
        {
            "total": 0.0006,
            "balance": 0.0006,
            "coinName": "ETH",
            "freezingBalance": 0.0000
        },
        {
            "total": 0.0031,
            "balance": 0.0031,
            "coinName": "BTC",
            "freezingBalance": 0.0000
        },
        {
            "total": 0.0000,
            "balance": 0.0000,
            "coinName": "USDT",
            "freezingBalance": 0.0000
        },
        {
            "total": 5.0086,
            "balance": 5.0086,
            "coinName": "CAD",
            "freezingBalance": 0.0000
        }
    ],
    "success": true
}
```

#### Response Parameters:

| Parameter Name  | Type    | Description                            |
|-----------------|---------|----------------------------------------|
| freezingBalance | Decimal | Frozen balance                         |
| total           | Decimal | Total balance(balance+freezingBalance) |
| balance         | Decimal | Balance (available balance)            |
| coinName        | String  | Coin name                              |

---
### 5. Query user orders

<br>

#### URL:

> https://virgocx.ca/api/member/queryOrder

#### Request Method:

> GET

<br>

#### Request Parameters:

| Parameter Name | Required | Type    | Description         |
|----------------|----------|---------|---------------------|
| apiKey         | Yes      | String  | User private key    |
| sign           | Yes      | String  | Parameter signature |
| symbol         | Yes      | String  | Trading pairs       |
| status         | Optional | Integer | Order status        |

#### Request Example:
> https://virgocx.ca/api/member/queryOrder?apiKey=AAA&sign=BBB&symbol=BTC/CAD&status=3

<br>

>AAA: Your API key

>BBB: Sign calculated by MD5,for example:b60743ad70bad7d1fc47777c0d58604e

>status: Hope to search completed orders
#### Response example:
```
{
    "code": 0,
    "msg": "success",
    "data": [
        {
            "total": null,
            "createTime": 1674687750000,
            "price": null,
            "qty": 0.002900000000000000,
            "tradeQty": 0.002900000000000000,
            "id": 5915781451,
            "averagePrice": 30534.990000000000000000,
            "type": 2,
            "direction": 2,
            "tradeTotal": null,
            "status": 3
        },
        {
            "total": null,
            "createTime": 1625036965000,
            "price": 43199.700000000000000000,
            "qty": 0.003000000000000000,
            "tradeQty": 0.003000000000000000,
            "id": 4436825255,
            "averagePrice": 43218.200000000000000000,
            "type": 1,
            "direction": 2,
            "tradeTotal": null,
            "status": 3
        },
        {
            "total": null,
            "createTime": 1625036896000,
            "price": 43622.800000000000000000,
            "qty": 0.001500000000000000,
            "tradeQty": 0.001500000000000000,
            "id": 4436822307,
            "averagePrice": 43589.800000000000000000,
            "type": 1,
            "direction": 1,
            "tradeTotal": null,
            "status": 3
        },
        {
            "total": null,
            "createTime": 1623730191000,
            "price": 49338.800000000000000000,
            "qty": 0.000405300000000000,
            "tradeQty": 0.000405300000000000,
            "id": 4381482507,
            "averagePrice": 49320.200000000000000000,
            "type": 1,
            "direction": 1,
            "tradeTotal": null,
            "status": 3
        }
    ],
    "success": true
}
```

#### Response Parameters:

| Parameter Name | Type    | Description                                                    |
|----------------|---------|----------------------------------------------------------------|
| createTime     | Date    | Order create time                                              |
| price          | Decimal |                                                                |
| qty            | Decimal |                                                                |
| tradeQty       | Decimal |                                                                |
| total          | Decimal |                                                                |
| tradeTotal     | Decimal |                                                                |
| averagePrice   | Decimal | Average price of order                                         |
| id             | Integer | Order id                                                       |
| type           | Integer | Order type, 1 Limit order, 2 Market order, 3 Quick trade order |
| direction      | Integer | 1 Buy, 2 Sell                                                  |
| status         | Integer | -1 Canceled, 0 Placed, 1 Open, 2 Matching, 3 Completed         |
---
### 6. Query completed orders

<br>

#### URL:

> https://virgocx.ca/api/member/queryTrade

#### Request Method:

> GET

<br>

#### Request Parameters:

| Parameter Name | Required | Type    | Description         |
|----------------|----------|---------|---------------------|
| apiKey         | Yes      | String  | User private key    |
| sign           | Yes      | String  | Parameter signature |
| symbol         | Yes      | String  | Trading pairs       |
#### Request example:

> https://virgocx.ca/api/member/queryTrade?apiKey=AAA&sign=BBB&symbol=CCC
<br>

>AAA: Your API key

>BBB: Value of sign

>CCC: Value of symbol

#### Response example with symbol=BTC/CAD:
```
{
    "code": 0,
    "msg": "success",
    "data": [
        {
            "id": "12249370",
            "amount": 88.551471000000000000000000000000,
            "qty": 0.002900000000000000,
            "price": 30534.990000000000000000,
            "type": "sell",
            "createTime": 1674687751
        },
        {
            "id": "12230441",
            "amount": 17.359773890200000000000000000000,
            "qty": 0.000764740000000000,
            "price": 22700.230000000000000000,
            "type": "buy",
            "createTime": 1672336598
        },
        {
            "id": "12080372",
            "amount": 19.999610888400000000000000000000,
            "qty": 0.000497430000000000,
            "price": 40205.880000000000000000,
            "type": "buy",
            "createTime": 1654058408
        },
        {
            "id": "12080370",
            "amount": 19.999912098100000000000000000000,
            "qty": 0.000497330000000000,
            "price": 40214.570000000000000000,
            "type": "buy",
            "createTime": 1654058344
        },
        {
            "id": "12075098",
            "amount": 29.999948340600000000000000000000,
            "qty": 0.000772020000000000,
            "price": 38859.030000000000000000,
            "type": "buy",
            "createTime": 1653450306
        },
        {
            "id": "12075084",
            "amount": 29.999854430600000000000000000000,
            "qty": 0.000774470000000000,
            "price": 38735.980000000000000000,
            "type": "buy",
            "createTime": 1653449766
        },
        {
            "id": "12075022",
            "amount": 99.999653193400000000000000000000,
            "qty": 0.002609770000000000,
            "price": 38317.420000000000000000,
            "type": "buy",
            "createTime": 1653444675
        },
        {
            "id": "11756653",
            "amount": 129.654600000000000000000000000000,
            "qty": 0.003000000000000000,
            "price": 43218.200000000000000000,
            "type": "sell",
            "createTime": 1625036964
        },
        {
            "id": "11756650",
            "amount": 65.384700000000000000000000000000,
            "qty": 0.001500000000000000,
            "price": 43589.800000000000000000,
            "type": "buy",
            "createTime": 1625036895
        },
        {
            "id": "11749196",
            "amount": 19.989477060000000000000000000000,
            "qty": 0.000405300000000000,
            "price": 49320.200000000000000000,
            "type": "buy",
            "createTime": 1623730191
        },
        {
            "id": "11749194",
            "amount": 19.999975968000000000000000000000,
            "qty": 0.000405360000000000,
            "price": 49338.800000000000000000,
            "type": "buy",
            "createTime": 1623730156
        },
        {
            "id": "11746584",
            "amount": 9.999641883000000000000000000000,
            "qty": 0.000243430000000000,
            "price": 41078.100000000000000000,
            "type": "buy",
            "createTime": 1623220058
        },
        {
            "id": "11687269",
            "amount": 30.899671257000000000000000000000,
            "qty": 0.000499170000000000,
            "price": 61902.100000000000000000,
            "type": "buy",
            "createTime": 1619157775
        }
    ],
    "success": true
}
```

#### Response Parameters:

| Parameter Name | Type    | Description                               |
|----------------|---------|-------------------------------------------|
| id             | Integer | Trade Id                                  |
| amount         | Decimal | Total trading value(fiat value),qty*price |
| qty            | Decimal | Total trading amount(crypto)              |
| price          | Decimal | Trading price                             |
| type           | String  | buy or sell                               |
| createTime     | String  | Completion time String format             |
---
### 7. Place Order

<br>

#### URL:

> https://virgocx.ca/api/member/addOrder

#### Request Method:

> POST

<br>

#### Request Parameters:

| Parameter Name | Required | Type    | Description                                            |
|----------------|----------|---------|--------------------------------------------------------|
| apiKey         | Yes      | String  | User private key                                       |
| sign           | Yes      | String  | Parameter signature                                    |
| symbol         | Yes      | String  | Trading pairs                                          |
| category       | Yes      | Integer | Order Category, 1 Limit, 2 Market Order, 3 Quick Trade |
| type           | Yes      | Integer | Order type, 1 Buy, 2 Sell                              |
| price          | Optional | Decimal | Order price                                            |
| qty            | Optional | Decimal | Value or crypto currency                               |
| total          | Optional | Decimal | Value of Canadian Dollars                              |
| country        | Yes      | Integer | Canada:1                                               |

#### Notes：
>(1) You only need to provide price value in the parameter list when category is limit.

>(2) You only need to provide total value in the parameter list when category is market order or quick trade and type is buy.
>For example, buy value of 100 canadian dollars BTC, value of total is 100. Other combinations of category and type, please provide qty(amount)
>of crypto currency you want to trade.
#### Request example 1(category of limit):

> https://virgocx.ca/api/member/addOrder?apiKey=AAA&symbol=BBB&sign=CCC&category=DDD&qty=EEE&price=FFF&type=GGG&country=HHH
<br>

>AAA: Your API key

>BBB: Value of symbol

>CCC: Value of sign

>DDD: Value of category

>EEE: Value of qty

>FFF: Value of price

>GGG: Value of type

>HHH: Value of country

#### Request example 2(category of market order and type is buy):

> https://virgocx.ca/api/member/addOrder?apiKey=AAA&symbol=BBB&sign=CCC&category=DDD&total=III&type=GGG&country=HHH

>AAA: Your API key

>BBB: Value of symbol

>CCC: Value of sign

>DDD: Value of category

>GGG: Value of type

>HHH: Value of country

>III: Value of canadian dollars

#### Request example 3(category of market order and type is sell):

> https://virgocx.ca/api/member/addOrder?apiKey=AAA&symbol=BBB&sign=CCC&category=DDD&qty=EEE&type=GGG&country=HHH

>AAA: Your API key

>BBB: Value of symbol

>CCC: Value of sign

>DDD: Value of category

>EEE: Value of qty

>GGG: Value of type

>HHH: Value of country

#### Response example:
```
{
    "code": 0,
    "msg": "success",
    "data": {
        "orderId": "812795"
    },
    "success": true
}
```

#### Response Parameters:

| Parameter Name | Type   | Description |
|----------------|--------|-------------|
| orderId        | String | Order Id    |
---

### 8. Cancel Order

<br>

#### URL:

> https://virgocx.ca/api/member/cancelOrder

#### Request Method:

> GET

<br>

#### Request Parameters:

| Parameter Name | Required | Type    | Description         |
|----------------|----------|---------|---------------------|
| apiKey         | Yes      | String  | User private key    |
| sign           | Yes      | String  | Parameter signature |
| id             | Yes      | Integer | Order Id            |

#### Request example:

> https://virgocx.ca/api/member/cancelOrder?apiKey=AAA&sign=BBB&id=CCC
> <br>

>AAA: Your API key

>BBB: Value of sign

>CCC: Value of id(orderId)

#### Response example:
```

{
    "code": 0,
    "msg": "success",
    "data": "Order cancel successfully!",
    "success": true
}
```

#### Response Parameters:NO

### 9. Get discount price(bid && ask) depend on account's tier level

<br>

#### URL:

> https://virgocx.ca/api/member/discountPrice

#### Note:get discount price depend on your account's tier level, for tier level details, you may check your current Reward Tier by visiting https://virgocx.ca/ and logging in to the VirgoCX account.

#### Request Method:

> GET

<br>

#### Request Parameters:

| Parameter Name | Required | Type   | Description                        |
|----------------|----------|--------|------------------------------------|
| apiKey         | Yes      | String | User private key                   |
| sign           | Yes      | String | Parameter signature                |
| symbol         | Optional | String | Trading pairs,for example: ETH/CAD |

#### Request example(1), get discount price of all trading pairs:

> https://virgocx.ca/api/member/discountPrice?apiKey=AAA&sign=BBB
> <br>

>AAA: Your API key

>BBB: Value of sign

#### Request example(2), get discount price of specific trading pair:
> https://virgocx.ca/api/member/discountPrice?apiKey=AAA&symbol=ETH/CAD
> <br>

>AAA: Your API key

>BBB: Value of sign

>CCC: Trading pair name

#### Response example(1):
```
{
    "code": 0,
    "msg": "success",
    "data": [
        {
            "symbol": "BTC/CAD",
            "last": "37978.01",
            "minTotal": 5.00000000,
            "volume": "0",
            "high": "38053.90",
            "low": "37897.79",
            "Ask": 38585.72,
            "priceDecimals": 2,
            "qtyDecimals": 4,
            "id": 24,
            "Bid": 37370.29,
            "changeRate": "+0.10%",
            "open": "37938.54",
            "minQty": 0.00018000
        },
        {
            "symbol": "ETH/CAD",
            "last": "2396.51",
            "minTotal": 5.00000000,
            "volume": "0",
            "high": "2398.31",
            "low": "2389.47",
            "Ask": 2434.85,
            "priceDecimals": 2,
            "qtyDecimals": 3,
            "id": 25,
            "Bid": 2358.15,
            "changeRate": "+0.11%",
            "open": "2393.82",
            "minQty": 0.00200000
        },
        {
            "symbol": "USDC/CAD",
            "last": "1.3213",
            "minTotal": 5.00000000,
            "volume": "0",
            "high": "1.3220",
            "low": "1.3212",
            "Ask": 1.3424,
            "priceDecimals": 4,
            "qtyDecimals": 4,
            "id": 55,
            "Bid": 1.3000,
            "changeRate": "-0.05%",
            "open": "1.3220",
            "minQty": 4.00000000
        },
        {
            "symbol": "ADA/CAD",
            "last": "0.368747",
            "minTotal": 5.00000000,
            "volume": "0",
            "high": "0.371880",
            "low": "0.368474",
            "Ask": 0.374725,
            "priceDecimals": 6,
            "qtyDecimals": 2,
            "id": 68,
            "Bid": 0.362767,
            "changeRate": "-0.67%",
            "open": "0.371239",
            "minQty": 7.50000000
        },
        {
            "symbol": "SOL/CAD",
            "last": "22.13",
            "minTotal": 5.00000000,
            "volume": "0",
            "high": "22.17",
            "low": "22.07",
            "Ask": 22.48,
            "priceDecimals": 2,
            "qtyDecimals": 6,
            "id": 75,
            "Bid": 21.76,
            "changeRate": "+0.00%",
            "open": "22.13",
            "minQty": 0.12000000
        },
        {
            "symbol": "AVAX/CAD",
            "last": "16.25",
            "minTotal": 5.00000000,
            "volume": "0",
            "high": "16.26",
            "low": "16.19",
            "Ask": 16.51,
            "priceDecimals": 2,
            "qtyDecimals": 6,
            "id": 79,
            "Bid": 15.97,
            "changeRate": "+0.06%",
            "open": "16.24",
            "minQty": 0.14000000
        },
        {
            "symbol": "DOT/CAD",
            "last": "6.2197",
            "minTotal": 5.00000000,
            "volume": "0",
            "high": "6.2479",
            "low": "6.2175",
            "Ask": 6.3205,
            "priceDecimals": 4,
            "qtyDecimals": 3,
            "id": 69,
            "Bid": 6.1187,
            "changeRate": "-0.40%",
            "open": "6.2452",
            "minQty": 0.45000000
        },
        {
            "symbol": "DOGE/CAD",
            "last": "0.0844076",
            "minTotal": 5.00000000,
            "volume": "0",
            "high": "0.0845970",
            "low": "0.0842134",
            "Ask": 0.0857643,
            "priceDecimals": 7,
            "qtyDecimals": 1,
            "id": 57,
            "Bid": 0.0830507,
            "changeRate": "-0.22%",
            "open": "0.0845964",
            "minQty": 60.00000000
        },
        {
            "symbol": "SHIB/CAD",
            "last": "0.00000978",
            "minTotal": 5.00000000,
            "volume": "0",
            "high": "0.00000978",
            "low": "0.00000973",
            "Ask": 0.00000993,
            "priceDecimals": 8,
            "qtyDecimals": 0,
            "id": 76,
            "Bid": 0.00000961,
            "changeRate": "+0.30%",
            "open": "0.00000975",
            "minQty": 342745.00000000
        },
    ],
    "success": true
}
```
#### Response example(2):
```
{
    "code": 0,
    "msg": "success",
    "data": [
        {
            "symbol": "ETH/CAD",
            "last": "2399.25",
            "minTotal": 5.00000000,
            "volume": "0",
            "high": "2401.52",
            "low": "2389.47",
            "Ask": 2437.64,
            "priceDecimals": 2,
            "qtyDecimals": 3,
            "id": 25,
            "Bid": 2360.85,
            "changeRate": "+0.22%",
            "open": "2393.82",
            "minQty": 0.00200000
        }
    ],
    "success": true
}
```
#### Response Parameters:

| Parameter Name | Type    | Description                          |
|----------------|---------|--------------------------------------|
| volume         | String  | Volume                               |
| symbol         | String  | Trading pairs                        |
| high           | String  | Highest market price                 |
| last           | String  | Market close price                   |
| low            | String  | Lowest market price                  |
| bid            | Decimal | Virgocx bid price                    |
| ask            | Decimal | Virgocx ask price                    |
| id             | Integer | Market id                            |
| changeRate     | String  | Change rate in past 24 hours         |
| open           | String  | Market open price                    |
| minQty         | Decimal | Minimum order quantity               |
| priceDecimals  | Integer | The maximum accuracy of the price    |
| qtyDecimals    | Integer | The maximum accuracy of the quantity |
| minTotal       | Decimal | Minimum order amount                 |

---
