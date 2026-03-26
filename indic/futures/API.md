---
name: futures
description: Futures request using the CoinGlass API. 
metadata:
  version: 1.0.0
  author: CoinGlass
  openclaw:
    requires:
      bins:
        - curl
        - openssl
    homepage: https://github.com/coinglass-official/coinglass-api-skills/tree/main/indic/futures/API.md
license: MIT
---

# CoinGlass Futures Skill

Futures request on CoinGLass API endpoints. Return the result in JSON format.


## Quick Reference

| API                                          | Endpoint                               | Function                                                                                                                                                                                                                                                                   |
| -------------------------------------------- | -------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Coin RSI List                                | /api/futures/rsi/list                  | This endpoint provides the Relative Strength Index (RSI) values for multiple cryptocurrencies across different timeframes.                                                                                                                                                 |
| Pair RSI                                     | /api/futures/indicators/rsi            | This endpoint provides RSI values for trading pairs .                                                                                                                                                                                                                      |
| Pair Moving Average (MA)                     | /api/futures/indicators/ma             | This endpoint provides Moving Average (MA) for trading pairs .                                                                                                                                                                                                             |
| Coin Moving Average List(MA)                 | /api/futures/ma/list                   | This API provides moving average (MA) indicator data for multiple cryptocurrencies across different time periods.                                                                                                                                                          |
| Exponential Moving Average (EMA)             | /api/futures/indicators/ema            | This endpoint provides Exponential Moving Average (EMA) for trading pairs .                                                                                                                                                                                                |
| Coin Exponential Moving Average List (EMA)   | /api/futures/ema/list                  | This API provides exponential moving average (EMA) indicator data for multiple cryptocurrencies across different time periods.                                                                                                                                             |
| Bollinger Bands (BOLL)                       | /api/futures/indicators/boll           | This endpoint provides Bollinger Bands (BOLL) for trading pairs .                                                                                                                                                                                                          |
| Moving Average Convergence Divergence (MACD) | /api/futures/indicators/macd           | This endpoint provides Moving Average Convergence Divergence (MACD) for pairs .                                                                                                                                                                                            |
| Coin MACD List                               | /api/futures/macd/list                 | This endpoint returns current MACD values across multiple timeframes for each symbol.  This endpoint returns current Moving Average Convergence Divergence (MACD) values across multiple timeframes for each symbol, calculated using the standard parameters (12, 26, 9). |
| Futures Basis                                | /api/futures/basis/history             | This endpoint provides historical futures basis data, including open and close basis rates and their corresponding annualized percentage changes over time.                                                                                                                |
| Whale Index                                  | /api/futures/whale-index/history       | This endpoint provides historical Whale Index data.                                                                                                                                                                                                                        |
| CGDI Index                                   | /api/futures/cgdi-index/history        | This endpoint provides historical CGDI (CoinGlass Derivatives Index) data                                                                                                                                                                                                  |
| CDRI Index                                   | /api/futures/cdri-index/history        | This endpoint provides historical CDRI (CoinGlass Derivatives Risk Index) data.                                                                                                                                                                                            |
| Pair Average True Range (ATR)                | /api/futures/indicators/avg-true-range | This endpoint provides Average True Range (ATR) for trading pairs.                                                                                                                                                                                                         |
| Coin Average True Range (ATR) List           | /api/futures/avg-true-range/list       | This API provides Average True Range (ATR) indicator data for multiple coins across different time intervals.                                                                                                                                                              |

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
        
## API 1: Coin RSI List


**Supported Plans, Intervals, and Historical Data Access**

Hobbyist:Not Available
Startup:Not Available
Standard:Available
Professional:Available


### Method: GET

