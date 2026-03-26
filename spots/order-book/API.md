---
name: order-book
description: Order book request using the CoinGlass API. 
metadata:
  version: 1.0.0
  author: CoinGlass
  openclaw:
    requires:
      bins:
        - curl
        - openssl
    homepage: https://github.com/coinglass-official/coinglass-api-skills/tree/main/spots/order-book/API.md
license: MIT
---

# CoinGlass Order book Skill

Order book request on CoinGLass API endpoints. Return the result in JSON format.


## Quick Reference

| API                            | Endpoint                                        | Function                                                                                                                                                 |
| ------------------------------ | ----------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Pair Orderbook Bid&Ask(±range) | /api/spot/orderbook/ask-bids-history            | This endpoint provides historical data of the order book for spot trading, including total bid/ask volumes within a specific price range.                |
| Coin Orderbook Bid&Ask(±range) | /api/spot/orderbook/aggregated-ask-bids-history | This endpoint provides historical data of the aggregated order book for spot trading, including total bid/ask volumes within a specific price range.     |
| Orderbook Heatmap              | /api/spot/orderbook/history                     | This endpoint provides historical order book depth data for spot trading, supporting heatmap visualization.                                              |
| Large Orderbook                | /api/spot/orderbook/large-limit-order           | This endpoint provides large open limit orders from the current order book for spot trading.(thresholds: BTC ≥ 350K, ETH ≥ 250K, Other ≥ 10K)            |
| Large Orderbook History        | /api/spot/orderbook/large-limit-order-history   | This endpoint provides completed historical large limit orders from the order book for futures trading.(thresholds: BTC ≥ 350K, ETH ≥ 250K, Other ≥ 10K) |

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
        
## API 1: Pair Orderbook Bid&Ask(±range)


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
https://open-api-v4.coinglass.com//api/spot/orderbook/ask-bids-history
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

| Parameter  | Type    | Required | Description                                                                                          | Example value |
| ---------- | ------- | -------- | ---------------------------------------------------------------------------------------------------- | ------------- |
| exchange   | string  | yes      | Exchange name (e.g., Binance). Retrieve supported exchanges via the 'supported-exchange-pair' API.   | Binance       |
| symbol     | string  | yes      | Trading pair (e.g., BTCUSDT). Check supported pairs through the 'supported-exchange-pair' API.       | BTCUSDT       |
| interval   | string  | yes      | Data aggregation time interval. Supported values: 1m, 3m, 5m, 15m, 30m, 1h, 4h, 6h, 8h, 12h, 1d, 1w. | 1d            |
| limit      | integer | no       | Number of results per request. Default: 1000, Maximum: 1000.                                         |               |
| start_time | integer | no       | Start timestamp in milliseconds (e.g., 1641522717000).                                               |               |
| end_time   | integer | no       |  End timestamp in milliseconds (e.g., 1641522717000).                                                |               |
| range      | string  | no       | Depth percentage (e.g., 0.25, 0.5, 0.75, 1, 2, 3, 5, 10).                                            | 1             |


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/spot/orderbook/ask-bids-history?exchange=Binance&symbol=BTCUSDT&interval=1d' \
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
      "bids_usd": 81639959.9338,        // Total long position amount (USD)
      "bids_quantity": 1276.645,        // Total long quantity
      "asks_usd": 78533053.6862,        // Total short position amount (USD)
      "asks_quantity": 1217.125,        // Total short quantity
      "time": 1714003200000             // Timestamp (in milliseconds)
    },
    {
      "bids_usd": 62345879.8821,
      "bids_quantity": 980.473,
      "asks_usd": 65918423.4715,
      "asks_quantity": 1021.644,
      "time": 1714089600000
    }
  ]
}
```

---
  
  
  ---
        
## API 2: Coin Orderbook Bid&Ask(±range)


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
https://open-api-v4.coinglass.com//api/spot/orderbook/aggregated-ask-bids-history
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

| Parameter     | Type    | Required | Description                                                                                          | Example value |
| ------------- | ------- | -------- | ---------------------------------------------------------------------------------------------------- | ------------- |
| exchange_list | string  | yes      | List of exchange names to retrieve data from (e.g., 'ALL', or 'Binance, OKX, Bybit')                 | Binance       |
| symbol        | string  | yes      | Trading coin (e.g., BTC). Retrieve supported coins via the 'supported-coins' API.                    | BTC           |
| interval      | string  | yes      | Data aggregation time interval. Supported values: 1m, 3m, 5m, 15m, 30m, 1h, 4h, 6h, 8h, 12h, 1d, 1w. | h1            |
| limit         | integer | no       | Number of results per request. Default: 1000, Maximum: 1000.                                         | 10            |
| start_time    | integer | no       | Start timestamp in milliseconds (e.g., 1641522717000).                                               |               |
| end_time      | integer | no       | End timestamp in milliseconds (e.g., 1641522717000).                                                 |               |
| range         | string  | no       | Depth percentage (e.g., 0.25, 0.5, 0.75, 1, 2, 3, 5, 10).                                            | 1             |


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/spot/orderbook/aggregated-ask-bids-history?exchange_list=Binance&symbol=BTC&interval=h1' \
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
      "aggregated_bids_usd": 12679537.0806,         // Aggregated long amount (USD)
      "aggregated_bids_quantity": 197.99861,        // Aggregated long quantity
      "aggregated_asks_usd": 10985519.9268,         // Aggregated short amount (USD)
      "aggregated_asks_quantity": 170.382,          // Aggregated short quantity
      "time": 1714003200000                         // Timestamp (milliseconds)
    },
    {
      "aggregated_bids_usd": 18423845.1947,
      "aggregated_bids_quantity": 265.483,
      "aggregated_asks_usd": 17384271.5521,
      "aggregated_asks_quantity": 240.785,
      "time": 1714089600000
    }
  ]
}
```

