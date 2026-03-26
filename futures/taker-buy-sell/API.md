---
name: taker-buy/sell
description: Taker Buy/Sell request using the CoinGlass API. 
metadata:
  version: 1.0.0
  author: CoinGlass
  openclaw:
    requires:
      bins:
        - curl
        - openssl
    homepage: https://github.com/coinglass-official/coinglass-api-skills/tree/main/futures/taker-buy-sell/API.md
license: MIT
---

# CoinGlass Taker Buy/Sell Skill

Taker Buy/Sell request on CoinGLass API endpoints. Return the result in JSON format.


## Quick Reference

| API                                      | Endpoint                                              | Function                                                                                                                                                         |
| ---------------------------------------- | ----------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Pair Taker Buy/Sell History              | /api/futures/v2/taker-buy-sell-volume/history         | This endpoint provides historical data for the long/short ratio of taker buy and sell volumes in futures markets.                                                |
| Coin Taker Buy/Sell History              | /api/futures/aggregated-taker-buy-sell-volume/history | This endpoint provides historical data for the long/short ratio of aggregated taker buy and sell volumes for futures cryptocurrencies.                           |
| Footprint History (90d)                  | /api/futures/volume/footprint-history                 | This endpoint provides historical footprint chart data for futures markets, including buy and sell volumes at each price level.                                  |
| Cumulative Volume Delta (CVD)            | /api/futures/cvd/history                              | This endpoint provides historical Cumulative Volume Delta (CVD) data for a single futures exchange trading pair, including taker buy and sell volumes over time. |
| Aggregated Cumulative Volume Delta (CVD) | /api/futures/aggregated-cvd/history                   | This endpoint provides historical CVD data for a single cryptocurrency within one futures exchange, aggregated across multiple trading pairs.                    |
| Coin NetFlow List                        | /api/futures/netflow-list                             | This API provides inflow and outflow data for multiple coins across multiple time intervals in the futures market.                                               |
| Coin NetFlow                             | /api/futures/coin/netflow                             | This API provides inflow and outflow data for a single coin across multiple time intervals in the futures market.                                                |

## Rate Limits

**Rate Limits**
HOBBYIST:30 Rate limit/min
STARTUP:80 Rate limit/min
STANDARD:300 Rate limit/min
PROFESSIONAL:1200 Rate limit/min

**Response Headers**
API-KEY-MAX-LIMIT: Indicates the maximum allowed request limit for your API key (per minute).
API-KEY-USE-LIMIT: Shows the current usage count of your API key (requests made in the current time period).

## Errors Codes

For detailed information on error codes , please refer to [Errors](references/errors-codes.md).

  
  ---
        
## API 1: Pair Taker Buy/Sell History


**Supported Plans, Intervals, and Historical Data Access**

Hobbyist:Available
Startup:Available
Standard:Available
Professional:Available


The available historical data length depends on your subscription plan and the selected interval. Please refer to the table below for more details:

For more information on historical data access by plan and interval, see [references/plans-interval-history-length.md](references/plans-interval-history-length.md).



### Method: GET

**URL**:
```
https://open-api-v4.coinglass.com//api/futures/v2/taker-buy-sell-volume/history
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

| Parameter  | Type    | Required | Description                                                                                                      | Example value |
| ---------- | ------- | -------- | ---------------------------------------------------------------------------------------------------------------- | ------------- |
| exchange   | string  | yes      | Futures exchange names (e.g., Binance, OKX) .Retrieve supported exchanges via the 'supported-exchange-pair' API. | Binance       |
| symbol     | string  | yes      | Trading pair (e.g., BTCUSDT). Retrieve supported pairs via the 'supported-exchange-pair' API.                    | BTCUSDT       |
| interval   | string  | yes      | Time interval for data aggregation.  Supported values: 1m, 3m, 5m, 15m, 30m, 1h, 4h, 6h, 8h, 12h, 1d, 1w         | h1            |
| limit      | integer | no       | Number of results per request.  Default: 1000, Maximum: 1000                                                     | 10            |
| start_time | integer | no       | Start timestamp in milliseconds (e.g., 1641522717000).                                                           |               |
| end_time   | integer | no       | End timestamp in milliseconds (e.g., 1641522717000).                                                             |               |


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/futures/v2/taker-buy-sell-volume/history?exchange=Binance&symbol=BTCUSDT&interval=h1' \
-H 'Content-Type: application/json' \
-H 'CG-API-KEY: ${YOUR_API_KEY}' \
-H 'User-Agent: coinglass-skill/1.0.0'
```
        