**URL**:
```
https://open-api-v4.coinglass.com//api/futures/rsi/list
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

*No parameters required*


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/futures/rsi/list' \
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
      "symbol": "BTC",                                  // Token symbol, e.g., BTC = Bitcoin
      "rsi_15m": 54.71,                                 // RSI (Relative Strength Index) over 15 minutes
      "price_change_percent_15m": 0.04,                 // Price change percentage over 15 minutes
      "rsi_1h": 71.91,                                  // RSI over 1 hour
      "price_change_percent_1h": -0.23,                 // Price change percentage over 1 hour
      "rsi_4h": 72.12,                                  // RSI over 4 hours
      "price_change_percent_4h": -0.09,                 // Price change percentage over 4 hours
      "rsi_12h": 62.33,                                 // RSI over 12 hours
      "price_change_percent_12h": 2.72,                 // Price change percentage over 12 hours
      "rsi_24h": 57.88,                                 // RSI over 24 hours
      "price_change_percent_24h": 3.4,                  // Price change percentage over 24 hours
      "rsi_1w": 52.04,                                  // RSI over 1 week
      "price_change_percent_1w": 2.6,                   // Price change percentage over 1 week
      "current_price": 87348.6                          // Current market price
    },
    {
      "symbol": "ETH",                                  // Token symbol, e.g., ETH = Ethereum
      "rsi_15m": 54.35,                                 // RSI over 15 minutes
      "price_change_percent_15m": -0.13,                // Price change percentage over 15 minutes
      "rsi_1h": 67.93,                                  // RSI over 1 hour
      "price_change_percent_1h": -0.26,                 // Price change percentage over 1 hour
      "rsi_4h": 63.6,                                   // RSI over 4 hours
      "price_change_percent_4h": 0.2,                   // Price change percentage over 4 hours
      "rsi_12h": 52.09,                                 // RSI over 12 hours
      "price_change_percent_12h": 3.41,                 // Price change percentage over 12 hours
      "rsi_24h": 45.03,                                 // RSI over 24 hours
      "price_change_percent_24h": 3.27,                 // Price change percentage over 24 hours
      "rsi_1w": 33.31,                                  // RSI over 1 week
      "price_change_percent_1w": 3.45,                  // Price change percentage over 1 week
      "current_price": 1641.36                          // Current market price
    }
  ]
}
```

---
  
  
  ---
        
## API 2: Pair RSI


**Supported Plans, Intervals, and Historical Data Access**

Hobbyist:Not Available
Startup:Available
Standard:Available
Professional:Available


### Method: GET

**URL**:
```
https://open-api-v4.coinglass.com//api/futures/indicators/rsi
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

| Parameter   | Type    | Required | Description                                                                                                    | Example value |
| ----------- | ------- | -------- | -------------------------------------------------------------------------------------------------------------- | ------------- |
| exchange    | string  | yes      | Futures exchange names (e.g., Binance, OKX) .Retrieve supported exchanges via the 'support-exchange-pair' API. | Binance       |
| symbol      | string  | yes      |  Trading pair (e.g., BTCUSDT). Retrieve supported pairs via the 'support-exchange-pair' API.                   | BTCUSDT       |
| interval    | string  | yes      | Time interval for data aggregation.  Supported values: 1m, 3m, 5m, 15m, 30m, 1h, 4h, 6h, 8h, 12h, 1d, 1w       | 1h            |
| limit       | string  | no       | Number of results per request.  Default: 1000, Maximum: 4500                                                   |               |
| start_time  | integer | no       | Start timestamp in milliseconds (e.g., 1641522717000).                                                         |               |
| end_time    | integer | no       | End timestamp in milliseconds (e.g., 1641522717000).                                                           |               |
| window      | integer | no       | Window size — defines the number of data points used for indicator calculation (e.g., 14 for RSI).             |               |
| series_type | string  | no       | Price type used in calculation. Supported values: open, high, low, close. Default: close.                      |               |


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/futures/indicators/rsi?exchange=Binance&symbol=BTCUSDT&interval=1h' \
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
      "time": 1759287600000,
      "rsi_value": 59.32633395
    },
    {
      "time": 1759291200000,
      "rsi_value": 60.90396216
    },
}
```