---
  
  
  ---
        
## API 3: Orderbook Heatmap


**Supported Plans, Intervals, and Historical Data Access**

Hobbyist:Not Available
Startup:Not Available
Standard:Available
Professional:Available


The available historical data length depends on your subscription plan and the selected interval. Please refer to the table below for more details:

For more information on historical data access by plan and interval, see [references/plans-interval-history-length.md](references/plans-interval-history-length.md).



### Method: GET

**URL**:
```
https://open-api-v4.coinglass.com//api/spot/orderbook/history
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

| Parameter  | Type   | Required | Description                                                                                                               | Example value |
| ---------- | ------ | -------- | ------------------------------------------------------------------------------------------------------------------------- | ------------- |
| exchange   | string | yes      | Spot exchange names (e.g., Binance, OKX) .Retrieve supported exchanges via the 'supported-exchange-pair' API.             | Binance       |
| symbol     | string | yes      | Trading pair (e.g., BTCUSDT). Retrieve supported pairs via the 'supported-exchange-pair' API.                             | BTCUSDT       |
| interval   | string | yes      | Time intervals for data aggregation. Supported values: 1m、3m、5m、15m、30m、1h、4h、6h、8h、12h、1d.                               | 1h            |
| limit      | string | no       | Number of results per request. Default: 100, Maximum: 100.  Historical range – 1m: 3 days, 5m: 15 days, others: 150 days. |               |
| start_time | string | no       | Start timestamp in milliseconds (e.g., 1641522717000).                                                                    |               |
| end_time   | string | no       | End timestamp in milliseconds (e.g., 1641522717000).                                                                      |               |


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/spot/orderbook/history?exchange=Binance&symbol=BTCUSDT&interval=1h' \
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
        [
            1723611600,
            [
                [
                    56420, //Price
                    4.777 //Quantity
                ],
                [
                    40300,
                    2.191
                ]
            ],
            [
                [
                    56420,
                    4.777
                ],
                [
                    40300,
                    2.191
                ]
            ]
        ]
    ],
    "success": true
}
```

---
  
  
  ---
        
## API 4: Large Orderbook


**Supported Plans, Intervals, and Historical Data Access**

Hobbyist:Not Available
Startup:Not Available
Standard:Available
Professional:Available


### Method: GET

