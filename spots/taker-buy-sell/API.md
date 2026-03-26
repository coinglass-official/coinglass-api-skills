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
    homepage: https://github.com/coinglass-official/coinglass-api-skills/tree/main/spots/taker-buy-sell/API.md
license: MIT
---

# CoinGlass Taker Buy/Sell Skill

Taker Buy/Sell request on CoinGLass API endpoints. Return the result in JSON format.


## Quick Reference

| API                                      | Endpoint                                           | Function                                                                                                                                                      |
| ---------------------------------------- | -------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Pair Taker Buy/Sell History              | /api/spot/taker-buy-sell-volume/history            | This endpoint provides historical data for the long/short ratio of taker buy and sell volumes in spot markets.                                                |
| Coin Taker Buy/Sell History              | /api/spot/aggregated-taker-buy-sell-volume/history | This endpoint provides historical data for the long/short ratio of aggregated taker buy and sell volumes for spot cryptocurrencies.                           |
| Footprint History (90d)                  | /api/spot/volume/footprint-history                 | This endpoint provides historical footprint chart data for spot markets, including buy and sell volumes at each price level.                                  |
| Cumulative Volume Delta (CVD)            | /api/spot/cvd/history                              | This endpoint provides historical Cumulative Volume Delta (CVD) data for a single spot exchange trading pair, including taker buy and sell volumes over time. |
| Aggregated Cumulative Volume Delta (CVD) | /api/spot/aggregated-cvd/history                   | This endpoint provides historical CVD data for a single cryptocurrency within one spot exchange, aggregated across multiple trading pairs.                    |
| Coin NetFlow List                        | /api/spot/netflow-list                             | This API provides inflow and outflow data for multiple coins across multiple time intervals in the spot market.                                               |
| Coin NetFlow                             | /api/spot/coin/netflow                             | This API provides inflow and outflow data for a single coin across multiple time intervals in the spot market.                                                |

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
https://open-api-v4.coinglass.com//api/spot/taker-buy-sell-volume/history
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

| Parameter  | Type    | Required | Description                                                                                              | Example value |
| ---------- | ------- | -------- | -------------------------------------------------------------------------------------------------------- | ------------- |
| exchange   | string  | yes      | Exchange name (e.g., Binance). Retrieve supported exchanges via the 'supported-exchange-pair' API.       | Binance       |
| symbol     | string  | yes      | Trading pair (e.g., BTCUSDT). Retrieve supported pairs via the 'supported-exchange-pair' API.            | BTCUSDT       |
| interval   | string  | yes      | Time interval for data aggregation.  Supported values: 1m, 3m, 5m, 15m, 30m, 1h, 4h, 6h, 8h, 12h, 1d, 1w | h1            |
| limit      | integer | no       | Number of results per request.  Default: 1000, Maximum: 1000                                             | 10            |
| start_time | integer | no       | Start timestamp in milliseconds (e.g., 1641522717000).                                                   |               |
| end_time   | integer | no       | End timestamp in milliseconds (e.g., 1641522717000).                                                     |               |


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/spot/taker-buy-sell-volume/history?exchange=Binance&symbol=BTCUSDT&interval=h1' \
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
      "taker_buy_volume_usd": "10551.033", // Taker buy volume (USD)
      "taker_sell_volume_usd": "11308" // Taker sell volume (USD)
    },
    {
      "time": 1741626000000,
      "taker_buy_volume_usd": "15484.245",
      "taker_sell_volume_usd": "16316.118"
    },
    {
      "time": 1741629600000,
      "taker_buy_volume_usd": "20340.501",
      "taker_sell_volume_usd": "18977.660"
    }
  ]
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
https://open-api-v4.coinglass.com//api/spot/aggregated-taker-buy-sell-volume/history
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

