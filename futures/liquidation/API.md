---
name: liquidation
description: Liquidation request using the CoinGlass API. 
metadata:
  version: 1.0.0
  author: CoinGlass
  openclaw:
    requires:
      bins:
        - curl
        - openssl
    homepage: https://github.com/coinglass-official/coinglass-api-skills/tree/main/futures/liquidation/API.md
license: MIT
---

# CoinGlass Liquidation Skill

Liquidation request on CoinGLass API endpoints. Return the result in JSON format.


## Quick Reference

| API                             | Endpoint                                           | Function                                                                                                                                                        |
| ------------------------------- | -------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Pair Liquidation History        | /api/futures/liquidation/history                   | This endpoint provides historical data for long and short liquidations of a trading pair on the exchange.                                                       |
| Coin Liquidation History        | /api/futures/liquidation/aggregated-history        | This endpoint provides aggregated historical data for both long and short liquidations of a coin across multiple exchanges.                                     |
| Liquidation Coin List           | /api/futures/liquidation/coin-list                 | This endpoint provides liquidation data for all coins on a specific exchange.                                                                                   |
| Liquidation Exchange List       | /api/futures/liquidation/exchange-list             | This endpoint provides liquidation data for a specific coin across all exchanges.                                                                               |
| Liquidation Order               | /api/futures/liquidation/order                     | This endpoint provides liquidation order data from the past 7 days, including exchange, trading pair, and liquidation amount details.                           |
| Pair Liquidation Heatmap Model1 | /api/futures/liquidation/heatmap/model1            | This endpoint provides liquidation levels on a heatmap chart for trading pairs, calculated based on market data and liquidation leverage levels.                |
| Pair Liquidation Heatmap Model2 | /api/futures/liquidation/heatmap/model2            | This endpoint provides liquidation levels on a heatmap chart for trading pairs, calculated based on market data and liquidation leverage levels.                |
| Pair Liquidation Heatmap Model3 | /api/futures/liquidation/heatmap/model3            | This endpoint provides liquidation levels on a heatmap chart for trading pairs, calculated based on market data and liquidation leverage levels.                |
| Coin Liquidation Heatmap Model1 | /api/futures/liquidation/aggregated-heatmap/model1 | This endpoint provides aggregated liquidation levels on a heatmap chart, calculated based on market data and liquidation leverage levels.                       |
| Coin Liquidation Heatmap Model2 | /api/futures/liquidation/aggregated-heatmap/model2 | This endpoint provides aggregated liquidation levels on a heatmap chart, calculated based on market data and liquidation leverage levels.                       |
| Coin Liquidation Heatmap Model3 | /api/futures/liquidation/aggregated-heatmap/model3 | This endpoint provides aggregated liquidation levels on a heatmap chart, calculated based on market data and liquidation leverage levels.                       |
| Pair Liquidation Map            | /api/futures/liquidation/map                       | This endpoint provides a mapped visualization of liquidation events for trading pairs, calculated based on market data and liquidation leverage levels.         |
| Coin Liquidation Map            | /api/futures/liquidation/aggregated-map            | This endpoint provides a mapped visualization of aggregated liquidation events for coins, calculated based on market data and liquidation leverage levels.      |
| Liquidation Max Pain            | /api/futures/liquidation/max-pain                  | This endpoint provides key liquidation “max-pain” price for major cryptocurrencies, indicating potential pressure zones between current and liquidation prices. |

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
        
