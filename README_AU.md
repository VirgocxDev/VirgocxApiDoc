# Virgo API DOCS

### Get API Authorization

Please contact us to get your apiKey and apiSecret.
Note: Pay attention that these two keys are related to your account security. So keep them securely.
> Public interfaces do not need signatures. Request parameters of all interfaces which need signature must contain sign parameters.

> apiKey: private api key provided by Virgo.

> apiSecret: private api secret provided by Virgo.

```
Signature rules, as example of placing order interface:
original parameters list ==>{apiKey sign symbol category type price qty}
update parameters list ==>{apiKey apiSecret symbol category type price qty},remove sign and add apiSecret into this list

step-1:Sort the update parameters list by initial. 
{
    "apiKey":"AAAAA",
    "apiSecret":"BBBBB",
    "category":1,
    "country":AU
    "price":100000.00,
    "qty":0.05,
    "symbol":"BTC/AUD",
    "type":1
}

If the first character is same, continue to compare next one,until see the difference,for example, apiKey and apiSecret,
the fourth character is different, character K front of character S, so apiKey is front of apiSecret in the parameter list
when calculate MD5 hash.

step-2:Generate the character string by putting them together. 
Get: AAAAABBBBB19000.11.2BTC/AUD1

step-3:Execute MD5 algorithm. 
md5(AAAAABBBBB1100000.000.05BTC/AUD1)
Get: 84cde2e3ab9d55cf6eedf1dc5497c06d

step-4:Final parameters list used to call https://virgo.co/api/member/addOrder.
{
    "symbol":"BTC/AUD",
    "category":1,
    "type":1,
    "price":100000.00,
    "qty":0.05,
    "apiKey":"AAAAA",
    "sign":"84cde2e3ab9d55cf6eedf1dc5497c06d"
}
```


### 1. K-line Data (candlestick chart)

<br>

#### URL:

> https://virgo.co/api/market/history/kline

#### Request Method:

> GET

<br>

#### Request Parameters:

| Parameter Name | Required | Type    | Description                                                                                                                      |
|----------------|----------|---------|----------------------------------------------------------------------------------------------------------------------------------|
| symbol         | Yes      | String  | Trading pairs,for example: ETH/AUD                                                                                               |
| period         | Yes      | Integer | K-Line Type (1 minutes-1, 5 minutes-5,10 minutes-10,30 minutes-30,1hr-60,4hrs-240,1day-1440,5days-7200,1week-10080,1month-43200) |
| country        | Yes      | String  | Australia, AU                                                                                                                    |

<br>


#### Request Example:
> https://virgo.co/api/market/history/kline?country=AU&symbol=ETH/AUD&period=43200

