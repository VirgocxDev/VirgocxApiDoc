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
| symbol         | String  | Trading pairs,divided by "/"(Such as ETH/BTC)                                                                                    |
| period         | Integer | K-Line Type (1 minutes-1, 5 minutes-5,10 minutes-10,30 minutes-30,1hr-60,4hrs-240,1day-1440,5days-7200,1week-10080,1month-43200) |

<br>

```
Response example here...
{
	"code": 0,
	"msg": "success",
	"success": true,
	"data": [{
		"id": 1,
		"marketId": 21,
		"open": 1.0,
		"high": 1.0,
		"low": 1.0,
		"close": 1.0,
		"qty": 1.0,
		"createTime": 1557211356000
	}]
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

| Parameter Name | Required | Type   | Description                                                                |
|----------------|----------|--------|----------------------------------------------------------------------------|
| symbol         | Yes      | String | "/" needs to be added between the Market name and the Coin name (btc/usdt) |

<br>

```
Response example here...
{
	"code": 0,
	"msg": "success",
	"success": true,
	"data": {
		"volume": "0.0000",
		"symbol": "EURS/ETH",
		"high": "0.0000",
		"last": "0.0000",
		"low": "0.0000",
		"buy": 1.9000,
		"sell": 2.0000,
		"id": 21,
		"changeRate": "+0.00%",
		"open": "0.0000"
	}
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

```
Response example here...
{
	"code": 0,
	"msg": "success",
	"success": true,
	"data": [{
		"volume": "0.0000",
		"symbol": "EURS/ETH",
		"high": "0.0000",
		"last": "0.0000",
		"low": "0.0000",
		"buy": 1.9000,
		"sell": 2.0000,
		"id": 21,
		"changeRate": "+0.00%",
		"open": "0.0000"
	}, {
		"volume": "0.0",
		"symbol": "ETH/X",
		"high": "0.0",
		"last": "0.0",
		"low": "0.0",
		"id": 22,
		"changeRate": "+0.00%",
		"open": "0.0"
	}, {
		"volume": "0.00",
		"symbol": "ETH/USDT",
		"high": "0.00",
		"last": "0.00",
		"low": "0.00",
		"id": 12,
		"changeRate": "+0.00%",
		"open": "0.00"
	}, {
		"volume": "0.00",
		"symbol": "BTC/USDT",
		"high": "0.00",
		"last": "0.00",
		"low": "0.00",
		"id": 13,
		"changeRate": "+0.00%",
		"open": "0.00"
	}, {
		"volume": "0.0000",
		"symbol": "PAX/USDT",
		"high": "0.0000",
		"last": "0.0000",
		"low": "0.0000",
		"id": 16,
		"changeRate": "+0.00%",
		"open": "0.0000"
	}, {
		"volume": "0.0000",
		"symbol": "USDC/USDT",
		"high": "0.0000",
		"last": "0.0000",
		"low": "0.0000",
		"id": 17,
		"changeRate": "+0.00%",
		"open": "0.0000"
	}, {
		"volume": "0.0000",
		"symbol": "GUSD/USDT",
		"high": "0.0000",
		"last": "0.0000",
		"low": "0.0000",
		"id": 18,
		"changeRate": "+0.00%",
		"open": "0.0000"
	}, {
		"volume": "0.0000",
		"symbol": "EURS/USDT",
		"high": "0.0000",
		"last": "0.0000",
		"low": "0.0000",
		"id": 19,
		"changeRate": "+0.00%",
		"open": "0.0000"
	}, {
		"volume": "0.0000",
		"symbol": "HKDT/USDT",
		"high": "0.0000",
		"last": "0.0000",
		"low": "0.0000",
		"id": 20,
		"changeRate": "+0.00%",
		"open": "0.0000"
	}]
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

### 4. Market Depth

<br>

#### URL:

> www.virgocx.ca/api/market/depth

#### Request Method:

> GET

<br>

#### Request Parameters:

| Parameter Name | Required | Type   | Description                                                                |
|----------------|----------|--------|----------------------------------------------------------------------------|
| symbol         | Yes      | String | "/" needs to be added between the Market name and the Coin name (btc/usdt) |

```
Response example here...
{
	"code": 0,
	"msg": "success",
        "success": true,
	"data": {
		"asks": [{
			"price": 2.0000,
			"qty": 0.0000,
			"volume": 0.0000
		}],
		"bids": [{
			"price": 1.9000,
			"qty": 1.0000,
			"volume": 1.9000
		}, {
			"price": 1.7000,
			"qty": 0.0000,
			"volume": 0.0000
		}, {
			"price": 1.6000,
			"qty": 1.0000,
			"volume": 1.6000
		}, {
			"price": 1.4000,
			"qty": 0.0000,
			"volume": 0.0000
		}, {
			"price": 1.3000,
			"qty": 1.0000,
			"volume": 1.3000
		}, {
			"price": 1.1000,
			"qty": 0.0000,
			"volume": 0.0000
		}],
		"ts": 1557905596952
	}
}
```

#### Response Parameters:

| Parameter Name | Type    | Description |
|----------------|---------|-------------|
| price          | Decimal | Price       |
| volume         | Decimal | Volume      |
| qty            | Decimal | Quantity    |
| ts             | Long    | TimeStamp   |

---

### 5. The latest completed history on the market

<br>

#### URL:

> www.virgocx.ca/api/market/trade

#### Request Method:

> GET

<br>

#### Request Parameters:

| Parameter Name | Required | Type   | Description                                                                |
|----------------|----------|--------|----------------------------------------------------------------------------|
| symbol         | Yes      | String | "/" needs to be added between the Market name and the Coin name (btc/usdt) |

```
Response example here...
{
   "code":0,
   "msg":"success",
   "data":{
            "tradeList":[{
                          "id":"12035066",
                          "qty":0.0005804,
                          "price":51113.7,
                          "type":1,
                          "createTime":1650594315000,
                          "doublePrice":51113.7
                        },
                        {
                          "id":"12035056",
                          "qty":0.0051073,
                          "price":51102.8,
                          "type":1,
                          "createTime":1650590515000,
                          "doublePrice":51102.8
                         },
                         {
                          "id":"12035054",
                          "qty":0.00049563,
                          "price":51247.6,
                          "type":1,
                          "createTime":1650588967000,
                          "doublePrice":51247.6
                        }],
            "ts":1650595525220
           },
   "success":true
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
### 6. Account information

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
```
Response example here...
{
	"code": 0,
	"msg": "success",
	"data": [{
		"freezingBalance": 1.0000,
		"total": 5000.0000,
		"balance": 4999.0000,
		"coinName ": "ETH"
	}, {
		"freezingBalance": 0.0000,
		"total": 20000.0000,
		"balance": 20000.0000,
		"coinName ": "X"
	}, {
		"freezingBalance": 0.0000,
		"total": 4.0000,
		"balance": 4.0000,
		"coinName ": "USDT"
	}, {
		"freezingBalance": 0.0000,
		"total": 0.0000,
		"balance": 0.0000,
		"coinName ": "EURS"
	}],
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
### 7. Query user orders

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
```
Response example here...
{
	"code": 0,
	"msg": "success",
	"data": [{
		"price": 2.000000000000000000,
		"qty": 2.000000000000000000,
		"tradeQty": 2.000000000000000000,
		"id": 13,
		"type": 1,
		"direction": 2,
		"status": 1
	}, {
		"price": 1.400000000000000000,
		"qty": 1.000000000000000000,
		"tradeQty": 1.000000000000000000,
		"id": 6,
		"type": 1,
		"direction": 1,
		"status": 1
	}, {
		"price": 2.000000000000000000,
		"qty": 2.000000000000000000,
		"tradeQty": 2.000000000000000000,
		"id": 5,
		"type": 1,
		"direction": 2,
		"status": 1
	}, {
		"price": 1.100000000000000000,
		"qty": 1.000000000000000000,
		"tradeQty": 1.000000000000000000,
		"id": 2,
		"type": 1,
		"direction": 1,
		"status": 1
	}],
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
### 8. Query completed orders

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
```
Response example here...
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
### 9. Place Order

<br>

#### URL:

> www.virgocx.ca/api/member/addOrder

#### Request Method:

> POST

<br>

#### Request Parameters:

| Parameter Name | Required | Type    | Description                            |
|----------------|----------|---------|----------------------------------------|
| apiKey         | Yes      | String  | User private key                       |
| sign           | Yes      | String  | Parameter signature                    |
| symbol         | Yes      | String  | Trading pairs                          |
| category       | Yes      | Integer | Order Category, 1 Limit, 3 Quick Trade |
| type           | Yes      | Integer | Order type, 1 Buy, 2 Sell              |
| price          | Yes      | Decimal | Price                                  |
| qty            | Yes      | Decimal | Quantity                               |
| country        | Yes      | Integer | Canada:1                               |
```
Response example here...
{
	"code": 0,
	"msg": "success",
	"data": {
		"orderId": 15
	},
	"success": true
}
```

#### Response Parameters:

| Parameter Name | Type    | Description |
|----------------|---------|-------------|
| orderId        | Integer | Order Id    |
---

### 10. Cancel Order

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
```
Response example here...
{
    "code": 0, 
    "msg": "success", 
    "data": "successful Cancel!", 
    "success": true
}
```

#### Response Parameters:NO

---