## API 1: Pair Liquidation History


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
https://open-api-v4.coinglass.com//api/futures/liquidation/history
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
curl 'https://open-api-v4.coinglass.com/api/futures/liquidation/history?exchange=Binance&symbol=BTCUSDT&interval=1d' \
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
      "long_liquidation_usd": "2369935.19562", // Long position liquidation amount (USD)
      "short_liquidation_usd": "6947459.43674" // Short position liquidation amount (USD)
    },
    {
      "time": 1658966400000, // Timestamp (milliseconds)
      "long_liquidation_usd": "5118407.85124", // Long position liquidation amount (USD)
      "short_liquidation_usd": "8517330.44192" // Short position liquidation amount (USD)
    }
  ]
}
```

---
  
  
  ---
        
## API 2: Coin Liquidation History


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
https://open-api-v4.coinglass.com//api/futures/liquidation/aggregated-history
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

| Parameter     | Type    | Required | Description                                                                                              | Example value |
| ------------- | ------- | -------- | -------------------------------------------------------------------------------------------------------- | ------------- |
| exchange_list | string  | yes      | List of exchange names to retrieve data from (e.g.,  'Binance, OKX, Bybit')                              | Binance       |
| symbol        | string  | yes      | Trading coin (e.g., BTC). Retrieve supported coins via the 'supported-coins' API.                        | BTC           |
| interval      | string  | yes      | Time interval for data aggregation. Supported values: 1m, 3m, 5m, 15m, 30m, 1h, 4h, 6h, 8h, 12h, 1d, 1w. | 1d            |
| limit         | integer | no       | Number of results per request. Default: 1000, Maximum: 1000.                                             |               |
| start_time    | integer | no       | Start timestamp in milliseconds (e.g., 1641522717000).                                                   |               |
| end_time      | integer | no       | End timestamp in milliseconds (e.g., 1641522717000).                                                     |               |


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/futures/liquidation/aggregated-history?exchange_list=Binance&symbol=BTC&interval=1d' \
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
      "time": 1658966400000, // Timestamp (milliseconds) 
      "aggregated_long_liquidation_usd": 5916885.14234,//aggregated Long position liquidation amount (USD)
      "aggregated_short_liquidation_usd": 12969583.87632 //aggregated Short position liquidation amount (USD)
    },
    {
      "time": 1659052800000,  // Timestamp (milliseconds)
      "aggregated_long_liquidation_usd": 5345708.23191, //aggregated Long position liquidation amount (USD)
      "aggregated_short_liquidation_usd": 6454875.54909 //aggregated Short position liquidation amount (USD)
    },
  ]
}
```

---
  
  
  ---
        
## API 3: Liquidation Coin List


**Supported Plans, Intervals, and Historical Data Access**

Hobbyist:Not Available
Startup:Available
Standard:Available
Professional:Available


### Method: GET

**URL**:
```
https://open-api-v4.coinglass.com//api/futures/liquidation/coin-list
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

| Parameter | Type   | Required | Description                                                                                                      | Example value |
| --------- | ------ | -------- | ---------------------------------------------------------------------------------------------------------------- | ------------- |
| exchange  | string | yes      | Futures exchange names (e.g., Binance, OKX) .Retrieve supported exchanges via the 'supported-exchange-pair' API. | Binance       |


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/futures/liquidation/coin-list?exchange=Binance' \
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
      "symbol": "BTC", // Token symbol
      "liquidation_usd_24h": 82280481.50425325, // Total liquidation amount in the past 24 hours (USD)
      "long_liquidation_usd_24h": 68437447.33734027, // Long position liquidation in the past 24 hours (USD)
      "short_liquidation_usd_24h": 13843034.16691298, // Short position liquidation in the past 24 hours (USD)

      "liquidation_usd_12h": 68331844.36224127, // Total liquidation in the past 12 hours
      "long_liquidation_usd_12h": 66614158.47451427, // Long liquidation (12h)
      "short_liquidation_usd_12h": 1717685.887727, // Short liquidation (12h)

      "liquidation_usd_4h": 11381137.080643, // Total liquidation in the past 4 hours
      "long_liquidation_usd_4h": 10921633.272973, // Long liquidation (4h)
      "short_liquidation_usd_4h": 459503.80767, // Short liquidation (4h)

      "liquidation_usd_1h": 3283635.95309, // Total liquidation in the past 1 hour
      "long_liquidation_usd_1h": 3182915.16289, // Long liquidation (1h)
      "short_liquidation_usd_1h": 100720.7902 // Short liquidation (1h)
    }
  ]
}
```

---
  
  
  ---
        
## API 4: Liquidation Exchange List


**Supported Plans, Intervals, and Historical Data Access**

Hobbyist:Available
Startup:Available
Standard:Available
Professional:Available


### Method: GET

**URL**:
```
https://open-api-v4.coinglass.com//api/futures/liquidation/exchange-list
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

| Parameter | Type   | Required | Description                                                                                                                                                 | Example value |
| --------- | ------ | -------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------- |
| symbol    | string | no       | Trading coin (e.g., BTC).  Retrieve supported coins via the 'supported-coins' API. When symbol = '', return total liquidations across all cryptocurrencies. | BTC           |
| range     | string | yes      | Time range for data aggregation.  Supported values: 1h, 4h, 12h, 24h.                                                                                       | 1h            |


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/futures/liquidation/exchange-list?range=1h' \
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
      "exchange": "All", // Total data from all exchanges
      "liquidation_usd": 14673519.81739075, // Total liquidation amount (USD)
      "long_liquidation_usd": 451394.17404598, // Long position liquidation amount (USD)
      "short_liquidation_usd": 14222125.64334477 // Short position liquidation amount (USD)
    },
    {
      "exchange": "Bybit", // Exchange name
      "liquidation_usd": 4585290.13404, // Total liquidation amount (USD)
      "long_liquidation_usd": 104560.13885, // Long position liquidation (USD)
      "short_liquidation_usd": 4480729.99519 // Short position liquidation (USD)
    }
  ]
}
```

