---
name: long-short-ratio
description: Long-Short Ratio request using the CoinGlass API. 
metadata:
  version: 1.0.0
  author: CoinGlass
  openclaw:
    requires:
      bins:
        - curl
        - openssl
    homepage: https://github.com/coinglass-official/coinglass-api-skills/tree/main/futures/long-short-ratio/API.md
license: MIT
---

# CoinGlass Long-Short Ratio Skill

Long-Short Ratio request on CoinGLass API endpoints. Return the result in JSON format.


## Quick Reference

| API                           | Endpoint                                             | Function                                                                                                                        |
| ----------------------------- | ---------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------- |
| Global Account Ratio          | /api/futures/global-long-short-account-ratio/history | This endpoint provides the long/short account ratio history for trading pairs on a specific exchange.                           |
| Top Account Ratio History     | /api/futures/top-long-short-account-ratio/history    | This endpoint provides historical data for the long/short account ratio of top traders.                                         |
| Top Position Ratio History    | /api/futures/top-long-short-position-ratio/history   | This endpoint provides historical data for the long/short position ratio of top traders.                                        |
| Exchange Taker Buy/Sell Ratio | /api/futures/taker-buy-sell-volume/exchange-list     | This endpoint provides the long/short ratio of aggregated taker buy/sell volumes across exchanges.                              |
| Net Long/Short Position       | /api/futures/net-position/history                    | This endpoint provides the historical net position data for futures, including the net_long_change and net_short_change values. |
| Net Long/Short Position (v2)  | /api/futures/v2/net-position/history                 | This endpoint provides the historical net position data for futures, including the net_long_change and net_short_change values. |

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
        
## API 1: Global Account Ratio


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
https://open-api-v4.coinglass.com//api/futures/global-long-short-account-ratio/history
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

| Parameter  | Type    | Required | Description                                                                                                      | Example value |
| ---------- | ------- | -------- | ---------------------------------------------------------------------------------------------------------------- | ------------- |
| exchange   | string  | yes      | Futures exchange names (e.g., Binance, OKX) .Retrieve supported exchanges via the 'supported-exchange-pair' API. | Binance       |
| symbol     | string  | yes      | Trading pair (e.g., BTCUSDT). Retrieve supported pairs via the 'supported-exchange-pair' API.                    | BTCUSDT       |
| interval   | string  | yes      | Time interval for data aggregation.  Supported values: 1m, 3m, 5m, 15m, 30m, 1h, 4h, 6h, 8h, 12h, 1d, 1w         | 4h            |
| limit      | integer | no       | Number of results per request.  Default: 1000, Maximum: 1000                                                     |               |
| start_time | integer | no       | Start timestamp in milliseconds (e.g., 1641522717000).                                                           |               |
| end_time   | integer | no       | End timestamp in milliseconds (e.g., 1641522717000).                                                             |               |


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/futures/global-long-short-account-ratio/history?exchange=Binance&symbol=BTCUSDT&interval=4h' \
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
      "time": 1741604400000, // Timestamp (in milliseconds)
      "global_account_long_percent": 73.88, // Long position percentage of accounts (%)
      "global_account_short_percent": 26.12, // Short position percentage of accounts (%)
      "global_account_long_short_ratio": 2.83 // Long/Short ratio of accounts
    },
    {
      "time": 1741608000000, // Timestamp (in milliseconds)
      "global_account_long_percent": 73.24, // Long position percentage of accounts (%)
      "global_account_short_percent": 26.76, // Short position percentage of accounts (%)
      "global_account_long_short_ratio": 2.74 // Long/Short ratio of accounts
    }
  ]
}
```

---
  
  
  ---
        
## API 2: Top Account Ratio History


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
https://open-api-v4.coinglass.com//api/futures/top-long-short-account-ratio/history
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

| Parameter  | Type    | Required | Description                                                                                                      | Example value |
| ---------- | ------- | -------- | ---------------------------------------------------------------------------------------------------------------- | ------------- |
| exchange   | string  | yes      | Futures exchange names (e.g., Binance, OKX) .Retrieve supported exchanges via the 'supported-exchange-pair' API. | Binance       |
| symbol     | string  | yes      | Trading pair (e.g., BTCUSDT). Retrieve supported pairs via the 'supported-exchange-pair' API.                    | BTCUSDT       |
| interval   | string  | yes      | Time interval for data aggregation.  Supported values: 1m, 3m, 5m, 15m, 30m, 1h, 4h, 6h, 8h, 12h, 1d, 1w         | 4h            |
| limit      | integer | no       | Number of results per request.  Default: 1000, Maximum: 1000                                                     |               |
| start_time | integer | no       | Start timestamp in milliseconds (e.g., 1641522717000).                                                           |               |
| end_time   | integer | no       | End timestamp in milliseconds (e.g., 1641522717000).                                                             |               |


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/futures/top-long-short-account-ratio/history?exchange=Binance&symbol=BTCUSDT&interval=4h' \
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
      "time": 1741615200000, // Timestamp (in milliseconds)
      "top_account_long_percent": 73.3, // Long position percentage of top accounts (%)
      "top_account_short_percent": 26.7, // Short position percentage of top accounts (%)
      "top_account_long_short_ratio": 2.75 // Long/Short ratio of top accounts
    },
    {
      "time": 1741618800000, // Timestamp (in milliseconds)
      "top_account_long_percent": 74.18, // Long position percentage of top accounts (%)
      "top_account_short_percent": 25.82, // Short position percentage of top accounts (%)
      "top_account_long_short_ratio": 2.87 // Long/Short ratio of top accounts
    }
  ]
}
```