---
  
  
  ---
        
## API 3: Pair Moving Average (MA)


**Supported Plans, Intervals, and Historical Data Access**

Hobbyist:Not Available
Startup:Available
Standard:Available
Professional:Available


### Method: GET

**URL**:
```
https://open-api-v4.coinglass.com//api/futures/indicators/ma
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

| Parameter   | Type    | Required | Description                                                                                                    | Example value |
| ----------- | ------- | -------- | -------------------------------------------------------------------------------------------------------------- | ------------- |
| exchange    | string  | yes      | Futures exchange names (e.g., Binance, OKX) .Retrieve supported exchanges via the 'support-exchange-pair' API. | Binance       |
| symbol      | string  | yes      |  Trading pair (e.g., BTCUSDT). Retrieve supported pairs via the 'support-exchange-pair' API.                   | BTCUSDT       |
| interval    | string  | yes      | Time interval for data aggregation.  Supported values: 1m, 3m, 5m, 15m, 30m, 1h, 4h, 6h, 8h, 12h, 1d, 1w       | 1h            |
| limit       | string  | no       | Number of results per request.  Default: 1000, Maximum: 4500                                                   |               |
| start_time  | integer | no       | Start timestamp in milliseconds (e.g., 1641522717000).                                                         |               |
| end_time    | integer | no       | End timestamp in milliseconds (e.g., 1641522717000).                                                           |               |
| window      | integer | no       | Window size — defines the number of data points used for indicator calculation (e.g., 10 for MA).              |               |
| series_type | string  | no       | Price type used in calculation. Supported values: open, high, low, close. Default: close.                      |               |


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/futures/indicators/ma?exchange=Binance&symbol=BTCUSDT&interval=1h' \
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
      "time": 1759287600000,
      "ma_value": 114209.64
    },
    {
      "time": 1759291200000,
      "ma_value": 114200.6
    },
}
```

---
  
  
  ---
        
## API 4: Coin Moving Average List(MA)


**Supported Plans, Intervals, and Historical Data Access**

Hobbyist:Not Available
Startup:Not Available
Standard:Available
Professional:Available


### Method: GET

**URL**:
```
https://open-api-v4.coinglass.com//api/futures/ma/list
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

*No parameters required*


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/futures/ma/list' \
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
      "close_price": 68026.7,
      "ma_1m": 68034.8,
      "ma_5m": 67987.1,
      "ma_15m": 67879.6,
      "ma_30m": 67997,
      "ma_1h": 68131.6,
      "ma_4h": 68717.9,
      "ma_1d": 70866.4,
      "ma_1w": 69008.5
    },
    {
      "symbol": "ETH",
      "close_price": 2054.27,
      "ma_1m": 2054.86,
      "ma_5m": 2055.33,
      "ma_15m": 2051.83,
      "ma_30m": 2054.24,
      "ma_1h": 2058.39,
      "ma_4h": 2084.59,
      "ma_1d": 2168.92,
      "ma_1w": 2048.88
    },
  ]
}
```

---
  
  
  ---
        
## API 5: Exponential Moving Average (EMA)


**Supported Plans, Intervals, and Historical Data Access**

Hobbyist:Not Available
Startup:Available
Standard:Available
Professional:Available


### Method: GET