**URL**:
```
https://open-api-v4.coinglass.com//api/spot/orderbook/large-limit-order
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

| Parameter | Type   | Required | Description                                                                                        | Example value |
| --------- | ------ | -------- | -------------------------------------------------------------------------------------------------- | ------------- |
| exchange  | string | yes      | Exchange name (e.g., Binance). Retrieve supported exchanges via the 'supported-exchange-pair' API. | Binance       |
| symbol    | string | yes      | Trading pair (e.g., BTCUSDT). Retrieve supported pairs via the 'supported-exchange-pair' API.      | BTCUSDT       |


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/spot/orderbook/large-limit-order?exchange=Binance&symbol=BTCUSDT' \
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
      "id": 2536823422,
      "exchange_name": "Binance",                // Exchange name
      "symbol": "BTCUSDT",                       // Trading pair
      "base_asset": "BTC",                       // Base asset
      "quote_asset": "USDT",                     // Quote asset
      "price": 20000,                            // Order price
      "start_time": 1742615617000,               // Order start time (timestamp)
      "start_quantity": 109.42454,               // Initial quantity
      "start_usd_value": 2188490.8,              // Initial order value in USD
      "current_quantity": 104.00705,             // Current remaining quantity
      "current_usd_value": 2080141,              // Current remaining value in USD
      "current_time": 1745287267958,             // Current update time (timestamp)
      "executed_volume": 0,                      // Executed volume
      "executed_usd_value": 0,                   // Executed value in USD
      "trade_count": 0,                          // Number of executed trades
      "order_side": 2,                           // Order side: 1 = Buy, 2 = Sell
      "order_state": 1                           // Order state: 1 = Active, 2 = Completed
    }
  ]
}
```

---
  
  
  ---
        
## API 5: Large Orderbook History


**Supported Plans, Intervals, and Historical Data Access**

Hobbyist:Not Available
Startup:Not Available
Standard:Available
Professional:Available


The available historical data length depends on your subscription plan and the selected interval. Please refer to the table below for more details:

For more information on historical data access by plan and interval, see [references/plans-interval-history-length.md](references/plans-interval-history-length.md).



### Method: GET

**URL**:
```
https://open-api-v4.coinglass.com//api/spot/orderbook/large-limit-order-history
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

| Parameter  | Type   | Required | Description                                                                                        | Example value |
| ---------- | ------ | -------- | -------------------------------------------------------------------------------------------------- | ------------- |
| exchange   | string | yes      | Exchange name (e.g., Binance). Retrieve supported exchanges via the 'supported-exchange-pair' API. | Binance       |
| symbol     | string | yes      | Trading pair (e.g., BTCUSDT). Check supported pairs through the 'supported-exchange-pair' API.     | BTCUSDT       |
| start_time | string | yes      | Start timestamp in milliseconds (e.g., 1723625037000).                                             |               |
| end_time   | string | yes      | End timestamp in milliseconds (e.g., 1723626037000).                                               |               |
| state      | string | yes      | Status of the order — 1for ''In Progress'' 2 for "Finish" 3 for "Revoke"                           | 1             |


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/spot/orderbook/large-limit-order-history?exchange=Binance&symbol=BTCUSDT&start_time=&end_time=&state=1' \
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
      "id": 2895605135,
      "exchange_name": "Binance",               // Exchange name
      "symbol": "BTCUSDT",                      // Trading pair
      "base_asset": "BTC",                      // Base asset
      "quote_asset": "USDT",                    // Quote asset
      "price": 89205.9,                         // Order price
      "start_time": 1745287309000,              // Order start time (milliseconds)
      "start_quantity": 25.779,                 // Initial order quantity
      "start_usd_value": 2299638.8961,          // Initial order value (USD)
      "current_quantity": 25.779,               // Remaining quantity
      "current_usd_value": 2299638.8961,        // Remaining value (USD)
      "current_time": 1745287309000,            // Current timestamp (milliseconds)
      "executed_volume": 0,                     // Executed volume
      "executed_usd_value": 0,                  // Executed value (USD)
      "trade_count": 0,                         // Number of trades executed
      "order_side": 1,                          // Order side: 1 = Sell, 2 = Buy
      "order_state": 2,                         // Order state: 0 = Not started, 1 = Open, 2 = Filled, 3 = Cancelled
      "order_end_time": 1745287328000           // Order end time (milliseconds)
    }
    ....
  ]
}
```

---
  