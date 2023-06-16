# Virgocx API DOCS

### Get API Authorization

Please contact us to get your apiKey and apiSecret.
Note: Pay attention that these two keys are related to your account security. So keep them securely.
> Public interfaces do not need signatures. Request parameters of all interfaces which need signature must contain sign parameters.

> apiKey: private key of user access provided by VirgoCX.

> apiSecret: private key of parameter signature request.

```
Signature rules, as example of placing order interface:
original parameters list ==>{apiKey sign symbol category type price qty}
update parameters list ==>{apiKey apiSecret symbol category type price qty},remove sign and add apiSecret into this list

step-1:Sort the update parameters list by initial. 
{
    "apiKey":"AAAAA",
    "apiSecret":"BBBBB",
    "category":"1",
    "price":"9000.1",
    "qty":"1.2",
    "symbol":"BTC/CAD",
    "type":"1"
}

step-2:Generate the character string by putting them together. 
Get: AAAAABBBBB19000.11.2BTC/CAD1

step-3:Execute MD5 algorithm. 
md5(AAAAABBBBB19000.11.2BTC/CAD1)
Get: b60743ad70bad7d1fc47777c0d58604e

step-4:Final parameters list used to call https://virgocx.ca/api/member/addOrder.
{
    "symbol":"BTC/CAD",
    "category":"1",
    "type":"1",
    "price":"9000.1",
    "qty":"1.2",
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
            "country": null,
            "marketId": 25,
            "open": 401.0,
            "high": 475.95,
            "low": 360.65,
            "close": 388.3,
            "qty": 10873.662506,
            "createTime": 1559318400000,
            "countTime": null
        },
        {
            "id": 408678,
            "country": null,
            "marketId": 25,
            "open": 387.06,
            "high": 416.59,
            "low": 252.5,
            "close": 285.49,
            "qty": 39631.3236542,
            "createTime": 1561910400000,
            "countTime": null
        },
        {
            "id": 806012,
            "country": null,
            "marketId": 25,
            "open": 285.72,
            "high": 315.69,
            "low": 219.61,
            "close": 223.87,
            "qty": 8346.04195532,
            "createTime": 1564588800000,
            "countTime": null
        },
        {
            "id": 1345976,
            "country": null,
            "marketId": 25,
            "open": 223.89,
            "high": 418.8,
            "low": 202.23,
            "close": 237.32,
            "qty": 19125.03882276,
            "createTime": 1567267200000,
            "countTime": null
        },
        {
            "id": 1960838,
            "country": null,
            "marketId": 25,
            "open": 237.13,
            "high": 259.89,
            "low": 208.99,
            "close": 239.54,
            "qty": 10960.61274312,
            "createTime": 1569859200000,
            "countTime": null
        },
        {
            "id": 2641817,
            "country": null,
            "marketId": 25,
            "open": 239.61,
            "high": 255.87,
            "low": 175.78,
            "close": 201.8,
            "qty": 43234.79312868,
            "createTime": 1572537600000,
            "countTime": null
        },
        {
            "id": 3369813,
            "country": null,
            "marketId": 25,
            "open": 201.56,
            "high": 202.98,
            "low": 152.79,
            "close": 167.82,
            "qty": 44053.47159586,
            "createTime": 1575129600000,
            "countTime": null
        },
        {
            "id": 3848988,
            "country": null,
            "marketId": 25,
            "open": 167.91,
            "high": 246.32,
            "low": 162.72,
            "close": 237.77,
            "qty": 30077.39236914,
            "createTime": 1577808000000,
            "countTime": null
        },
        {
            "id": 4070825,
            "country": null,
            "marketId": 25,
            "open": 237.82,
            "high": 382.72,
            "low": 234.92,
            "close": 301.2,
            "qty": 2721.21959982,
            "createTime": 1580486400000,
            "countTime": null
        },
        {
            "id": 4284913,
            "country": null,
            "marketId": 25,
            "open": 300.04,
            "high": 309.66,
            "low": 145.0,
            "close": 187.84,
            "qty": 370.3166959,
            "createTime": 1582992000000,
            "countTime": null
        },
        {
            "id": 4633451,
            "country": null,
            "marketId": 25,
            "open": 187.92,
            "high": 315.15,
            "low": 183.41,
            "close": 289.99,
            "qty": 8900.03927458,
            "createTime": 1585670400000,
            "countTime": null
        },
        {
            "id": 4996227,
            "country": null,
            "marketId": 25,
            "open": 289.49,
            "high": 339.67,
            "low": 247.86,
            "close": 321.68,
            "qty": 9290.38332074,
            "createTime": 1588262400000,
            "countTime": null
        },
        {
            "id": 5347054,
            "country": null,
            "marketId": 25,
            "open": 321.04,
            "high": 342.42,
            "low": 296.0,
            "close": 307.68,
            "qty": 8927.43066564,
            "createTime": 1590940800000,
            "countTime": null
        },
        {
            "id": 5709609,
            "country": null,
            "marketId": 25,
            "open": 307.92,
            "high": 466.95,
            "low": 303.03,
            "close": 461.41,
            "qty": 9393.82438502,
            "createTime": 1593532800000,
            "countTime": null
        },
        {
            "id": 6063986,
            "country": null,
            "marketId": 25,
            "open": 496.65,
            "high": 588.86,
            "low": 487.03,
            "close": 520.19,
            "qty": 2577.4169199000003,
            "createTime": 1596214800000,
            "countTime": null
        },
        {
            "id": 6531682,
            "country": null,
            "marketId": 25,
            "open": 461.7,
            "high": 527.43,
            "low": 426.45,
            "close": 471.06,
            "qty": 0.0,
            "createTime": 1598893200000,
            "countTime": null
        },
        {
            "id": 7073396,
            "country": null,
            "marketId": 25,
            "open": 470.08,
            "high": 552.09,
            "low": 443.9,
            "close": 543.83,
            "qty": 0.0,
            "createTime": 1601485200000,
            "countTime": null
        },
        {
            "id": 7568326,
            "country": null,
            "marketId": 25,
            "open": 518.81,
            "high": 810.71,
            "low": 493.82,
            "close": 688.33,
            "qty": 0.0,
            "createTime": 1604163600000,
            "countTime": null
        },
        {
            "id": 8100966,
            "country": null,
            "marketId": 25,
            "open": 762.37,
            "high": 848.59,
            "low": 687.3,
            "close": 808.68,
            "qty": 0.0,
            "createTime": 1606755600000,
            "countTime": null
        },
        {
            "id": 8711518,
            "country": null,
            "marketId": 25,
            "open": 1169.55,
            "high": 1828.36,
            "low": 1169.55,
            "close": 1566.82,
            "qty": 0.0,
            "createTime": 1609434000000,
            "countTime": null
        },
        {
            "id": 9318087,
            "country": null,
            "marketId": 25,
            "open": 1674.46,
            "high": 2572.31,
            "low": 1640.68,
            "close": 2572.31,
            "qty": 0.0,
            "createTime": 1612112400000,
            "countTime": null
        },
        {
            "id": 10055754,
            "country": null,
            "marketId": 25,
            "open": 1773.88,
            "high": 2377.11,
            "low": 1773.88,
            "close": 2110.23,
            "qty": 0.0,
            "createTime": 1614531600000,
            "countTime": null
        },
        {
            "id": 10858992,
            "country": null,
            "marketId": 25,
            "open": 2594.71,
            "high": 3235.89,
            "low": 2453.25,
            "close": 2743.3,
            "qty": 0.0,
            "createTime": 1617210000000,
            "countTime": null
        },
        {
            "id": 11705684,
            "country": null,
            "marketId": 25,
            "open": 3650.5,
            "high": 5285.36,
            "low": 2309.65,
            "close": 2907.02,
            "qty": 0.0,
            "createTime": 1619802000000,
            "countTime": null
        },
        {
            "id": 12525424,
            "country": null,
            "marketId": 25,
            "open": 3236.02,
            "high": 3442.52,
            "low": 2117.94,
            "close": 2135.47,
            "qty": 0.0,
            "createTime": 1622480400000,
            "countTime": null
        }
    ],
    "success": true
}
```