**URL**:
```
https://open-api-v4.coinglass.com//api/futures/indicators/ema
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

| Parameter   | Type    | Required | Description                                                                                                    | Example value |
| ----------- | ------- | -------- | -------------------------------------------------------------------------------------------------------------- | ------------- |
| exchange    | string  | yes      | Futures exchange names (e.g., Binance, OKX) .Retrieve supported exchanges via the 'support-exchange-pair' API. | Binance       |
| symbol      | string  | yes      |  Trading pair (e.g., BTCUSDT). Retrieve supported pairs via the 'support-exchange-pair' API.                   | BTCUSDT       |
| interval    | string  | yes      | Time interval for data aggregation.  Supported values: 1m, 3m, 5m, 15m, 30m, 1h, 4h, 6h, 8h, 12h, 1d, 1w       | 1h            |
| limit       | string  | no       | Number of results per request.  Default: 1000, Maximum: 4500                                                   |               |
| start_time  | integer | no       | Start timestamp in milliseconds (e.g., 1641522717000).                                                         |               |
| end_time    | integer | no       | End timestamp in milliseconds (e.g., 1641522717000).                                                           |               |
| window      | integer | no       | Window size — defines the number of data points used for indicator calculation (e.g., 10 for EMA).             |               |
| series_type | string  | no       | Price type used in calculation. Supported values: open, high, low, close. Default: close.                      |               |


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/futures/indicators/ema?exchange=Binance&symbol=BTCUSDT&interval=1h' \
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
      "time": 1759287600000,
      "ema_value": 114209.64
    },
    {
      "time": 1759291200000,
      "ema_value": 114200.6
    },
}
```

---
  
  
  ---
        
## API 6: Coin Exponential Moving Average List (EMA)


**Supported Plans, Intervals, and Historical Data Access**

Hobbyist:Not Available
Startup:Not Available
Standard:Available
Professional:Available


### Method: GET

**URL**:
```
https://open-api-v4.coinglass.com//api/futures/ema/list
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

*No parameters required*


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/futures/ema/list' \
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
      "close_price": 67943.4,
      "ema_1m": 68003.4,
      "ema_5m": 67961.8,
      "ema_15m": 67932.2,
      "ema_30m": 67995.9,
      "ema_1h": 68095.9,
      "ema_4h": 68666.9,
      "ema_1d": 69689.8,
      "ema_1w": 71404.6
    },
    {
      "symbol": "ETH",
      "close_price": 2051.63,
      "ema_1m": 2053.93,
      "ema_5m": 2053.7,
      "ema_15m": 2052.7,
      "ema_30m": 2054.45,
      "ema_1h": 2057.74,
      "ema_4h": 2081.84,
      "ema_1d": 2112.42,
      "ema_1w": 2188.84
    },
  ]
}
```

---
  
  
  ---
        
## API 7: Bollinger Bands (BOLL)


**Supported Plans, Intervals, and Historical Data Access**

Hobbyist:Not Available
Startup:Available
Standard:Available
Professional:Available


### Method: GET

**URL**:
```
https://open-api-v4.coinglass.com//api/futures/indicators/boll
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

| Parameter   | Type    | Required | Description                                                                                                    | Example value |
| ----------- | ------- | -------- | -------------------------------------------------------------------------------------------------------------- | ------------- |
| exchange    | string  | yes      | Futures exchange names (e.g., Binance, OKX) .Retrieve supported exchanges via the 'support-exchange-pair' API. | Binance       |
| symbol      | string  | yes      |  Trading pair (e.g., BTCUSDT). Retrieve supported pairs via the 'support-exchange-pair' API.                   | BTCUSDT       |
| interval    | string  | yes      | Time interval for data aggregation.  Supported values: 1m, 3m, 5m, 15m, 30m, 1h, 4h, 6h, 8h, 12h, 1d, 1w       | 1h            |
| limit       | string  | no       | Number of results per request.  Default: 1000, Maximum: 4500                                                   |               |
| start_time  | integer | no       | Start timestamp in milliseconds (e.g., 1641522717000).                                                         |               |
| end_time    | integer | no       | End timestamp in milliseconds (e.g., 1641522717000).                                                           |               |
| series_type | string  | no       | Price type used in calculation. Supported values: open, high, low, close. Default: close.                      |               |
| window      | integer | no       | Window size — defines the number of data points used for indicator calculation (e.g., 20 for BOLL).            |               |
| mult        | number  | no       | mult: Standard deviation multiplier that defines the width of the Bollinger Bands. Default is 2.               |               |


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/futures/indicators/boll?exchange=Binance&symbol=BTCUSDT&interval=1h' \
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
      "time": 1759287600000,
      "mb_value": 114209.633,
      "ub_value": 114626.49,
      "lb_value": 113792.776
    },
    {
      "time": 1759291200000,
      "mb_value": 114200.6,
      "ub_value": 114611.931,
      "lb_value": 113789.269
    },
}
```

