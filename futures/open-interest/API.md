---
name: open-interest
description: Open Interest request using the CoinGlass API. 
metadata:
  version: 1.0.0
  author: CoinGlass
  openclaw:
    requires:
      bins:
        - curl
        - openssl
    homepage: https://github.com/coinglass-official/coinglass-api-skills/tree/main/futures/open-interest/API.md
license: MIT
---

# CoinGlass Open Interest Skill

Open Interest request on CoinGLass API endpoints. Return the result in JSON format.


## Quick Reference

| API                                         | Endpoint                                                  | Function                                                                                                                           |
| ------------------------------------------- | --------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------- |
| History (OHLC)                              | /api/futures/open-interest/history                        | This endpoint provides open interest data in OHLC (open, high, low, close) candlestick format for futures trading pairs.           |
| Aggregated History (OHLC)                   | /api/futures/open-interest/aggregated-history             | This endpoint provides aggregated open interest data across exchanges in OHLC (open, high, low, close) candlestick format.         |
| Aggregated Stablecoin Margin History (OHLC) | /api/futures/open-interest/aggregated-stablecoin-history  | This endpoint provides aggregated stablecoin-margined open interest data in OHLC (open, high, low, close) candlestick format.      |
| Aggregated Coin Margin History (OHLC)       | /api/futures/open-interest/aggregated-coin-margin-history | This endpoint provides aggregated coin-margined open interest data in OHLC (open, high, low, close) candlestick format.            |
| Exchange List                               | /api/futures/open-interest/exchange-list                  | This endpoint provides open interest data for a specific coin across multiple exchanges.                                           |
| Exchange History Chart                      | /api/futures/open-interest/exchange-history-chart         | This endpoint retrieves historical open interest data for a specific cryptocurrency across exchanges, formatted for chart display. |

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
https://open-api-v4.coinglass.com//api/futures/open-interest/history
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

| Parameter  | Type    | Required | Description                                                                                                       | Example value |
| ---------- | ------- | -------- | ----------------------------------------------------------------------------------------------------------------- | ------------- |
| exchange   | string  | yes      |  Futures exchange names (e.g., Binance, OKX) .Retrieve supported exchanges via the 'supported-exchange-pair' API. | Binance       |
| symbol     | string  | yes      | Trading pair (e.g., BTCUSDT).  Retrieve supported pairs via the 'supported-exchange-pair' API.                    | BTCUSDT       |
| interval   | string  | yes      | Time interval for data aggregation.  Supported values: 1m, 3m, 5m, 15m, 30m, 1h, 4h, 6h, 8h, 12h, 1d, 1w          | 1d            |
| limit      | integer | no       | Number of results per request.  Default 1000, Max 1000                                                            | 10            |
| start_time | integer | no       | Start timestamp in milliseconds (e.g., 1641522717000).                                                            |               |
| end_time   | integer | no       | End timestamp in milliseconds (e.g., 1641522717000).                                                              |               |
| unit       | string  | no       | Unit for the returned data, choose between 'usd' or 'coin'.                                                       | usd           |


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/futures/open-interest/history?exchange=Binance&symbol=BTCUSDT&interval=1d' \
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
      "time": 2644845344000, // Timestamp (ms)
      "open": "2644845344",   // Open interest at interval start
      "high": "2692643311",   // Highest open interest during interval
      "low": "2576975597",    // Lowest open interest during interval
      "close": "2608846475"   // Open interest at interval end
    },
    {
      "time": 2608846475000, // Timestamp (ms)
      "open": "2608846475",  // Open interest at interval start
      "high": "2620807645",  // Highest open interest during interval
      "low": "2327236202",   // Lowest open interest during interval
      "close": "2340177420"  // Open interest at interval end
    },
    ....
  ]
}
```

---
  
  
  ---
        
## API 2: Aggregated History (OHLC)


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
https://open-api-v4.coinglass.com//api/futures/open-interest/aggregated-history
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

| Parameter  | Type    | Required | Description                                                                                              | Example value |
| ---------- | ------- | -------- | -------------------------------------------------------------------------------------------------------- | ------------- |
| symbol     | string  | yes      | Trading coin (e.g., BTC).  Retrieve supported coins via the 'supported-coins' API.                       | BTC           |
| interval   | string  | yes      | Time interval for data aggregation.  Supported values: 1m, 3m, 5m, 15m, 30m, 1h, 4h, 6h, 8h, 12h, 1d, 1w | 1d            |
| limit      | integer | no       | Number of results per request.  Default: 1000, Maximum: 1000                                             |               |
| start_time | integer | no       | Start timestamp in milliseconds (e.g., 1641522717000).                                                   |               |
| end_time   | integer | no       | End timestamp in milliseconds (e.g., 1641522717000).                                                     |               |
| unit       | string  | no       | Unit for the returned data, choose between 'usd' or 'coin'.                                              | usd           |


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/futures/open-interest/aggregated-history?symbol=BTC&interval=1d' \
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
      "time": 2644845344000, // Timestamp (ms)
      "open": "2644845344",   // Open interest at interval start
      "high": "2692643311",   // Highest open interest during interval
      "low": "2576975597",    // Lowest open interest during interval
      "close": "2608846475"   // Open interest at interval end
    },
    {
      "time": 2608846475000, // Timestamp (ms)
      "open": "2608846475",  // Open interest at interval start
      "high": "2620807645",  // Highest open interest during interval
      "low": "2327236202",   // Lowest open interest during interval
      "close": "2340177420"  // Open interest at interval end
    },
    ....
  ]
}
```

