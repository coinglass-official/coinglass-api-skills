---
name: funding-rate
description: Funding Rate request using the CoinGlass API. 
metadata:
  version: 1.0.0
  author: CoinGlass
  openclaw:
    requires:
      bins:
        - curl
        - openssl
    homepage: https://github.com/coinglass-official/coinglass-api-skills/tree/main/futures/funding-rate/API.md
license: MIT
---

# CoinGlass Funding Rate Skill

Funding Rate request on CoinGLass API endpoints. Return the result in JSON format.


## Quick Reference

| API                       | Endpoint                                            | Function                                                                                                                                          |
| ------------------------- | --------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------- |
| History (OHLC)            | /api/futures/funding-rate/history                   | This endpoint provides funding rate data in OHLC (open, high, low, close) candlestick format for futures trading pairs.                           |
| OI Weight History (OHLC)  | /api/futures/funding-rate/oi-weight-history         | This endpoint provides open interest-weighted funding rate data in OHLC (open, high, low, close) candlestick format for futures cryptocurrencies. |
| Vol Weight History (OHLC) | /api/futures/funding-rate/vol-weight-history        | This endpoint provides volume-weighted funding rate data in OHLC (open, high, low, close) candlestick format for futures cryptocurrencies.        |
| Exchange List             | /api/futures/funding-rate/exchange-list             | This endpoint provides funding rate data from exchanges.                                                                                          |
| Cumulative Exchange List  | /api/futures/funding-rate/accumulated-exchange-list | This endpoint provides cumulative funding rate data from exchanges.                                                                               |
| Arbitrage                 | /api/futures/funding-rate/arbitrage                 | This endpoint provides funding rate arbitrage data across exchanges for futures cryptocurrencies.                                                 |

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
        
## API 1: History (OHLC)


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
https://open-api-v4.coinglass.com//api/futures/funding-rate/history
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

| Parameter  | Type    | Required | Description                                                                                                      | Example value |
| ---------- | ------- | -------- | ---------------------------------------------------------------------------------------------------------------- | ------------- |
| exchange   | string  | yes      | Futures exchange names (e.g., Binance, OKX) .Retrieve supported exchanges via the 'supported-exchange-pair' API. | Binance       |
| symbol     | string  | yes      | Trading pair (e.g., BTCUSDT). Retrieve supported pairs via the 'supported-exchange-pair' API.                    | BTCUSDT       |
| interval   | string  | yes      | Time interval for data aggregation.  Supported values: 1m, 3m, 5m, 15m, 30m, 1h, 4h, 6h, 8h, 12h, 1d, 1w         | 1d            |
| limit      | integer | no       | Number of results per request.  Default: 1000, Maximum: 1000                                                     |               |
| start_time | integer | no       | Start timestamp in milliseconds (e.g., 1641522717000).                                                           |               |
| end_time   | integer | no       | End timestamp in milliseconds (e.g., 1641522717000).                                                             |               |


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/futures/funding-rate/history?exchange=Binance&symbol=BTCUSDT&interval=1d' \
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
      "time": 1658880000000, // Timestamp (milliseconds)
      "open": "0.004603",     // Opening funding rate
      "high": "0.009388",     // Highest funding rate
      "low": "-0.005063",     // Lowest funding rate
      "close": "0.009229"     // Closing funding rate
    },
    {
      "time": 1658966400000, // Timestamp (milliseconds)
      "open": "0.009229",     // Opening funding rate
      "high": "0.01",         // Highest funding rate
      "low": "0.007794",      // Lowest funding rate
      "close": "0.01"         // Closing funding rate
    }
  ]
}
```

---
  
  
  ---
        
## API 2: OI Weight History (OHLC)


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
https://open-api-v4.coinglass.com//api/futures/funding-rate/oi-weight-history
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

| Parameter  | Type    | Required | Description                                                                                             | Example value |
| ---------- | ------- | -------- | ------------------------------------------------------------------------------------------------------- | ------------- |
| symbol     | string  | yes      | Trading coin (e.g., BTC). Retrieve supported coins via the 'supported-coins' API.                       | BTC           |
| interval   | string  | yes      | Time interval for data aggregation. Supported values: 1m, 3m, 5m, 15m, 30m, 1h, 4h, 6h, 8h, 12h, 1d, 1w | 1d            |
| limit      | integer | no       | Number of results per request. Default: 1000, Maximum: 1000                                             |               |
| start_time | integer | no       | Start timestamp in seconds (e.g., 1641522717000).                                                       |               |
| end_time   | integer | no       | End timestamp in seconds (e.g., 1641522717000).                                                         |               |


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/futures/funding-rate/oi-weight-history?symbol=BTC&interval=1d' \
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
      "time": 1658880000000, // Timestamp (milliseconds)
      "open": "0.004603",     // Opening funding rate
      "high": "0.009388",     // Highest funding rate
      "low": "-0.005063",     // Lowest funding rate
      "close": "0.009229"     // Closing funding rate
    },
    {
      "time": 1658966400000, // Timestamp (milliseconds)
      "open": "0.009229",     // Opening funding rate
      "high": "0.01",         // Highest funding rate
      "low": "0.007794",      // Lowest funding rate
      "close": "0.01"         // Closing funding rate
    }
  ]
}
```

---
  
  
  ---
        
## API 3: Vol Weight History (OHLC)


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
https://open-api-v4.coinglass.com//api/futures/funding-rate/vol-weight-history
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

