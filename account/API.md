---
name: account-level-query
description: Account Level Query request using the CoinGlass API. 
metadata:
  version: 1.0.0
  author: CoinGlass
  openclaw:
    requires:
      bins:
        - curl
        - openssl
    homepage: https://github.com/coinglass-official/coinglass-api-skills/tree/main/account/API.md
license: MIT
---

# CoinGlass Account Level Query Skill

Account Level Query request on CoinGLass API endpoints. Return the result in JSON format.


## Quick Reference

| API                 | Endpoint                       | Function                                                                                                                                 |
| ------------------- | ------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------- |
| Account Level Query | /api/user/account/subscription | This endpoint retrieves the user's account subscription details, including the current API tier, expiration time, and expiration status. |

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
        
## API 1: Account Level Query


**Supported Plans, Intervals, and Historical Data Access**

Hobbyist:Limited
Startup:Limited
Standard:Limited
Professional:Limited


### Method: GET

**URL**:
```
https://open-api-v4.coinglass.com//api/user/account/subscription
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

*No parameters required*


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/user/account/subscription' \
-H 'Content-Type: application/json' \
-H 'CG-API-KEY: ${YOUR_API_KEY}' \
-H 'User-Agent: coinglass-skill/1.0.0'
```
        
**Response**:
```json
{"code":"0","data":{"level":"PROFESSIONAL","expire_time":1805943491000,"expired":false}}
```

---
  