---
  
  
  ---
        
## API 5: Liquidation Order


**Supported Plans, Intervals, and Historical Data Access**

Hobbyist:Not Available
Startup:Not Available
Standard:Available
Professional:Available


### Method: GET

**URL**:
```
https://open-api-v4.coinglass.com//api/futures/liquidation/order
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

| Parameter              | Type    | Required | Description                                                                                             | Example value |
| ---------------------- | ------- | -------- | ------------------------------------------------------------------------------------------------------- | ------------- |
| exchange               | string  | yes      | Exchange name (e.g., Binance, OKX). Retrieve supported exchanges via the 'supported-exchange-pair' API. | Binance       |
| symbol                 | string  | yes      | Trading coin (e.g., BTC). Retrieve supported coins via the 'supported-coins' API.                       | BTC           |
| min_liquidation_amount | string  | yes      | Minimum threshold for liquidation events.  Max 200 records per request.                                 | 10000         |
| start_time             | integer | no       | Start timestamp in milliseconds (e.g., 1641522717000).                                                  |               |
| end_time               | integer | no       | End timestamp in milliseconds (e.g., 1641522717000).                                                    |               |


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/futures/liquidation/order?exchange=Binance&symbol=BTC&min_liquidation_amount=10000' \
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
      "exchange_name": "BINANCE", // Exchange name
      "symbol": "BTCUSDT", // Trading pair symbol
      "base_asset": "BTC", // Base asset
      "price": 87535.9, // Liquidation price
      "usd_value": 205534.2932, // Transaction amount (USD)
      "side": 2, // Order direction (1: Buy, 2: Sell)
      "time": 1745216319263 // Timestamp
    },
    {
      "exchange_name": "BINANCE", // Exchange name
      "symbol": "BTCUSDT", // Trading pair symbol
      "base_asset": "BTC", // Base asset
      "price": 87465.2, // Liquidation price
      "usd_value": 15918.6664, // Transaction amount (USD)
      "side": 2, // Order direction (1: Buy, 2: Sell)
      "time": 1745215647165 // Timestamp
    }
  ]
}
```

---
  
  
  ---
        
## API 6: Pair Liquidation Heatmap Model1


**Supported Plans, Intervals, and Historical Data Access**

Hobbyist:Not Available
Startup:Not Available
Standard:Not Available
Professional:Available


### Method: GET

**URL**:
```
https://open-api-v4.coinglass.com//api/futures/liquidation/heatmap/model1
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

| Parameter | Type   | Required | Description                                                                                             | Example value |
| --------- | ------ | -------- | ------------------------------------------------------------------------------------------------------- | ------------- |
| exchange  | string | yes      | Exchange name (e.g., Binance, OKX). Retrieve supported exchanges via the 'supported-exchange-pair' API. | Binance       |
| symbol    | string | yes      | Trading pair (e.g., BTCUSDT). Retrieve supported pairs via the 'supported-exchange-pair' API.           | BTCUSDT       |
| range     | string | yes      | Time range for data aggregation. Supported values: 12h, 24h, 3d, 7d, 30d, 90d, 180d, 1y.                | 3d            |


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/futures/liquidation/heatmap/model1?exchange=Binance&symbol=BTCUSDT&range=3d' \
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
    "y_axis": [47968.54, 48000.00, 48031.46], // Y-axis price levels
    "liquidation_leverage_data": [
      [5, 124, 2288867.26], // Each array: [X-axis index, Y-axis index, liquidation leverage ]
      [6, 123, 318624.82],
      [7, 122, 1527940.12]
    ],
    "price_candlesticks": [
      [
        1722676500, // Timestamp (seconds)
        "61486",    // Open price
        "61596.4",  // High price
        "61434.4",  // Low price
        "61539.9",  // Close price
        "63753192.1129" // Trading volume (USD)
      ],
      [
        1722676800,
        "61539.9",
        "61610.0",
        "61480.0",
        "61590.5",
        "42311820.8720"
      ]
    ]
  }
}
```