#### Response Parameters:

| Parameter Name | Type    | Description          |
|----------------|---------|----------------------|
| id             | Integer | K-Line id            |
| country        | Integer | Country id, Canada:1 |
| marketId       | Integer | Market id            |
| open           | Decimal | Market open price    |
| high           | Decimal | Highest market price |
| low            | Decimal | Lowest market price  |
| close          | Decimal | Market close price   |
| qty            | Decimal | ()                   |
| createTime     | Date    | Create Time          |
| countTime      |         | ()                   |

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
        "volume": "0",
        "symbol": "ETH/CAD",
        "high": "2351.91",
        "last": "2314.16",
        "low": "2293.77",
        "bid": 2277.13,
        "ask": 2351.20,
        "id": 25,
        "changeRate": "-0.83%",
        "open": "2333.59"
    },
    "success": true
}
```
#### Response Parameters:

| Parameter Name | Type    | Description                  |
|----------------|---------|------------------------------|
| volume         | String  | Volume                       |
| symbol         | String  | Trading pairs                |
| high           | String  | Highest market price         |
| last           | String  | Market close price           |
| low            | String  | Lowest market price          |
| bid            | Decimal | Virgocx bid price            |
| ask            | Decimal | Virgocx ask price            |
| id             | Integer | Market id                    |
| changeRate     | String  | Change rate in last 24 hours |
| open           | String  | Market open price            |

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
            "volume": "0",
            "symbol": "BTC/CAD",
            "high": "35177.92",
            "last": "34433.90",
            "low": "34201.58",
            "bid": 33882.89,
            "ask": 34984.91,
            "id": 24,
            "changeRate": "-1.08%",
            "open": "34810.03"
        },
        {
            "volume": "0",
            "symbol": "ENJ/CAD",
            "high": "0.3511",
            "last": "0.3402",
            "low": "0.3357",
            "bid": 0.3331,
            "ask": 0.3474,
            "id": 72,
            "changeRate": "-1.07%",
            "open": "0.3439"
        },
        {
            "volume": "0",
            "symbol": "KSM/CAD",
            "high": "30.87",
            "last": "29.52",
            "low": "29.21",
            "bid": 28.97,
            "ask": 30.07,
            "id": 86,
            "changeRate": "-2.99%",
            "open": "30.43"
        },
        {
            "volume": "0",
            "symbol": "CELO/CAD",
            "high": "0.5656",
            "last": "0.5467",
            "low": "0.5391",
            "bid": 0.5362,
            "ask": 0.5572,
            "id": 118,
            "changeRate": "-2.30%",
            "open": "0.5596"
        },
        {
            "volume": "0",
            "symbol": "CRV/CAD",
            "high": "0.884",
            "last": "0.864",
            "low": "0.857",
            "bid": 0.847,
            "ask": 0.881,
            "id": 61,
            "changeRate": "-0.46%",
            "open": "0.868"
        },
        {
            "volume": "0",
            "symbol": "LRC/CAD",
            "high": "0.2943",
            "last": "0.2855",
            "low": "0.2832",
            "bid": 0.2802,
            "ask": 0.2909,
            "id": 87,
            "changeRate": "-1.10%",
            "open": "0.2887"
        },
        {
            "volume": "0",
            "symbol": "COMP/CAD",
            "high": "37.63",
            "last": "36.20",
            "low": "35.88",
            "bid": 35.53,
            "ask": 36.88,
            "id": 66,
            "changeRate": "-3.26%",
            "open": "37.42"
        },
        {
            "volume": "0",
            "symbol": "ANKR/CAD",
            "high": "0.02778",
            "last": "0.02667",
            "low": "0.02625",
            "bid": 0.02615,
            "ask": 0.02719,
            "id": 96,
            "changeRate": "-1.87%",
            "open": "0.02718"
        },
        {
            "volume": "0",
            "symbol": "LUNA2/USD",
            "high": "0.63236",
            "last": "0.60505",
            "low": "0.60080",
            "bid": 0.59314,
            "ask": 0.61697,
            "id": 125,
            "changeRate": "-1.40%",
            "open": "0.61367"
        }
    ],
    "success": true
}
```