**Response**:
```json
{
  "code": "0",
  "data": [
    {
      "time": 1750183200000,
      "taker_buy_volume_usd": "414120141.0714",
      "taker_sell_volume_usd": "350417509.655"
    },
    {
      "time": 1750186800000,
      "taker_buy_volume_usd": "882509979.6914",
      "taker_sell_volume_usd": "808715578.4428"
    },
    {
      "time": 1750190400000,
      "taker_buy_volume_usd": "572589140.5759",
      "taker_sell_volume_usd": "571005164.3247"
    },
}
```

---
  
  
  ---
        
## API 2: Coin Taker Buy/Sell History


**Supported Plans, Intervals, and Historical Data Access**

Hobbyist:Available
Startup:Available
Standard:Available
Professional:Available


The available historical data length depends on your subscription plan and the selected interval. Please refer to the table below for more details:

For more information on historical data access by plan and interval, see [references/plans-interval-history-length.md](references/plans-interval-history-length.md).



### Method: GET

**URL**:
```
https://open-api-v4.coinglass.com//api/futures/aggregated-taker-buy-sell-volume/history
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

| Parameter     | Type    | Required | Description                                                                                              | Example value |
| ------------- | ------- | -------- | -------------------------------------------------------------------------------------------------------- | ------------- |
| exchange_list | string  | yes      | exchange_list: List of exchange names to retrieve data from (e.g., 'Binance,OKX,Bybit')                  | Binance       |
| symbol        | string  | yes      | Trading pair (e.g., BTC). Retrieve supported coins via the 'supported-coins' API.                        | BTC           |
| interval      | string  | yes      | Time interval for data aggregation.  Supported values: 1m, 3m, 5m, 15m, 30m, 1h, 4h, 6h, 8h, 12h, 1d, 1w | h1            |
| limit         | integer | no       | Number of results per request.  Default: 1000, Maximum: 1000                                             | 10            |
| start_time    | integer | no       | Start timestamp in milliseconds (e.g., 1641522717000).                                                   |               |
| end_time      | integer | no       | End timestamp in milliseconds (e.g., 1641522717000).                                                     |               |
| unit          | string  | no       | Unit for the returned data, choose between 'usd' or 'coin'.                                              | usd           |


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/futures/aggregated-taker-buy-sell-volume/history?exchange_list=Binance&symbol=BTC&interval=h1' \
-H 'Content-Type: application/json' \
-H 'CG-API-KEY: ${YOUR_API_KEY}' \
-H 'User-Agent: coinglass-skill/1.0.0'
```
        
**Response**:
```json
{
  "code": "0",
  "msg": "success",
  "data": [
    {
      "time": 1741622400000, // Timestamp in milliseconds
      "aggregated_buy_volume_usd": 968834542.3787, // Aggregated buy volume (USD)
      "aggregated_sell_volume_usd": 1054582654.8138 // Aggregated sell volume (USD)
    },
    {
      "time": 1741626000000,
      "aggregated_buy_volume_usd": 1430620763.2041,
      "aggregated_sell_volume_usd": 1559166911.2821
    },
    {
      "time": 1741629600000,
      "aggregated_buy_volume_usd": 1897261721.0129,
      "aggregated_sell_volume_usd": 2003812276.7812
    }
  ]
}
```

---
  
  
  ---
        
## API 3: Footprint History (90d)


**Supported Plans, Intervals, and Historical Data Access**