#### Response Example:
```
{
    "code": 0,
    "msg": "success",
    "data": [
        {
            "id": 59215375,
            "country": 2,
            "marketId": 449,
            "open": 1963.46,
            "high": 2067.38,
            "low": 1951.29,
            "close": 1980.55,
            "createTime": 1661994000000
        },
        {
            "id": 67764183,
            "country": 2,
            "marketId": 449,
            "open": 2051.1,
            "high": 2570.76,
            "low": 1793.27,
            "close": 2456.04,
            "createTime": 1664582520000
        },
        {
            "id": 76158113,
            "country": 2,
            "marketId": 449,
            "open": 2458.97,
            "high": 2592.58,
            "low": 1621.75,
            "close": 1905.68,
            "createTime": 1667260800000
        },
        {
            "id": 84594708,
            "country": 2,
            "marketId": 449,
            "open": 1905.85,
            "high": 1968.5,
            "low": 1719.86,
            "close": 1756.31,
            "createTime": 1669852800000
        },
        {
            "id": 92613415,
            "country": 2,
            "marketId": 449,
            "open": 1756.31,
            "high": 2411.16,
            "low": 1750.33,
            "close": 2249.47,
            "createTime": 1672531200000
        },
        {
            "id": 99804244,
            "country": 2,
            "marketId": 449,
            "open": 2249.49,
            "high": 2532.53,
            "low": 2103.91,
            "close": 2382.64,
            "createTime": 1675209600000
        },
        {
            "id": 108377308,
            "country": 2,
            "marketId": 449,
            "open": 2382.64,
            "high": 2765.72,
            "low": 2081.9,
            "close": 2688.1,
            "createTime": 1677628800000
        },
        {
            "id": 116585598,
            "country": 2,
            "marketId": 449,
            "open": 2688.1,
            "high": 3189.13,
            "low": 2611.67,
            "close": 2838.24,
            "createTime": 1680307200000
        },
        {
            "id": 124887128,
            "country": 2,
            "marketId": 449,
            "open": 2838.45,
            "high": 2985.32,
            "low": 2598.39,
            "close": 2879.79,
            "createTime": 1682899200000
        },
        {
            "id": 133041141,
            "country": 2,
            "marketId": 449,
            "open": 2879.73,
            "high": 2915.41,
            "low": 2377.6,
            "close": 2902.32,
            "createTime": 1685577600000
        },
        {
            "id": 141541750,
            "country": 2,
            "marketId": 449,
            "open": 2902.78,
            "high": 2967.14,
            "low": 2717.15,
            "close": 2763.02,
            "createTime": 1688169600000
        },
        {
            "id": 150035709,
            "country": 2,
            "marketId": 449,
            "open": 2762.96,
            "high": 2867.78,
            "low": 2431.38,
            "close": 2536.71,
            "createTime": 1690848000000
        },
        {
            "id": 158208778,
            "country": 2,
            "marketId": 449,
            "open": 2536.71,
            "high": 2632.04,
            "low": 2383.18,
            "close": 2593.72,
            "createTime": 1693526400000
        },
        {
            "id": 166653157,
            "country": 2,
            "marketId": 449,
            "open": 2593.72,
            "high": 2956.98,
            "low": 2396.62,
            "close": 2866.24,
            "createTime": 1696118400000
        },
        {
            "id": 174857282,
            "country": 2,
            "marketId": 449,
            "open": 2866.24,
            "high": 3358.74,
            "low": 2759.91,
            "close": 3109.02,
            "createTime": 1698796800000
        },
        {
            "id": 183417076,
            "country": 2,
            "marketId": 449,
            "open": 3107.98,
            "high": 3650.83,
            "low": 3093.67,
            "close": 3349.92,
            "createTime": 1701388800000
        },
        {
            "id": 192090803,
            "country": 2,
            "marketId": 449,
            "open": 3349.89,
            "high": 4041.92,
            "low": 3232.02,
            "close": 3479.45,
            "createTime": 1704067200000
        },
        {
            "id": 200346281,
            "country": 2,
            "marketId": 449,
            "open": 3504.25,
            "high": 5279.7,
            "low": 3481.4,
            "close": 5213.06,
            "createTime": 1706745660000
        },
        {
            "id": 209564516,
            "country": 2,
            "marketId": 449,
            "open": 5149.69,
            "high": 6188.87,
            "low": 4687.58,
            "close": 5585.43,
            "createTime": 1709251200000
        },
        {
            "id": 218973592,
            "country": 2,
            "marketId": 449,
            "open": 5585.33,
            "high": 5642.81,
            "low": 4407.3,
            "close": 4649.17,
            "createTime": 1711929600000
        },
        {
            "id": 229901828,
            "country": 2,
            "marketId": 449,
            "open": 4649.17,
            "high": 5968.55,
            "low": 4322.96,
            "close": 5650.99,
            "createTime": 1714521600000
        },
        {
            "id": 241890266,
            "country": 2,
            "marketId": 449,
            "open": 5650.24,
            "high": 5840.73,
            "low": 4867.12,
            "close": 5144.03,
            "createTime": 1717200000000
        },
        {
            "id": 254564692,
            "country": 2,
            "marketId": 449,
            "open": 5143.91,
            "high": 5343.78,
            "low": 4188.22,
            "close": 4933.44,
            "createTime": 1719792000000
        },
        {
            "id": 267212760,
            "country": 2,
            "marketId": 449,
            "open": 4933.25,
            "high": 4955.75,
            "low": 3277.28,
            "close": 3714.49,
            "createTime": 1722470400000
        },
        {
            "id": 279551476,
            "country": 2,
            "marketId": 449,
            "open": 3714.49,
            "high": 3947.19,
            "low": 3223.51,
            "close": 3764.54,
            "createTime": 1725148800000
        },
        {
            "id": 279551478,
            "country": 2,
            "marketId": 449,
            "open": 3764.52,
            "high": 4123.05,
            "low": 3376.5,
            "close": 3825.54,
            "createTime": 1727740800000
        }
    ],
    "success": true
}
```

#### Response Parameters:

| Parameter Name | Type    | Description                                                                                                  |
|----------------|---------|--------------------------------------------------------------------------------------------------------------|
| id             | Integer | K-Line record id                                                                                             |
| country        | Integer | Australia:2                                                                                                  |
| marketId       | Integer | Market id                                                                                                    |
| open           | Decimal | Market open price                                                                                            |
| high           | Decimal | Highest market price                                                                                         |
| low            | Decimal | Lowest market price                                                                                          |
| close          | Decimal | Market close price                                                                                           |
| createTime     | Date    | K-Line create Time, Unix timestamp in milliseconds, representing the exact date and time of the event in UTC |

---

### 2. Ticker Matching

<br>

#### URL:

> https://virgo.co/api/market/detail/merged