| Parameter     | Type    | Required | Description                                                                                              | Example value |
| ------------- | ------- | -------- | -------------------------------------------------------------------------------------------------------- | ------------- |
| exchange_list | string  | yes      | exchange_list: List of exchange names to retrieve data from (e.g., 'Binance, OKX, Bybit')                | Binance       |
| symbol        | string  | yes      | Trading coin (e.g., BTC). Retrieve supported coins via the 'supported-coins' API.                        | BTC           |
| interval      | string  | yes      | Time interval for data aggregation.  Supported values: 1m, 3m, 5m, 15m, 30m, 1h, 4h, 6h, 8h, 12h, 1d, 1w | h1            |
| limit         | integer | no       | Number of results per request.  Default: 1000, Maximum: 1000                                             | 10            |
| start_time    | integer | no       | Start timestamp in milliseconds (e.g., 1641522717000).                                                   |               |
| end_time      | integer | no       | End timestamp in milliseconds (e.g., 1641522717000).                                                     |               |
| unit          | string  | no       | Unit for the returned data, choose between 'usd' or 'coin'.                                              | usd           |


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/spot/aggregated-taker-buy-sell-volume/history?exchange_list=Binance&symbol=BTC&interval=h1' \
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


The available historical data length depends on your subscription plan and the selected interval. Please refer to the table below for more details:

For more information on historical data access by plan and interval, see [references/plans-interval-history-length.md](references/plans-interval-history-length.md).



### Method: GET