| Parameter  | Type    | Required | Description                                                                                             | Example value |
| ---------- | ------- | -------- | ------------------------------------------------------------------------------------------------------- | ------------- |
| symbol     | string  | yes      | Trading coin (e.g., BTC). Retrieve supported coins via the 'supported-coins' API.                       | BTC           |
| interval   | string  | yes      | Time interval for data aggregation. Supported values: 1m, 3m, 5m, 15m, 30m, 1h, 4h, 6h, 8h, 12h, 1d, 1w | 1d            |
| limit      | integer | no       | Number of results per request. Default: 1000, Maximum: 1000                                             |               |
| start_time | integer | no       | Start timestamp in milliseconds (e.g., 1641522717000).                                                  |               |
| end_time   | integer | no       | End timestamp in milliseconds (e.g., 1641522717000).                                                    |               |


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/futures/funding-rate/vol-weight-history?symbol=BTC&interval=1d' \
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
      "time": 1658880000000, // Timestamp (milliseconds)
      "open": "0.004603",     // Opening funding rate
      "high": "0.009388",     // Highest funding rate
      "low": "-0.005063",     // Lowest funding rate
      "close": "0.009229"     // Closing funding rate
    },
    {
      "time": 1658966400000, // Timestamp (milliseconds)
      "open": "0.009229",     // Opening funding rate
      "high": "0.01",         // Highest funding rate
      "low": "0.007794",      // Lowest funding rate
      "close": "0.01"         // Closing funding rate
    }
  ]
}
```

---
  
  
  ---
        
## API 4: Exchange List


**Supported Plans, Intervals, and Historical Data Access**

Hobbyist:Available
Startup:Available
Standard:Available
Professional:Available


### Method: GET

**URL**:
```
https://open-api-v4.coinglass.com//api/futures/funding-rate/exchange-list
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

*No parameters required*


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/futures/funding-rate/exchange-list' \
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
      "symbol": "BTC", // Symbol
      "stablecoin_margin_list": [ // USDT/USD margin mode
        {
          "exchange": "Binance", // Exchange
          "funding_rate_interval": 8, // Funding rate interval (hours)
          "funding_rate": 0.007343, // Current funding rate
          "next_funding_time": 1745222400000 // Next funding time (milliseconds)
        },
        {
          "exchange": "OKX", // Exchange
          "funding_rate_interval": 8, // Funding rate interval (hours)
          "funding_rate": 0.00736901950628, // Current funding rate
          "next_funding_time": 1745222400000 // Next funding time (milliseconds)
        }
      ],
      "token_margin_list": [ // Coin-margined mode
        {
          "exchange": "Binance", // Exchange
          "funding_rate_interval": 8, // Funding rate interval (hours)
          "funding_rate": -0.001829, // Current funding rate
          "next_funding_time": 1745222400000 // Next funding time (milliseconds)
        }
      ]
    }
  ]
}
```

---
  
  
  ---
        
## API 5: Cumulative Exchange List


**Supported Plans, Intervals, and Historical Data Access**

Hobbyist:Available
Startup:Available
Standard:Available
Professional:Available


### Method: GET

**URL**:
```
https://open-api-v4.coinglass.com//api/futures/funding-rate/accumulated-exchange-list
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

| Parameter | Type   | Required | Description                                       | Example value |
| --------- | ------ | -------- | ------------------------------------------------- | ------------- |
| range     | string | yes      | Time range for the data (e.g.,1d, 7d, 30d, 365d). | 1d            |


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/futures/funding-rate/accumulated-exchange-list?range=1d' \
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
      "symbol": "BTC", // Symbol
      "stablecoin_margin_list": [ // Accumulated funding rate for USDT/USD margin mode
        {
          "exchange": "BINANCE", // Exchange name
          "funding_rate": 0.001873 // Accumulated funding rate
        },
        {
          "exchange": "OKX", // Exchange name
          "funding_rate": 0.00775484 // Accumulated funding rate
        }
      ],

      "token_margin_list": [ // Accumulated funding rate for coin-margined mode
        {
          "exchange": "BINANCE", // Exchange name
          "funding_rate": -0.003149 // Accumulated funding rate
        }
      ]
    }
  ]
}
```

---
  
  
  ---
        
## API 6: Arbitrage


**Supported Plans, Intervals, and Historical Data Access**

Hobbyist:Not Available
Startup:Available
Standard:Available
Professional:Available


### Method: GET

**URL**:
```
https://open-api-v4.coinglass.com//api/futures/funding-rate/arbitrage
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

| Parameter     | Type    | Required | Description                                                               | Example value |
| ------------- | ------- | -------- | ------------------------------------------------------------------------- | ------------- |
| usd           | integer | yes      | Investment principal for arbitrage (e.g., 10000).                         | 10000         |
| exchange_list | string  | no       | List of exchange names to retrieve data from (e.g.,  'Binance,OKX,Bybit') |               |


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/futures/funding-rate/arbitrage?usd=10000' \
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
      "symbol": "SUPRA", // Token symbol
      "buy": { //  (lower funding rate)
        "exchange": "MEXC", // Exchange name
        "open_interest_usd": 848218.2833, // Open interest in USD on the exchange
        "funding_rate_interval": 4, // Funding rate interval (hours)
        "funding_rate": -0.994 // Current funding rate (%)
      },
      "sell": { //  (higher funding rate)
        "exchange": "Gate.io", // Exchange name
        "open_interest_usd": 448263.5072, // Open interest in USD on the exchange
        "funding_rate_interval": 4, // Funding rate interval (hours)
        "funding_rate": 0.005 // Current funding rate (%)
      },
      "apr": 2187.81, // Annual Percentage Rate (APR, %)
      "funding": 0.999, // Funding rate difference (between long and short)
      "fee": 0.03, // Total trading fee (both sides)
      "spread": -0.09, // Price spread between platforms (%)
      "next_funding_time": 1745222400000 // Next funding settlement time (timestamp in milliseconds)
    }
  ]
}
```

---
  