---
name: solana-etf
description: Solana ETF request using the CoinGlass API. 
metadata:
  version: 1.0.0
  author: CoinGlass
  openclaw:
    requires:
      bins:
        - curl
        - openssl
    homepage: https://github.com/coinglass-official/coinglass-api-skills/tree/main/etf/solana-etf/API.md
license: MIT
---

# CoinGlass Solana ETF Skill

Solana ETF request on CoinGLass API endpoints. Return the result in JSON format.


## Quick Reference

| API               | Endpoint                     | Function                                                                                    |
| ----------------- | ---------------------------- | ------------------------------------------------------------------------------------------- |
| ETF Flows History | /api/etf/solana/flow-history | This endpoint provides a list of key status information regarding the history of ETF flows. |

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
        
## API 1: ETF Flows History


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
https://open-api-v4.coinglass.com//api/etf/solana/flow-history
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

*No parameters required*


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/etf/solana/flow-history' \
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
      "timestamp": 1762473600000,
      "flow_usd": 12700000,
      "price_usd": 155.2,
      "etf_flows": [
        {
          "etf_ticker": "BSOL",
          "flow_usd": 11700000
        },
        {
          "etf_ticker": "VSOL"
        },
        {
          "etf_ticker": "FSOL"
        },
        {
          "etf_ticker": "TSOL"
        },
        {
          "etf_ticker": "GSOL",
          "flow_usd": 1000000
        }
      ]
    },
  ]
}
```

---
  