---
  
  
  ---
        
## API 8: Moving Average Convergence Divergence (MACD)


**Supported Plans, Intervals, and Historical Data Access**

Hobbyist:Not Available
Startup:Available
Standard:Available
Professional:Available


### Method: GET

**URL**:
```
https://open-api-v4.coinglass.com//api/futures/indicators/macd
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

| Parameter     | Type    | Required | Description                                                                                                    | Example value |
| ------------- | ------- | -------- | -------------------------------------------------------------------------------------------------------------- | ------------- |
| exchange      | string  | yes      | Futures exchange names (e.g., Binance, OKX) .Retrieve supported exchanges via the 'support-exchange-pair' API. | Binance       |
| symbol        | string  | yes      |  Trading pair (e.g., BTCUSDT). Retrieve supported pairs via the 'support-exchange-pair' API.                   | BTCUSDT       |
| interval      | string  | yes      | Time interval for data aggregation.  Supported values: 1m, 3m, 5m, 15m, 30m, 1h, 4h, 6h, 8h, 12h, 1d, 1w       | 1h            |
| limit         | string  | no       | Number of results per request.  Default: 1000, Maximum: 4500                                                   |               |
| start_time    | integer | no       | Start timestamp in milliseconds (e.g., 1641522717000).                                                         |               |
| end_time      | integer | no       | End timestamp in milliseconds (e.g., 1641522717000).                                                           |               |
| series_type   | string  | no       | Price type used in calculation. Supported values: open, high, low, close. Default: close.                      |               |
| fast_window   | integer | no       | Fast period window size used for indicator calculation (e.g., 12 for MACD).                                    |               |
| slow_window   | integer | no       | Slow period window size used for indicator calculation (e.g., 26 for MACD).                                    |               |
| signal_window | integer | no       | Signal line window size used to smooth the fast–slow difference (e.g., 9 for MACD).                            |               |


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/futures/indicators/macd?exchange=Binance&symbol=BTCUSDT&interval=1h' \
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
      "time": 1759352400000,
      "macd_value": 1200.54
    },
    {
      "time": 1759356000000,
      "macd_value": 1175.91
    },
}
```

---
  
  
  ---
        
## API 9: Coin MACD List


**Supported Plans, Intervals, and Historical Data Access**

Hobbyist:Not Available
Startup:Not Available
Standard:Available
Professional:Available


### Method: GET

**URL**:
```
https://open-api-v4.coinglass.com//api/futures/macd/list
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

*No parameters required*


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/futures/macd/list' \
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
      "macd_1m": 81.80561,
      "macd_5m": 143.48905,
      "signal_5m": 91.452,
      "macd_15m": -16.18165,
      "signal_15m": -87.99726,
      "macd_30m": -95.87941,
      "signal_30m": -122.73658,
      "macd_1h": 88.56051,
      "signal_1h": 182.9783,
      "macd_4h": 977.82453,
      "signal_4h": 888.912,
      "macd_1d": 722.9137,
      "signal_1d": -219.23382,
      "macd_1w": -8949.2849,
      "signal_1w": -7934.24745
    },
    {
      "symbol": "ETH",
      "macd_1m": 1.13198,
      "macd_5m": 3.80416,
      "signal_5m": 4.17097,
      "macd_15m": 3.55342,
      "signal_15m": 1.73445,
      "macd_30m": 2.12428,
      "signal_30m": 0.70135,
      "macd_1h": 15.12386,
      "signal_1h": 19.77531,
      "macd_4h": 69.31752,
      "signal_4h": 57.72725,
      "macd_1d": 34.24028,
      "signal_1d": -15.63182,
      "macd_1w": -366.30054,
      "signal_1w": -302.1124
    },
}
```

