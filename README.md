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

step-4:Final parameters list used to call www.virgocx.ca/api/member/addOrder.
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

> www.virgocx.ca/api/market/history/kline

#### Request Method:

> GET

<br>

#### Request Parameters:

| Parameter Name | Type    | Description                                                                                                                      |
|----------------|---------|----------------------------------------------------------------------------------------------------------------------------------|
| symbol         | String  | Trading pairs,divided by "/"(Such as ETH/CAD)                                                                                    |
| period         | Integer | K-Line Type (1 minutes-1, 5 minutes-5,10 minutes-10,30 minutes-30,1hr-60,4hrs-240,1day-1440,5days-7200,1week-10080,1month-43200) |

<br>


### Request Example:
> www.virgocx.ca/api/market/history/kline?symbol=ETH/CAD&period=43200

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
| marketId       | Integer | Market id            |
| low            | Decimal | Lowest market price  |
| high           | Decimal | Highest market price |
| close          | Decimal | Market close price   |
| open           | Decimal | Market open price    |
| qty            | Decimal | Quantity             |

---

### 2. Ticker Matching

<br>

#### URL:

> www.virgocx.ca/api/market/detail/merged

#### Request Method:

> GET

<br>

#### Request Parameters:

| Parameter Name | Required | Type   | Description                                                               |
|----------------|----------|--------|---------------------------------------------------------------------------|
| symbol         | Yes      | String | "/" needs to be added between the Market name and the Coin name (ETH/CAD) |

<br>

#### Request Example:
> www.virgocx.ca/api/market/detail/merged?symbol=ETH/CAD


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
        "buy": 2277.13,
        "sell": 2351.20,
        "id": 25,
        "changeRate": "-0.83%",
        "open": "2333.59"
    },
    "success": true
}
```
#### Response Parameters:

| Parameter Name | Type    | Description          |
|----------------|---------|----------------------|
| id             | Integer | K-Line id            |
| low            | Decimal | Lowest market price  |
| high           | Decimal | Highest market price |
| open           | Decimal | Market open price    |
| last           | Decimal | Market close price   |
| sell           | Decimal | Sell one price       |
| buy            | Decimal | Buy one price        |
| volume         | Decimal | Volume               |
| symbol         | String  | Trading pairs        |
| changeRate     | Decimal | Change rate          |

---

### 3. The latest tickers of all trading pairs

<br>

#### URL:

> www.virgocx.ca/api/market/tickers

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
            "buy": 33882.89,
            "sell": 34984.91,
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
            "buy": 0.3331,
            "sell": 0.3474,
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
            "buy": 28.97,
            "sell": 30.07,
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
            "buy": 0.5362,
            "sell": 0.5572,
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
            "buy": 0.847,
            "sell": 0.881,
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
            "buy": 0.2802,
            "sell": 0.2909,
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
            "buy": 35.53,
            "sell": 36.88,
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
            "buy": 0.02615,
            "sell": 0.02719,
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
            "buy": 0.59314,
            "sell": 0.61697,
            "id": 125,
            "changeRate": "-1.40%",
            "open": "0.61367"
        }
    ],
    "success": true
}
```

#### Response Parameters:

| Parameter Name | Type    | Description          |
|----------------|---------|----------------------|
| id             | Integer | K-Line id            |
| low            | Decimal | Lowest market price  |
| high           | Decimal | Highest market price |
| open           | Decimal | Market open price    |
| last           | Decimal | Market close price   |
| volume         | Decimal | Volume               |
| symbol         | String  | Trading pairs        |
| changeRate     | Decimal | Change rate          |

---

### 4. The latest completed history on the market

<br>

#### URL:

> www.virgocx.ca/api/market/trade

#### Request Method:

> GET

<br>

#### Request Parameters:

| Parameter Name | Required | Type   | Description                                                               |
|----------------|----------|--------|---------------------------------------------------------------------------|
| symbol         | Yes      | String | "/" needs to be added between the Market name and the Coin name (BTC/CAD) |