Hobbyist:Not Available
Startup:Not Available
Standard:Not Available
Professional:Available


**Supported Intervals, and Historical Data Access**
History limits for this endpoint: Maximum history query limit is 90 days.


### Method: GET

**URL**:
```
https://open-api-v4.coinglass.com//api/futures/volume/footprint-history
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

| Parameter  | Type    | Required | Description                                                                                             | Example value |
| ---------- | ------- | -------- | ------------------------------------------------------------------------------------------------------- | ------------- |
| exchange   | string  | yes      | Futures exchange names (Supported Binance, OKX,Bybit,Hyperliquid)                                       | Binance       |
| symbol     | string  | yes      | Trading pair (e.g., BTCUSDT). Retrieve supported pairs via the 'support-exchange-pair' API.             | BTCUSDT       |
| interval   | string  | yes      | Time interval for data aggregation. Supported values: 1m, 3m, 5m, 15m, 30m, 1h, 4h, 6h, 8h, 12h, 1d, 1w | 1h            |
| limit      | integer | no       | Number of results per request. Default: 1000, Maximum: 1000                                             |               |
| start_time | integer | no       | Start timestamp in milliseconds (e.g., 1641522717000).                                                  |               |
| end_time   | integer | no       | End timestamp in milliseconds (e.g., 1641522717000).                                                    |               |


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/futures/volume/footprint-history?exchange=Binance&symbol=BTCUSDT&interval=1h' \
-H 'Content-Type: application/json' \
-H 'CG-API-KEY: ${YOUR_API_KEY}' \
-H 'User-Agent: coinglass-skill/1.0.0'
```
        
**Response**:
```json
{
  "code": "0",  // code (0 = success)
  "data": [
    [
      1757808000,  // Timestamp (seconds)
      [
        [
          115765,        // Price start
          115770,        // Price end
          3.223,         // Taker buy volume 
          9.906,         // Taker sell volume 
          373118.1958,   // Taker buy volume (quote currency)
          1146773.5391,  // Taker sell volume (quote currency)
          373118.1958,   // Taker buy volume (USDT)
          1146773.5391,  // Taker sell volume (USDT)
          193,           // Taker buy trade count
          153            // Taker sell trade count
        ],
        [
          115770,
          115775,
          3.315,         // Taker buy volume
          0.528,         // Taker sell volume
          383782.5569,   // Taker buy volume (quote currency)
          61127.0686,    // Taker sell volume (quote currency)
          383782.5569,   // Taker buy volume (USDT)
          61127.0686,    // Taker sell volume (USDT)
          40,            // Taker buy trade count
          64             // Taker sell trade count
        ]
      ]
    ]
  ]
}
```

---
  
  
  ---
        
## API 4: Cumulative Volume Delta (CVD)


**Supported Plans, Intervals, and Historical Data Access**

Hobbyist:Not Available
Startup:Available
Standard:Available
Professional:Available


The available historical data length depends on your subscription plan and the selected interval. Please refer to the table below for more details:

For more information on historical data access by plan and interval, see [references/plans-interval-history-length.md](references/plans-interval-history-length.md).



### Method: GET

**URL**:
```
https://open-api-v4.coinglass.com//api/futures/cvd/history
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

| Parameter  | Type    | Required | Description                                                                                                       | Example value |
| ---------- | ------- | -------- | ----------------------------------------------------------------------------------------------------------------- | ------------- |
| exchange   | string  | yes      | Futures exchange names (e.g., Binance, OKX) .Retrieve supported exchanges via the 'supported-exchange-pair' API.  | Binance       |
| symbol     | string  | yes      | Trading pair (e.g., BTCUSDT). Retrieve supported pairs via the 'supported-exchange-pair' API.                     | BTCUSDT       |
| interval   | string  | yes      | Time interval for data aggregation. Supported values: 1m, 3m, 5m, 15m, 30m, 1h, 4h, 6h, 8h, 12h, 1d, 1w           | 1h            |
| limit      | integer | no       | Number of results per request. Default: 1000, Maximum: 1000                                                       |               |
| start_time | integer | no       | Start timestamp in milliseconds (e.g., 1641522717000).  The starting timestamp from which CVD calculation begins. |               |
| end_time   | integer | no       | End timestamp in milliseconds (e.g., 1641522717000).                                                              |               |


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/futures/cvd/history?exchange=Binance&symbol=BTCUSDT&interval=1h' \
-H 'Content-Type: application/json' \
-H 'CG-API-KEY: ${YOUR_API_KEY}' \
-H 'User-Agent: coinglass-skill/1.0.0'
```
        