#### Response Parameters:

| Parameter Name | Type    | Description                  |
|----------------|---------|------------------------------|
| volume         | String  | Volume                       |
| symbol         | String  | Trading pairs                |
| high           | String  | Highest market price         |
| last           | String  | Market close price           |
| low            | String  | Lowest market price          |
| bid            | Decimal | Virgocx bid price            |
| ask            | Decimal | Virgocx ask price            |
| id             | Integer | Market Id                    |
| changeRate     | String  | Change rate in last 24 hours |
| open           | String  | Market open price            |

---

### 4. The latest completed history on the market

<br>

#### URL:

> https://virgocx.ca/api/market/trade

#### Request Method:

> GET

<br>

#### Request Parameters:

| Parameter Name | Required | Type   | Description                                                               |
|----------------|----------|--------|---------------------------------------------------------------------------|
| symbol         | Yes      | String | "/" needs to be added between the Market name and the Coin name (BTC/CAD) |

#### Request example:
> virgocx.ca/api/market/trade?symbol=BTC/CAD
> 
#### Response example:
```
{
    "code": 0,
    "msg": "success",
    "data": {
        "tradeList": [
            {
                "id": "12351556",
                "qty": 0.028395650000000000,
                "price": 34427.86,
                "type": 1,
                "createTime": 1686692928000,
                "doublePrice": 34427.86
            },
            {
                "id": "12351554",
                "qty": 0.085952220000000000,
                "price": 34903.110000000000000000,
                "type": 1,
                "createTime": 1686692690000,
                "doublePrice": 34903.11
            },
            {
                "id": "12351527",
                "qty": 0.000700000000000000,
                "price": 33942.280000000000000000,
                "type": 2,
                "createTime": 1686688931000,
                "doublePrice": 33942.28
            },
            {
                "id": "12351524",
                "qty": 0.001369460000000000,
                "price": 35057.510000000000000000,
                "type": 1,
                "createTime": 1686688822000,
                "doublePrice": 35057.51
            },
            {
                "id": "12351309",
                "qty": 0.000200000000000000,
                "price": 35220.000000000000000000,
                "type": 2,
                "createTime": 1686660953000,
                "doublePrice": 35220.0
            }
        ],
        "ts": 1686693389173
    },
    "success": true
}
```