---
  
  
  ---
        
## API 3: Top Position Ratio History


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
https://open-api-v4.coinglass.com//api/futures/top-long-short-position-ratio/history
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

| Parameter  | Type    | Required | Description                                                                                                      | Example value |
| ---------- | ------- | -------- | ---------------------------------------------------------------------------------------------------------------- | ------------- |
| exchange   | string  | yes      | Futures exchange names (e.g., Binance, OKX) .Retrieve supported exchanges via the 'supported-exchange-pair' API. | Binance       |
| symbol     | string  | yes      | Trading pair (e.g., BTCUSDT). Retrieve supported pairs via the 'supported-exchange-pair' API.                    | BTCUSDT       |
| interval   | string  | yes      | Time interval for data aggregation.  Supported values: 1m, 3m, 5m, 15m, 30m, 1h, 4h, 6h, 8h, 12h, 1d, 1w         | 4h            |
| limit      | integer | no       | Number of results per request.  Default: 1000, Maximum: 1000                                                     |               |
| start_time | integer | no       | Start timestamp in milliseconds (e.g., 1641522717000).                                                           |               |
| end_time   | integer | no       | End timestamp in milliseconds (e.g., 1641522717000).                                                             |               |


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/futures/top-long-short-position-ratio/history?exchange=Binance&symbol=BTCUSDT&interval=4h' \
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
      "time": 1741615200000, // Timestamp (in milliseconds)
      "top_position_long_percent": 64.99, // Long position percentage of top positions (%)
      "top_position_short_percent": 35.01, // Short position percentage of top positions (%)
      "top_position_long_short_ratio": 1.86 // Long/Short ratio of top positions
    },
    {
      "time": 1741618800000, // Timestamp (in milliseconds)
      "top_position_long_percent": 64.99, // Long position percentage of top positions (%)
      "top_position_short_percent": 35.01, // Short position percentage of top positions (%)
      "top_position_long_short_ratio": 1.86 // Long/Short ratio of top positions
    }
  ]
}
```

---
  
  
  ---
        
## API 4: Exchange Taker Buy/Sell Ratio


**Supported Plans, Intervals, and Historical Data Access**

Hobbyist:Available
Startup:Available
Standard:Available
Professional:Available


### Method: GET

**URL**:
```
https://open-api-v4.coinglass.com//api/futures/taker-buy-sell-volume/exchange-list
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