#### Request example:
> www.virgocx.ca/api/market/trade?symbol=BTC/CAD
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
| ts             | Long    | Current timeStamp                   |

---
### 5. Account information

<br>

#### URL:

> www.virgocx.ca/api/member/accounts

#### Request Method:

> GET

<br>

#### Request Parameters:

| Parameter Name | Required | Type   | Description         |
|----------------|----------|--------|---------------------|
| apiKey         | Yes      | String | User private key    |
| sign           | Yes      | String | Parameter signature |

#### Request Example:
> www.virgocx.ca/api/member/accounts?apiKey=AAA&sign=BBB
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

| Parameter Name  | Type    | Description    |
|-----------------|---------|----------------|
| freezingBalance | Decimal | Frozen balance |
| total           | Decimal | Total quantity |
| balance         | Decimal | Balance        |
| coinName        | String  | Coin name      |

---
### 6. Query user orders

<br>

#### URL:

> www.virgocx.ca/api/member/queryOrder

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
>www.virgocx.ca/api/member/queryOrder?apiKey=AAA&sign=BBB&symbol=BTC/CAD
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

| Parameter Name | Type     | Description                                                    |
|----------------|----------|----------------------------------------------------------------|
| price          | Decimal  | Order price                                                    |
| qty            | Decimal  | Order quantity                                                 |
| tradeQty       | Decimal  | Matched quantity                                               |
| id             | Integer  | Order id                                                       |
| type           | Integer  | Order type, 1 Limit order, 2 Market order, 3 Quick trade order |
| direction      | Integer  | 1 Buy, 2 Sell                                                  |
| status         | Integer  | -1 Canceled, 0 Placed, 1 Open, 2 Matching, 3 Completed         |
---
### 7. Query completed orders

<br>

#### URL:

> www.virgocx.ca/api/member/queryTrade

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

> https://www.virgocx.ca/api/member/queryTrade?apiKey=AAA&sign=BBB&symbol=CCC
<br>

>AAA: Your API key

>BBB: Value of sign

>CCC: Value of symbol

#### Response example:
```
{
	"code": 0,
	"msg": "success",
	"data": [{
		"id": 1,
		"amount": 12.000000000000000000000000000000,
		"qty": 1.000000000000000000,
		"price": 12.000000000000000000,
		"type": "buy",
		"createTime": "2019-04-28 15:34:11.0",
		"createTimeMs": 1556436851000
	}],
	"success": true
}
```

#### Response Parameters:

| Parameter Name | Type    | Description                      |
|----------------|---------|----------------------------------|
| id             | String  | Trade Id                         |
| amount         | Decimal | Total amount                     |
| qty            | Decimal | Quantity                         |
| price          | Decimal | Price                            |
| type           | String  | Buy or Sell                      |
| createTime     | String  | Completion time String format    |
| createTimeMs   | Long    | Completion time timeStamp format |
---
### 8. Place Order

<br>

#### URL:

> www.virgocx.ca/api/member/addOrder

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

> https://www.virgocx.ca/api/member/addOrder?apiKey=AAA&symbol=BBB&sign=CCC&category=DDD&qty=EEE&price=FFF&type=GGG&country=HHH
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

> https://www.virgocx.ca/api/member/addOrder?apiKey=AAA&symbol=BBB&sign=CCC&category=DDD&total=III&type=GGG&country=HHH

>III: Value of canadian dollars

#### Request example 3(category of market order and type is sell):

> https://www.virgocx.ca/api/member/addOrder?apiKey=AAA&symbol=BBB&sign=CCC&category=DDD&qty=EEE&type=GGG&country=HHH

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

| Parameter Name | Type    | Description |
|----------------|---------|-------------|
| orderId        | Integer | Order Id    |
---

### 9. Cancel Order

<br>

#### URL:

> www.virgocx.ca/api/member/cancelOrder

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

> www.virgocx.ca/api/member/cancelOrder?apiKey=AAA&sign=BBB&id=CCC
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

---