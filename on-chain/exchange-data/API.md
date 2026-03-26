---
name: exchange-data
description: Exchange data request using the CoinGlass API. 
metadata:
  version: 1.0.0
  author: CoinGlass
  openclaw:
    requires:
      bins:
        - curl
        - openssl
    homepage: https://github.com/coinglass-official/coinglass-api-skills/tree/main/on-chain/exchange-data/API.md
license: MIT
---

# CoinGlass Exchange data Skill

Exchange data request on CoinGLass API endpoints. Return the result in JSON format.


## Quick Reference

| API                    | Endpoint                    | Function                                                                                                                                                             |
| ---------------------- | --------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Exchange Assets        | /api/exchange/assets        | This endpoint provides asset holdings data for exchange wallets, including wallet address, asset balance, USD value, and real-time price information for each asset. |
| Exchange Balance List  | /api/exchange/balance/list  | This endpoint provides exchange-level asset balance data, including total holdings and percentage changes over 1-day, 7-day, and 30-day periods.                     |
| Exchange Balance Chart | /api/exchange/balance/chart | This endpoint provides historical chart data of exchange asset balances over time, along with corresponding price data.                                              |

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
        
## API 1: Exchange Assets


**Supported Plans, Intervals, and Historical Data Access**

Hobbyist:Available
Startup:Available
Standard:Available
Professional:Available


### Method: GET

**URL**:
```
https://open-api-v4.coinglass.com//api/exchange/assets
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

| Parameter | Type   | Required | Description                                                                                        | Example value |
| --------- | ------ | -------- | -------------------------------------------------------------------------------------------------- | ------------- |
| exchange  | string | yes      | Exchange name (e.g., Binance). Retrieve supported exchanges via the 'supported-exchange-pair' API. | Binance       |
| per_page  | string | no       | Number of results per page.                                                                        | 10            |
| page      | string | no       | Page number for pagination, default: 1                                                             | 1             |


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/exchange/assets?exchange=Binance' \
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
      "wallet_address": "34xp4vRoCGJym3xR7yCVPFHoCNxv4Twseo",
      "balance": 248597.54,
      "balance_usd": 21757721869.92,
      "symbol": "BTC",
      "assets_name": "Bitcoin",
      "price": 87521.87117346626
    },
    {
      "wallet_address": "3M219KR5vEneNb47ewrPfWyb5jQ2DjxRP6",
      "balance": 139456.08,
      "balance_usd": 12205457068.12,
      "symbol": "BTC",
      "assets_name": "Bitcoin",
      "price": 87521.87117346626
    },
```

---
  
  
  ---
        
## API 2: Exchange Balance List


**Supported Plans, Intervals, and Historical Data Access**

Hobbyist:Available
Startup:Available
Standard:Available
Professional:Available


### Method: GET

**URL**:
```
https://open-api-v4.coinglass.com//api/exchange/balance/list
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

| Parameter | Type   | Required | Description                            | Example value |
| --------- | ------ | -------- | -------------------------------------- | ------------- |
| symbol    | string | yes      | Trading coin eg. BTC , ETH , USDT(ETH) | BTC           |


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/exchange/balance/list?symbol=BTC' \
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
      "exchange_name": "Coinbase",               // Exchange name
      "total_balance": 716590.351233,            // Total balance
      "balance_change_1d": 638.797302,           // Balance change in 24 hours
      "balance_change_percent_1d": 0.09,         // Balance change percentage in 24 hours (%)
      "balance_change_7d": 799.967408,           // Balance change in 7 days
      "balance_change_percent_7d": 0.11,         // Balance change percentage in 7 days (%)
      "balance_change_30d": -29121.977486,       // Balance change in 30 days
      "balance_change_percent_30d": -3.91        // Balance change percentage in 30 days (%)
    },
    {
      "exchange_name": "Binance",                // Exchange name
      "total_balance": 582344.497738,            // Total balance
      "balance_change_1d": 505.682778,           // Balance change in 24 hours
      "balance_change_percent_1d": 0.09,         // Balance change percentage in 24 hours (%)
      "balance_change_7d": -3784.88544,          // Balance change in 7 days
      "balance_change_percent_7d": -0.65,        // Balance change percentage in 7 days (%)
      "balance_change_30d": 3753.870055,         // Balance change in 30 days
      "balance_change_percent_30d": 0.65         // Balance change percentage in 30 days (%)
    }
  ]
}
```

---
  
  
  ---
        
## API 3: Exchange Balance Chart


**Supported Plans, Intervals, and Historical Data Access**

Hobbyist:Available
Startup:Available
Standard:Available
Professional:Available


### Method: GET

**URL**:
```
https://open-api-v4.coinglass.com//api/exchange/balance/chart
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

| Parameter | Type   | Required | Description               | Example value |
| --------- | ------ | -------- | ------------------------- | ------------- |
| symbol    | string | yes      | Trading coin eg. BTC, ETH | BTC           |


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/exchange/balance/chart?symbol=BTC' \
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
      "time_list": [1691460000000, ...],       // Array of timestamps (in milliseconds)
      "price_list": [29140.9, ...],            // Array of prices corresponding to each timestamp
      "data_map": {                            // Balance data by exchange
        "huobi": [15167.03527, ...],           // Balance data from Huobi exchange
        "gate": [23412.723, ...],              // Balance data from Gate exchange
        ...
      }
    }
  ]
}
```

---
  