---
name: ethereum-etf
description: Ethereum ETF request using the CoinGlass API. 
metadata:
  version: 1.0.0
  author: CoinGlass
  openclaw:
    requires:
      bins:
        - curl
        - openssl
    homepage: https://github.com/coinglass-official/coinglass-api-skills/tree/main/etf/ethereum-etf/API.md
license: MIT
---

# CoinGlass Ethereum ETF Skill

Ethereum ETF request on CoinGLass API endpoints. Return the result in JSON format.


## Quick Reference

| API                   | Endpoint                             | Function                                                                                           |
| --------------------- | ------------------------------------ | -------------------------------------------------------------------------------------------------- |
| ETF NetAssets History | /api/etf/ethereum/net-assets/history | This endpoint provides historical net assets data for Ethereum-based Exchange-Traded Funds (ETFs). |
| Ethereum ETF List     | /api/etf/ethereum/list               | This endpoint provides a list of key status information for Ethereum Exchange-Traded Funds (ETFs). |
| ETF Flows History     | /api/etf/ethereum/flow-history       | This endpoint provides a list of key status information regarding the history of ETF flows.        |

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
        
## API 1: ETF NetAssets History


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
https://open-api-v4.coinglass.com//api/etf/ethereum/net-assets/history
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

*No parameters required*


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/etf/ethereum/net-assets/history' \
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
      "net_assets_usd": 51671409241.39,         // Net asset value (USD)
      "change_usd": 655300000,                  // Daily capital change (USD)
      "timestamp": 1704931200000,               // Date (timestamp in milliseconds)
      "price_usd": 1637.8                      // ETH price on that date (USD)
    },
    {
      "net_assets_usd": 51874409241.39,         // Net asset value (USD)
      "change_usd": 203000000,                  // Daily capital change (USD)
      "timestamp": 1705017600000,               // Date (timestamp in milliseconds)
      "price_usd": 1637.8                      // ETH price on that date (USD)
    }
  ]
}
```

---
  
  
  ---
        
## API 2: Ethereum ETF List


**Supported Plans, Intervals, and Historical Data Access**

Hobbyist:Available
Startup:Available
Standard:Available
Professional:Available


### Method: GET

**URL**:
```
https://open-api-v4.coinglass.com//api/etf/ethereum/list
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

*No parameters required*


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/etf/ethereum/list' \
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
      "ticker": "ETHA",                                  // ETF ticker
      "name": "iShares Ethereum Trust ETF",              // ETF name
      "region": "us",                                    // Region
      "market_status": "closed",                         // Market status
      "primary_exchange": "XNAS",                        // Primary exchange
      "cik_code": "0002000638",                          // CIK code
      "type": "Spot",                                    // Type
      "market_cap": "544896000.00",                      // Market capitalization
      "list_date": 1721692800000,                        // Listing date
      "shares_outstanding": "28800000",                  // Shares outstanding
      "aum": "",                                         // Assets under management
      "management_fee_percent": "0.25",                  // Management fee percentage
      "last_trade_time": 1722988779939,                  // Last trade time
      "last_quote_time": 1722988799379,                  // Last quote time
      "volume_quantity": 5592645,                        // Volume quantity
      "volume_usd": 106447049.343,                       // Volume in USD
      "price": 18.92,                                    // Market price
      "price_change": 0.67,                              // Price change
      "price_change_percent": 3.67,                      // Price change percentage
      "asset_info": {
        "nav": 18.11,                                  // Net asset value
        "premium_discount": 0.77,                      // Premium/discount
        "holding_quantity": 237882.8821,                 // Holding quantity
        "change_percent_1d": 0,                        // 1-day change percentage
        "change_quantity_1d": 0,                         // 1-day change quantity
        "change_percent_7d": 56.69,                    // 7-day change percentage
        "change_quantity_7d": 86060.9115,                // 7-day change quantity
        "date": "2024-08-05"                           // Data date
      },
      "update_time": 1722995656637                       // Update time
    }
  ]
}
```

---
  
  
  ---
        
## API 3: ETF Flows History


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
https://open-api-v4.coinglass.com//api/etf/ethereum/flow-history
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

*No parameters required*


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/etf/ethereum/flow-history' \
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
      "timestamp": 1721692800000,
      "flow_usd": 106600000,
      "price_usd": 3438.09,
      "etf_flows": [
        {
          "etf_ticker": "ETHA",
          "flow_usd": 266500000
        },
        {
          "etf_ticker": "FETH",
          "flow_usd": 71300000
        },
      ]
    }
  ]
}
```

---
  