#### Request Method:

> GET

<br>

#### Request Parameters:

| Parameter Name | Required | Type   | Description                                                               |
|----------------|----------|--------|---------------------------------------------------------------------------|
| symbol         | Yes      | String | "/" needs to be added between the Market name and the Coin name (ETH/AUD) |
| country        | Yes      | String | Australia, AU                                                             |


<br>

#### Request Example:
> https://virgo.co/api/market/detail/merged?symbol=ETH/AUD&country=AU

#### Response Example:
```
{
    "code": 0,
    "msg": "success",
    "data": {
        "symbol": "ETH/AUD",
        "last": "3829.72",
        "minTotal": 5.00000000,
        "volume": "0",
        "high": "3860.87",
        "low": "3715.81",
        "Ask": 3864.20,
        "priceDecimals": 2,
        "qtyDecimals": 3,
        "id": 449,
        "Bid": 3795.25,
        "changeRate": "+0.27%",
        "open": "3819.40",
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
| Bid            | Decimal | Virgocx bid price                    |
| Ask            | Decimal | Virgocx ask price                    |
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

> https://virgo.co/api/market/tickers

#### Request method:

> GET

<br>

#### Request Parameters:

| Parameter Name | Required | Type   | Description                                                         |
|----------------|----------|--------|---------------------------------------------------------------------|
| country        | Yes      | String | Australia, AU                                                       |

<br>

#### Request Example:
> https://virgo.co/api/market/tickers?country=AU

#### Response example
```
{
    "code": 0,
    "msg": "success",
    "data": [
        {
            "symbol": "BTC/AUD",
            "last": "102339.71",
            "minTotal": 5.00000000,
            "volume": "0",
            "timeStamp": 1729875749737,
            "high": "103544.42",
            "low": "101455.33",
            "Ask": 103260.84,
            "priceDecimals": 2,
            "qtyDecimals": 4,
            "id": 450,
            "Bid": 101418.58,
            "changeRate": "-0.40%",
            "open": "102755.43",
            "minQty": 0.00018000
        },
        {
            "symbol": "USDT/AUD",
            "last": "1.5118",
            "minTotal": 5.00000000,
            "volume": "0",
            "timeStamp": 1729875750050,
            "high": "1.5118",
            "low": "1.5034",
            "Ask": 1.5254,
            "priceDecimals": 4,
            "qtyDecimals": 4,
            "id": 526,
            "Bid": 1.4982,
            "changeRate": "+0.36%",
            "open": "1.5063",
            "minQty": 5.00000000
        },
        {
            "symbol": "ETH/AUD",
            "last": "3827.07",
            "minTotal": 5.00000000,
            "volume": "0",
            "timeStamp": 1729875749640,
            "high": "3860.87",
            "low": "3715.81",
            "Ask": 3861.53,
            "priceDecimals": 2,
            "qtyDecimals": 3,
            "id": 449,
            "Bid": 3792.62,
            "changeRate": "+0.20%",
            "open": "3819.40",
            "minQty": 0.00200000
        },
        {
            "symbol": "USDC/AUD",
            "last": "1.5117",
            "minTotal": 5.00000000,
            "volume": "0",
            "timeStamp": 1729875229328,
            "high": "1.5120",
            "low": "1.5044",
            "Ask": 1.5254,
            "priceDecimals": 4,
            "qtyDecimals": 2,
            "id": 453,
            "Bid": 1.4980,
            "changeRate": "+0.36%",
            "open": "1.5062",
            "minQty": 0.01000000
        },
        {
            "symbol": "ADA/AUD",
            "last": "0.51847",
            "minTotal": 5.00000000,
            "volume": "0",
            "timeStamp": 1729875749166,
            "high": "0.52300",
            "low": "0.50858",
            "Ask": 0.52321,
            "priceDecimals": 5,
            "qtyDecimals": 5,
            "id": 514,
            "Bid": 0.51373,
            "changeRate": "-0.68%",
            "open": "0.52207",
            "minQty": 7.80000000
        },
        {
            "symbol": "SOL/AUD",
            "last": "259.97",
            "minTotal": 5.00000000,
            "volume": "0",
            "timeStamp": 1729875749858,
            "high": "267.36",
            "low": "257.67",
            "Ask": 262.32,
            "priceDecimals": 2,
            "qtyDecimals": 6,
            "id": 494,
            "Bid": 257.63,
            "changeRate": "-2.58%",
            "open": "266.88",
            "minQty": 0.12000000
        },
        {
            "symbol": "AVAX/AUD",
            "last": "39.566",
            "minTotal": 5.00000000,
            "volume": "0",
            "timeStamp": 1729875750079,
            "high": "40.452",
            "low": "39.009",
            "Ask": 39.930,
            "priceDecimals": 3,
            "qtyDecimals": 3,
            "id": 491,
            "Bid": 39.203,
            "changeRate": "-2.11%",
            "open": "40.419",
            "minQty": 0.14000000
        },
        {
            "symbol": "TIA/AUD",
            "last": "8.5967",
            "minTotal": 5.00000000,
            "volume": "0",
            "timeStamp": 1729875750151,
            "high": "9.4176",
            "low": "8.4355",
            "Ask": 8.7533,
            "priceDecimals": 4,
            "qtyDecimals": 5,
            "id": 550,
            "Bid": 8.4402,
            "changeRate": "-6.99%",
            "open": "9.2434",
            "minQty": 0.60000000
        },
        {
            "symbol": "DOT/AUD",
            "last": "6.2835",
            "minTotal": 5.00000000,
            "volume": "0",
            "timeStamp": 1729875749872,
            "high": "6.3555",
            "low": "6.1916",
            "Ask": 6.3402,
            "priceDecimals": 4,
            "qtyDecimals": 4,
            "id": 501,
            "Bid": 6.2269,
            "changeRate": "-0.81%",
            "open": "6.3354",
            "minQty": 0.40000000
        },
        {
            "symbol": "DOGE/AUD",
            "last": "0.2067340",
            "minTotal": 5.00000000,
            "volume": "0",
            "timeStamp": 1729875749189,
            "high": "0.2151424",
            "low": "0.2046148",
            "Ask": 0.2086151,
            "priceDecimals": 7,
            "qtyDecimals": 1,
            "id": 513,
            "Bid": 0.2048255,
            "changeRate": "-3.28%",
            "open": "0.2137518",
            "minQty": 60.00000000
        }
    ],
    "success": true
}
```

#### Response Parameters:

| Parameter Name | Type    | Description                                                                              |
|----------------|---------|------------------------------------------------------------------------------------------|
| volume         | String  | Volume                                                                                   |
| symbol         | String  | Trading pairs                                                                            |
| high           | String  | Highest market price                                                                     |
| last           | String  | Market close price                                                                       |
| low            | String  | Lowest market price                                                                      |
| Bid            | Decimal | Virgocx bid price                                                                        |
| Ask            | Decimal | Virgocx ask price                                                                        |
| id             | Integer | Market Id                                                                                |
| changeRate     | String  | Change rate in last 24 hours                                                             |
| open           | String  | Market open price                                                                        |
| minQty         | Decimal | Minimum order quantity                                                                   |
| priceDecimals  | Integer | The maximum accuracy of the price                                                        |
| qtyDecimals    | Integer | The maximum accuracy of the quantity                                                     |
| minTotal       | Decimal | Minimum order amount                                                                     |
| timeStamp      | Long    | Unix timestamp in milliseconds, representing the exact date and time of the event in UTC |
---
### 4. Account information

<br>

#### URL:

> https://virgo.co/api/member/accounts

#### Request Method:

> GET

<br>

#### Request Parameters:

| Parameter Name | Required | Type   | Description         |
|----------------|----------|--------|---------------------|
| apiKey         | Yes      | String | Api Key             |
| country        | Yes      | String | Australia AU        |
| sign           | Yes      | String | Parameter signature |

#### Request Example:
> https://virgo.co/api/member/accounts?apiKey=AAA&country=HHH&sign=BBB

> https://virgo.co/api/member/accounts?apiKey=AAA&country=AU&sign=BBB


>AAA: Your API key

>BBB: Sign calculated by MD5,for example:84cde2e3ab9d55cf6eedf1dc5497c06d
 
>HHH: AU (country)

#### Response example:
```
{
    "code": 0,
    "msg": "success",
    "data": [
        {
            "total": 0.3221,
            "balance": 0.3221,
            "coinName": "ETH",
            "freezingBalance": 0.0000
        },
        {
            "total": 1.0145,
            "balance": 1.0145,
            "coinName": "BTC",
            "freezingBalance": 0.0000
        },
        {
            "total": 0.0000,
            "balance": 0.0000,
            "coinName": "USD",
            "freezingBalance": 0.0000
        },
        {
            "total": 11025251.1364,
            "balance": 11025251.1364,
            "coinName": "AUD",
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

> https://virgo.co/api/member/queryOrder

#### Request Method:

> GET

<br>

#### Request Parameters:

| Parameter Name | Required | Type    | Description         |
|----------------|----------|---------|---------------------|
| apiKey         | Yes      | String  | User private key    |
| country        | Yes      | String  | Australia AU        |
| status         | Optional | Integer | Order status        |
| symbol         | Yes      | String  | Trading pairs       |
| sign           | Yes      | String  | Parameter signature |

#### Request Example:
> https://virgo.co/api/member/queryOrder?apiKey=AAA&country=HHH&status=EEE&symbol=ETH/AUD&sign=BBB
 
> https://virgo.co/api/member/queryOrder?apiKey=AAA&country=AU&status=3&symbol=ETH/AUD&sign=BBB

<br>

>AAA: Your API key

>BBB: Sign calculated by MD5,for example:b60743ad70bad7d1fc47777c0d58604e
 
>CCC: Value of symbol(ETH/AUD)

>HHH: AU (country)

>EEE: Order status
#### Response example:
```
{
    "code": 0,
    "msg": "success",
    "data": [
        {
            "total": null,
            "createTime": 1729921736000,
            "price": null,
            "qty": 0.200000000000000000,
            "tradeQty": 0.200000000000000000,
            "id": 894375,
            "averagePrice": 3762.230000000000000000,
            "type": 2,
            "direction": 2,
            "tradeTotal": null,
            "status": 3
        },
        {
            "total": 1000.000000000000000000,
            "createTime": 1729921703000,
            "price": null,
            "qty": null,
            "tradeQty": 0.261060470000000000,
            "id": 894373,
            "averagePrice": 3830.530000000000000000,
            "type": 2,
            "direction": 1,
            "tradeTotal": 999.999962149100000000,
            "status": 3
        },
        {
            "total": 1000.000000000000000000,
            "createTime": 1729921691000,
            "price": null,
            "qty": null,
            "tradeQty": 0.261059110000000000,
            "id": 894371,
            "averagePrice": 3830.550000000000000000,
            "type": 2,
            "direction": 1,
            "tradeTotal": 999.999973810500000000,
            "status": 3
        }
    ],
    "success": true
}
```

#### Response Parameters:

| Parameter Name | Type    | Description                                                                                                 |
|----------------|---------|-------------------------------------------------------------------------------------------------------------|
| createTime     | Date    | Order create time, Unix timestamp in milliseconds, representing the exact date and time of the event in UTC |
| price          | Decimal | Limit order price                                                                                           |
| qty            | Decimal | Order quantity                                                                                              |
| tradeQty       | Decimal | Actually filled quantity                                                                                    |
| total          | Decimal | qty * price or order amount of market order                                                                 |
| tradeTotal     | Decimal | tradeQty * price                                                                                            |
| averagePrice   | Decimal | Average price of order                                                                                      |
| id             | Integer | Order id                                                                                                    |
| type           | Integer | Order type, 1 Limit order, 2 Market order, 3 Quick trade order                                              |
| direction      | Integer | 1 Buy, 2 Sell                                                                                               |
| status         | Integer | -1 Canceled, 0 Placed, 1 Open, 2 Matching, 3 Completed                                                      |
---
### 6. Query user trades

<br>

#### URL:

> https://virgo.co/api/member/queryTrade

#### Request Method:

> GET

<br>

#### Request Parameters:

| Parameter Name | Required | Type   | Description         |
|----------------|----------|--------|---------------------|
| apiKey         | Yes      | String | User private key    |
| sign           | Yes      | String | Parameter signature |
| symbol         | Yes      | String | Trading pairs       |
| country        | Yes      | String | Australia AU        |
#### Request example:

> https://virgo.co/api/member/queryTrade?apiKey=AAA&country=HHH&sign=BBB&symbol=CCC

> https://virgo.co/api/member/queryTrade?apiKey=AAA&country=AU&symbol=ETH/AUD&sign=BBB

>AAA: Your API key

>BBB: Sign calculated by MD5,for example:84cde2e3ab9d55cf6eedf1dc5497c06d

>CCC: Value of symbol(ETH/AUD)
 
>HHH: AU (country)

#### Response example with symbol=ETH/AUD:
```
{
    "code": 0,
    "msg": "success",
    "data": [
        {
            "id": "2666",
            "amount": 752.446000000000000000000000000000,
            "qty": 0.200000000000000000,
            "price": 3762.230000000000000000,
            "type": "sell",
            "createTime": 1729878537
        },
        {
            "id": "2663",
            "amount": 999.999962149100000000000000000000,
            "qty": 0.261060470000000000,
            "price": 3830.530000000000000000,
            "type": "buy",
            "createTime": 1729878504
        },
        {
            "id": "2661",
            "amount": 999.999973810500000000000000000000,
            "qty": 0.261059110000000000,
            "price": 3830.550000000000000000,
            "type": "buy",
            "createTime": 1729878492
        }
    ],
    "success": true
}
```

#### Response Parameters:

| Parameter Name | Type    | Description                                                                                                        |
|----------------|---------|--------------------------------------------------------------------------------------------------------------------|
| id             | String  | Trade Id                                                                                                           |
| amount         | Decimal | Total trading value(fiat value),qty*price                                                                          |
| qty            | Decimal | Total trading amount(crypto)                                                                                       |
| price          | Decimal | Trading price                                                                                                      |
| type           | String  | buy or sell                                                                                                        |
| createTime     | Long    | trade record create time, Unix timestamp in milliseconds, representing the exact date and time of the event in UTC |
---
### 7. Place Order

<br>

#### URL:

> https://virgo.co/api/member/addOrder

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
| country        | Yes      | String  | Australia AU                                           |

#### Notes：
>(1) You only need to provide price value in the parameter list when category is limit.

>(2) You only need to provide total value in the parameter list when category is market order or quick trade and type is buy.
>For example, buy value of 100 australian dollars BTC, value of total is 100. Other combinations of category and type, please provide qty(amount)
>of crypto currency you want to trade.
#### Request example 1(category of limit,purchase 0.005 BTC at a price of 102,000 AUD.):

> https://virgo.co/api/member/addOrder?apiKey=AAA&category=DDD&country=HHH&price=FFF&qty=EEE&symbol=BBB&type=GGG&sign=CCC

> http://virgo.co/api/member/addOrder?apiKey=AAA&category=1&country=AU&price=102000.00&qty=1&symbol=BTC/AUD&type=1&sign=CCC

>AAA: Your API key

>BBB: Value of symbol(BTC/AUD)

>CCC: Sign calculated by MD5,for example:84cde2e3ab9d55cf6eedf1dc5497c06d

>DDD: Value of category(1:Limit, 2:Market Order, 3:Quick Trade)

>EEE: Value of qty(0.005)

>FFF: Value of price(102000.00)

>GGG: Value of type(1:buy, 2:Sell)

>HHH: AU (country)

#### Request example 2(category of market order and type is buy,purchase BTC worth 1000 AUD.):

> https://virgo.co/api/member/addOrder?apiKey=AAA&category=DDD&country=HHH&symbol=BBB&total=III&type=GGG&sign=CCC

> http://virgo.co/api/member/addOrder?apiKey=AAA&category=2&country=AU&symbol=BTC/AUD&total=1000&type=1&sign=CCC

>AAA: Your API key

>BBB: Value of symbol(BTC/AUD)

>CCC: Sign calculated by MD5,for example:84cde2e3ab9d55cf6eedf1dc5497c06d

>DDD: Value of category(1:Limit, 2:Market Order, 3:Quick Trade)

>GGG: Value of type(1:buy, 2:Sell)

>III: Value of australian dollars(1000)
 
>HHH: AU (country)

#### Request example 3(category of market order and type is sell,sell 0.005 BTC):

> https://virgo.co/api/member/addOrder?apiKey=AAA&category=DDD&country=HHH&qty=EEE&symbol=BBB&type=GGG&sign=CCC

> https://virgo.co/api/member/addOrder?apiKey=AAA&category=2&country=AU&qty=0.005&symbol=BTC/AUD&type=2&sign=CCC

>AAA: Your API key

>BBB: Value of symbol(BTC/AUD)

>CCC: Sign calculated by MD5,for example:84cde2e3ab9d55cf6eedf1dc5497c06d

>DDD: Value of category(1:Limit, 2:Market Order, 3:Quick Trade)

>EEE: Value of qty

>GGG: Value of type(1:buy, 2:Sell)

>HHH: AU (country)

#### Response example:
```
Success:
{
    "code": 0,
    "msg": "success",
    "data": {
        "orderId": "812795"
    },
    "success": true
}

Failed:
{
    "code": -1,
    "msg": "AUD Insufficient balance.",
    "data": null,
    "success": false
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

> https://virgo.co/api/member/cancelOrder

#### Request Method:

> GET

<br>

#### Request Parameters:

| Parameter Name | Required | Type    | Description         |
|----------------|----------|---------|---------------------|
| apiKey         | Yes      | String  | User private key    |
| country        | Yes      | String  | Australia AU        |
| id             | Yes      | Integer | Order Id            |
| sign           | Yes      | String  | Parameter signature |

#### Request example:

> https://virgo.co/api/member/cancelOrder?apiKey=AAA&country=HHH&id=CCC&sign=BBB

> https://virgo.co/api/member/cancelOrder?apiKey=AAA&country=AU&id=812795&sign=BBB

>AAA: Your API key

>BBB: Sign calculated by MD5,for example:84cde2e3ab9d55cf6eedf1dc5497c06d

>CCC: Value of id(orderId)

>HHH: AU (country)

#### Response example:
```
Success:
{
    "code": 0,
    "msg": "success",
    "data": "Order cancel successfully!",
    "success": true
}

Failed:
{
    "code": -1,
    "msg": "Order cancel failed!",
    "data": null,
    "success": false
}
```

#### Response Parameters:NO

### 9. Get discount price(bid && ask) depend on account's tier level

<br>

#### URL:

> https://virgo.co/api/member/discountPrice

#### Note:get discount price depend on your account's tier level, for tier level details, you may check your current Reward Tier by visiting https://virgo.co/ and logging in to the Virgo account.

#### Request Method:

> GET

<br>

#### Request Parameters:

| Parameter Name | Required | Type   | Description                        |
|----------------|----------|--------|------------------------------------|
| apiKey         | Yes      | String | User private key                   |
| sign           | Yes      | String | Parameter signature                |
| symbol         | Optional | String | Trading pairs,for example: ETH/AUD |
| country        | Yes      | String | Australia AU                       |

#### Request example(1), get discount price of all trading pairs:

> https://virgo.co/api/member/discountPrice?apiKey=AAA&country=HHH&sign=BBB

> https://virgo.co/api/member/discountPrice?apiKey=AAA&country=AU&sign=BBB


>AAA: Your API key

>BBB: Sign calculated by MD5,for example:84cde2e3ab9d55cf6eedf1dc5497c06d

>HHH: AU (country)

#### Request example(2), get discount price of specific trading pair:
> https://virgo.co/api/member/discountPrice?apiKey=AAA&country=HHH&symbol=CCC&sign=BBB

> https://virgo.co/api/member/discountPrice?apiKey=AAA&country=AU&symbol=BTC/AUD&sign=BBB

>AAA: Your API key

>BBB: Sign calculated by MD5,for example:84cde2e3ab9d55cf6eedf1dc5497c06d

>CCC: Trading pair name(BTC/AUD)

>HHH: AU (country)

#### Response example(1):
```
{
    "code": 0,
    "msg": "success",
    "data": [
        {
            "symbol": "BTC/AUD",
            "last": "101147.94",
            "minTotal": 5.00000000,
            "volume": "0",
            "high": "103544.42",
            "low": "99809.34",
            "Ask": 101673.81,
            "priceDecimals": 2,
            "qtyDecimals": 4,
            "id": 450,
            "Bid": 100581.47,
            "changeRate": "-1.56%",
            "open": "102755.43",
            "minQty": 0.00018000
        },
        {
            "symbol": "USDT/AUD",
            "last": "1.5117",
            "minTotal": 5.00000000,
            "volume": "0",
            "high": "1.5134",
            "low": "1.5034",
            "Ask": 1.5198,
            "priceDecimals": 4,
            "qtyDecimals": 4,
            "id": 526,
            "Bid": 1.5035,
            "changeRate": "+0.35%",
            "open": "1.5063",
            "minQty": 5.00000000
        },
        {
            "symbol": "ETH/AUD",
            "last": "3744.64",
            "minTotal": 5.00000000,
            "volume": "0",
            "high": "3861.09",
            "low": "3715.81",
            "Ask": 3764.86,
            "priceDecimals": 2,
            "qtyDecimals": 3,
            "id": 449,
            "Bid": 3724.41,
            "changeRate": "-1.95%",
            "open": "3819.41",
            "minQty": 0.00200000
        },
        {
            "symbol": "DOT/AUD",
            "last": "0",
            "minTotal": 5.00000000,
            "volume": "0",
            "high": "0",
            "low": "0",
            "Ask": 6.3345,
            "priceDecimals": 4,
            "qtyDecimals": 4,
            "id": 501,
            "Bid": 6.2659,
            "changeRate": "+0.00%",
            "open": "0",
            "minQty": 0.40000000
        },
        {
            "symbol": "DOGE/AUD",
            "last": "0",
            "minTotal": 5.00000000,
            "volume": "0",
            "high": "0",
            "low": "0",
            "Ask": 0.1482367,
            "priceDecimals": 7,
            "qtyDecimals": 1,
            "id": 513,
            "Bid": 0.1466263,
            "changeRate": "+0.00%",
            "open": "0",
            "minQty": 60.00000000
        },
        {
            "symbol": "SHIB/AUD",
            "last": "0",
            "minTotal": 5.00000000,
            "volume": "0",
            "high": "0",
            "low": "0",
            "Ask": 0.00002037,
            "priceDecimals": 8,
            "qtyDecimals": 8,
            "id": 493,
            "Bid": 0.00002015,
            "changeRate": "+0.00%",
            "open": "0",
            "minQty": 342745.00000000
        },
        {
            "symbol": "MATIC/AUD",
            "last": "0",
            "minTotal": 5.00000000,
            "volume": "0",
            "high": "0",
            "low": "0",
            "Ask": 0.61293,
            "priceDecimals": 5,
            "qtyDecimals": 2,
            "id": 523,
            "Bid": 0.60620,
            "changeRate": "+0.00%",
            "open": "0",
            "minQty": 6.30000000
        },
        {
            "symbol": "DAI/AUD",
            "last": "0",
            "minTotal": 5.00000000,
            "volume": "0",
            "high": "0",
            "low": "0",
            "Ask": 1.4873,
            "priceDecimals": 4,
            "qtyDecimals": 4,
            "id": 512,
            "Bid": 1.4712,
            "changeRate": "+0.00%",
            "open": "0",
            "minQty": 3.80000000
        },
        {
            "symbol": "OSMO/AUD",
            "last": "0",
            "minTotal": 5.00000000,
            "volume": "0",
            "high": "0",
            "low": "0",
            "Ask": 0.5708,
            "priceDecimals": 4,
            "qtyDecimals": 2,
            "id": 566,
            "Bid": 0.5573,
            "changeRate": "+0.00%",
            "open": "0",
            "minQty": 2.00000000
        },
        {
            "symbol": "ARB/AUD",
            "last": "0",
            "minTotal": 5.00000000,
            "volume": "0",
            "high": "0",
            "low": "0",
            "Ask": 0.7698,
            "priceDecimals": 4,
            "qtyDecimals": 5,
            "id": 548,
            "Bid": 0.7568,
            "changeRate": "+0.00%",
            "open": "0",
            "minQty": 2.00000000
        },
        {
            "symbol": "RNDR/AUD",
            "last": "0",
            "minTotal": 5.00000000,
            "volume": "0",
            "high": "0",
            "low": "0",
            "Ask": 5.4908,
            "priceDecimals": 4,
            "qtyDecimals": 4,
            "id": 549,
            "Bid": 5.3816,
            "changeRate": "+0.00%",
            "open": "0",
            "minQty": 1.00000000
        },
        {
            "symbol": "ATOM/AUD",
            "last": "0",
            "minTotal": 5.00000000,
            "volume": "0",
            "high": "0",
            "low": "0",
            "Ask": 6.631,
            "priceDecimals": 3,
            "qtyDecimals": 3,
            "id": 497,
            "Bid": 6.551,
            "changeRate": "+0.00%",
            "open": "0",
            "minQty": 0.36000000
        },
        {
            "symbol": "INJ/AUD",
            "last": "0",
            "minTotal": 5.00000000,
            "volume": "0",
            "high": "0",
            "low": "0",
            "Ask": 25.675,
            "priceDecimals": 3,
            "qtyDecimals": 2,
            "id": 557,
            "Bid": 25.112,
            "changeRate": "+0.00%",
            "open": "0",
            "minQty": 0.10000000
        },
        {
            "symbol": "BONK/AUD",
            "last": "0",
            "minTotal": 5.00000000,
            "volume": "0",
            "high": "0",
            "low": "0",
            "Ask": 0.00002687,
            "priceDecimals": 8,
            "qtyDecimals": 0,
            "id": 558,
            "Bid": 0.00002628,
            "changeRate": "+0.00%",
            "open": "0",
            "minQty": 270000.00000000
        },
        {
            "symbol": "HNT/AUD",
            "last": "0",
            "minTotal": 5.00000000,
            "volume": "0",
            "high": "0",
            "low": "0",
            "Ask": 10.947,
            "priceDecimals": 3,
            "qtyDecimals": 2,
            "id": 559,
            "Bid": 10.699,
            "changeRate": "+0.00%",
            "open": "0",
            "minQty": 0.50000000
        },
        {
            "symbol": "LTC/AUD",
            "last": "107.34",
            "minTotal": 5.00000000,
            "volume": "0",
            "high": "108.89",
            "low": "106.04",
            "Ask": 107.86,
            "priceDecimals": 2,
            "qtyDecimals": 6,
            "id": 451,
            "Bid": 106.69,
            "changeRate": "+0.14%",
            "open": "107.18",
            "minQty": 0.06000000
        }
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
            "symbol": "BTC/AUD",
            "last": "101366.46",
            "minTotal": 5.00000000,
            "volume": "0",
            "high": "103544.42",
            "low": "99809.34",
            "Ask": 101918.62,
            "priceDecimals": 2,
            "qtyDecimals": 4,
            "id": 450,
            "Bid": 100823.66,
            "changeRate": "-1.35%",
            "open": "102755.43",
            "minQty": 0.00018000
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
| Bid            | Decimal | Virgocx bid price                    |
| Ask            | Decimal | Virgocx ask price                    |
| id             | Integer | Market id                            |
| changeRate     | String  | Change rate in past 24 hours         |
| open           | String  | Market open price                    |
| minQty         | Decimal | Minimum order quantity               |
| priceDecimals  | Integer | The maximum accuracy of the price    |
| qtyDecimals    | Integer | The maximum accuracy of the quantity |
| minTotal       | Decimal | Minimum order amount                 |

---