**URL**:
```
https://open-api-v4.coinglass.com//api/spot/volume/footprint-history
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

| Parameter  | Type    | Required | Description                                                                                             | Example value |
| ---------- | ------- | -------- | ------------------------------------------------------------------------------------------------------- | ------------- |
| exchange   | string  | yes      | Spot exchange names (Supported Binance, OKX, Bybit)                                                     | Binance       |
| symbol     | string  | yes      | Trading pair (e.g., BTCUSDT). Retrieve supported pairs via the 'support-exchange-pair' API.             | BTCUSDT       |
| interval   | string  | yes      | Time interval for data aggregation. Supported values: 1m, 3m, 5m, 15m, 30m, 1h, 4h, 6h, 8h, 12h, 1d, 1w | 1h            |
| limit      | integer | no       | Number of results per request. Default: 1000, Maximum: 1000                                             |               |
| start_time | integer | no       | Start timestamp in milliseconds (e.g., 1641522717000).                                                  |               |
| end_time   | integer | no       | End timestamp in milliseconds (e.g., 1641522717000).                                                    |               |


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/spot/volume/footprint-history?exchange=Binance&symbol=BTCUSDT&interval=1h' \
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
https://open-api-v4.coinglass.com//api/spot/cvd/history
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

| Parameter  | Type    | Required | Description                                                                                                       | Example value |
| ---------- | ------- | -------- | ----------------------------------------------------------------------------------------------------------------- | ------------- |
| exchange   | string  | yes      | Exchange name (e.g., Binance). Retrieve supported exchanges via the 'supported-exchange-pair' API.                | Binance       |
| symbol     | string  | yes      | Trading pair (e.g., BTCUSDT). Retrieve supported pairs via the 'supported-exchange-pair' API.                     | BTCUSDT       |
| interval   | string  | yes      | Time interval for data aggregation. Supported values: 1m, 3m, 5m, 15m, 30m, 1h, 4h, 6h, 8h, 12h, 1d, 1w           | 1h            |
| limit      | integer | no       | Number of results per request. Default: 1000, Maximum: 1000                                                       |               |
| start_time | integer | no       | Start timestamp in milliseconds (e.g., 1641522717000).  The starting timestamp from which CVD calculation begins. |               |
| end_time   | integer | no       | Start timestamp in milliseconds (e.g., 1641522717000).                                                            |               |
| unit       | string  | no       | Unit for the returned data, choose between 'usd' or 'coin'.   Default: 'usd'                                      |               |


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/spot/cvd/history?exchange=Binance&symbol=BTCUSDT&interval=1h' \
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
https://open-api-v4.coinglass.com//api/spot/aggregated-cvd/history
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

| Parameter     | Type    | Required | Description                                                                                                                        | Example value |
| ------------- | ------- | -------- | ---------------------------------------------------------------------------------------------------------------------------------- | ------------- |
| exchange_list | string  | yes      | Comma-separated exchange names (e.g., "binance, okx, bybit"). Retrieve supported exchanges via the 'supported-exchange-pairs' API. | Binance       |
| symbol        | string  | yes      | Trading pair (e.g., BTC). Retrieve supported coins via the 'support-coins' API.                                                    | BTC           |
| interval      | string  | yes      | Time interval for data aggregation.
Supported values: 1m, 3m, 5m, 15m, 30m, 1h, 4h, 6h, 8h, 12h, 1d, 1w
                           | 1h            |
| limit         | integer | no       | Number of results per request. Default: 1000, Maximum: 4500                                                                        |               |
| start_time    | integer | no       | Start timestamp in milliseconds (e.g., 1641522717000).  The starting timestamp from which CVD calculation begins.                  |               |
| end_time      | integer | no       | 
End timestamp in milliseconds (e.g., 1641522717000).                                                                              |               |
| unit          | string  | no       | Unit for the returned data, choose between 'usd' or 'coin'.  Default: 'usd'                                                        |               |


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/spot/aggregated-cvd/history?exchange_list=Binance&symbol=BTC&interval=1h' \
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
https://open-api-v4.coinglass.com//api/spot/netflow-list
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

| Parameter | Type    | Required | Description                               | Example value |
| --------- | ------- | -------- | ----------------------------------------- | ------------- |
| per_page  | integer | no       | Number of results per page.               |               |
| page      | integer | no       | Page number for pagination, default: 1.

 |               |


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/spot/netflow-list' \
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
      "taker_buy_volume_usd_5m": 23817063.00355,
      "taker_sell_volume_usd_5m": 14688850.4490948,
      "net_flow_usd_5m": 9128212.5544552,
      "taker_buy_volume_usd_15m": 64458138.15245,
      "taker_sell_volume_usd_15m": 56267852.8582948,
      "net_flow_usd_15m": 8190285.2941552,
      "taker_buy_volume_usd_30m": 152744538.92745,
      "taker_sell_volume_usd_30m": 122661161.6758948,
      "net_flow_usd_30m": 30083377.2515552,
      "taker_buy_volume_usd_1h": 440544708.75065,
      "taker_sell_volume_usd_1h": 326579508.8264948,
      "net_flow_usd_1h": 113965199.9241552,
      "taker_buy_volume_usd_2h": 762982613.25415,
      "taker_sell_volume_usd_2h": 579323636.6009948,
      "net_flow_usd_2h": 183658976.6531552,
      "taker_buy_volume_usd_4h": 2083240736.38015,
      "taker_sell_volume_usd_4h": 1464050013.7042947,
      "net_flow_usd_4h": 619190722.6758552,
      "taker_buy_volume_usd_6h": 2811782257.79735,
      "taker_sell_volume_usd_6h": 2115918461.0476947,
      "net_flow_usd_6h": 695863796.7496552,
      "taker_buy_volume_usd_8h": 5569645388.97045,
      "taker_sell_volume_usd_8h": 4908424264.731495,
      "net_flow_usd_8h": 661221124.2389553,
      "taker_buy_volume_usd_12h": 9808385961.73665,
      "taker_sell_volume_usd_12h": 9239720429.892195,
      "net_flow_usd_12h": 568665531.8444552,
      "taker_buy_volume_usd_24h": 15783807234.40935,
      "taker_sell_volume_usd_24h": 15888011086.572395,
      "net_flow_usd_24h": -104203852.1630448,
      "taker_buy_volume_usd_3d": 172158061928.49524,
      "taker_sell_volume_usd_3d": 171369751943.40836,
      "net_flow_usd_3d": 588309985.0868665,
      "taker_buy_volume_usd_7d": 98531427734.15463,
      "taker_sell_volume_usd_7d": 97358408204.01096,
      "net_flow_usd_1w": 1173019530.1436665,
      "taker_buy_volume_usd_15d": 173153061928.49524,
      "taker_sell_volume_usd_15d": 172364751943.40836,
      "net_flow_usd_15d": 788309985.0868665,
      "taker_buy_volume_usd_30d": 423872219745.3059,
      "taker_sell_volume_usd_30d": 427388634817.09235,
      "net_flow_usd_30d": -3516415071.7864337,
      "market_cap": 1823476500360.4873
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
https://open-api-v4.coinglass.com//api/spot/coin/netflow
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

| Parameter     | Type   | Required | Description                                                                                                                                         | Example value                     |
| ------------- | ------ | -------- | --------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------- |
| symbol        | string | yes      | Trading coin (e.g., BTC). Retrieve supported coins via the 'supported-coins' API.                                                                   | BTC                               |
| exchange_list | string | yes      | exchange_list: List of exchange names to retrieve data from (e.g., 'Binance, OKX, Bybit') . Default exchanges: "Binance, Bybit, OKX, Bitget, Gate". | Binance, Bybit, OKX, Bitget, Gate |


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/spot/coin/netflow?symbol=BTC&exchange_list=Binance%2C+Bybit%2C+OKX%2C+Bitget%2C+Gate' \
-H 'Content-Type: application/json' \
-H 'CG-API-KEY: ${YOUR_API_KEY}' \
-H 'User-Agent: coinglass-skill/1.0.0'
```
        
