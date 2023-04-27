# Spot trading

## public

### Security Type: None

#### Test connection
Request method: [GET](#fenced-code-block)

URL : [https://openapi.xxx.com/sapi/v1/ping](#fenced-code-block)

#####describe
* Test the connectivity of the REST API

#####Parameters
* No parameters

#####Responses
`
{
    🟩200: OK
}
`

<br>
####server time
Request method: [GET](#fenced-code-block)

URL : [https://openapi.xxx.com/sapi/v1/time](#fenced-code-block)

#####describe
* Get server time

#####Parameters
* No parameters

#####Responses
🟩200: OK
```
{
     "timezone": "GMT+08:00",
     "serverTime": 1595563624731
}
```


<br>
####Coin pair list
Request method: [GET](#fenced-code-block)

URL : [https://openapi.xxx.com/sapi/v1/symbols](#fenced-code-block)

#####describe
* The currency pairs supported by the market esponse:
* Name type example description timelong `1595563624731` current time (Unix Timestamp, milliseconds ms) bidslist is as follows: order book buying information askslist is as follows: order book selling information The information corresponding to bids and asks represents all prices in the order book and the corresponding prices Quantity information, arranged by the best price from top to bottom Name type Example description' 'float`131.1`price' 'float`2.3` The quantity corresponding to the current price GEThttps://openapi.xxx.com/sapi/v1/ticker \

#####Parameters
* No parameters

#####Responses
  🟩200: OK

```javascript
{
     "symbols": [
         {
             "quantityPrecision": 3,
             "symbol": "sccadai",
             "pricePrecision": 6,
             "baseAsset": "SCCA",
             "quoteAsset": "DAI"
         },
         {
             "quantityPrecision": 8,
             "symbol": "btcusdt",
             "pricePrecision": 2,
             "baseAsset": "BTC",
             "quoteAsset": "USDT"
         },
         {
             "quantityPrecision": 3,
             "symbol": "bchusdt",
             "pricePrecision": 2,
             "baseAsset": "BCH",
             "quoteAsset": "USDT"
         },
         {
             "quantityPrecision": 2,
             "symbol": "etcdt",
             "pricePrecision": 2,
             "baseAsset": "ETC",
             "quoteAsset": "USDT"
         },
         {
             "quantityPrecision": 2,
             "symbol": "ltcbtc",
             "pricePrecision": 6,
             "baseAsset": "LTC",
             "quoteAsset": "BTC"
         }
     ]
}
```
**Weight (IP/UID): 1**

#### Response: <a href="#bi-dui-lie-biao" id="bi-dui-lie-biao"></a>

| Name | Type | Example | Description |
| ----------------- | ------- | --------- | ------ |
| symbol | string | `BTCUSDT` | currency pair name |
| baseAsset | string | `BTC` | base currency |
| quoteAsset | string | `USDT` | quote currency |
| pricePrecision | integer | `2` | price precision |
| quantityPrecision | integer | `6` | quantity precision |

<br>
<br>
## market
### Security Type: None

#### order book
Request method: [GET](#fenced-code-block)

URL : [https://openapi.xxx.com/sapi/v1/depth](#fenced-code-block)

#####describe
* Market order thin depth information

#####Parameters
######Query

| parameter name | type | example |
| ----------- | ----------- | ----------- |
| Limit | integer | default 100; maximum 100 |
| synbol | String | BTCUSDT |

#####Responses
* 🟩200: OK Successfully obtained depth information

```javascript
{
   "bids": [
     [
       "3.90000000", // price
       "431.00000000" // Quantity
     ],
     [
       "4.00000000",
       "431.00000000"
     ]
   ],
   "asks": [
     [
       "4.00000200", // price
       "12.00000000" // Quantity
     ],
     [
       "5.10000000",
       "28.00000000"
     ]
   ]
}
```

**Weight (IP/UID): 5**

#### Response: <a href="#bi-dui-lie-biao" id="bi-dui-lie-biao"></a>

| time | long | `1595563624731` | current time (Unix Timestamp, milliseconds ms) |
| ---- | ---- | --------------- | ----------------------- --- |
| bids | list | as follows | order book buying information |
| asks | list | as follows | order book selling information |

The information corresponding to bids and asks represents all the prices of the order book and the information of the quantity corresponding to the price, and is arranged from top to bottom by the best price

| ' ' | float | `131.1` | price |
| --- | ----- | ------- | --------- |
| ' ' | float | `2.3` | Quantity corresponding to the current price |




<br>
#### Quotes ticker
Request method: [GET](#fenced-code-block)

URL : [https://openapi.xxx.com/sapi/v1/klines](#fenced-code-block)

#####describe
* 24 hours price change data

#####Parameters
######Query

| parameter name | type | example |
| ----------- | ----------- | ----------- |
| symbol | String | currency pair name E.g.BTCUSDT |
| interval | String | k-line chart interval, the identifiable sent values are: 1min, 5min, 15min, 30min, 60min, 1day, 1week, 1month (min=minute, h=hour, day=day, week=week, month = month) |

#####Responses
* 🟩200: OK Successfully obtained ticker information


```javascript
{
     "high": "9279.0301",
     "vol": "1302",
     "last": "9200",
     "low": "9279.0301",
     "rose": "0",
     "time": 1595563624731
}
```

**Weight (IP/UID): 5**

#### Response:

| time | long | `1595563624731` | timestamp |
| ---- | ----- | --------------- | ------|
| high | float | `9900` | highest price |
| low | float | `8800.34` | lowest price |
| open | float | `8700` | opening price |
| last | float | `8900` | latest price |
| vol | float | `4999` | transaction volume |

<br>
####最近成交
Request method : [GET](#fenced-code-block)

URL : [https://openapi.xxx.com/sapi/v1/trades](#fenced-code-block)

#####描述
* 最近成交

#####Parameters
######Query

| 参数名      | 类型 | 示例 |
| ----------- | ----------- | ----------- |
| limit      | integer       | 默认100；最大100       |
| synbol*    | Text        | Text        |

#####Responses
* 🟩200: OK 成功

```javascript
{
    "list":[
        {
            "price":"3.00000100",
            "qty":"11.00000000",
            "time":1499865549590,
            "side":"BUY"
        }
    ]
}
```


**权重(IP/UID): 5**

#### Response:

| price | float  | `0.055`         | 交易价格             |   
| ----- | ------ | --------------- | ---------------- | - |
| time  | long   | `1537797044116` | 当前Unix时间戳，毫秒(ms) |   
| qty   | float  | `5`             | 数量（张数）           |   
| side  | string | `BUY/SELL`      | 主动单方向            |   




<br>
####K线/蜡烛图数据
Request method : [GET](#fenced-code-block)

URL : [https://openapi.xxx.com/sapi/v1/trades](#fenced-code-block)

#####Parameters
######Query

| 参数名      | 类型 | 示例 |
| ----------- | ----------- | ----------- |
| synbol*    | String        | BTCUSDT        |
| interval      | integer       |k线图区间, 可识别发送的值为：1min,5min,15min,30min,60min,1day,1week,1month（min=分钟，h=小时,day=天，week=星期，month=月）      |

#####Responses
* 🟩200: OK 成功


```javascript
[
    {
        "high": "6228.77",
        "vol": "111",
        "low": "6228.77",
        "idx": 1594640340,
        "close": "6228.77",
        "open": "6228.77"
    },
    {
        "high": "6228.77",
        "vol": "222",
        "low": "6228.77",
        "idx": 1587632160,
        "close": "6228.77",
        "open": "6228.77"
    },
    {
        "high": "6228.77",
        "vol": "333",
        "low": "6228.77",
        "idx": 1587632100,
        "close": "6228.77",
        "open": "6228.77"
    }
]
```
**权重(IP/UID): 1**

#### Response:

| `idx` | long  | `1538728740000` | 开始时间戳，毫秒（ms）   |   
| ----- | ----- | --------------- | -------------- | 
| open  | float | `36.00000`      | 开盘价            |   
| close | float | `33.00000`      | 收盘价            |   
| high  | float | `36.00000`      | 最高价            |   
| low   | float | `30.00000`      | 最低价            |   
| vol   | float | `2456.111`      | <p>成交量<br></p> |   

<br>
<br>
## 交易

### 安全类型: TRADE

#####交易下方的接口都需要签名和API-Key验证

####创建新订单
Request method : [POST](#fenced-code-block)

URL : [https://openapi.xxx.com/sapi/v1/order](#fenced-code-block)

#####描述
* 限速规则：100次/2s

#####Parameters
######Header
| 参数名      | 类型 | 示例 |
| ----------- | ----------- | ----------- |
| X-CH-SIGN  | String        | 签名        |
| X-CH-APIKEY     | String       |您的API-Key     |
| X-CH-TS     | integer       |时间戳     |
######Body
| 参数名      | 类型 | 示例 |
| ----------- | ----------- | ----------- |
| symbol*  |      String  | 币对名称        |
| volume*     | number       |订单数量     |
| side*     |    String   |订单方向 BUY/SELL     |
| type*    |     String  |   订单类型 LIMIT/MARKET  |
| price     |   number    |订单价格,对于LIMIT订单必须发送    |
| newClientorderId     |       |客户端订单标识    |
| recvwindow    |    number   |时间窗口     |

#####Responses
* 🟩200: OK 成功


```javascript
{
    'symbol': 'LXTUSDT', 
    'orderId': '150695552109032492', 
    'clientOrderId': '157371322565051',
    'transactTime': '1573713225668', 
    'price': '0.005452', 
    'origQty': '110', 
    'executedQty': '0', 
    'status': 'NEW',
    'type': 'LIMIT', 
    'side': 'SELL'
}
```
**权重(IP/UID): 5**
#### Response:

|  |   |          |              |   
| ----- | ------ | --------------- | ---------------- | - |
| price  | float   | `0.055` | 交易价格   |  
| time  | long   | `1537797044116` | 当前Unix时间戳，毫秒(ms) |   
| qty   | float  | `5`             | 数量（张数）           |   
| side  | string | `BUY/SELL`      | 主动单方向            |   

|     |   |  |                                                                                                 |   
| ------------- | ------- | -------------------- | ---------------------------------------------------------------------------------------------------------- | 
| orderId       | long    | `150695552109032492` | 订单ID（系统生成）                                                                                                 | 
| clientorderId | string  | `213443`             | 订单ID（自己发送的）                                                                                                |   
| symbol        | string  | `BTCUSDT`            | 币对名称                                                                                                       |   
| transactTime  | integer | `1273774892913`      | 订单创建时间                                                                                                     |   
| price         | float   | `4765.29`            | 订单价格                                                                                                       |   
| origQty       | float   | `1.01`               | 订单数量                                                                                                       |   
| executedQty   | float   | `1.01`               | 已经成交订单数量                                                                                                   |   
| type          | string  | `LIMIT`              | 订单类型`LIMIT`(限价)`MARKET`（市价）                                                                                |   
| side          | string  | `BUY`                | 订单方向。可能出现的值只能为：`BUY`（买入做多） 和 `SELL`（卖出做空）                                                                  |   
| status        | string  | `NEW`                | 订单状态。可能出现的值为：`NEW`(新订单，无成交)、`PARTIALLY_FILLED`（部分成交）、`FILLED`（全部成交）、`CANCELED`（已取消）和`REJECTED`（订单被拒绝）.POST |  

<br>
####Create test order
Request method: [POST](#fenced-code-block)

URL : [https://openapi.xxx.com/sapi/v1/order/test](#fenced-code-block)

#####describe
* Create and verify new orders, but will not be sent to the matching engine

#####Parameters
######Query
| parameter name | type | example |
| ----------- | ----------- | ----------- |
| X-CH-SIGN | String | Signature |
| X-CH-APIKEY | String | Your API-Key |
| X-CH-TS | integer |time stamp |
######Header
| parameter name | type | example |
| ----------- | ----------- | ----------- |
| symbol* | String | currency pair name |
| volume* | number |order quantity |
| side* | String |Order direction BUY/SELL |
| type* | String | order type LIMIT/MARKET |
| price | number | order price, must send for LIMIT order |
| newClientorderId | |Client order ID |
| recvwindow | number | time window |

#####Responses
* 🟩200: OK success


```javascript
{
     // Response
}
```

**Weight (IP/UID): 1**

****

****
####Batch order
Request method: [POST](#fenced-code-block)

URL : [https://openapi.xxx.com/sapi/v1/batchOrders](#fenced-code-block)

#####describe
* A batch of up to 10 orders

#####Parameters
######Header
| parameter name | type | example |
| ----------- | ----------- | ----------- |
| X-CH-SIGN | String | Signature |
| X-CH-APIKEY | String | Your API-Key |
| X-CH-TS | integer |time stamp |
######Body
| parameter name | type | example |
| ----------- | ----------- | ----------- |
| symbol* | String | currency pair name |
| orders* | number |Batch order information up to 10 |

#####Responses
* 🟩200: OK success

**Weight (IP/UID): 10**

#### Resquest `orders` field: <a href="#resquest-orders-field" id="resquest-orders-field"></a>

| price | long | 1000 | price |
| --------- | ------ | -------------- | -- |
| volume | folat | 20.1 | quantity |
| side | string | `BUY/SELL` | direction |
| batchType | string | `LIMIT/MARKET` | type |





####Order Tracking
Request method: [GET](#fenced-code-block)

URL : [https://openapi.xxx.com/sapi/v1/order](#fenced-code-block)

#####describe
* Speed limit rule: 20 times/2s

#####Parameters
######Query

| parameter name | type | example |
| ----------- | ----------- | ----------- |
| orderId* | | order id |
| newClientorderId | integer |Client order ID |
| symbol* | |Coin pair name BTCUSDT |
######Header
| parameter name | type | example |
| ----------- | ----------- | ----------- |
| X-CH-SIGN | String | Signature |
| X-CH-APIKEY | String | Your API-Key |
| X-CH-TS | integer |time stamp |

#####Responses
* 🟩200: OK success

**Weight (IP/UID): 1**

#### **Response:**

| orderId | long | `150695552109032492` | order ID (generated by the system) |
| ------------- | ------- | -------------------- | ------ -------------------------------------------------- -------------------------------------------------- |
| clientorderId | string | `213443` | order ID (sent by yourself) |
| symbol | string | `BTCUSDT` | currency pair name |
| transactTime | integer | `1273774892913` | order creation time |
| price | float | `4765.29` | order price |
| origQty | float | `1.01` | order quantity |
| executedQty | float | `1.01` | Quantity of executed orders |
| avgPrice | float | `4754.24` | The average price of the order that has been executed |
| side | string | `BUY` | Order direction. The possible values can only be: `BUY` (buy long) and `SELL` (sell short) | |
| status | string | `NEW` | Order status. Possible values are: `NEW` (new order, no fill), `PARTIALLY_FILLED` (partial fill), `FILLED` (full fill), `CANCELED` (cancelled), and `REJECTED` (order rejected). POST |
####Cancel order
Request method: [POST](#fenced-code-block)

URL : [https://openapi.xxx.com/sapi/v1/cancel](#fenced-code-block)

#####describe
* Speed limit rule: 100 times/2s

#####Parameters
######Header
| parameter name | type | example |
| ----------- | ----------- | ----------- |
| X-CH-SIGN | String | Signature |
| X-CH-APIKEY | String | Your API-Key |
| X-CH-TS | integer |time stamp |
######Body
| parameter name | type | example |
| ----------- | ----------- | ----------- |
| orderId* | | order id |
| newClientorderId | String |Client order ID |
| symbol* | String |Token pair name |
| type* | String | order type LIMIT/MARKET |
| price | number | order price, must send for LIMIT order |
| newClientorderId | |Client order ID |
| recvwindow | number | time window |

#####Responses
* 🟩200: OK Cancellation successful
**Weight (IP/UID): 5**

#### Response:

| orderId | long | `150695552109032492` | order ID (generated by the system) |
| ------------- | ------ | -------------------- | ------- -------------------------------------------------- -------------------------------------------------- |
| clientorderId | string | `213443` | order ID (sent by yourself) |
| symbol | string | `BTCUSDT` | currency pair name |
| status | string | `NEW` | Order status. Possible values are: `NEW` (new order, no fill), `PARTIALLY_FILLED` (partial fill), `FILLED` (full fill), `CANCELED` (cancelled) and `REJECTED` (order rejected). POST |





#### Batch cancellation of orders
Request method: [POST](#fenced-code-block)

URL : [https://openapi.xxx.com/sapi/v1/batchCancel](#fenced-code-block)

#####describe
* A batch of up to 10 orders

#####Parameters
######Header
| parameter name | type | example |
| ----------- | ----------- | ----------- |
| X-CH-SIGN | String | Signature |
| X-CH-APIKEY | String | Your API-Key |
| X-CH-TS | integer |time stamp |
######Body
| parameter name | type | example |
| ----------- | ----------- | ----------- |
| orderIds* | | The collection of order ids to be canceled [123,456] Responses200GET |
| symbol* | String |Token pair name |

#####Responses
* 🟩200: OK Cancellation successful


```javascript
{
     "success": [
         165964665990709251,
         165964665990709252,
         165964665990709253
     ],
     "failed": [ //The cancellation failure is generally because the order does not exist or the order status has reached the final state
         165964665990709250
     ]
}
```
{% endswagger-response %}
{% endswagger %}

**Weight (IP/UID): 10**

****

****


<br>

####Current order
Request method: [GET](#fenced-code-block)

URL : [https://openapi.xxx.com/sapi/v1/openOrders](#fenced-code-block)

#####describe
* Speed limit rule: 20 times/2s

#####Parameters
######Query

| parameter name | type | example |
| ----------- | ----------- | ----------- |
| symbol* | |Coin pair name BTCUSDT |
######Header
| parameter name | type | example |
| ----------- | ----------- | ----------- |
| X-CH-SIGN | String | Signature |
| X-CH-APIKEY | String | Your API-Key |
| X-CH-TS | integer |time stamp |

#####Responses
* 🟩200: OK success


```javascript
[
     {
         'orderId': '499902955766523648',
         'symbol': 'BHTUSDT',
         'price': '0.01',
         'origQty': '50',
         'executedQty': '0',
         'avgPrice': '0',
         'status': 'NEW',
         'type': 'LIMIT',
         'side': 'BUY',
         'time': '1574329076202'
         },...
]
```
{% endswagger-response %}
{% endswagger %}

#### **Weight (IP/UID): 1**

**Response:**

| orderId | long | `150695552109032492` | order ID (generated by the system) |
| ------------- | ------ | -------------------- | ------- -------------------------------------------------- -------------------------------------------------- |
| clientorderId | string | `213443` | order ID (sent by yourself) |
| symbol | string | `BTCUSDT` | currency pair name |
| price | float | `4765.29` | order price |
| origQty | float | `1.01` | order quantity |
| executedQty | float | `1.01` | Quantity of executed orders |
| avgPrice | float | `4754.24` | The average price of the order that has been executed |
| type | string | `LIMIT` | order type `LIMIT` (limit price) `MARKET` (market price) |
| side | string | `BUY` | order
<br>
####Transaction Record
Request method: [GET](#fenced-code-block)

URL : [https://openapi.xxx.com/sapi/v1/myTrades](#fenced-code-block)

#####describe
* Speed limit rule: 20 times/2s

#####Parameters
######Query

| parameter name | type | example |
| ----------- | ----------- | ----------- |
| symbol* | |Coin pair name BTCUSDT |
| limit* | | default 100, maximum 1000 |
| fromId* | |Coin pair name BTCUSDT |
######Header
| parameter name | type | example |
| ----------- | ----------- | ----------- |
| X-CH-SIGN | String | Signature |
| X-CH-APIKEY | String | Your API-Key |
| X-CH-TS | integer |time stamp |

#####Responses
* 🟩200: OK success
```javascript
[
   {
     "symbol": "ETHBTC",
     "id": 100211,
     "bidId": 150695552109032492,
     "askId": 150695552109032493,
     "price": "4.00000100",
     "qty": "12.00000000",
     "time": 1499865549590,
     "isBuyer": true,
     "isMaker": false,
     "feeCoin": "ETH",
     "fee": "0.001"
   },...
]
```
{% endswagger-response %}
{% endswagger %}

**Weight (IP/UID): 1**

<br>
<br>
## account

### Security type: USER\_DATA

####account information
Request method: [GET](#fenced-code-block)

URL : [https://openapi.xxx.com/sapi/v1/account](#fenced-code-block)

#####describe
* Speed limit rule: 20 times/2s

#####Parameters
######Header
| parameter name | type | example |
| ----------- | ----------- | ----------- |
| X-CH-SIGN | String | Signature |
| X-CH-APIKEY | String | Your API-Key |
| X-CH-TS | integer |time stamp |

#####Responses
* 🟩200: OK success
```javascript
```

**Weight (IP/UID): 1**