---
  
  
  ---
        
## API 7: Pair Liquidation Heatmap Model2


**Supported Plans, Intervals, and Historical Data Access**

Hobbyist:Not Available
Startup:Not Available
Standard:Not Available
Professional:Available


### Method: GET

**URL**:
```
https://open-api-v4.coinglass.com//api/futures/liquidation/heatmap/model2
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

| Parameter | Type   | Required | Description                                                                                             | Example value |
| --------- | ------ | -------- | ------------------------------------------------------------------------------------------------------- | ------------- |
| exchange  | string | yes      | Exchange name  eg. Binance ，OKX （ Check supported exchanges through the 'supported-exchange-pair' API.） | Binance       |
| symbol    | string | yes      | Trading pair eg. BTCUSDT   （ Check supported pair through the 'supported-exchange-pair' API.）           | BTCUSDT       |
| range     | string | yes      | 12h, 24h, 3d, 7d, 30d, 90d, 180d, 1y                                                                    | 3d            |


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/futures/liquidation/heatmap/model2?exchange=Binance&symbol=BTCUSDT&range=3d' \
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
    "y_axis": [47968.54, 48000.00, 48031.46], // Y-axis price levels
    "liquidation_leverage_data": [
      [5, 124, 2288867.26], // Each array: [X-axis index, Y-axis index, liquidation leverage]
      [6, 123, 318624.82],
      [7, 122, 1527940.12]
    ],
    "price_candlesticks": [
      [
        1722676500, // Timestamp (seconds)
        "61486",    // Open price
        "61596.4",  // High price
        "61434.4",  // Low price
        "61539.9",  // Close price
        "63753192.1129" // Trading volume (USD)
      ],
      [
        1722676800,
        "61539.9",
        "61610.0",
        "61480.0",
        "61590.5",
        "42311820.8720"
      ]
    ]
  }
}
```

---
  
  
  ---
        
## API 8: Pair Liquidation Heatmap Model3


**Supported Plans, Intervals, and Historical Data Access**

Hobbyist:Not Available
Startup:Not Available
Standard:Not Available
Professional:Available


### Method: GET

**URL**:
```
https://open-api-v4.coinglass.com//api/futures/liquidation/heatmap/model3
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

| Parameter | Type   | Required | Description                                                                                             | Example value |
| --------- | ------ | -------- | ------------------------------------------------------------------------------------------------------- | ------------- |
| exchange  | string | yes      | Exchange name (e.g., Binance, OKX). Retrieve supported exchanges via the 'supported-exchange-pair' API. | Binance       |
| symbol    | string | yes      | Trading pair (e.g., BTCUSDT). Retrieve supported pairs via the 'supported-exchange-pair' API.           | BTCUSDT       |
| range     | string | yes      | Time range for data aggregation. Supported values: 12h, 24h, 3d, 7d, 30d, 90d, 180d, 1y.                | 3d            |


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/futures/liquidation/heatmap/model3?exchange=Binance&symbol=BTCUSDT&range=3d' \
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
    "y_axis": [47968.54, 48000.00, 48031.46], // Y-axis price levels
    "liquidation_leverage_data": [
      [5, 124, 2288867.26], // Each array: [X-axis index, Y-axis index, liquidation leverage]
      [6, 123, 318624.82],
      [7, 122, 1527940.12]
    ],
    "price_candlesticks": [
      [
        1722676500, // Timestamp (seconds)
        "61486",    // Open price
        "61596.4",  // High price
        "61434.4",  // Low price
        "61539.9",  // Close price
        "63753192.1129" // Trading volume (USD)
      ],
      [
        1722676800,
        "61539.9",
        "61610.0",
        "61480.0",
        "61590.5",
        "42311820.8720"
      ]
    ]
  }
}
```

---
  
  
  ---
        
## API 9: Coin Liquidation Heatmap Model1


**Supported Plans, Intervals, and Historical Data Access**

Hobbyist:Not Available
Startup:Not Available
Standard:Not Available
Professional:Available


### Method: GET

