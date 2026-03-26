---
name: exchange-volume-history
description: Exchange Volume History request using the CoinGlass API. 
metadata:
  version: 1.0.0
  author: CoinGlass
  openclaw:
    requires:
      bins:
        - curl
        - openssl
    homepage: https://github.com/coinglass-official/coinglass-api-skills/tree/main/options/API.md
license: MIT
---

# CoinGlass Exchange Volume History Skill

Exchange Volume History request on CoinGLass API endpoints. Return the result in JSON format.


## Quick Reference

| API                            | Endpoint                         | Function                                                                                                                  |
| ------------------------------ | -------------------------------- | ------------------------------------------------------------------------------------------------------------------------- |
| Option Max Pain                | /api/option/max-pain             | This endpoint provides the max pain price for options.                                                                    |
| Options Info                   | /api/option/info                 | This endpoint provides detailed information about open interest and trading volume for options across different exchanges |
| Exchange Open Interest History | /api/option/exchange-oi-history  | This endpoint provides historical open interest data for options across different exchanges                               |
| Exchange Volume History        | /api/option/exchange-vol-history | This endpoint provides historical trading volume data for options across different exchanges                              |

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
        
## API 1: Option Max Pain


**Supported Plans, Intervals, and Historical Data Access**

Hobbyist:Available
Startup:Available
Standard:Available
Professional:Available


### Method: GET

**URL**:
```
https://open-api-v4.coinglass.com//api/option/max-pain
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

| Parameter | Type   | Required | Description                                   | Example value |
| --------- | ------ | -------- | --------------------------------------------- | ------------- |
| symbol    | string | yes      | Trading coin (e.g., BTC,ETH).                 | BTC           |
| exchange  | string | yes      | Exchange name (e.g., Deribit, Binance, OKX).  | Deribit       |


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/option/max-pain?symbol=BTC&exchange=Deribit' \
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
      "date": "250422",                                   // Date (YYMMDD format)
      "call_open_interest_market_value": 1616749.22,      // Call option market value (USD)
      "put_open_interest": 512.5,                         // Put option open interest (contracts)
      "put_open_interest_market_value": 49687.62,         // Put option market value (USD)
      "max_pain_price": "84000",                          // Max pain price
      "call_open_interest": 953.7,                        // Call option open interest (contracts)
      "call_open_interest_notional": 83519113.56,         // Call option notional value (USD)
      "put_open_interest_notional": 44881569.13           // Put option notional value (USD)
    },
    {
      "date": "250423",                                   // Date (YYMMDD format)
      "call_open_interest_market_value": 2274700.52,      // Call option market value (USD)
      "put_open_interest": 1204.3,                        // Put option open interest (contracts)
      "put_open_interest_market_value": 374536.01,        // Put option market value (USD)
      "max_pain_price": "85000",                          // Max pain price
      "call_open_interest": 1302.2,                       // Call option open interest (contracts)
      "call_open_interest_notional": 114040373.53,        // Call option notional value (USD)
      "put_open_interest_notional": 105465691.73          // Put option notional value (USD)
    }
  ]
}
```

---
  
  
  ---
        
## API 2: Options Info


**Supported Plans, Intervals, and Historical Data Access**

Hobbyist:Available
Startup:Available
Standard:Available
Professional:Available


### Method: GET

**URL**:
```
https://open-api-v4.coinglass.com//api/option/info
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

| Parameter | Type   | Required | Description                    | Example value |
| --------- | ------ | -------- | ------------------------------ | ------------- |
| symbol    | string | yes      | Trading coin (e.g., BTC,ETH).  | BTC           |


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/option/info?symbol=BTC' \
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
      "exchange_name": "All",                           // Exchange name
      "open_interest": 361038.78,                       // Open interest (contracts)
      "oi_market_share": 100,                           // Market share (%)
      "open_interest_change_24h": 2.72,                 // 24h open interest change (%)
      "open_interest_usd": 31623069708.138245,          // Open interest value (USD)
      "volume_usd_24h": 2764676957.0569425,             // 24h trading volume (USD)
      "volume_change_percent_24h": 303.1                // 24h volume change (%)
    },
    {
      "exchange_name": "Deribit",                       // Exchange name
      "open_interest": 262641.9,                        // Open interest (contracts)
      "oi_market_share": 72.74,                         // Market share (%)
      "open_interest_change_24h": 2.57,                 // 24h open interest change (%)
      "open_interest_usd": 23005403973.349,             // Open interest value (USD)
      "volume_usd_24h": 2080336672.709                  // 24h trading volume (USD)
    }
  ]
}
```

---
  
  
  ---
        
## API 3: Exchange Open Interest History


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
https://open-api-v4.coinglass.com//api/option/exchange-oi-history
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

| Parameter | Type   | Required | Description                                                                                                                                                     | Example value |
| --------- | ------ | -------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------- |
| symbol    | string | yes      | Trading coin (e.g., BTC,ETH).                                                                                                                                   | BTC           |
| unit      | string | yes      | Specify the unit for the returned data. Supported values depend on the symbol. If symbol is BTC, choose between USD or BTC. For ETH, choose between USD or ETH. | USD           |
| range     | string | yes      | Time range for the data. Supported values: 1h, 4h, 12h, all.                                                                                                    | 1h            |


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/option/exchange-oi-history?symbol=BTC&unit=USD&range=1h' \
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
      "data_map": {                            // Open Interest (OI) data by exchange
        "huobi": [15167.03527, ...],           // OI data from Huobi exchange
        "gate": [23412.723, ...],              // OI data from Gate exchange
        ...
      }
    }
  ]
}
```

---
  
  
  ---
        
## API 4: Exchange Volume History


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
https://open-api-v4.coinglass.com//api/option/exchange-vol-history
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

| Parameter | Type   | Required | Description                                                                                                                                                     | Example value |
| --------- | ------ | -------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------- |
| symbol    | string | yes      | Trading coin (e.g., BTC,ETH).                                                                                                                                   | BTC           |
| unit      | string | yes      | Specify the unit for the returned data. Supported values depend on the symbol. If symbol is BTC, choose between USD or BTC. For ETH, choose between USD or ETH. | USD           |


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/option/exchange-vol-history?symbol=BTC&unit=USD' \
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
      "data_map": {                            // Volume data by exchange
        "huobi": [15167.03527, ...],           // Volume data from Huobi exchange
        "gate": [23412.723, ...],              // Volume data from Gate exchange
        ...
      }
    }
  ]
}
```

---
  