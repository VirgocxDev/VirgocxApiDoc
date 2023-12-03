# Snaplii API DOCS Version-0.0.1

### Get API Authorization

Please register a corporation account on our platform and get API credential for production purpose.
Note: Pay attention that these two keys are related to your account security. So keep them securely.

> apiKey: "94e1cef3531c41bdbd420fc49359f5f2"(Non-product)

> apiSecret: "881a0e2413044015b64acd59cf295864"(Non-product)

```
Signature rules, as example of get BTC change rate API:
original parameters list ==>{apiKey sign marketSymbol}
update parameters list ==>{apiKey apiSecret marketSymbol},remove sign and add apiSecret into this list

step-1:Sort the update parameters list by initial. 
{
    "apiKey":"94e1cef3531c41bdbd420fc49359f5f2",
    "apiSecret":"881a0e2413044015b64acd59cf295864",
    "marketSymbol":"BTC/CAD"
}

If the first character is same, continue to compare next one,until see the difference,for example, apiKey and apiSecret,
the fourth character is different, character K front of character S, so apiKey is front of apiSecret in the parameter list
when calculate MD5 hash.(https://www.md5hashgenerator.com/)

step-2:Generate the character string by putting them together. 
Get: 94e1cef3531c41bdbd420fc49359f5f2881a0e2413044015b64acd59cf295864BTC/CAD

step-3:Execute MD5 algorithm. 
md5(94e1cef3531c41bdbd420fc49359f5f2881a0e2413044015b64acd59cf295864BTC/CAD)
Get: 3d14adf8addcb373801229f2b97d6b32

step-4:Final parameters list used to call https://virgocx.ca/api/member/addOrder.
{
    "apiKey":"94e1cef3531c41bdbd420fc49359f5f2",
    "sign":"b60743ad70bad7d1fc47777c0d58604e",
    "marketSymbol":"BTC/CAD"
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