---
  
  
  ---
        
## API 10: Futures Basis


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
https://open-api-v4.coinglass.com//api/futures/basis/history
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

| Parameter  | Type   | Required | Description                                                                                                      | Example value |
| ---------- | ------ | -------- | ---------------------------------------------------------------------------------------------------------------- | ------------- |
| exchange   | string | yes      | Futures exchange names (e.g., Binance, OKX) .Retrieve supported exchanges via the 'supported-exchange-pair' API. | Binance       |
| symbol     | string | yes      | Trading pair (e.g., BTCUSDT). Retrieve supported pairs via the 'supported-exchange-pair' API.                    | BTCUSDT       |
| interval   | string | yes      | Data aggregation time interval. Supported values: 1m, 3m, 5m, 15m, 30m, 1h, 4h, 6h, 8h, 12h, 1d, 1w.             | 1h            |
| limit      | string | no       | Number of results per request. Default: 1000, Maximum: 1000.                                                     | 10            |
| start_time | string | no       | Start timestamp in milliseconds (e.g., 1641522717000).                                                           |               |
| end_time   | string | no       | End timestamp in milliseconds (e.g., 1641522717000).                                                             |               |


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/futures/basis/history?exchange=Binance&symbol=BTCUSDT&interval=1h' \
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
      "time": 1741629600000,            // Timestamp (in milliseconds)
      "open_basis": 0.0504,             // Opening basis (%) - the basis at the start of the interval
      "close_basis": 0.0445,            // Closing basis (%) - the basis at the end of the interval
      "open_change": 39.5,              // Percentage change in basis at opening compared to previous period
      "close_change": 34.56             // Percentage change in basis at closing compared to previous period
    },
    {
      "time": 1741633200000,            // Timestamp (in milliseconds)
      "open_basis": 0.0446,             // Opening basis (%)
      "close_basis": 0.03,              // Closing basis (%)
      "open_change": 34.65,             // Opening basis change (%)
      "close_change": 23.74             // Closing basis change (%)
    }
  ]
}
```

---
  
  
  ---
        
## API 11: Whale Index


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
https://open-api-v4.coinglass.com//api/futures/whale-index/history
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

| Parameter  | Type    | Required | Description                                                                                                      | Example value |
| ---------- | ------- | -------- | ---------------------------------------------------------------------------------------------------------------- | ------------- |
| exchange   | string  | yes      | Futures exchange names (e.g., Binance, OKX) .Retrieve supported exchanges via the 'supported-exchange-pair' API. | Binance       |
| symbol     | string  | yes      | Trading pair (e.g., BTCUSDT). Retrieve supported pairs via the 'supported-exchange-pair' API.                    | BTCUSDT       |
| interval   | string  | yes      | Time interval for data aggregation. Supported values: 1m, 3m, 5m, 15m, 30m, 1h, 4h, 6h, 8h, 12h, 1d, 1w          | 1d            |
| limit      | integer | no       | Number of results per request. Default 1000, Max 1000                                                            | 1000          |
| start_time | integer | no       | Start timestamp in milliseconds (e.g., 1641522717000).                                                           |               |
| end_time   | integer | no       | End timestamp in milliseconds (e.g., 1641522717000).                                                             |               |


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/futures/whale-index/history?exchange=Binance&symbol=BTCUSDT&interval=1d' \
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
      "time": 1665532800000,
      "whale_index_value": -184.8
    },
    {
      "time": 1665619200000,
      "whale_index_value": -118.965
    },
    {
      "time": 1665705600000,
      "whale_index_value": -58.795
    },
    {
      "time": 1665792000000,
      "whale_index_value": -84.095
    },
}
```

---
  
  
  ---
        