**URL**:
```
https://open-api-v4.coinglass.com//api/futures/liquidation/aggregated-heatmap/model1
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

| Parameter | Type   | Required | Description                                                                              | Example value |
| --------- | ------ | -------- | ---------------------------------------------------------------------------------------- | ------------- |
| symbol    | string | yes      | Trading coin (e.g., BTC). Retrieve supported coins via the 'supported-coins' API.        | BTC           |
| range     | string | yes      | Time range for data aggregation. Supported values: 12h, 24h, 3d, 7d, 30d, 90d, 180d, 1y. | 3d            |


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/futures/liquidation/aggregated-heatmap/model1?symbol=BTC&range=3d' \
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
    "y_axis": [47968.54, 48000.00, 48031.46], // Y-axis price levels
    "liquidation_leverage_data": [
      [5, 124, 2288867.26], // Each array: [X-axis index, Y-axis index, liquidation leverage]
      [6, 123, 318624.82],
      [7, 122, 1527940.12]
    ],
    "price_candlesticks": [
      [
        1722676500, // Timestamp (seconds)
        "61486",    // Open price
        "61596.4",  // High price
        "61434.4",  // Low price
        "61539.9",  // Close price
        "63753192.1129" // Trading volume (USD)
      ],
      [
        1722676800,
        "61539.9",
        "61610.0",
        "61480.0",
        "61590.5",
        "42311820.8720"
      ]
    ]
  }
}
```

---
  
  
  ---
        
## API 10: Coin Liquidation Heatmap Model2


**Supported Plans, Intervals, and Historical Data Access**

Hobbyist:Not Available
Startup:Not Available
Standard:Not Available
Professional:Available


### Method: GET

**URL**:
```
https://open-api-v4.coinglass.com//api/futures/liquidation/aggregated-heatmap/model2
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

| Parameter | Type   | Required | Description                                                                              | Example value |
| --------- | ------ | -------- | ---------------------------------------------------------------------------------------- | ------------- |
| symbol    | string | yes      | Trading coin (e.g., BTC). Retrieve supported coins via the 'supported-coins' API.        | BTC           |
| range     | string | yes      | Time range for data aggregation. Supported values: 12h, 24h, 3d, 7d, 30d, 90d, 180d, 1y. | 3d            |


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/futures/liquidation/aggregated-heatmap/model2?symbol=BTC&range=3d' \
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
    "y_axis": [47968.54, 48000.00, 48031.46], // Y-axis price levels
    "liquidation_leverage_data": [
      [5, 124, 2288867.26], // Each array: [X-axis index, Y-axis index, liquidation leverage]
      [6, 123, 318624.82],
      [7, 122, 1527940.12]
    ],
    "price_candlesticks": [
      [
        1722676500, // Timestamp (seconds)
        "61486",    // Open price
        "61596.4",  // High price
        "61434.4",  // Low price
        "61539.9",  // Close price
        "63753192.1129" // Trading volume (USD)
      ],
      [
        1722676800,
        "61539.9",
        "61610.0",
        "61480.0",
        "61590.5",
        "42311820.8720"
      ]
    ]
  }
}
```

---
  
  
  ---
        
## API 11: Coin Liquidation Heatmap Model3


**Supported Plans, Intervals, and Historical Data Access**

Hobbyist:Not Available
Startup:Not Available
Standard:Not Available
Professional:Available


### Method: GET

**URL**:
```
https://open-api-v4.coinglass.com//api/futures/liquidation/aggregated-heatmap/model3
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

| Parameter | Type   | Required | Description                                                                              | Example value |
| --------- | ------ | -------- | ---------------------------------------------------------------------------------------- | ------------- |
| symbol    | string | yes      | Trading coin (e.g., BTC). Retrieve supported coins via the 'supported-coins' API.        | BTC           |
| range     | string | yes      | Time range for data aggregation. Supported values: 12h, 24h, 3d, 7d, 30d, 90d, 180d, 1y. | 3d            |


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/futures/liquidation/aggregated-heatmap/model3?symbol=BTC&range=3d' \
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
    "y_axis": [47968.54, 48000.00, 48031.46], // Y-axis price levels
    "liquidation_leverage_data": [
      [5, 124, 2288867.26], // Each array: [X-axis index, Y-axis index, liquidation leverage]
      [6, 123, 318624.82],
      [7, 122, 1527940.12]
    ],
    "price_candlesticks": [
      [
        1722676500, // Timestamp (seconds)
        "61486",    // Open price
        "61596.4",  // High price
        "61434.4",  // Low price
        "61539.9",  // Close price
        "63753192.1129" // Trading volume (USD)
      ],
      [
        1722676800,
        "61539.9",
        "61610.0",
        "61480.0",
        "61590.5",
        "42311820.8720"
      ]
    ]
  }
}
```

---
  
  
  ---
        
