# 币币交易

## 公共

### 安全类型: None

####测试连接
Request method : [GET](#fenced-code-block)

URL : [https://openapi.xxx.com/sapi/v1/ping](#fenced-code-block)

#####描述
* 测试REST API的连通性

#####Parameters
* No parameters

#####Responses
`
{
   🟩200: OK
}
`

<br>
####服务器时间
Request method : [GET](#fenced-code-block)

URL : [https://openapi.xxx.com/sapi/v1/time](#fenced-code-block)

#####描述
* 获取服务器时间

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
####币对列表
Request method : [GET](#fenced-code-block)

URL : [https://openapi.xxx.com/sapi/v1/symbols](#fenced-code-block)

#####描述
* 市场支持的币对集合esponse:
* 名称类型例子描述timelong`1595563624731`当前时间(Unix Timestamp, 毫秒ms)bidslist如下订单薄买盘信息askslist如下订单薄卖盘信息bids和asks所对应的信息代表了订单薄的所有价格以及价格对应的数量的信息, 由最优价格从上倒下排列名称类型例子描述' 'float`131.1`价格' 'float`2.3`当前价格对应的数量GEThttps://openapi.xxx.com/sapi/v1/ticker\

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
            "symbol": "etcusdt",
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
**权重(IP/UID): 1**

#### Response: <a href="#bi-dui-lie-biao" id="bi-dui-lie-biao"></a>

| 名称                | 类型      | 例子        | 描述     |
| ----------------- | ------- | --------- | ------ |
| symbol            | string  | `BTCUSDT` | 币对名称   |
| baseAsset         | string  | `BTC`     | base货币 |
| quoteAsset        | string  | `USDT`    | 计价货币   |
| pricePrecision    | integer | `2`       | 价格精度   |
| quantityPrecision | integer | `6`       | 数量精度   |

<br>
<br>
## 行情

### 安全类型: None

####订单薄
Request method : [GET](#fenced-code-block)

URL : [https://openapi.xxx.com/sapi/v1/depth](#fenced-code-block)

#####描述
* 市场订单薄深度信息

#####Parameters
######Query

| 参数名      | 类型 | 示例 |
| ----------- | ----------- | ----------- |
| Limit      | integer       | 默认100；最大100       |
| synbol    | String        | BTCUSDT        |

#####Responses
* 🟩200: OK 成功获取深度信息

```javascript
{
  "bids": [
    [
      "3.90000000",   // 价格
      "431.00000000"  // 数量
    ],
    [
      "4.00000000",
      "431.00000000"
    ]
  ],
  "asks": [
    [
      "4.00000200",  // 价格
      "12.00000000"  // 数量
    ],
    [
      "5.10000000",
      "28.00000000"
    ]
  ]
}
```

**权重(IP/UID): 5**

#### Response: <a href="#bi-dui-lie-biao" id="bi-dui-lie-biao"></a>

| time | long | `1595563624731` | 当前时间(Unix Timestamp, 毫秒ms) |
| ---- | ---- | --------------- | -------------------------- |
| bids | list | 如下              | 订单薄买盘信息                    |
| asks | list | 如下              | 订单薄卖盘信息                    |

bids和asks所对应的信息代表了订单薄的所有价格以及价格对应的数量的信息, 由最优价格从上倒下排列

| ' ' | float | `131.1` | 价格        |
| --- | ----- | ------- | --------- |
| ' ' | float | `2.3`   | 当前价格对应的数量 |




<br>
####行情ticker
Request method : [GET](#fenced-code-block)

URL : [https://openapi.xxx.com/sapi/v1/klines](#fenced-code-block)

#####描述
* 24小时价格变化数据

#####Parameters
######Query

| 参数名      | 类型 | 示例 |
| ----------- | ----------- | ----------- |
| synbol    | String        | 币对名称 E.g.BTCUSDT     |

#####Responses
* 🟩200: OK 成功获取ticker信息


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

**权重(IP/UID): 5**

#### Response:

| time | long  | `1595563624731` | 时间戳 | 
| ---- | ----- | --------------- | ------|  
| high | float | `9900`          | 最高价 |   
| low  | float | `8800.34`       | 最低价 |   
| open | float | `8700`          | 开盘价 |   
| last | float | `8900`          | 最新价 |   
| vol  | float | `4999`          | 交易量 | 


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
| Limit      | integer       | 默认100；最大100       |
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
####创建测试订单
Request method : [POST](#fenced-code-block)

URL : [https://openapi.xxx.com/sapi/v1/order/test](#fenced-code-block)

#####描述
* 创建和验证新订单, 但不会送入撮合引擎

#####Parameters
######Query
| 参数名      | 类型 | 示例 |
| ----------- | ----------- | ----------- |
| X-CH-SIGN  | String        | 签名        |
| X-CH-APIKEY     | String       |您的API-Key     |
| X-CH-TS     | integer       |时间戳     |
######Header
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
    // Response
}
```

**权重(IP/UID): 1**

****

****
####批量下单
Request method : [POST](#fenced-code-block)

URL : [https://openapi.xxx.com/sapi/v1/batchOrders](#fenced-code-block)

#####描述
* 一次批量最多下10个订单

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
| orders*     | number       |批量订单信息 最多10条    |

#####Responses
* 🟩200: OK 成功

**权重(IP/UID): 10**

#### Resquest `orders` field: <a href="#resquest-orders-field" id="resquest-orders-field"></a>

| price     | long   | 1000           | 价格 |  
| --------- | ------ | -------------- | -- | 
| volume    | folat  | 20.1           | 数量 |   
| side      | string | `BUY/SELL`     | 方向 |   
| batchType | string | `LIMIT/MARKET` | 类型 |   





####订单查询
Request method : [GET](#fenced-code-block)

URL : [https://openapi.xxx.com/sapi/v1/order](#fenced-code-block)

#####描述
* 限速规则: 20次/2s

#####Parameters
######Query

| 参数名      | 类型 | 示例 |
| ----------- | ----------- | ----------- |
| orderId*    |        | 订单id        |
| newClientorderId      | integer       |客户端订单标识      |
| symbol*      |       |币对名称 BTCUSDT      |
######Header
| 参数名      | 类型 | 示例 |
| ----------- | ----------- | ----------- |
| X-CH-SIGN  | String        | 签名        |
| X-CH-APIKEY     | String       |您的API-Key     |
| X-CH-TS     | integer       |时间戳     |

#####Responses
* 🟩200: OK 成功

**权重(IP/UID): 1**

#### **Response:**

| orderId       | long    | `150695552109032492` | 订单ID（系统生成）                                                                                                 |   
| ------------- | ------- | -------------------- | ---------------------------------------------------------------------------------------------------------- | 
| clientorderId | string  | `213443`             | 订单ID（自己发送的）                                                                                                |   
| symbol        | string  | `BTCUSDT`            | 币对名称                                                                                                       |   
| transactTime  | integer | `1273774892913`      | 订单创建时间                                                                                                     |   
| price         | float   | `4765.29`            | 订单价格                                                                                                       |   
| origQty       | float   | `1.01`               | 订单数量                                                                                                       |   
| executedQty   | float   | `1.01`               | 已经成交订单数量                                                                                                   |   
| avgPrice      | float   | `4754.24`            | 订单已经成交的平均价格                                                                                                |   
| side          | string  | `BUY`                | 订单方向。可能出现的值只能为：`BUY`（买入做多） 和 `SELL`（卖出做空）                                                                  |   |
| status        | string  | `NEW`                | 订单状态。可能出现的值为：`NEW`(新订单，无成交)、`PARTIALLY_FILLED`（部分成交）、`FILLED`（全部成交）、`CANCELED`（已取消）和`REJECTED`（订单被拒绝）.POST |   





####撤销订单
Request method : [POST](#fenced-code-block)

URL : [https://openapi.xxx.com/sapi/v1/cancel](#fenced-code-block)

#####描述
* 限速规则: 100次/2s

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
| orderId*  |       | 订单id       |
| newClientorderId    | String       |客户端订单标识     |
| symbol*     |    String   |币对名称     |
| type*    |     String  |   订单类型 LIMIT/MARKET  |
| price     |   number    |订单价格,对于LIMIT订单必须发送    |
| newClientorderId     |       |客户端订单标识    |
| recvwindow    |    number   |时间窗口     |

#####Responses
* 🟩200: OK 撤单成功
**权重(IP/UID): 5**

#### Response:

| orderId       | long   | `150695552109032492` | 订单ID（系统生成）                                                                                                 |   
| ------------- | ------ | -------------------- | ---------------------------------------------------------------------------------------------------------- | 
| clientorderId | string | `213443`             | 订单ID（自己发送的）                                                                                                |   
| symbol        | string | `BTCUSDT`            | 币对名称                                                                                                       |   
| status        | string | `NEW`                | 订单状态。可能出现的值为：`NEW`(新订单，无成交)、`PARTIALLY_FILLED`（部分成交）、`FILLED`（全部成交）、`CANCELED`（已取消）和`REJECTED`（订单被拒绝）.POST |   





####批量撤销订单
Request method : [POST](#fenced-code-block)

URL : [https://openapi.xxx.com/sapi/v1/batchCancel](#fenced-code-block)

#####描述
* 一次批量最多10个订单

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
| orderIds*  |       | 要取消的订单id集合[123,456] Responses200GET      |
| symbol*     |    String   |币对名称     |

#####Responses
* 🟩200: OK 撤单成功


```javascript
{
    "success": [
        165964665990709251,
        165964665990709252,
        165964665990709253
    ],
    "failed": [ //取消失败一般是因为订单不存在或订单状态已经到终态
        165964665990709250  
    ]
}
```
{% endswagger-response %}
{% endswagger %}

**权重(IP/UID): 10**

****

****


<br>

####当前订单
Request method : [GET](#fenced-code-block)

URL : [https://openapi.xxx.com/sapi/v1/openOrders](#fenced-code-block)

#####描述
* 限速规则: 20次/2s

#####Parameters
######Query

| 参数名      | 类型 | 示例 |
| ----------- | ----------- | ----------- |
| symbol*      |       |币对名称 BTCUSDT      |
######Header
| 参数名      | 类型 | 示例 |
| ----------- | ----------- | ----------- |
| X-CH-SIGN  | String        | 签名        |
| X-CH-APIKEY     | String       |您的API-Key     |
| X-CH-TS     | integer       |时间戳     |

#####Responses
* 🟩200: OK 成功


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

#### **权重(IP/UID): 1**

**Response:**

| orderId       | long   | `150695552109032492` | 订单ID（系统生成）                                                                                                 |   
| ------------- | ------ | -------------------- | ---------------------------------------------------------------------------------------------------------- | 
| clientorderId | string | `213443`             | 订单ID（自己发送的）                                                                                                |   
| symbol        | string | `BTCUSDT`            | 币对名称                                                                                                       |   
| price         | float  | `4765.29`            | 订单价格                                                                                                       |   
| origQty       | float  | `1.01`               | 订单数量                                                                                                       |   
| executedQty   | float  | `1.01`               | 已经成交订单数量                                                                                                   |   
| avgPrice      | float  | `4754.24`            | 订单已经成交的平均价格                                                                                                |   
| type          | string | `LIMIT`              | 订单类型`LIMIT`(限价)`MARKET`（市价）                                                                                |   
| side          | string | `BUY`                | 订单方向。可能出现的值只能为：`BUY`（买入做多） 和 `SELL`（卖出做空）                                                                  |   
| status        | string | `NEW`                | 订单状态。可能出现的值为：`NEW`(新订单，无成交)、`PARTIALLY_FILLED`（部分成交）、`FILLED`（全部成交）、`CANCELED`（已取消）和`REJECTED`（订单被拒绝）.POST |   



<br>
####交易记录
Request method : [GET](#fenced-code-block)

URL : [https://openapi.xxx.com/sapi/v1/myTrades](#fenced-code-block)

#####描述
* 限速规则: 20次/2s

#####Parameters
######Query

| 参数名      | 类型 | 示例 |
| ----------- | ----------- | ----------- |
| symbol*      |       |币对名称 BTCUSDT      |
| limit*      |       |默认100,最大1000   |
| fromId*      |       |币对名称 BTCUSDT      |
######Header
| 参数名      | 类型 | 示例 |
| ----------- | ----------- | ----------- |
| X-CH-SIGN  | String        | 签名        |
| X-CH-APIKEY     | String       |您的API-Key     |
| X-CH-TS     | integer       |时间戳     |

#####Responses
* 🟩200: OK 成功
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
    "fee":"0.001"
  },...
]
```
{% endswagger-response %}
{% endswagger %}

**权重(IP/UID): 1**

<br>
<br>
## 账户

### 安全类型: USER\_DATA

####账户信息
Request method : [GET](#fenced-code-block)

URL : [https://openapi.xxx.com/sapi/v1/account](#fenced-code-block)

#####描述
* 限速规则: 20次/2s

#####Parameters
######Header
| 参数名      | 类型 | 示例 |
| ----------- | ----------- | ----------- |
| X-CH-SIGN  | String        | 签名        |
| X-CH-APIKEY     | String       |您的API-Key     |
| X-CH-TS     | integer       |时间戳     |

#####Responses
* 🟩200: OK 成功
```javascript
```

**权重(IP/UID): 1**
