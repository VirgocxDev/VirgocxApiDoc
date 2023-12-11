# Snaplii API DOCS Version-0.0.2

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

step-4:Final parameters list used to call https://casnapliitest.virgocx.ca/v2/snaplii/getByMarketSymbol.
{
    "apiKey":"94e1cef3531c41bdbd420fc49359f5f2",
    "sign":"b60743ad70bad7d1fc47777c0d58604e",
    "marketSymbol":"BTC/CAD"
}
```
### 1. Market Price Change Info

#### URL:

> https://casnapliitest.virgocx.ca/v2/snaplii/getByMarketSymbol?apiKey=94e1cef3531c41bdbd420fc49359f5f2&sign=3d14adf8addcb373801229f2b97d6b32&marketSymbol=BTC/CAD

#### Request Method:

> GET

#### Request Parameters:

| Parameter Name | Required | Type   | Description                      |
|----------------|----------|--------|----------------------------------|
| apiKey         | Yes      | String | Non-production API Key See Above |
| sign           | Yes      | String | See Above example                |
| marketSymbol   | Yes      | String | BTC/CAD,ETH/CAD,DOGE/CAD         |

### Request Example:
> https://casnapliitest.virgocx.ca/v2/snaplii/getByMarketSymbolb

> https://casnapliitest.virgocx.ca/v2/app/snaplii/getByMarketSymbol

### Response Example:
```
{
    "code": 0,
    "msg": "success",
    "data": {
        "symbol": "BTC/CAD",
        "high": "51220.97",
        "buyOne": "39299.09",
        "last": "50437.11",
        "low": "50093.90",
        "changeRate": "-1.31%",
        "sellOne": "40577.21"
    },
    "success": true
}
```
#### Response Parameters:

| Parameter Name | Type   | Description                                 |
|----------------|--------|---------------------------------------------|
| symbol         | String | Market Name                                 |
| high           | String | last 24 hours highest price,real time value |
| last           | String | last trade price                            |
| low            | String | last 24 hours lowest price,real time value  |
| changeRate     | String | last 24 hours change rate, real time value  |
| sellOne        | String | latest sell order price on Virgo            |
| buyOne         | String | latest buy order price on Virgo             |
---
#### Note: If need more info return by this API, contact us, data is real time, call this API up to your design.

### 2. Coin Price Chart(K-line)

#### URL:

>https://casnapliitest.virgocx.ca/v2/snaplii/findListByMarketId
 
>https://casnapliitest.virgocx.ca/v2/app/snaplii/findListByMarketId

#### Request Method:

> GET

#### Request Parameters:

| Parameter Name | Required | Type    | Description                                                      |
|----------------|----------|---------|------------------------------------------------------------------|
| apiKey         | Yes      | String  | Non-production API Key See Above                                 |
| sign           | Yes      | String  | See Above example                                                |
| marketId       | Yes      | Integer | fix value 24,if support more coins later, we can provide new API |
| minType        | Yes      | Integer | See notes in the notes                                           |
<br>

#### Request Example:
> https://casnapliitest.virgocx.ca/v2/snaplii/findListByMarketId?apiKey=94e1cef3531c41bdbd420fc49359f5f2&sign=227c5febaa6c6a9fae80c3d61d71dd12&marketId=24&minType=1440

### Response Example:
```
{
    "code": 0,
    "msg": "success",
    "data": [
        {
            "id": 242728,
            "country": 1,
            "marketId": 24,
            "open": 36037.1,
            "high": 37012.15,
            "low": 35904.1,
            "close": 36147.66,
            "createTime": 1695009600000
        },
        {
            "id": 258407,
            "country": 1,
            "marketId": 24,
            "open": 36089.23,
            "high": 36952.64,
            "low": 35956.23,
            "close": 36582.23,
            "createTime": 1695081600000
        }
    ],
    "success": true
}
```
#### Response Parameters:

| Parameter Name | Type    | Description                                               |
|----------------|---------|-----------------------------------------------------------|
| id             | Integer | Record Id in our side                                     |
| country        | String  | Country ID                                                |
| marketId       | String  | Market ID of BTC/CAD                                      |
| open           | String  | Open price for that k-line data (1 hour in this example)  |
| high           | String  | high price for that k-line data (1 hour in this example)  |
| low            | Decimal | low price for that k-line data (1 hour in this example)   |
| close          | Decimal | close price for that k-line data (1 hour in this example) |
| createTime     | Integer | k-line creation time                                      |
---
#### 
Note:
* (1) 
* value list of minType
* minType 1, 1 minute
* minType 5, 5 minutes
* minType 10, 10 minutes
* minType 30, 30 minutes
* minType 60, 1 hour
* minType 240, 4 hours
* minType 1440, 1 day
* minType 10080, 1 week
* minType 43200, 1 month
* (2)
* if need we provide this page embed to your app, let us know, we can do that and provide you a page include related info. This API provide you
another choice to show BTC price change.
---
### 3. Redeem points to BTC(update On ASAP)
#### URL:

>https://casnapliitest.virgocx.ca/v2/snaplii/redeemPoints

>https://casnapliitest.virgocx.ca/v2/app/snaplii/redeemPoints
#### Request Method:

> GET

#### Request Parameters:

| Parameter Name | Required | Type    | Description                      |
|----------------|----------|---------|----------------------------------|
| apiKey         | Yes      | String  | Non-production API Key See Above |
| sign           | Yes      | String  | See Above example                |
| userId         | Yes      | String  | User Id on Virgo Side            |
| points         | Yes      | Integer | Amount of redeem points          |
<br>

#### Request Example:
> https://casnapliitest.virgocx.ca/v2/snaplii/redeemPoints?apiKey=94e1cef3531c41bdbd420fc49359f5f2&sign=1bb9c04a922d0e85dcfd4b1ae244d703&userId=180106745&points=5000

### Response Example:
```
{
    "code": 0,
    "msg": "success",
    "data": {
        "snapliiUserId": 180103132,
        "snapliiBalance": "300.0105305",
        "redeemUserId": 180106745,
        "redeemUserBalance": "21.79454698"
    },
    "success": true
}
```
#### Response Parameters:

| Parameter Name    | Type    | Description                                     |
|-------------------|---------|-------------------------------------------------|
| snapliiUserId     | Integer | Snaplii User ID on our side                     |
| snapliiBalance    | String  | BTC balance after client redeem points (reduce) |
| redeemUserId      | Integer | Redeem User ID on our side                      |
| redeemUserBalance | String  | BTC balance after redeem points (add)           |


#### 
Note:
* (1)
  If need more details in the response, we can discuss later.
* (2)
  Rate of points to btc should discuss later with our head of product Andy.
---

### 4. Detect user from Snaplii(update On ASAP)

### 5. Get User Id from Virgo
#### URL:

>https://casnapliitest.virgocx.ca/v2/snaplii/getUserId

>https://casnapliitest.virgocx.ca/v2/app/snaplii/getUserId
#### Request Method:

> GET

#### Request Parameters:

| Parameter Name | Required | Type     | Description                      |
|----------------|----------|----------|----------------------------------|
| apiKey         | Yes      | String   | Non-production API Key See Above |
| sign           | Yes      | String   | See Above example                |
| birthday       | Yes      | String   | User birthday                    |
| email          | Yes      | String   | Register email on virgo side     |
| postalCode     | Yes      | String   | PostalCode of address            |
<br>

#### Request Example:
> https://casnapliitest.virgocx.ca/v2/snaplii/getUserId?apiKey=94e1cef3531c41bdbd420fc49359f5f2&sign=691b3fae9f6bd56b74e10c2567da1a6d&birthday=1989-02-23&email=xiaofei19890223@outlook.com&postalCode=M2N6K1

### Response Example:
```
{
    "code": 0,
    "msg": "success",
    "data": {
        "userId": 180103132
    },
    "success": true
}
```
#### Response Parameters:

| Parameter Name | Type    | Description         |
|----------------|---------|---------------------|
| userId         | Integer | User ID on our side |
---
#### 
Note:
* (1)
We plan use three parameters include "email","birthday","postalCode" to inquire a client if already register on our side,if need more parameters or have another plan, we can discuss.
* (2)
This user is unique and will use in points redeem. 
---