**Response**:
```json
{
  "code": "0",
  "data": [
    {
      "time": 1762254000000,
      "taker_buy_vol": 350281007.0211,
      "taker_sell_vol": 325339470.9493,
      "cum_vol_delta": 24941536.0718
    },
    {
      "time": 1762257600,
      "taker_buy_vol": 286399814.1275,
      "taker_sell_vol": 347409544.4937,
      "cum_vol_delta": -36068194.2944
    },
    {
      "time": 1762261200,
      "taker_buy_vol": 299952362.4807,
      "taker_sell_vol": 323978642.5934,
      "cum_vol_delta": -60094474.4071
    },
  ]
}
```

---
  
  
  ---
        
## API 5: Aggregated Cumulative Volume Delta (CVD)


**Supported Plans, Intervals, and Historical Data Access**

Hobbyist:Not Available
Startup:Available
Standard:Available
Professional:Available


The available historical data length depends on your subscription plan and the selected interval. Please refer to the table below for more details:

For more information on historical data access by plan and interval, see [references/plans-interval-history-length.md](references/plans-interval-history-length.md).



### Method: GET

**URL**:
```
https://open-api-v4.coinglass.com//api/futures/aggregated-cvd/history
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

| Parameter     | Type    | Required | Description                                                                                                                        | Example value |
| ------------- | ------- | -------- | ---------------------------------------------------------------------------------------------------------------------------------- | ------------- |
| exchange_list | string  | yes      | Comma-separated exchange names (e.g., "binance, okx, bybit"). Retrieve supported exchanges via the 'supported-exchange-pairs' API. | Binance       |
| symbol        | string  | yes      | Trading pair (e.g., BTC). Retrieve supported coins via the 'support-coins' API.                                                    | BTC           |
| interval      | string  | yes      | Time interval for data aggregation.Supported values: 1m, 3m, 5m, 15m, 30m, 1h, 4h, 6h, 8h, 12h, 1d, 1w                             | 1h            |
| limit         | integer | no       | Number of results per request.Default: 1000, Maximum: 4500                                                                         |               |
| start_time    | integer | no       | Start timestamp in milliseconds (e.g., 1641522717000).   The starting timestamp from which CVD calculation begins.                 |               |
| end_time      | string  | no       | End timestamp in milliseconds (e.g., 1641522717000).                                                                               |               |
| unit          | string  | no       | Unit for the returned data, choose between 'usd' or 'coin'.  Default: 'usd'                                                        |               |


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/futures/aggregated-cvd/history?exchange_list=Binance&symbol=BTC&interval=1h' \
-H 'Content-Type: application/json' \
-H 'CG-API-KEY: ${YOUR_API_KEY}' \
-H 'User-Agent: coinglass-skill/1.0.0'
```
        
**Response**:
```json
{
  "code": "0",
  "data": [
    {
      "time": 1762254000000,
      "agg_taker_buy_vol": 461937243.0899,
      "agg_taker_sell_vol": 415687343.2719,
      "cum_vol_delta": 46249899.818
    },
    {
      "time": 1762257600,
      "agg_taker_buy_vol": 390296231.4588,
      "agg_taker_sell_vol": 469137635.9107,
      "cum_vol_delta": -32591504.6339
    },
    {
      "time": 1762261200,
      "agg_taker_buy_vol": 461378798.1884,
      "agg_taker_sell_vol": 450407935.7885,
      "cum_vol_delta": -21620642.234
    },
  ]
}
```

