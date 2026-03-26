---
name: spots
description: Spots request using the CoinGlass API. 
metadata:
  version: 1.0.0
  author: CoinGlass
  openclaw:
    requires:
      bins:
        - curl
        - openssl
    homepage: https://github.com/coinglass-official/coinglass-api-skills/tree/main/indic/spots/API.md
license: MIT
---

# CoinGlass Spots Skill

Spots request on CoinGLass API endpoints. Return the result in JSON format.


## Quick Reference

| API                        | Endpoint                          | Function                                                                                                                                     |
| -------------------------- | --------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------- |
| Coinbase Premium Index     | /api/coinbase-premium-index       | This endpoint provides the Coinbase Bitcoin Premium Index, which indicates the price difference between Bitcoin on Coinbase Pro and Binance. |
| Bitfinex Margin Long/Short | /api/bitfinex-margin-long-short   | This endpoint provides data on margin long and short positions from Bitfinex.                                                                |
| Borrow Interest Rate       | /api/borrow-interest-rate/history | This endpoint provides daily borrowing interest rates for cryptocurrencies.                                                                  |

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
        
## API 1: Coinbase Premium Index


**Supported Plans, Intervals, and Historical Data Access**

Hobbyist:Available
Startup:Available
Standard:Available
Professional:Available


### Method: GET

**URL**:
```
https://open-api-v4.coinglass.com//api/coinbase-premium-index
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

| Parameter  | Type    | Required | Description                                                                                          | Example value |
| ---------- | ------- | -------- | ---------------------------------------------------------------------------------------------------- | ------------- |
| interval   | string  | yes      | Data aggregation time interval. Supported values: 1m, 3m, 5m, 15m, 30m, 1h, 4h, 6h, 8h, 12h, 1d, 1w. | 1d            |
| limit      | integer | no       | Number of results per request. Default: 1000, Maximum: 1000.                                         |               |
| start_time | integer | no       | Start timestamp in milliseconds (e.g., 1641522717000).                                               |               |
| end_time   | integer | no       | End timestamp in milliseconds (e.g., 1641522717000).                                                 |               |


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/coinbase-premium-index?interval=1d' \
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
      "time": 1658880000,         // Timestamp (in seconds)
      "premium": 5.55,            // Premium amount (USD)
      "premium_rate": 0.0261      // Premium rate (e.g., 0.0261 = 2.61%)

    },
    {
       "time": 1658880000,         // Timestamp (in seconds)
       "premium": 5.55,            // Premium amount (USD)
       "premium_rate": 0.0261      // Premium rate (e.g., 0.0261 = 2.61%)

    }
  ]
}
```

---
  
  
  ---
        
## API 2: Bitfinex Margin Long/Short


**Supported Plans, Intervals, and Historical Data Access**

Hobbyist:Available
Startup:Available
Standard:Available
Professional:Available


### Method: GET

**URL**:
```
https://open-api-v4.coinglass.com//api/bitfinex-margin-long-short
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

| Parameter  | Type    | Required | Description                                                                                          | Example value |
| ---------- | ------- | -------- | ---------------------------------------------------------------------------------------------------- | ------------- |
| symbol     | string  | yes      | BTC,ETH                                                                                              | BTC           |
| limit      | integer | no       | Number of results per request. Default: 1000, Maximum: 1000.                                         |               |
| interval   | string  | yes      | Data aggregation time interval. Supported values: 1m, 3m, 5m, 15m, 30m, 1h, 4h, 6h, 8h, 12h, 1d, 1w. | 1d            |
| start_time | integer | no       | Start timestamp in milliseconds (e.g., 1641522717000).                                               |               |
| end_time   | integer | no       | End timestamp in milliseconds (e.g., 1641522717000).                                                 |               |


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/bitfinex-margin-long-short?symbol=BTC&interval=1d' \
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
      "time": 1658880000,              // Timestamp, representing the data's corresponding time point
      "long_quantity": 104637.94,       // Long position quantity
      "short_quantity": 2828.53        // Short position quantity
    },
    {
      "time": 1658966400,              // Timestamp, representing the data's corresponding time point
      "long_quantity": 105259.46,       // Long position quantity
      "short_quantity": 2847.84        // Short position quantity
    }
    // More data entries...
  ]
}
```

---
  
  
  ---
        
## API 3: Borrow Interest Rate


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
https://open-api-v4.coinglass.com//api/borrow-interest-rate/history
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

| Parameter  | Type    | Required | Description                                                                                          | Example value |
| ---------- | ------- | -------- | ---------------------------------------------------------------------------------------------------- | ------------- |
| exchange   | string  | yes      | Exchange name  support:Binance ,OKX,Bybit                                                            | Binance       |
| symbol     | string  | yes      | Trading coin (e.g., BTC). Retrieve supported coins via the 'supported-coins' API.                    | BTC           |
| interval   | string  | yes      | Data aggregation time interval. Supported values: 1m, 3m, 5m, 15m, 30m, 1h, 4h, 6h, 8h, 12h, 1d, 1w. | h1            |
| limit      | integer | no       | Number of results per request. Default: 1000, Maximum: 1000.                                         | 500           |
| start_time | integer | no       |  Start timestamp in milliseconds (e.g., 1641522717000).                                              | 1706089927315 |
| end_time   | integer | no       | End timestamp in milliseconds (e.g., 1641522717000).                                                 |               |


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/borrow-interest-rate/history?exchange=Binance&symbol=BTC&interval=h1' \
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
      "time": 1741636800,                  // Timestamp (in seconds)
      "interest_rate": 0.002989            // daily Interest rate
    },
    {
      "time": 1741640400,                  // Timestamp (in seconds)
      "interest_rate": 0.002989            // daily Interest rate
    }
  ]
}
```

---
  