## API 12: CGDI Index


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
https://open-api-v4.coinglass.com//api/futures/cgdi-index/history  
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

*No parameters required*


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/futures/cgdi-index/history  ' \
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
      "time": 1704067200000,
      "cgdi_index_value": 1000
    },
    {
      "time": 1704153600000,
      "cgdi_index_value": 1053.2551
    },
  ]
}
```

---
  
  
  ---
        
## API 13: CDRI Index


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
https://open-api-v4.coinglass.com//api/futures/cdri-index/history 
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

*No parameters required*


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/futures/cdri-index/history ' \
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
      "time": 1646438400000,
      "cdri_index_value": 50
    },
    {
      "time": 1646524800000,
      "cdri_index_value": 47
    },
  ]
}
```

---
  
  
  ---
        
## API 14: Pair Average True Range (ATR)


**Supported Plans, Intervals, and Historical Data Access**

Hobbyist:Not Available
Startup:Available
Standard:Available
Professional:Available


### Method: GET

**URL**:
```
https://open-api-v4.coinglass.com//api/futures/indicators/avg-true-range
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

| Parameter  | Type    | Required | Description                                                                                                    | Example value |
| ---------- | ------- | -------- | -------------------------------------------------------------------------------------------------------------- | ------------- |
| exchange   | string  | yes      | Futures exchange names (e.g., Binance, OKX) .Retrieve supported exchanges via the 'support-exchange-pair' API. | Binance       |
| symbol     | string  | yes      | Trading pair (e.g., BTCUSDT). Retrieve supported pairs via the 'support-exchange-pair' API.                    | BTCUSDT       |
| interval   | string  | yes      | Time interval for data aggregation. Supported values: 1m, 3m, 5m, 15m, 30m, 1h, 4h, 6h, 8h, 12h, 1d, 1w        | 1h            |
| limit      | integer | no       | Number of results per request. Default: 1000 Max:1000                                                          |               |
| start_time | integer | no       | Start timestamp in milliseconds (e.g., 1641522717000).                                                         |               |
| end_time   | integer | no       | End timestamp in milliseconds (e.g., 1641522717000).                                                           |               |
| window     | integer | no       | Window size — defines the number of data points used for indicator calculation (e.g., 14 for ATR).             |               |


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/futures/indicators/avg-true-range?exchange=Binance&symbol=BTCUSDT&interval=1h' \
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
      "time": 1765522800000,
      "avg_true_range_value": 830.736
    },
    {
      "time": 1765526400000,
      "avg_true_range_value": 799.548
    },
    {
      "time": 1765530000000,
      "avg_true_range_value": 775.838
    }
}
```

---
  
  
  ---
        
## API 15: Coin Average True Range (ATR) List


**Supported Plans, Intervals, and Historical Data Access**

Hobbyist:Not Available
Startup:Not Available
Standard:Available
Professional:Available


### Method: GET

**URL**:
```
https://open-api-v4.coinglass.com//api/futures/avg-true-range/list
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

*No parameters required*


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/futures/avg-true-range/list' \
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
      "avg_true_range_1m": 29.96118,
      "avg_true_range_5m": 81.93299,
      "avg_true_range_15m": 170.15648,
      "avg_true_range_30m": 279.27184,
      "avg_true_range_1h": 495.52303,
      "avg_true_range_4h": 1080.68816,
      "avg_true_range_1d": 2998.03821,
      "avg_true_range_1w": 9003.12081
    },
    {
      "symbol": "ETH",
      "avg_true_range_1m": 1.25441,
      "avg_true_range_5m": 3.40808,
      "avg_true_range_15m": 6.68785,
      "avg_true_range_30m": 11.25638,
      "avg_true_range_1h": 20.12117,
      "avg_true_range_4h": 44.65185,
      "avg_true_range_1d": 123.54839,
      "avg_true_range_1w": 436.83828
    },
  ]
}
```

---
  