## API 12: Pair Liquidation Map


**Supported Plans, Intervals, and Historical Data Access**

Hobbyist:Not Available
Startup:Not Available
Standard:Not Available
Professional:Available


### Method: GET

**URL**:
```
https://open-api-v4.coinglass.com//api/futures/liquidation/map
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

| Parameter | Type   | Required | Description                                                                                        | Example value |
| --------- | ------ | -------- | -------------------------------------------------------------------------------------------------- | ------------- |
| exchange  | string | yes      | Exchange name (e.g., Binance). Retrieve supported exchanges via the 'supported-exchange-pair' API. | Binance       |
| symbol    | string | yes      | Trading pair (e.g., BTCUSDT). Retrieve supported pairs via the 'supported-exchange-pair' API.      | BTCUSDT       |
| range     | string | yes      | Time range for data aggregation. Supported values: 1d, 7d, 30d.                                    | 1d            |


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/futures/liquidation/map?exchange=Binance&symbol=BTCUSDT&range=1d' \
-H 'Content-Type: application/json' \
-H 'CG-API-KEY: ${YOUR_API_KEY}' \
-H 'User-Agent: coinglass-skill/1.0.0'
```
        
**Response**:
```json
{
  "code": "0",
  "msg": "success",
  "data": 
  {
    "data": 
    {
      "48935": //liquidation price
      [
        [
          48935,//liquidation price
          1579370.77,//Liquidation Level
          25,//Leverage Ratio
          null
        ]
      ],
      ...  
    }
  }
}
```

---
  
  
  ---
        
## API 13: Coin Liquidation Map


**Supported Plans, Intervals, and Historical Data Access**

Hobbyist:Not Available
Startup:Not Available
Standard:Not Available
Professional:Available


### Method: GET

**URL**:
```
https://open-api-v4.coinglass.com//api/futures/liquidation/aggregated-map
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

| Parameter | Type   | Required | Description                                                                       | Example value |
| --------- | ------ | -------- | --------------------------------------------------------------------------------- | ------------- |
| symbol    | string | yes      | Trading coin (e.g., BTC). Retrieve supported coins via the 'supported-coins' API. | BTC           |
| range     | string | yes      | Time range for data aggregation. Supported values: 1d, 7d, 30d.                   | 1d            |


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/futures/liquidation/aggregated-map?symbol=BTC&range=1d' \
-H 'Content-Type: application/json' \
-H 'CG-API-KEY: ${YOUR_API_KEY}' \
-H 'User-Agent: coinglass-skill/1.0.0'
```
        
**Response**:
```json
{
  "code": "0",
  "msg": "success",
  "data": 
  {
    "data": 
    {
      "48935": //liquidation price
      [
        [
          48935,//liquidation price
          1579370.77,//Liquidation Level
          null,
          null
        ]
      ],
      ...  
    }
  }
}
```

---
  
  
  ---
        
## API 14: Liquidation Max Pain


**Supported Plans, Intervals, and Historical Data Access**

Hobbyist:Not Available
Startup:Not Available
Standard:Not Available
Professional:Available


### Method: GET

**URL**:
```
https://open-api-v4.coinglass.com//api/futures/liquidation/max-pain
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

| Parameter | Type   | Required | Description                                                                           | Example value |
| --------- | ------ | -------- | ------------------------------------------------------------------------------------- | ------------- |
| range     | string | no       | Time interval for data aggregation. Supported values: 12h, 24h, 48h, 3d, 7d, 14d, 30d | 24h           |


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/futures/liquidation/max-pain' \
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
      "price": 110625.1, //symbol price
      "long_max_pain_liq_level": 75677278.26,//long max pain liquidation level
      "long_max_pain_liq_price": 113046.71, //long max pain luquidation price
      "short_max_pain_liq_level": 44617473.19,
      "short_max_pain_liq_price": 109748.37
    
    {
      "symbol": "ETH",
      "price": 3914.14,
      "long_max_pain_liq_level": 34406421.23,
      "long_max_pain_liq_price": 3955.722,
      "short_max_pain_liq_level": 44375943.61,
      "short_max_pain_liq_price": 3820.002
    },
    {
      "symbol": "SOL",
      "price": 195.1,
      "long_max_pain_liq_level": 12467317.12,
      "long_max_pain_liq_price": 199.468,
      "short_max_pain_liq_level": 12927647.29,
      "short_max_pain_liq_price": 190.186
    },
    ....
  ]
}
```

---
  