---
  
  
  ---
        
## API 3: Aggregated Stablecoin Margin History (OHLC)


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
https://open-api-v4.coinglass.com//api/futures/open-interest/aggregated-stablecoin-history
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

| Parameter     | Type    | Required | Description                                                                                                                     | Example value |
| ------------- | ------- | -------- | ------------------------------------------------------------------------------------------------------------------------------- | ------------- |
| exchange_list | string  | yes      | Comma-separated exchange names (e.g., "Binance,OKX,Bybit"). Retrieve supported exchanges via the 'supported-exchange-pair' API. | Binance       |
| symbol        | string  | yes      | Trading coin (e.g., BTC).Retrieve supported coins via the 'supported-coins' API.                                                | BTC           |
| interval      | string  | yes      | Time interval for data aggregation.Supported values: 1m, 3m, 5m, 15m, 30m, 1h, 4h, 6h, 8h, 12h, 1d, 1w                          | 1d            |
| limit         | integer | no       | Number of results per request. Default: 1000, Maximum: 1000                                                                     |               |
| start_time    | integer | no       | Start timestamp in milliseconds (e.g., 1641522717000).                                                                          |               |
| end_time      | integer | no       | End timestamp in milliseconds (e.g., 1641522717000).                                                                            |               |


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/futures/open-interest/aggregated-stablecoin-history?exchange_list=Binance&symbol=BTC&interval=1d' \
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
      "time": 2644845344000, // Timestamp (ms)
      "open": "2644845344",   // Open interest at interval start
      "high": "2692643311",   // Highest open interest during interval
      "low": "2576975597",    // Lowest open interest during interval
      "close": "2608846475"   // Open interest at interval end
    },
    {
      "time": 2608846475000, // Timestamp (ms)
      "open": "2608846475",  // Open interest at interval start
      "high": "2620807645",  // Highest open interest during interval
      "low": "2327236202",   // Lowest open interest during interval
      "close": "2340177420"  // Open interest at interval end
    },
    ....
  ]
}
```

---
  
  
  ---
        
## API 4: Aggregated Coin Margin History (OHLC)


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
https://open-api-v4.coinglass.com//api/futures/open-interest/aggregated-coin-margin-history
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

| Parameter     | Type    | Required | Description                                                                                                                     | Example value |
| ------------- | ------- | -------- | ------------------------------------------------------------------------------------------------------------------------------- | ------------- |
| exchange_list | string  | yes      | Comma-separated exchange names (e.g., "Binance,OKX,Bybit"). Retrieve supported exchanges via the 'supported-exchange-pair' API. | Binance       |
| symbol        | string  | yes      | Trading coin (e.g., BTC).Retrieve supported coins via the 'supported-coins' API.                                                | BTC           |
| interval      | string  | yes      | Time interval for data aggregation.Supported values: 1m, 3m, 5m, 15m, 30m, 1h, 4h, 6h, 8h, 12h, 1d, 1w                          | 1d            |
| limit         | integer | no       | Number of results per request.  Default: 1000, Maximum: 1000                                                                    |               |
| start_time    | integer | no       | Start timestamp in milliseconds (e.g., 1641522717000).                                                                          |               |
| end_time      | integer | no       | End timestamp in milliseconds (e.g., 1641522717000).                                                                            |               |


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/futures/open-interest/aggregated-coin-margin-history?exchange_list=Binance&symbol=BTC&interval=1d' \
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
      "time": 2644845344000, // Timestamp (ms)
      "open": "2644845344",   // Open interest at interval start
      "high": "2692643311",   // Highest open interest during interval
      "low": "2576975597",    // Lowest open interest during interval
      "close": "2608846475"   // Open interest at interval end
    },
    {
      "time": 2608846475000, // Timestamp (ms)
      "open": "2608846475",  // Open interest at interval start
      "high": "2620807645",  // Highest open interest during interval
      "low": "2327236202",   // Lowest open interest during interval
      "close": "2340177420"  // Open interest at interval end
    },
    ....
  ]
}
```