| Parameter | Type   | Required | Description                                                                        | Example value |
| --------- | ------ | -------- | ---------------------------------------------------------------------------------- | ------------- |
| symbol    | string | yes      | Trading coin (e.g., BTC).  Retrieve supported coins via the 'supported-coins' API. | BTC           |
| range     | string | yes      | Time range for the data (e.g., 5m, 15m, 30m, 1h, 4h,12h, 24h).                     | 4h            |


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/futures/taker-buy-sell-volume/exchange-list?symbol=BTC&range=4h' \
-H 'Content-Type: application/json' \
-H 'CG-API-KEY: ${YOUR_API_KEY}' \
-H 'User-Agent: coinglass-skill/1.0.0'
```
        
**Response**:
```json
{
  "code": "0",
  "msg": "success",
  "data": {
    "symbol": "BTC", // Token symbol
    "buy_ratio": 51.01, // Buy ratio (%)
    "sell_ratio": 48.99, // Sell ratio (%)
    "buy_vol_usd": 1112108532.1688, // Total buy volume (USD)
    "sell_vol_usd": 1068220541.0417, // Total sell volume (USD)
    "exchange_list": [ // Buy/sell data per exchange
      {
        "exchange": "Binance", // Exchange name
        "buy_ratio": 49.22, // Buy ratio (%)
        "sell_ratio": 50.78, // Sell ratio (%)
        "buy_vol_usd": 240077939.5811, // Buy volume (USD)
        "sell_vol_usd": 247674925.1653 // Sell volume (USD)
      },
      {
        "exchange": "OKX", // Exchange name
        "buy_ratio": 50.84, // Buy ratio (%)
        "sell_ratio": 49.16, // Sell ratio (%)
        "buy_vol_usd": 108435724.6214, // Buy volume (USD)
        "sell_vol_usd": 104834502.5904 // Sell volume (USD)
      }
    ]
  }
}
```

---
  
  
  ---
        
## API 5: Net Long/Short Position


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
https://open-api-v4.coinglass.com//api/futures/net-position/history
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

| Parameter  | Type    | Required | Description                                                                                         | Example value |
| ---------- | ------- | -------- | --------------------------------------------------------------------------------------------------- | ------------- |
| exchange   | string  | yes      | Spot exchange names (Supported Binance, OKX,Bybit,Hyperliquid)                                      | Binance       |
| symbol     | string  | yes      | Trading pair (e.g., BTCUSDT). Retrieve supported pairs via the 'support-exchange-pair' API.         | BTCUSDT       |
| interval   | string  | yes      | Time interval for data aggregation. Supported values: 1m, 3m, 5m, 15m, 30m, 1h, 4h, 6h, 8h, 12h, 1d | 4h            |
| limit      | integer | no       | Number of results per request. Default: 1000, Maximum: 1000                                         |               |
| start_time | integer | no       | Start timestamp in milliseconds (e.g., 1641522717000).                                              |               |
| end_time   | integer | no       | End timestamp in milliseconds (e.g., 1641522717000).                                                |               |


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/futures/net-position/history?exchange=Binance&symbol=BTCUSDT&interval=4h' \
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
      "net_long_change": -50.11,
      "net_short_change": 0,
      "net_long_change_cum": -50.11,
      "net_short_change_cum": 0,
      "net_position_change_cum": -50.11,
      "time": 1767272400000
    },
    {
      "net_long_change": 0,
      "net_short_change": -64.88,
      "net_long_change_cum": -50.11,
      "net_short_change_cum": -64.88,
      "net_position_change_cum": 14.77,
      "time": 1767276000000
    },
}
```

---
  
  
  ---
        
## API 6: Net Long/Short Position (v2)


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
https://open-api-v4.coinglass.com//api/futures/v2/net-position/history
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

| Parameter  | Type    | Required | Description                                                                                             | Example value |
| ---------- | ------- | -------- | ------------------------------------------------------------------------------------------------------- | ------------- |
| exchange   | string  | yes      | Currently available for Binance exchange only.                                                          | Binance       |
| symbol     | string  | yes      | Trading pair (e.g., BTCUSDT). Retrieve supported pairs via the 'supported-exchange-pair' API.           | BTCUSDT       |
| interval   | string  | yes      | Time interval for data aggregation. Supported values: 1m, 3m, 5m, 15m, 30m, 1h, 4h, 6h, 8h, 12h, 1d, 1w | 4h            |
| limit      | integer | no       | Number of results per request. Default: 1000, Maximum: 1000                                             |               |
| start_time | integer | no       | Start timestamp in milliseconds (e.g., 1641522717000).                                                  |               |
| end_time   | integer | no       | End timestamp in milliseconds (e.g., 1641522717000).                                                    |               |


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/futures/v2/net-position/history?exchange=Binance&symbol=BTCUSDT&interval=4h' \
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
      "net_long_change": -50.11,
      "net_short_change": 0,
      "net_long_change_cum": -50.11,
      "net_short_change_cum": 0,
      "net_position_change_cum": -50.11,
      "time": 1767272400000
    },
    {
      "net_long_change": 0,
      "net_short_change": -64.88,
      "net_long_change_cum": -50.11,
      "net_short_change_cum": -64.88,
      "net_position_change_cum": 14.77,
      "time": 1767276000000
    },
}
```

---
  