---
  
  
  ---
        
## API 6: Coin NetFlow List


**Supported Plans, Intervals, and Historical Data Access**

Hobbyist:Not Available
Startup:Available
Standard:Available
Professional:Available


### Method: GET

**URL**:
```
https://open-api-v4.coinglass.com//api/futures/netflow-list
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

| Parameter | Type    | Required | Description                             | Example value |
| --------- | ------- | -------- | --------------------------------------- | ------------- |
| per_page  | integer | no       | Number of results per page.             |               |
| page      | integer | no       | Page number for pagination, default: 1. |               |


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/futures/netflow-list' \
-H 'Content-Type: application/json' \
-H 'CG-API-KEY: ${YOUR_API_KEY}' \
-H 'User-Agent: coinglass-skill/1.0.0'
```
        
**Response**:
```json
{
  "code": "0",
  "data": [
    {
      "symbol": "BTC",
      "taker_buy_volume_usd_5m": 27146667.47128,
      "taker_sell_volume_usd_5m": 25201496.55780442,
      "net_flow_usd_5m": 1945170.91347558,
      "taker_buy_volume_usd_15m": 54111394.80018,
      "taker_sell_volume_usd_15m": 67747451.23550442,
      "net_flow_usd_15m": -13636056.43532442,
      "taker_buy_volume_usd_30m": 152868027.04698,
      "taker_sell_volume_usd_30m": 152828524.28170443,
      "net_flow_usd_30m": 39502.76527558,
      "taker_buy_volume_usd_1h": 352338438.86058,
      "taker_sell_volume_usd_1h": 291303140.33310443,
      "net_flow_usd_1h": 61035298.52747558,
      "taker_buy_volume_usd_2h": 709296803.64778,
      "taker_sell_volume_usd_2h": 614081331.5580044,
      "net_flow_usd_2h": 95215472.08977558,
      "taker_buy_volume_usd_4h": 1569315585.43488,
      "taker_sell_volume_usd_4h": 1581845620.3436043,
      "net_flow_usd_4h": -12530034.90872442,
      "taker_buy_volume_usd_6h": 2354747787.93288,
      "taker_sell_volume_usd_6h": 2348895018.781204,
      "net_flow_usd_6h": 5852769.15167558,
      "taker_buy_volume_usd_8h": 3794149243.47208,
      "taker_sell_volume_usd_8h": 3892310085.2722044,
      "net_flow_usd_8h": -98160841.80012442,
      "taker_buy_volume_usd_12h": 5864573201.23938,
      "taker_sell_volume_usd_12h": 5815311185.222104,
      "net_flow_usd_12h": 49262016.01727558,
      "taker_buy_volume_usd_24h": 15756184096.50828,
      "taker_sell_volume_usd_24h": 15965801767.996105,
      "net_flow_usd_24h": -209617671.4878244,
      "taker_buy_volume_usd_3d": 52915124850.76235,
      "taker_sell_volume_usd_3d": 49196035257.97723,
      "net_flow_usd_3d": 3719089592.7851286,
      "taker_buy_volume_usd_7d": 119184469478.04715,
      "taker_sell_volume_usd_7d": 112395037862.93982,
      "net_flow_usd_7d": 6789431615.107328,
      "taker_buy_volume_usd_15d": 248235961936.24756,
      "taker_sell_volume_usd_15d": 238537228671.88052,
      "net_flow_usd_15d": 9698733264.36703,
      "taker_buy_volume_usd_30d": 505994646097.17975,
      "taker_sell_volume_usd_30d": 498158228554.57495,
      "net_flow_usd_30d": 7836417542.604829,
      "taker_buy_volume_usd_40d": 649455680903.7959,
      "taker_sell_volume_usd_40d": 643329380917.7958,
      "net_flow_usd_40d": 6126299986.000029,
      "taker_buy_volume_usd_50d": 930774565738.1816,
      "taker_sell_volume_usd_50d": 936490347740.2704,
      "net_flow_usd_50d": -5715782002.088772,
      "taker_buy_volume_usd_60d": 1061193757142.713,
      "taker_sell_volume_usd_60d": 1072527283888.9313,
      "net_flow_usd_60d": -11333526746.218172,
      "taker_buy_volume_usd_90d": 1445912279513.429,
      "taker_sell_volume_usd_90d": 1456897621111.1091,
      "net_flow_usd_90d": 947754050958.854,
      "taker_buy_volume_usd_120d": 2021929039937.87,
      "taker_sell_volume_usd_120d": 2046744425362.1223,
      "net_flow_usd_120d": -24815385424.252373,
      "market_cap": 1488443584213.8738
    },
  ]
}
```