**Response**:
```json
{"code":"0","msg":"success","data":{"symbol":"BTC","taker_buy_volume_usd_5m":"8564899","taker_sell_volume_usd_5m":"9692915","net_flow_usd_5m":"-1128017","net_flow_usd_change_percent_5m":-51.73,"net_flow_usd_5m_market_cap_ratio":-0.000076,"taker_buy_volume_usd_15m":"29134420","taker_sell_volume_usd_15m":"44784583","net_flow_usd_15m":"-15650163","net_flow_usd_change_percent_15m":-206.69,"net_flow_usd_15m_market_cap_ratio":-0.001055,"taker_buy_volume_usd_30m":"79865179","taker_sell_volume_usd_30m":"80845695","net_flow_usd_30m":"-980517","net_flow_usd_change_percent_30m":-104.76,"net_flow_usd_30m_market_cap_ratio":-0.000066,"taker_buy_volume_usd_1h":"165477715","taker_sell_volume_usd_1h":"145832349","net_flow_usd_1h":"19645366","net_flow_usd_change_percent_1h":217.96,"net_flow_usd_1h_market_cap_ratio":0.001324,"taker_buy_volume_usd_4h":"760187107","taker_sell_volume_usd_4h":"729339048","net_flow_usd_4h":"30848059","net_flow_usd_change_percent_4h":135.14,"net_flow_usd_4h_market_cap_ratio":0.00208,"taker_buy_volume_usd_8h":"1005775816","taker_sell_volume_usd_8h":"1044121929","net_flow_usd_8h":"-38346114","net_flow_usd_change_percent_8h":-9.06,"net_flow_usd_8h_market_cap_ratio":-0.002585,"taker_buy_volume_usd_12h":"2442236886","taker_sell_volume_usd_12h":"2561495148","net_flow_usd_12h":"-119258262","net_flow_usd_change_percent_12h":-129.43,"net_flow_usd_12h_market_cap_ratio":-0.00804,"taker_buy_volume_usd_24h":"7566899147","taker_sell_volume_usd_24h":"7280826322","net_flow_usd_24h":"286072825","net_flow_usd_change_percent_24h":-60.91,"net_flow_usd_24h_market_cap_ratio":0.019286,"taker_buy_volume_usd_3d":"25868053532","taker_sell_volume_usd_3d":"24153912510","net_flow_usd_3d":"1714141022","net_flow_usd_change_percent_3d":-16.01,"net_flow_usd_3d_market_cap_ratio":0.115562,"taker_buy_volume_usd_5d":"35555399802","taker_sell_volume_usd_5d":"33163465367","net_flow_usd_5d":"2391934436","net_flow_usd_change_percent_5d":-9.4,"net_flow_usd_5d_market_cap_ratio":0.161257,"taker_buy_volume_usd_7d":"58795007181","taker_sell_volume_usd_7d":"55000626111","net_flow_usd_7d":"3794381071","net_flow_usd_change_percent_7d":1960.91,"net_flow_usd_7d_market_cap_ratio":0.255806,"taker_buy_volume_usd_10d":"90978663883","taker_sell_volume_usd_10d":"85946889007","net_flow_usd_10d":"5031774877","net_flow_usd_change_percent_10d":506.96,"net_flow_usd_10d_market_cap_ratio":0.339227,"taker_buy_volume_usd_15d":"137799491538","taker_sell_volume_usd_15d":"132072679473","net_flow_usd_15d":"5726812066","net_flow_usd_change_percent_15d":3668.93,"net_flow_usd_15d_market_cap_ratio":0.386085,"taker_buy_volume_usd_30d":"266960790361","taker_sell_volume_usd_30d":"261394441706","net_flow_usd_30d":"5566348656","net_flow_usd_change_percent_30d":151.96,"net_flow_usd_30d_market_cap_ratio":0.375267,"taker_buy_volume_usd_40d":"349549701197","taker_sell_volume_usd_40d":"344312184923","net_flow_usd_40d":"5237516274","net_flow_usd_change_percent_40d":152.76,"net_flow_usd_40d_market_cap_ratio":0.353098,"taker_buy_volume_usd_50d":"496844249786","taker_sell_volume_usd_50d":"499136038696","net_flow_usd_50d":"-2291788910","net_flow_usd_change_percent_50d":57.87,"net_flow_usd_50d_market_cap_ratio":-0.154506,"taker_buy_volume_usd_60d":"564792098258","taker_sell_volume_usd_60d":"569939808511","net_flow_usd_60d":"-5147710254","net_flow_usd_change_percent_60d":41.36,"net_flow_usd_60d_market_cap_ratio":-0.347043,"taker_buy_volume_usd_90d":"766953365285","taker_sell_volume_usd_90d":"771796120595","net_flow_usd_90d":"-4842755310","net_flow_usd_change_percent_90d":86.29,"net_flow_usd_90d_market_cap_ratio":-0.326484,"taker_buy_volume_usd_120d":"1062521073566","taker_sell_volume_usd_120d":"1076447240334","net_flow_usd_120d":"-13926166769","net_flow_usd_change_percent_120d":72.68,"net_flow_usd_120d_market_cap_ratio":-0.938861,"taker_buy_volume_usd_150d":"1374917377958","taker_sell_volume_usd_150d":"1401464473468","net_flow_usd_150d":"-26547095511","net_flow_usd_change_percent_150d":45.46,"net_flow_usd_150d_market_cap_ratio":-1.789726,"taker_buy_volume_usd_180d":"1713318564888","taker_sell_volume_usd_180d":"1753478516197","net_flow_usd_180d":"-40159951310","net_flow_usd_change_percent_180d":-23.01,"net_flow_usd_180d_market_cap_ratio":-2.707464,"taker_buy_volume_usd_1y":"3618522811709","taker_sell_volume_usd_1y":"3690105674385","net_flow_usd_1y":"-71582862676","net_flow_usd_change_percent_1y":-0.17,"net_flow_usd_1y_market_cap_ratio":-4.825903},"success":true}
```

---
  