#### Response Parameters:

| Parameter Name | Type    | Description                         |
|----------------|---------|-------------------------------------|
| id             | String  | Trade id                            |
| qty            | Decimal | Quantity                            |
| price          | Decimal | Price                               |
| type           | Integer | 1 Buy, 2 Sell                       |
| createTime     | Date    | Completion time in timeStamp format |
| doublePrice    | Double  | Price in double format              |
| ts             | Date    | Current timeStamp                   |

---
### 5. Account information

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
            "total": 0.0086,
            "balance": 0.0086,
            "coinName": "CAD",
            "freezingBalance": 0.0000
        },
        {
            "total": 35.0994,
            "balance": 35.0994,
            "coinName": "ARB",
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
### 6. Query user orders

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
| status         | No       | Integer | Order status        |

#### Request Example:
>https://virgocx.ca/api/member/queryOrder?apiKey=AAA&sign=BBB&symbol=BTC/CAD
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
            "createTime": 1674687750000,
            "price": null,
            "qty": 0.002900000000000000,
            "tradeQty": 0.002900000000000000,
            "id": 5915781451,
            "type": 2,
            "direction": 2,
            "status": 3
        },
        {
            "createTime": 1672336597000,
            "price": null,
            "qty": null,
            "tradeQty": 0.000764740000000000,
            "id": 5915760672,
            "type": 2,
            "direction": 1,
            "status": -1
        },
        {
            "createTime": 1654058408000,
            "price": null,
            "qty": null,
            "tradeQty": 0.000497430000000000,
            "id": 5915467829,
            "type": 3,
            "direction": 1,
            "status": -1
        },
        {
            "createTime": 1654058381000,
            "price": 40200.540000000000000000,
            "qty": 0.000400000000000000,
            "tradeQty": 0E-18,
            "id": 5915467828,
            "type": 1,
            "direction": 1,
            "status": -1
        },
        {
            "createTime": 1654058344000,
            "price": null,
            "qty": null,
            "tradeQty": 0.000497330000000000,
            "id": 5915467826,
            "type": 2,
            "direction": 1,
            "status": -1
        },
        {
            "createTime": 1653450306000,
            "price": null,
            "qty": null,
            "tradeQty": 0.000772020000000000,
            "id": 5915461772,
            "type": 3,
            "direction": 1,
            "status": -1
        },
        {
            "createTime": 1653449766000,
            "price": null,
            "qty": null,
            "tradeQty": 0.000774470000000000,
            "id": 5915461756,
            "type": 3,
            "direction": 1,
            "status": -1
        },
        {
            "createTime": 1653444675000,
            "price": null,
            "qty": null,
            "tradeQty": 0.002609770000000000,
            "id": 5915461681,
            "type": 2,
            "direction": 1,
            "status": -1
        },
        {
            "createTime": 1652726579000,
            "price": 20000.000000000000000000,
            "qty": 0.000500000000000000,
            "tradeQty": 0E-18,
            "id": 5915455405,
            "type": 1,
            "direction": 1,
            "status": -1
        },
        {
            "createTime": 1625036965000,
            "price": 43199.700000000000000000,
            "qty": 0.003000000000000000,
            "tradeQty": 0.003000000000000000,
            "id": 4436825255,
            "type": 1,
            "direction": 2,
            "status": 3
        },
        {
            "createTime": 1625036896000,
            "price": 43622.800000000000000000,
            "qty": 0.001500000000000000,
            "tradeQty": 0.001500000000000000,
            "id": 4436822307,
            "type": 1,
            "direction": 1,
            "status": 3
        },
        {
            "createTime": 1623730191000,
            "price": 49338.800000000000000000,
            "qty": 0.000405300000000000,
            "tradeQty": 0.000405300000000000,
            "id": 4381482507,
            "type": 1,
            "direction": 1,
            "status": 3
        },
        {
            "createTime": 1623730156000,
            "price": null,
            "qty": null,
            "tradeQty": 0.000405360000000000,
            "id": 4381481013,
            "type": 2,
            "direction": 1,
            "status": -1
        },
        {
            "createTime": 1623220130000,
            "price": 40894.200000000000000000,
            "qty": 0.000300000000000000,
            "tradeQty": 0E-18,
            "id": 4359685388,
            "type": 1,
            "direction": 1,
            "status": -1
        },
        {
            "createTime": 1623220058000,
            "price": null,
            "qty": null,
            "tradeQty": 0.000243430000000000,
            "id": 4359682287,
            "type": 2,
            "direction": 1,
            "status": -1
        },
        {
            "createTime": 1623219896000,
            "price": 41015.300000000000000000,
            "qty": 0.000300000000000000,
            "tradeQty": 0E-18,
            "id": 4359675356,
            "type": 1,
            "direction": 1,
            "status": -1
        },
        {
            "createTime": 1619157775000,
            "price": null,
            "qty": null,
            "tradeQty": 0.000499170000000000,
            "id": 4100049844,
            "type": 3,
            "direction": 1,
            "status": -1
        }
    ],
    "success": true
}
```

#### Response Parameters:

| Parameter Name | Type    | Description                                                    |
|----------------|---------|----------------------------------------------------------------|
| createTime     | Date    | Order create time                                              |
| price          | Decimal | Order price                                                    |
| qty            | Decimal | Order amount(qty)                                              |
| tradeQty       | Decimal | Matched amount(qty)                                            |
| id             | Integer | Order id                                                       |
| type           | Integer | Order type, 1 Limit order, 2 Market order, 3 Quick trade order |
| direction      | Integer | 1 Buy, 2 Sell                                                  |
| status         | Integer | -1 Canceled, 0 Placed, 1 Open, 2 Matching, 3 Completed         |
---
### 7. Query completed orders

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
            "createTime": "2023-01-26 07:02:31",
            "createTimeMs": 1674687751
        },
        {
            "id": "12230441",
            "amount": 17.359773890200000000000000000000,
            "qty": 0.000764740000000000,
            "price": 22700.230000000000000000,
            "type": "buy",
            "createTime": "2022-12-30 01:56:38",
            "createTimeMs": 1672336598
        },
        {
            "id": "12080372",
            "amount": 19.999610888400000000000000000000,
            "qty": 0.000497430000000000,
            "price": 40205.880000000000000000,
            "type": "buy",
            "createTime": "2022-06-01 12:40:08",
            "createTimeMs": 1654058408
        },
        {
            "id": "12080370",
            "amount": 19.999912098100000000000000000000,
            "qty": 0.000497330000000000,
            "price": 40214.570000000000000000,
            "type": "buy",
            "createTime": "2022-06-01 12:39:04",
            "createTimeMs": 1654058344
        },
        {
            "id": "12075098",
            "amount": 29.999948340600000000000000000000,
            "qty": 0.000772020000000000,
            "price": 38859.030000000000000000,
            "type": "buy",
            "createTime": "2022-05-25 11:45:06",
            "createTimeMs": 1653450306
        },
        {
            "id": "12075084",
            "amount": 29.999854430600000000000000000000,
            "qty": 0.000774470000000000,
            "price": 38735.980000000000000000,
            "type": "buy",
            "createTime": "2022-05-25 11:36:06",
            "createTimeMs": 1653449766
        },
        {
            "id": "12075022",
            "amount": 99.999653193400000000000000000000,
            "qty": 0.002609770000000000,
            "price": 38317.420000000000000000,
            "type": "buy",
            "createTime": "2022-05-25 10:11:15",
            "createTimeMs": 1653444675
        },
        {
            "id": "11756653",
            "amount": 129.654600000000000000000000000000,
            "qty": 0.003000000000000000,
            "price": 43218.200000000000000000,
            "type": "sell",
            "createTime": "2021-06-30 15:09:24",
            "createTimeMs": 1625036964
        },
        {
            "id": "11756650",
            "amount": 65.384700000000000000000000000000,
            "qty": 0.001500000000000000,
            "price": 43589.800000000000000000,
            "type": "buy",
            "createTime": "2021-06-30 15:08:15",
            "createTimeMs": 1625036895
        },
        {
            "id": "11749196",
            "amount": 19.989477060000000000000000000000,
            "qty": 0.000405300000000000,
            "price": 49320.200000000000000000,
            "type": "buy",
            "createTime": "2021-06-15 12:09:51",
            "createTimeMs": 1623730191
        },
        {
            "id": "11749194",
            "amount": 19.999975968000000000000000000000,
            "qty": 0.000405360000000000,
            "price": 49338.800000000000000000,
            "type": "buy",
            "createTime": "2021-06-15 12:09:16",
            "createTimeMs": 1623730156
        },
        {
            "id": "11746584",
            "amount": 9.999641883000000000000000000000,
            "qty": 0.000243430000000000,
            "price": 41078.100000000000000000,
            "type": "buy",
            "createTime": "2021-06-09 14:27:38",
            "createTimeMs": 1623220058
        },
        {
            "id": "11687269",
            "amount": 30.899671257000000000000000000000,
            "qty": 0.000499170000000000,
            "price": 61902.100000000000000000,
            "type": "buy",
            "createTime": "2021-04-23 14:02:55",
            "createTimeMs": 1619157775
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
| createTimeMs   | Date    | Completion time timeStamp format          |
---
### 8. Place Order

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

>III: Value of canadian dollars

#### Request example 3(category of market order and type is sell):

> https://virgocx.ca/api/member/addOrder?apiKey=AAA&symbol=BBB&sign=CCC&category=DDD&qty=EEE&type=GGG&country=HHH

>EEE: Value of qty

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

### 9. Cancel Order

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

### 10. Cancel Order

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
    "code":0,
    "msg":"success",
    "data":[
        {
            "volume":"0",
            "symbol":"BTC/CAD",
            "high":"33864.84",
            "last":"33839.85",
            "low":"33680.46",
            "bid":33298.34,
            "ask":34381.35,
            "id":24,
            "changeRate":"+0.08%",
            "open":"33809.50"
        },
        {
            "volume":"0",
            "symbol":"ETH/CAD",
            "high":"2215.85",
            "last":"2209.03",
            "low":"2203.67",
            "bid":2173.67,
            "ask":2244.38,
            "id":25,
            "changeRate":"+0.21%",
            "open":"2204.26"
        },
        {
            "volume":"0",
            "symbol":"USDC/CAD",
            "high":"1.3239",
            "last":"1.3229",
            "low":"1.3213",
            "bid":1.3016,
            "ask":1.344,
            "id":55,
            "changeRate":"-0.02%",
            "open":"1.3232"
        },
        {
            "volume":"0",
            "symbol":"ADA/CAD",
            "high":"0.349570",
            "last":"0.346358",
            "low":"0.345384",
            "bid":0.340731,
            "ask":0.351984,
            "id":68,
            "changeRate":"-0.61%",
            "open":"0.348490"
        },
        {
            "volume":"0",
            "symbol":"SOL/CAD",
            "high":"19.76",
            "last":"19.62",
            "low":"19.47",
            "bid":19.29,
            "ask":19.93,
            "id":75,
            "changeRate":"+0.15%",
            "open":"19.59"
        },
        {
            "volume":"0",
            "symbol":"AVAX/CAD",
            "high":"15.20",
            "last":"15.11",
            "low":"15.07",
            "bid":14.85,
            "ask":15.35,
            "id":79,
            "changeRate":"-0.46%",
            "open":"15.18"
        },
        {
            "volume":"0",
            "symbol":"DOT/CAD",
            "high":"5.8133",
            "last":"5.7906",
            "low":"5.7681",
            "bid":5.6976,
            "ask":5.8834,
            "id":69,
            "changeRate":"-0.08%",
            "open":"5.7956"
        },
        {
            "volume":"0",
            "symbol":"DOGE/CAD",
            "high":"0.0821072",
            "last":"0.0817154",
            "low":"0.0814499",
            "bid":0.0804001,
            "ask":0.0830306,
            "id":57,
            "changeRate":"+0.11%",
            "open":"0.0816216"
        },
        {
            "volume":"0",
            "symbol":"SHIB/CAD",
            "high":"0.00000897",
            "last":"0.00000892",
            "low":"0.00000891",
            "bid":0.00000876,
            "ask":0.00000907,
            "id":76,
            "changeRate":"-0.22%",
            "open":"0.00000894"
        },
        {
            "volume":"0",
            "symbol":"MATIC/CAD",
            "high":"0.7857",
            "last":"0.7803",
            "low":"0.7758",
            "bid":0.7677,
            "ask":0.7928,
            "id":71,
            "changeRate":"-0.01%",
            "open":"0.7804"
        },
        {
            "volume":"0",
            "symbol":"ARB/CAD",
            "high":"1.2732",
            "last":"1.2651",
            "low":"1.2506",
            "bid":1.2419,
            "ask":1.2881,
            "id":536,
            "changeRate":"+0.50%",
            "open":"1.2588"
        },
        {
            "volume":"0",
            "symbol":"ATOM/CAD",
            "high":"11.6602",
            "last":"11.6381",
            "low":"11.5358",
            "bid":11.4264,
            "ask":11.8497,
            "id":74,
            "changeRate":"+0.87%",
            "open":"11.5369"
        },
        {
            "volume":"0",
            "symbol":"IMX/CAD",
            "high":"0.811",
            "last":"0.802",
            "low":"0.798",
            "bid":0.785,
            "ask":0.817,
            "id":529,
            "changeRate":"-0.98%",
            "open":"0.810"
        },
        {
            "volume":"0",
            "symbol":"LTC/CAD",
            "high":"99.95",
            "last":"99.73",
            "low":"99.00",
            "bid":98.12,
            "ask":101.33,
            "id":30,
            "changeRate":"+0.23%",
            "open":"99.50"
        },
        {
            "volume":"0",
            "symbol":"LDO/CAD",
            "high":"2.301",
            "last":"2.275",
            "low":"2.257",
            "bid":2.232,
            "ask":2.316,
            "id":530,
            "changeRate":"+0.30%",
            "open":"2.268"
        },
        {
            "volume":"0",
            "symbol":"LINK/CAD",
            "high":"7.01392",
            "last":"6.96103",
            "low":"6.95325",
            "bid":6.83425,
            "ask":7.0878,
            "id":60,
            "changeRate":"-0.58%",
            "open":"7.00166"
        }
    ]
}
```
#### Response example(2):
```
{
    "code": 0,
    "msg": "success",
    "data": [
        {
            "volume": "0",
            "symbol": "ETH/CAD",
            "high": "2242.26",
            "last": "2240.76",
            "low": "2177.84",
            "bid": 2204.70,
            "ask": 2276.80,
            "id": 25,
            "changeRate": "+1.65%",
            "open": "2204.26"
        }
    ],
    "success": true
}
```
#### Response Parameters:

| Parameter Name | Type    | Description                  |
|----------------|---------|------------------------------|
| volume         | String  | Volume                       |
| symbol         | String  | Trading pairs                |
| high           | String  | Highest market price         |
| last           | String  | Market close price           |
| low            | String  | Lowest market price          |
| bid            | Decimal | Virgocx bid price            |
| ask            | Decimal | Virgocx ask price            |
| id             | Integer | Market id                    |
| changeRate     | String  | Change rate in past 24 hours |
| open           | String  | Market open price            |

---