---
  
  
  ---
        
## API 7: Coin NetFlow


**Supported Plans, Intervals, and Historical Data Access**

Hobbyist:Not Available
Startup:Available
Standard:Available
Professional:Available


### Method: GET

**URL**:
```
https://open-api-v4.coinglass.com//api/futures/coin/netflow
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

| Parameter     | Type   | Required | Description                                                                                                                                         | Example value                     |
| ------------- | ------ | -------- | --------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------- |
| symbol        | string | yes      | Trading coin (e.g., BTC). Retrieve supported coins via the 'supported-coins' API.                                                                   | BTC                               |
| exchange_list | string | yes      | exchange_list: List of exchange names to retrieve data from (e.g., 'Binance, OKX, Bybit') . Default exchanges: "Binance, Bybit, OKX, Bitget, Gate". | Binance, Bybit, OKX, Bitget, Gate |


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/futures/coin/netflow?symbol=BTC&exchange_list=Binance%2C+Bybit%2C+OKX%2C+Bitget%2C+Gate' \
-H 'Content-Type: application/json' \
-H 'CG-API-KEY: ${YOUR_API_KEY}' \
-H 'User-Agent: coinglass-skill/1.0.0'
```
        
**Response**:
```json
{"code":"0","msg":"success","data":{"symbol":"BTC","taker_buy_volume_usd_5m":"8564899","taker_sell_volume_usd_5m":"9692915","net_flow_usd_5m":"-1128017","net_flow_usd_change_percent_5m":-51.73,"net_flow_usd_5m_market_cap_ratio":-0.000076,"taker_buy_volume_usd_15m":"29134420","taker_sell_volume_usd_15m":"44784583","net_flow_usd_15m":"-15650163","net_flow_usd_change_percent_15m":-206.69,"net_flow_usd_15m_market_cap_ratio":-0.001055,"taker_buy_volume_usd_30m":"79865179","taker_sell_volume_usd_30m":"80845695","net_flow_usd_30m":"-980517","net_flow_usd_change_percent_30m":-104.76,"net_flow_usd_30m_market_cap_ratio":-0.000066,"taker_buy_volume_usd_1h":"165477715","taker_sell_volume_usd_1h":"145832349","net_flow_usd_1h":"19645366","net_flow_usd_change_percent_1h":217.96,"net_flow_usd_1h_market_cap_ratio":0.001324,"taker_buy_volume_usd_4h":"760187107","taker_sell_volume_usd_4h":"729339048","net_flow_usd_4h":"30848059","net_flow_usd_change_percent_4h":135.14,"net_flow_usd_4h_market_cap_ratio":0.00208,"taker_buy_volume_usd_8h":"1005775816","taker_sell_volume_usd_8h":"1044121929","net_flow_usd_8h":"-38346114","net_flow_usd_change_percent_8h":-9.06,"net_flow_usd_8h_market_cap_ratio":-0.002585,"taker_buy_volume_usd_12h":"2442236886","taker_sell_volume_usd_12h":"2561495148","net_flow_usd_12h":"-119258262","net_flow_usd_change_percent_12h":-129.43,"net_flow_usd_12h_market_cap_ratio":-0.00804,"taker_buy_volume_usd_24h":"7566899147","taker_sell_volume_usd_24h":"7280826322","net_flow_usd_24h":"286072825","net_flow_usd_change_percent_24h":-60.91,"net_flow_usd_24h_market_cap_ratio":0.019286,"taker_buy_volume_usd_3d":"25868053532","taker_sell_volume_usd_3d":"24153912510","net_flow_usd_3d":"1714141022","net_flow_usd_change_percent_3d":-16.01,"net_flow_usd_3d_market_cap_ratio":0.115562,"taker_buy_volume_usd_5d":"35555399802","taker_sell_volume_usd_5d":"33163465367","net_flow_usd_5d":"2391934436","net_flow_usd_change_percent_5d":-9.4,"net_flow_usd_5d_market_cap_ratio":0.161257,"taker_buy_volume_usd_7d":"58795007181","taker_sell_volume_usd_7d":"55000626111","net_flow_usd_7d":"3794381071","net_flow_usd_change_percent_7d":1960.91,"net_flow_usd_7d_market_cap_ratio":0.255806,"taker_buy_volume_usd_10d":"90978663883","taker_sell_volume_usd_10d":"85946889007","net_flow_usd_10d":"5031774877","net_flow_usd_change_percent_10d":506.96,"net_flow_usd_10d_market_cap_ratio":0.339227,"taker_buy_volume_usd_15d":"137799491538","taker_sell_volume_usd_15d":"132072679473","net_flow_usd_15d":"5726812066","net_flow_usd_change_percent_15d":3668.93,"net_flow_usd_15d_market_cap_ratio":0.386085,"taker_buy_volume_usd_30d":"266960790361","taker_sell_volume_usd_30d":"261394441706","net_flow_usd_30d":"5566348656","net_flow_usd_change_percent_30d":151.96,"net_flow_usd_30d_market_cap_ratio":0.375267,"taker_buy_volume_usd_40d":"349549701197","taker_sell_volume_usd_40d":"344312184923","net_flow_usd_40d":"5237516274","net_flow_usd_change_percent_40d":152.76,"net_flow_usd_40d_market_cap_ratio":0.353098,"taker_buy_volume_usd_50d":"496844249786","taker_sell_volume_usd_50d":"499136038696","net_flow_usd_50d":"-2291788910","net_flow_usd_change_percent_50d":57.87,"net_flow_usd_50d_market_cap_ratio":-0.154506,"taker_buy_volume_usd_60d":"564792098258","taker_sell_volume_usd_60d":"569939808511","net_flow_usd_60d":"-5147710254","net_flow_usd_change_percent_60d":41.36,"net_flow_usd_60d_market_cap_ratio":-0.347043,"taker_buy_volume_usd_90d":"766953365285","taker_sell_volume_usd_90d":"771796120595","net_flow_usd_90d":"-4842755310","net_flow_usd_change_percent_90d":86.29,"net_flow_usd_90d_market_cap_ratio":-0.326484,"taker_buy_volume_usd_120d":"1062521073566","taker_sell_volume_usd_120d":"1076447240334","net_flow_usd_120d":"-13926166769","net_flow_usd_change_percent_120d":72.68,"net_flow_usd_120d_market_cap_ratio":-0.938861,"taker_buy_volume_usd_150d":"1374917377958","taker_sell_volume_usd_150d":"1401464473468","net_flow_usd_150d":"-26547095511","net_flow_usd_change_percent_150d":45.46,"net_flow_usd_150d_market_cap_ratio":-1.789726,"taker_buy_volume_usd_180d":"1713318564888","taker_sell_volume_usd_180d":"1753478516197","net_flow_usd_180d":"-40159951310","net_flow_usd_change_percent_180d":-23.01,"net_flow_usd_180d_market_cap_ratio":-2.707464,"taker_buy_volume_usd_1y":"3618522811709","taker_sell_volume_usd_1y":"3690105674385","net_flow_usd_1y":"-71582862676","net_flow_usd_change_percent_1y":-0.17,"net_flow_usd_1y_market_cap_ratio":-4.825903},"success":true}
```

---
  