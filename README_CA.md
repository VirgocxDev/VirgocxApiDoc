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
    "country":CA,
    "price":9000.1,
    "qty":1.2,
    "symbol":"BTC/CAD",
    "type":1
}

If the first character is same, continue to compare next one,until see the difference,for example, apiKey and apiSecret,
the fourth character is different, character K front of character S, so apiKey is front of apiSecret in the parameter list
when calculate MD5 hash.

step-2:Generate the character string by putting them together. 
Get: AAAAABBBBB19000.11.2BTC/CAD1

step-3:Execute MD5 algorithm. 
md5(AAAAABBBBB1CA9000.11.2BTC/CAD1)
Get: 78f5c2953f02c1932b8f937b913aa2d6

step-4:Final parameters list used to call https://virgocx.ca/api/member/addOrder.
{
    "symbol":"BTC/CAD",
    "category":1,
    "type":1,
    "price":9000.1,
    "qty":1.2,
    "apiKey":"AAAAA",
    "sign":"78f5c2953f02c1932b8f937b913aa2d6"
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
| country        | Yes      | String  | Canada, CA                                                                                                                       |
<br>


### Request Example:
> https://virgocx.ca/api/market/history/kline?country=CA&symbol=ETH/CAD&period=43200

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

| Parameter Name | Type    | Description                                                                                                  |
|----------------|---------|--------------------------------------------------------------------------------------------------------------|
| id             | Integer | K-Line record id                                                                                             |
| country        | Integer | Country id, Canada:1                                                                                         |
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

> https://virgocx.ca/api/market/detail/merged

#### Request Method:

> GET

<br>

#### Request Parameters:

| Parameter Name | Required | Type   | Description                                                               |
|----------------|----------|--------|---------------------------------------------------------------------------|
| symbol         | Yes      | String | "/" needs to be added between the Market name and the Coin name (ETH/CAD) |
| country        | Yes      | String | Canada, CA                                                                |
<br>

#### Request Example:
> https://virgocx.ca/api/market/detail/merged?symbol=ETH/CAD&country=CA

### Response Example:
```
{
    "code": 0,
    "msg": "success",
    "data": {
        "symbol": "ETH/CAD",
        "last": "3438.80",
        "minTotal": 5.00000000,
        "volume": "0",
        "high": "3554.83",
        "low": "3406.49",
        "Ask": 3493.63,
        "priceDecimals": 2,
        "qtyDecimals": 4,
        "id": 25,
        "Bid": 3383.98,
        "changeRate": "-2.03%",
        "open": "3510.41",
        "minQty": 0.00100000
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

> https://virgocx.ca/api/market/tickers

#### Request method:

> GET

<br>

#### Request Parameters:

| Parameter Name | Required | Type   | Description |
|----------------|----------|--------|-------------|
| country        | Yes      | String | Canada, CA  |

<br>

#### Request Example:
> https://virgocx.ca/api/market/tickers?country=CA

#### Response example
```
{
    "code": 0,
    "msg": "success",
    "data": [
        {
            "symbol": "BTC/CAD",
            "last": "63492.03",
            "minTotal": 5.00000000,
            "volume": "0",
            "timeStamp": 1729890518056,
            "high": "65290.68",
            "low": "62598.86",
            "Ask": 64497.93,
            "priceDecimals": 2,
            "qtyDecimals": 5,
            "id": 24,
            "Bid": 62486.14,
            "changeRate": "-1.94%",
            "open": "64754.25",
            "minQty": 0.00010000
        },
        {
            "symbol": "ETH/CAD",
            "last": "3437.57",
            "minTotal": 5.00000000,
            "volume": "0",
            "timeStamp": 1729890517649,
            "high": "3554.83",
            "low": "3406.49",
            "Ask": 3492.09,
            "priceDecimals": 2,
            "qtyDecimals": 4,
            "id": 25,
            "Bid": 3382.99,
            "changeRate": "-2.07%",
            "open": "3510.41",
            "minQty": 0.00100000
        },
        {
            "symbol": "USDC/CAD",
            "last": "0",
            "minTotal": 5.00000000,
            "volume": "0",
            "timeStamp": null,
            "high": "0",
            "low": "0",
            "Ask": 1.3719,
            "priceDecimals": 4,
            "qtyDecimals": 4,
            "id": 55,
            "Bid": 1.3286,
            "changeRate": "+0.00%",
            "open": "0",
            "minQty": 4.00000000
        },
        {
            "symbol": "ADA/CAD",
            "last": "0.466355",
            "minTotal": 5.00000000,
            "volume": "0",
            "timeStamp": 1729890518032,
            "high": "0.480644",
            "low": "0.460451",
            "Ask": 0.473915,
            "priceDecimals": 6,
            "qtyDecimals": 2,
            "id": 68,
            "Bid": 0.458796,
            "changeRate": "-2.80%",
            "open": "0.479811",
            "minQty": 7.50000000
        },
        {
            "symbol": "SOL/CAD",
            "last": "167.33",
            "minTotal": 5.00000000,
            "volume": "0",
            "timeStamp": 1729890518046,
            "high": "694.65",
            "low": "165.01",
            "Ask": 170.01,
            "priceDecimals": 2,
            "qtyDecimals": 6,
            "id": 75,
            "Bid": 164.65,
            "changeRate": "-52.74%",
            "open": "354.10",
            "minQty": 0.02500000
        },
        {
            "symbol": "AVAX/CAD",
            "last": "0",
            "minTotal": 5.00000000,
            "volume": "0",
            "timeStamp": null,
            "high": "0",
            "low": "0",
            "Ask": 30.83,
            "priceDecimals": 2,
            "qtyDecimals": 6,
            "id": 79,
            "Bid": 29.85,
            "changeRate": "+0.00%",
            "open": "0",
            "minQty": 0.10000000
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
| bid            | Decimal | Virgocx bid price                                                                        |
| ask            | Decimal | Virgocx ask price                                                                        |
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

> https://virgocx.ca/api/member/accounts

#### Request Method:

> GET

<br>

#### Request Parameters:

| Parameter Name | Required | Type   | Description         |
|----------------|----------|--------|---------------------|
| apiKey         | Yes      | String | Api Key             |
| country        | Yes      | String | Canada CA           |
| sign           | Yes      | String | Parameter signature |

#### Request Example:
> https://virgocx.ca/api/member/accounts?apiKey=AAA&country=HHH&sign=BBB

> https://virgocx.ca/api/member/accounts?apiKey=AAA&country=CA&sign=BBB

>AAA: Your API key

>BBB: Sign calculated by MD5,for example:78f5c2953f02c1932b8f937b913aa2d6

>HHH: CA (country)

#### Response example:
```
{
    "code": 0,
    "msg": "success",
    "data": [
        {
            "total": 100119.4130,
            "balance": 100119.4130,
            "coinName": "ETH",
            "freezingBalance": 0.0000
        },
        {
            "total": 331.0237,
            "balance": 330.9990,
            "coinName": "BTC",
            "freezingBalance": 0.0246
        },
        {
            "total": 6250522.3671,
            "balance": 6250423.3671,
            "coinName": "CAD",
            "freezingBalance": 99.0000
        },
        {
            "total": 72.2543,
            "balance": 72.2543,
            "coinName": "USDC",
            "freezingBalance": 0.0000
        },
        {
            "total": 9944.0000,
            "balance": 9944.0000,
            "coinName": "USD",
            "freezingBalance": 0.0000
        },
        {
            "total": 32.0000,
            "balance": 32.0000,
            "coinName": "DOGE",
            "freezingBalance": 0.0000
        },
        {
            "total": 955.0000,
            "balance": 955.0000,
            "coinName": "ATOM",
            "freezingBalance": 0.0000
        },
        {
            "total": 258000.0000,
            "balance": 258000.0000,
            "coinName": "LUNA",
            "freezingBalance": 0.0000
        },
        {
            "total": 9957.9832,
            "balance": 9957.9832,
            "coinName": "AUDIO",
            "freezingBalance": 0.0000
        },
        {
            "total": 9920.0000,
            "balance": 9920.0000,
            "coinName": "BNT",
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
| country        | Yes      | String  | Canada CA           |
| status         | Optional | Integer | Order status        |
| symbol         | Yes      | String  | Trading pairs       |
| sign           | Yes      | String  | Parameter signature |

#### Request Example:
> https://virgocx.ca/api/member/queryOrder?apiKey=AAA&country=HHH&status=EEE&symbol=CCC&sign=BBB

> https://virgocx.ca/api/member/queryOrder?apiKey=AAA&country=CA&status=3&symbol=BTC/CAD&sign=BBB

<br>

>AAA: Your API key

>BBB: Sign calculated by MD5,for example:15290b12ed4fe7e6cbeb564bc3185f1b

>CCC: Value of symbol(BTC/CAD)

>HHH: CA (country)

>EEE: Order status
#### Response example:
```
{
    "code": 0,
    "msg": "success",
    "data": [
        {
            "total": null,
            "createTime": 1729521614000,
            "price": null,
            "qty": 1.000000000000000000,
            "tradeQty": 1.000000000000000000,
            "id": 893677,
            "averagePrice": 64953.360000000000000000,
            "type": 2,
            "direction": 2,
            "tradeTotal": null,
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

> https://virgocx.ca/api/member/queryTrade

#### Request Method:

> GET

<br>

#### Request Parameters:

| Parameter Name | Required | Type   | Description         |
|----------------|----------|--------|---------------------|
| apiKey         | Yes      | String | User private key    |
| sign           | Yes      | String | Parameter signature |
| symbol         | Yes      | String | Trading pairs       |
| country        | Yes      | String | Canada CA           |
#### Request example:

> https://virgocx.ca/api/member/queryTrade?apiKey=AAA&country=HHH&symbol=CCC&sign=BBB

> https://virgocx.ca/api/member/queryTrade?apiKey=AAA&country=CA&symbol=BTC/CAD&sign=BBB

>AAA: Your API key

>BBB: Sign calculated by MD5,for example:15290b12ed4fe7e6cbeb564bc3185f1b

>CCC: Value of symbol(BTC/CAD)

>HHH: CA (country)

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

| Parameter Name | Type    | Description                                                                                                        |
|----------------|---------|--------------------------------------------------------------------------------------------------------------------|
| id             | Integer | Trade Id                                                                                                           |
| amount         | Decimal | Total trading value(fiat value),qty*price                                                                          |
| qty            | Decimal | Total trading amount(crypto)                                                                                       |
| price          | Decimal | Trading price                                                                                                      |
| type           | String  | buy or sell                                                                                                        |
| createTime     | Long    | trade record create time, Unix timestamp in milliseconds, representing the exact date and time of the event in UTC |
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
| country        | Yes      | String  | Canada CA                                              |

#### Notes：
>(1) You only need to provide price value in the parameter list when category is limit.

>(2) You only need to provide total value in the parameter list when category is market order or quick trade and type is buy.
>For example, buy value of 100 canadian dollars BTC, value of total is 100. Other combinations of category and type, please provide qty(amount)
>of crypto currency you want to trade.
#### Request example 1(category of limit,purchase 0.5 BTC at a price of 64,000 CAD.):

> https://virgocx.ca/api/member/addOrder?apiKey=AAA&category=DDD&country=HHH&price=FFF&qty=EEE&symbol=BBB&type=GGG&sign=CCC

> http://virgocx.ca/api/member/addOrder?apiKey=AAA&category=1&country=CA&price=64000&qty=0.5&symbol=BTC/CAD&type=1&sign=CCC

>AAA: Your API key

>BBB: Value of symbol(BTC/CAD)

>CCC: Sign calculated by MD5,for example:15290b12ed4fe7e6cbeb564bc3185f1b

>DDD: Value of category(1:Limit, 2:Market Order, 3:Quick Trade)

>EEE: Value of qty(0.5)

>FFF: Value of price(64000.00)

>GGG: Value of type(1:buy, 2:Sell)

>HHH: CA (country)

#### Request example 2(category of market order and type is buy,purchase BTC worth 10000 CAD.):

> https://virgocx.ca/api/member/addOrder?apiKey=AAA&category=DDD&country=HHH&symbol=BBB&total=III&type=GGG&sign=CCC

> http://virgocx.ca/api/member/addOrder?apiKey=AAA&category=2&country=CA&symbol=BTC/CAD&total=10000&type=1&sign=CCC

>AAA: Your API key

>BBB: Value of symbol(BTC/CAD)

>CCC: Sign calculated by MD5,for example:15290b12ed4fe7e6cbeb564bc3185f1b

>DDD: Value of category(1:Limit, 2:Market Order, 3:Quick Trade)

>GGG: Value of type(1:buy, 2:Sell)

>III: Value of canadian dollars(10000)

>HHH: CA (country)

#### Request example 3(category of market order and type is sell,sell 1 BTC):

> https://virgocx.ca/api/member/addOrder?apiKey=AAA&category=DDD&country=HHH&qty=EEE&symbol=BBB&type=GGG&sign=CCC

> https://virgocx.ca/api/member/addOrder?apiKey=AAA&category=2&country=CA&qty=1&symbol=BTC/CAD&type=2&sign=CCC

>AAA: Your API key

>BBB: Value of symbol(BTC/CAD)

>CCC: Sign calculated by MD5,for example:15290b12ed4fe7e6cbeb564bc3185f1b

>DDD: Value of category(1:Limit, 2:Market Order, 3:Quick Trade)

>EEE: Value of qty

>GGG: Value of type(1:buy, 2:Sell)

>HHH: CA (country)

#### Response example:
```
Success:
{
    "code": 0,
    "msg": "success",
    "data": {
        "orderId": "894414"
    },
    "success": true
}

Failed:
{
    "code": -1,
    "msg": "CAD Insufficient balance.",
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

> https://virgocx.ca/api/member/cancelOrder

#### Request Method:

> GET

<br>

#### Request Parameters:

| Parameter Name | Required | Type    | Description         |
|----------------|----------|---------|---------------------|
| apiKey         | Yes      | String  | User private key    |
| country        | Yes      | String  | Canada CA           |
| id             | Yes      | Integer | Order Id            |
| sign           | Yes      | String  | Parameter signature |

#### Request example:

> https://virgocx.ca/api/member/cancelOrder?apiKey=AAA&country=HHH&id=CCC&sign=BBB
> 
> https://virgocx.ca/api/member/cancelOrder?apiKey=AAA&country=CA&id=894414&sign=BBB

>AAA: Your API key

>BBB: Sign calculated by MD5,for example:15290b12ed4fe7e6cbeb564bc3185f1b

>CCC: Value of id(orderId)

>HHH: CA (country)

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
| country        | Yes      | String | Canada CA                          |

#### Request example(1), get discount price of all trading pairs:

> https://virgocx.ca/api/member/discountPrice?apiKey=AAA&sign=BBB
 
> https://virgocx.ca/api/member/discountPrice?apiKey=AAA&country=CA&sign=BBB

>AAA: Your API key

>BBB: Sign calculated by MD5,for example:15290b12ed4fe7e6cbeb564bc3185f1b

>HHH: CA (country)

#### Request example(2), get discount price of specific trading pair:
> https://virgocx.ca/api/member/discountPrice?apiKey=AAA&symbol=BTC/CAD

> https://virgocx.ca/api/member/discountPrice?apiKey=AAA&country=CA&symbol=BTC/CAD&sign=BBB

>AAA: Your API key

>BBB: Sign calculated by MD5,for example:15290b12ed4fe7e6cbeb564bc3185f1b

>CCC: Trading pair name(BTC/CAD)

>HHH: CA (country)

#### Response example(1):
```
{
    "code": 0,
    "msg": "success",
    "data": [
       {
            "symbol": "BTC/CAD",
            "last": "63750.92",
            "minTotal": 5.00000000,
            "volume": "0",
            "high": "65290.68",
            "low": "62598.86",
            "Ask": 64379.96,
            "priceDecimals": 2,
            "qtyDecimals": 5,
            "id": 24,
            "Bid": 63157.78,
            "changeRate": "-1.54%",
            "open": "64754.25",
            "minQty": 0.00010000
        },
        {
            "symbol": "ETH/CAD",
            "last": "3453.45",
            "minTotal": 5.00000000,
            "volume": "0",
            "high": "3554.83",
            "low": "3406.49",
            "Ask": 3485.97,
            "priceDecimals": 2,
            "qtyDecimals": 4,
            "id": 25,
            "Bid": 3420.93,
            "changeRate": "-1.62%",
            "open": "3510.41",
            "minQty": 0.00100000
        },
        {
            "symbol": "USDC/CAD",
            "last": "0",
            "minTotal": 5.00000000,
            "volume": "0",
            "high": "0",
            "low": "0",
            "Ask": 1.3632,
            "priceDecimals": 4,
            "qtyDecimals": 4,
            "id": 55,
            "Bid": 1.3372,
            "changeRate": "+0.00%",
            "open": "0",
            "minQty": 4.00000000
        },
        {
            "symbol": "ADA/CAD",
            "last": "0.473247",
            "minTotal": 5.00000000,
            "volume": "0",
            "high": "0.480644",
            "low": "0.460451",
            "Ask": 0.477858,
            "priceDecimals": 6,
            "qtyDecimals": 2,
            "id": 68,
            "Bid": 0.468609,
            "changeRate": "-1.36%",
            "open": "0.479811",
            "minQty": 7.50000000
        },
        {
            "symbol": "SOL/CAD",
            "last": "167.65",
            "minTotal": 5.00000000,
            "volume": "0",
            "high": "694.65",
            "low": "165.01",
            "Ask": 169.26,
            "priceDecimals": 2,
            "qtyDecimals": 6,
            "id": 75,
            "Bid": 166.03,
            "changeRate": "-52.65%",
            "open": "354.10",
            "minQty": 0.02500000
        },
        {
            "symbol": "AVAX/CAD",
            "last": "0",
            "minTotal": 5.00000000,
            "volume": "0",
            "high": "0",
            "low": "0",
            "Ask": 30.63,
            "priceDecimals": 2,
            "qtyDecimals": 6,
            "id": 79,
            "Bid": 30.04,
            "changeRate": "+0.00%",
            "open": "0",
            "minQty": 0.10000000
        },
        {
            "symbol": "TIA/CAD",
            "last": "0",
            "minTotal": 5.00000000,
            "volume": "0",
            "high": "0",
            "low": "0",
            "Ask": 6.0899,
            "priceDecimals": 4,
            "qtyDecimals": 5,
            "id": 540,
            "Bid": 5.9454,
            "changeRate": "+0.00%",
            "open": "0",
            "minQty": 0.40000000
        },
        {
            "symbol": "DOT/CAD",
            "last": "5.7066",
            "minTotal": 5.00000000,
            "volume": "0",
            "high": "5.8370",
            "low": "5.6097",
            "Ask": 5.7614,
            "priceDecimals": 4,
            "qtyDecimals": 3,
            "id": 69,
            "Bid": 5.6518,
            "changeRate": "-1.99%",
            "open": "5.8228",
            "minQty": 0.50000000
        },
        {
            "symbol": "DOGE/CAD",
            "last": "0.1360150",
            "minTotal": 5.00000000,
            "volume": "0",
            "high": "0.1426246",
            "low": "0.1321200",
            "Ask": 0.1373207,
            "priceDecimals": 7,
            "qtyDecimals": 1,
            "id": 57,
            "Bid": 0.1347091,
            "changeRate": "-4.16%",
            "open": "0.1419257",
            "minQty": 25.00000000
        },
        {
            "symbol": "SHIB/CAD",
            "last": "0",
            "minTotal": 5.00000000,
            "volume": "0",
            "high": "0",
            "low": "0",
            "Ask": 0.00001867,
            "priceDecimals": 8,
            "qtyDecimals": 0,
            "id": 76,
            "Bid": 0.00001831,
            "changeRate": "+0.00%",
            "open": "0",
            "minQty": 165000.00000000
        },
        {
            "symbol": "MATIC/CAD",
            "last": "0",
            "minTotal": 5.00000000,
            "volume": "0",
            "high": "0",
            "low": "0",
            "Ask": 0.5617,
            "priceDecimals": 4,
            "qtyDecimals": 2,
            "id": 71,
            "Bid": 0.5508,
            "changeRate": "+0.00%",
            "open": "0",
            "minQty": 4.00000000
        },
        {
            "symbol": "ARB/CAD",
            "last": "0",
            "minTotal": 5.00000000,
            "volume": "0",
            "high": "0",
            "low": "0",
            "Ask": 0.7042,
            "priceDecimals": 4,
            "qtyDecimals": 5,
            "id": 536,
            "Bid": 0.6891,
            "changeRate": "+0.00%",
            "open": "0",
            "minQty": 3.00000000
        },
        {
            "symbol": "RNDR/CAD",
            "last": "0",
            "minTotal": 5.00000000,
            "volume": "0",
            "high": "0",
            "low": "0",
            "Ask": 4.9008,
            "priceDecimals": 4,
            "qtyDecimals": 4,
            "id": 541,
            "Bid": 4.7804,
            "changeRate": "+0.00%",
            "open": "0",
            "minQty": 0.40000000
        },
        {
            "symbol": "INJ/CAD",
            "last": "0",
            "minTotal": 5.00000000,
            "volume": "0",
            "high": "0",
            "low": "0",
            "Ask": 22.407,
            "priceDecimals": 3,
            "qtyDecimals": 2,
            "id": 542,
            "Bid": 21.913,
            "changeRate": "+0.00%",
            "open": "0",
            "minQty": 0.15000000
        },
        {
            "symbol": "BONK/CAD",
            "last": "0",
            "minTotal": 5.00000000,
            "volume": "0",
            "high": "0",
            "low": "0",
            "Ask": 0.00002456,
            "priceDecimals": 8,
            "qtyDecimals": 0,
            "id": 543,
            "Bid": 0.00002395,
            "changeRate": "+0.00%",
            "open": "0",
            "minQty": 240000.00000000
        },
        {
            "symbol": "OSMO/CAD",
            "last": "0",
            "minTotal": 5.00000000,
            "volume": "0",
            "high": "0",
            "low": "0",
            "Ask": 0.5216,
            "priceDecimals": 4,
            "qtyDecimals": 2,
            "id": 544,
            "Bid": 0.5081,
            "changeRate": "+0.00%",
            "open": "0",
            "minQty": 4.00000000
        },
        {
            "symbol": "HNT/CAD",
            "last": "0",
            "minTotal": 5.00000000,
            "volume": "0",
            "high": "0",
            "low": "0",
            "Ask": 10.002,
            "priceDecimals": 3,
            "qtyDecimals": 2,
            "id": 545,
            "Bid": 9.753,
            "changeRate": "+0.00%",
            "open": "0",
            "minQty": 0.80000000
        },
        {
            "symbol": "ATOM/CAD",
            "last": "0",
            "minTotal": 5.00000000,
            "volume": "0",
            "high": "0",
            "low": "0",
            "Ask": 6.0821,
            "priceDecimals": 4,
            "qtyDecimals": 6,
            "id": 74,
            "Bid": 5.9506,
            "changeRate": "+0.00%",
            "open": "0",
            "minQty": 0.40000000
        },
        {
            "symbol": "IMX/CAD",
            "last": "0",
            "minTotal": 5.00000000,
            "volume": "0",
            "high": "0",
            "low": "0",
            "Ask": 1.724,
            "priceDecimals": 3,
            "qtyDecimals": 2,
            "id": 529,
            "Bid": 1.682,
            "changeRate": "+0.00%",
            "open": "0",
            "minQty": 2.00000000
        },
        {
            "volume": "0",
            "symbol": "LTC/CAD",
            "high": "0",
            "last": "0",
            "minTotal": 5.00000000,
            "low": "0",
            "priceDecimals": 2,
            "qtyDecimals": 6,
            "id": 30,
            "changeRate": "+0.00%",
            "open": "0",
            "minQty": 0.04500000
        },
        {
            "symbol": "LINK/CAD",
            "last": "16.23414",
            "minTotal": 5.00000000,
            "volume": "0",
            "high": "16.73748",
            "low": "15.74977",
            "Ask": 16.41058,
            "priceDecimals": 5,
            "qtyDecimals": 3,
            "id": 60,
            "Bid": 16.05989,
            "changeRate": "+0.96%",
            "open": "16.07904",
            "minQty": 0.25000000
        },
        {
            "symbol": "LDO/CAD",
            "last": "0",
            "minTotal": 5.00000000,
            "volume": "0",
            "high": "0",
            "low": "0",
            "Ask": 1.447,
            "priceDecimals": 3,
            "qtyDecimals": 2,
            "id": 530,
            "Bid": 1.415,
            "changeRate": "+0.00%",
            "open": "0",
            "minQty": 1.80000000
        },
        {
            "symbol": "FET/CAD",
            "last": "0",
            "minTotal": 5.00000000,
            "volume": "0",
            "high": "0",
            "low": "0",
            "Ask": 1.6508,
            "priceDecimals": 4,
            "qtyDecimals": 1,
            "id": 531,
            "Bid": 1.6154,
            "changeRate": "+0.00%",
            "open": "0",
            "minQty": 2.00000000
        },
        {
            "symbol": "Blur/CAD",
            "last": "0",
            "minTotal": 5.00000000,
            "volume": "0",
            "high": "0",
            "low": "0",
            "Ask": 0.2147,
            "priceDecimals": 4,
            "qtyDecimals": 1,
            "id": 532,
            "Bid": 0.2096,
            "changeRate": "+0.00%",
            "open": "0",
            "minQty": 9.00000000
        },
        {
            "symbol": "UNI/CAD",
            "last": "10.805",
            "minTotal": 5.00000000,
            "volume": "0",
            "high": "11.331",
            "low": "10.710",
            "Ask": 10.923,
            "priceDecimals": 3,
            "qtyDecimals": 6,
            "id": 59,
            "Bid": 10.686,
            "changeRate": "-2.94%",
            "open": "11.133",
            "minQty": 0.50000000
        },
        {
            "symbol": "NEAR/CAD",
            "last": "0",
            "minTotal": 5.00000000,
            "volume": "0",
            "high": "0",
            "low": "0",
            "Ask": 5.425,
            "priceDecimals": 3,
            "qtyDecimals": 4,
            "id": 127,
            "Bid": 5.301,
            "changeRate": "+0.00%",
            "open": "0",
            "minQty": 0.60000000
        },
        {
            "symbol": "BCH/CAD",
            "last": "500.62",
            "minTotal": 5.00000000,
            "volume": "0",
            "high": "517.78",
            "low": "495.17",
            "Ask": 505.42,
            "priceDecimals": 2,
            "qtyDecimals": 6,
            "id": 29,
            "Bid": 495.83,
            "changeRate": "-1.68%",
            "open": "509.18",
            "minQty": 0.00800000
        },
        {
            "volume": "0",
            "symbol": "ALGO/CAD",
            "high": "0",
            "last": "0",
            "minTotal": 5.00000000,
            "low": "0",
            "priceDecimals": 5,
            "qtyDecimals": 5,
            "id": 108,
            "changeRate": "+0.00%",
            "open": "0",
            "minQty": 20.00000000
        },
        {
            "symbol": "APE/CAD",
            "last": "0",
            "minTotal": 5.00000000,
            "volume": "0",
            "high": "0",
            "low": "0",
            "Ask": 0.8232,
            "priceDecimals": 4,
            "qtyDecimals": 5,
            "id": 109,
            "Bid": 0.8051,
            "changeRate": "+0.00%",
            "open": "0",
            "minQty": 3.00000000
        },
        {
            "symbol": "XLM/CAD",
            "last": "0.131639",
            "minTotal": 5.00000000,
            "volume": "0",
            "high": "0.134788",
            "low": "0.131102",
            "Ask": 0.132927,
            "priceDecimals": 6,
            "qtyDecimals": 4,
            "id": 56,
            "Bid": 0.130361,
            "changeRate": "-1.53%",
            "open": "0.133695",
            "minQty": 45.00000000
        },
        {
            "symbol": "MANA/CAD",
            "last": "0",
            "minTotal": 5.00000000,
            "volume": "0",
            "high": "0",
            "low": "0",
            "Ask": 0.36267,
            "priceDecimals": 5,
            "qtyDecimals": 5,
            "id": 73,
            "Bid": 0.35471,
            "changeRate": "+0.00%",
            "open": "0",
            "minQty": 8.00000000
        },
        {
            "symbol": "XRP/CAD",
            "last": "0",
            "minTotal": 5.00000000,
            "volume": "0",
            "high": "0",
            "low": "0",
            "Ask": 0.77285,
            "priceDecimals": 5,
            "qtyDecimals": 2,
            "id": 538,
            "Bid": 0.75813,
            "changeRate": "+0.00%",
            "open": "0",
            "minQty": 7.00000000
        },
        {
            "symbol": "ETC/CAD",
            "last": "0",
            "minTotal": 5.00000000,
            "volume": "0",
            "high": "0",
            "low": "0",
            "Ask": 24.805,
            "priceDecimals": 3,
            "qtyDecimals": 6,
            "id": 81,
            "Bid": 24.260,
            "changeRate": "+0.00%",
            "open": "0",
            "minQty": 0.14000000
        },
        {
            "symbol": "HBAR/CAD",
            "last": "0",
            "minTotal": 5.00000000,
            "volume": "0",
            "high": "0",
            "low": "0",
            "Ask": 0.06592,
            "priceDecimals": 5,
            "qtyDecimals": 1,
            "id": 115,
            "Bid": 0.06441,
            "changeRate": "+0.00%",
            "open": "0",
            "minQty": 45.00000000
        },
        {
            "symbol": "ICP/CAD",
            "last": "0",
            "minTotal": 5.00000000,
            "volume": "0",
            "high": "0",
            "low": "0",
            "Ask": 10.280,
            "priceDecimals": 3,
            "qtyDecimals": 6,
            "id": 131,
            "Bid": 10.045,
            "changeRate": "+0.00%",
            "open": "0",
            "minQty": 0.30000000
        },
        {
            "symbol": "SAND/CAD",
            "last": "0",
            "minTotal": 5.00000000,
            "volume": "0",
            "high": "0",
            "low": "0",
            "Ask": 0.3442,
            "priceDecimals": 4,
            "qtyDecimals": 5,
            "id": 94,
            "Bid": 0.3366,
            "changeRate": "+0.00%",
            "open": "0",
            "minQty": 8.00000000
        },
        {
            "symbol": "FTM/CAD",
            "last": "0",
            "minTotal": 5.00000000,
            "volume": "0",
            "high": "0",
            "low": "0",
            "Ask": 0.5811,
            "priceDecimals": 4,
            "qtyDecimals": 6,
            "id": 93,
            "Bid": 0.5677,
            "changeRate": "+0.00%",
            "open": "0",
            "minQty": 5.00000000
        },
        {
            "symbol": "FIL/CAD",
            "last": "0",
            "minTotal": 5.00000000,
            "volume": "0",
            "high": "0",
            "low": "0",
            "Ask": 4.768,
            "priceDecimals": 3,
            "qtyDecimals": 6,
            "id": 70,
            "Bid": 4.664,
            "changeRate": "+0.00%",
            "open": "0",
            "minQty": 0.60000000
        },
        {
            "symbol": "AXS/CAD",
            "last": "0",
            "minTotal": 5.00000000,
            "volume": "0",
            "high": "0",
            "low": "0",
            "Ask": 6.367,
            "priceDecimals": 3,
            "qtyDecimals": 6,
            "id": 77,
            "Bid": 6.227,
            "changeRate": "+0.00%",
            "open": "0",
            "minQty": 0.50000000
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
            "symbol": "BTC/CAD",
            "last": "63761.20",
            "minTotal": 5.00000000,
            "volume": "0",
            "high": "65290.68",
            "low": "62598.86",
            "Ask": 64382.09,
            "priceDecimals": 2,
            "qtyDecimals": 5,
            "id": 24,
            "Bid": 63161.27,
            "changeRate": "-1.53%",
            "open": "64754.25",
            "minQty": 0.00010000
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
