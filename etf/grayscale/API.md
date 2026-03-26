---
name: grayscale
description: Grayscale request using the CoinGlass API. 
metadata:
  version: 1.0.0
  author: CoinGlass
  openclaw:
    requires:
      bins:
        - curl
        - openssl
    homepage: https://github.com/coinglass-official/coinglass-api-skills/tree/main/etf/grayscale/API.md
license: MIT
---

# CoinGlass Grayscale Skill

Grayscale request on CoinGLass API endpoints. Return the result in JSON format.


## Quick Reference

| API             | Endpoint                       | Function                                                                                                       |
| --------------- | ------------------------------ | -------------------------------------------------------------------------------------------------------------- |
| Holdings List   | /api/grayscale/holdings-list   | This endpoint provides a list of holdings managed by Grayscale Investments.                                    |
| Premium History | /api/grayscale/premium-history | This endpoint provides historical premium/discount data for Grayscale Investment Trusts relative to their NAV. |

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
        
## API 1: Holdings List


**Supported Plans, Intervals, and Historical Data Access**

Hobbyist:Available
Startup:Available
Standard:Available
Professional:Available


### Method: GET

**URL**:
```
https://open-api-v4.coinglass.com//api/grayscale/holdings-list
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

*No parameters required*


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/grayscale/holdings-list' \
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
      "symbol": "ETH",                                  // Token symbol, 
      "primary_market_price": 29.89,                    // Price in the primary market 
      "secondary_market_price": 29.71,                  // Price in the secondary market 
      "premium_rate": -0.6,                             // Premium rate (%),
      "holdings_amount": 2630007.61026,                 // Current holding amount (in tokens)
      "holdings_usd": 4290752215.8347797,               // Total market value of holdings in USD
      "holdings_amount_change_30d": 0,                  // Change in holding amount over the past 30 days (in tokens)
      "holdings_amount_change_7d": 0,                   // Change in holding amount over the past 7 days (in tokens)
      "holdings_amount_change1d": 0,                    // Change in holding amount over the past 1 day (in tokens)
      "close_time": 1721422800000,                      // Market close timestamp (milliseconds)
      "update_time": 1745203812007                      // Data update timestamp (milliseconds)
    },
    {
      "symbol": "ETC",                                  // Token symbol, e.g., ETC = Ethereum Classic
      "primary_market_price": 11.99,                    // Price in the primary market
      "secondary_market_price": 6.63,                   // Price in the secondary market
      "premium_rate": -44.7,                            // Premium rate, currently at a significant discount
      "holdings_amount": 11181376.733556,               // Current holding amount (in tokens)
      "holdings_usd": 181440200.2554132,                // Total market value of holdings in USD
      "holdings_amount_change_30d": -20697.669828,      // Change in holding amount over the past 30 days
      "holdings_amount_change_7d": -4596.123672,        // Change in holding amount over the past 7 days
      "holdings_amount_change1d": 0,                    // Change in holding amount over the past 1 day
      "close_time": 1744923600000,                      // Market close timestamp
      "update_time": 1745203812168                      // Data update timestamp
    }
  ]
}
```

---
  
  
  ---
        
## API 2: Premium History


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
https://open-api-v4.coinglass.com//api/grayscale/premium-history
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

| Parameter | Type   | Required | Description                                                                    | Example value |
| --------- | ------ | -------- | ------------------------------------------------------------------------------ | ------------- |
| symbol    | string | yes      | Supported values: ETC, LTC, BCH, SOL, XLM, LINK, ZEC, MANA, ZEN, FIL, BAT, LPT | BTC           |


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/grayscale/premium-history?symbol=BTC' \
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
      "primary_market_price": [     // Primary market price list
        0.14,
        0.14
        // ...
      ],
      "date_list": [                // Date list (timestamps)
        1380171600000,
        1380258000000
        // ...
      ],
      "secondary_market_price_list": [  // Secondary market price list
        0.57,
        0.53
        // ...
      ],
      "premium_rate_list": [          // Premium rate list
        19.37,
        15.59
        // ...
      ]
    },
      ....
  ]
}
```

---
  