---
  
  
  ---
        
## API 5: Exchange List


**Supported Plans, Intervals, and Historical Data Access**

Hobbyist:Available
Startup:Available
Standard:Available
Professional:Available


### Method: GET

**URL**:
```
https://open-api-v4.coinglass.com//api/futures/open-interest/exchange-list
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

| Parameter | Type   | Required | Description                                                                      | Example value |
| --------- | ------ | -------- | -------------------------------------------------------------------------------- | ------------- |
| symbol    | string | yes      | Trading coin (e.g., BTC).Retrieve supported coins via the 'supported-coins' API. | BTC           |


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/futures/open-interest/exchange-list?symbol=BTC' \
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
      "exchange": "All", // Exchange name; "All" means aggregated across all exchanges
      "symbol": "BTC", // Token symbol

      "open_interest_usd": 57437891724.5572, // Total open interest value in USD
      "open_interest_quantity": 659557.3064, // Total open interest quantity

      "open_interest_by_stable_coin_margin": 48920274435.15, // Open interest value in USD for stablecoin-margined futures
      "open_interest_quantity_by_coin_margin": 97551.2547, // Open interest quantity for coin-margined futures
      "open_interest_quantity_by_stable_coin_margin": 562006.0517, // Open interest quantity for stablecoin-margined futures

      "open_interest_change_percent_5m": 0.34, // Open interest change (%) in the last 5 minutes
      "open_interest_change_percent_15m": 0.59, // Open interest change (%) in the last 15 minutes
      "open_interest_change_percent_30m": 1.42, // Open interest change (%) in the last 30 minutes
      "open_interest_change_percent_1h": 2.27, // Open interest change (%) in the last 1 hour
      "open_interest_change_percent_4h": 2.95, // Open interest change (%) in the last 4 hours
      "open_interest_change_percent_24h": 0.9 // Open interest change (%) in the last 24 hours
    },
    {
      "exchange": "CME", // Exchange name
      "symbol": "BTC", // Token symbol

      "open_interest_usd": 12294999402.5, // Total open interest value in USD
      "open_interest_quantity": 141275.5, // Total open interest quantity

      "open_interest_by_stable_coin_margin": 12294999402.5, // Open interest value in USD for stablecoin-margined futures
      "open_interest_quantity_by_coin_margin": 0, // Open interest quantity for coin-margined futures
      "open_interest_quantity_by_stable_coin_margin": 141275.5, // Open interest quantity for stablecoin-margined futures

      "open_interest_change_percent_5m": 0.08, // Open interest change (%) in the last 5 minutes
      "open_interest_change_percent_15m": 0.14, // Open interest change (%) in the last 15 minutes
      "open_interest_change_percent_30m": 0.49, // Open interest change (%) in the last 30 minutes
      "open_interest_change_percent_1h": 1.13, // Open interest change (%) in the last 1 hour
      "open_interest_change_percent_4h": 2.4, // Open interest change (%) in the last 4 hours
      "open_interest_change_percent_24h": 2.08 // Open interest change (%) in the last 24 hours
    }
    ....
  ]
}
```

---
  
  
  ---
        
## API 6: Exchange History Chart


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
https://open-api-v4.coinglass.com//api/futures/open-interest/exchange-history-chart
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

| Parameter | Type   | Required | Description                                                                         | Example value |
| --------- | ------ | -------- | ----------------------------------------------------------------------------------- | ------------- |
| symbol    | string | yes      | Trading coin (e.g., BTC).  Check supported coins through the 'supported-coins' API. | BTC           |
| range     | string | yes      | Time range for the data (e.g., all, 1m, 15m, 1h, 4h, 12h).                          | 12h           |
| unit      | string | no       | Unit for the returned data, choose between 'usd' or 'coin'.                         | usd           |


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/futures/open-interest/exchange-history-chart?symbol=BTC&range=12h' \
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
    "time_list": [1721649600000, ...], // List of timestamps (in milliseconds)
    "price_list": [67490.3, ...], // List of prices corresponding to each timestamp

    "data_map": { // Open interest data of futures from each exchange
      "Binance": [8018229234, ...], // Binance open interest (corresponds to time_list)
      "Bitmex": [395160842, ...] // BitMEX open interest (corresponds to time_list)
      // ...
    }
  }
}
```

---
  