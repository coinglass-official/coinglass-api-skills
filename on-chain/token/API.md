---
name: token
description: Token request using the CoinGlass API. 
metadata:
  version: 1.0.0
  author: CoinGlass
  openclaw:
    requires:
      bins:
        - curl
        - openssl
    homepage: https://github.com/coinglass-official/coinglass-api-skills/tree/main/on-chain/token/API.md
license: MIT
---

# CoinGlass Token Skill

Token request on CoinGLass API endpoints. Return the result in JSON format.


## Quick Reference

| API               | Endpoint              | Function                                                                                        |
| ----------------- | --------------------- | ----------------------------------------------------------------------------------------------- |
| Token Unlock List | /api/coin/unlock-list | This endpoint returns token unlock data and upcoming unlock schedules.                          |
| Token Vesting     | /api/coin/vesting     | This endpoint returns detailed vesting data and upcoming unlock schedules for a specific token. |

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
        
## API 1: Token Unlock List


**Supported Plans, Intervals, and Historical Data Access**

Hobbyist:Not Available
Startup:Available
Standard:Available
Professional:Available


### Method: GET

**URL**:
```
https://open-api-v4.coinglass.com//api/coin/unlock-list
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

| Parameter | Type    | Required | Description                             | Example value |
| --------- | ------- | -------- | --------------------------------------- | ------------- |
| per_page  | integer | no       | Number of results per page.             |               |
| page      | integer | no       | Page number for pagination, default: 1. |               |


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/coin/unlock-list' \
-H 'Content-Type: application/json' \
-H 'CG-API-KEY: ${YOUR_API_KEY}' \
-H 'User-Agent: coinglass-skill/1.0.0'
```
        
**Response**:
```json
{
  "code": "0", // response code
  "data": [ // token list
    {
      "symbol": "GT", // token symbol
      "name": "GateToken", // token name
      "symbol_logo_url": "https://cdn.coinglasscdn.com/static/img/coins/gt.jpg", // logo url
      "price": 10.377, // last price
      "price_change_percent_24h": 2.67, // 24h change %
      "market_cap": 1217683606.698, // market cap
      "total_supply": 300000000, // total supply
      "fully_diluted_valuation": 3115642754.097, // FDV
      "total_locked": 74868300, // locked tokens
      "circulating_supply": 117344474, // circulating supply
      "total_unlocked": 162691500, // unlocked tokens
      "next_unlock_date": 1765152000000, // next unlock time
      "next_unlock_tokens": 48600, // next unlock amount
      "next_unlock_of_circulating": 0.041416522093745974, // % of circulating
      "next_unlock_of_supply": 0.0162 // % of total supply
    },
    ....
  ]
}
```

---
  
  
  ---
        
## API 2: Token Vesting


**Supported Plans, Intervals, and Historical Data Access**

Hobbyist:Not Available
Startup:Available
Standard:Available
Professional:Available


### Method: GET

**URL**:
```
https://open-api-v4.coinglass.com//api/coin/vesting
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

| Parameter | Type   | Required | Description                                                                          | Example value |
| --------- | ------ | -------- | ------------------------------------------------------------------------------------ | ------------- |
| symbol    | string | yes      | Trading coin (e.g., HYPE). Retrieve supported coins via the 'token-unlock-list' API. | HYPE          |


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/coin/vesting?symbol=HYPE' \
-H 'Content-Type: application/json' \
-H 'CG-API-KEY: ${YOUR_API_KEY}' \
-H 'User-Agent: coinglass-skill/1.0.0'
```
        
**Response**:
```json
{
  "code": "0",
  "data": {
 {
  "market_cap": 9366969675.066894, // market cap
  "symbol": "HYPE", // token symbol
  "total_untracked": 451880000, // untracked supply
  "listing_date": 1732838400000, // listing time
  "vesting_start_date": 1732838400000, // vesting start
  "total_supply": 999835210, // total supply
  "total_locked": 236721940, // total locked
  "total_unlocked": 310986320, // total unlocked
  "vesting_end_date": 1859068800000, // vesting end
  "next_unlock": { // next unlock info
    "date": 1764720000000, // unlock time
    "next_unlock_token_amount": "216580" // unlock amount
  },
  "circulating_supply": 270772999, // circulating supply
  "total_untracked_percent": 45.188, // untracked percent
  "allocations": [ // allocation list
    {
      "is_untracked": true, // untracked flag
      "allocation_of_supply": 38.888, // supply percent
      "name": "Future Emissions & Community Rewards", // allocation name
      "token_amount": "388880000" // token amount
    },
    {
      "is_untracked": false, // untracked flag
      "allocation_of_supply": 31, // supply percent
      "name": "Genesis Distribution", // allocation name
      "unlock_type": "nonlinear", // unlock type
      "token_amount": "310000000", // token amount
      "tge_unlocked_token_amount": "310000000", // TGE unlocked
      "unlocked_token_amount": "310000000", // total unlocked
      "tge_unlock_percent": 100 // TGE percent
    },
    {
      "is_untracked": false, // untracked flag
      "vesting_start_date": 1764374400000, // vesting start
      "locked_token_amount": "236721940", // locked amount
      "vesting_end_date": 1859068800000, // vesting end
      "tge_unlocked_token_amount": "0", // TGE unlocked
      "next_unlock": { // next unlock info
        "date": 1764720000000, // unlock time
        "next_unlock_token_amount": "216580" // unlock amount
      },
      "unlocked_token_amount": "866320", // unlocked amount
      "tge_unlock_percent": 0, // TGE percent
      "vesting_duration_value": 3, // duration value
      "vesting_duration_type": "year", // duration type
      "allocation_of_supply": 23.8, // supply percent
      "unlock_frequency_type": "day", // unlock unit
      "name": "Core Contributors", // allocation name
      "unlock_type": "linear", // unlock type
      "token_amount": "238000000", // token amount
      "unlock_frequency_value": 1 // unlock interval
    },
    {
      "is_untracked": true, // untracked flag
      "allocation_of_supply": 6, // supply percent
      "name": "Hyper Foundation", // allocation name
      "token_amount": "60000000" // token amount
    },
    {
      "is_untracked": true, // untracked flag
      "allocation_of_supply": 0.3, // supply percent
      "name": "Community Grants", // allocation name
      "token_amount": "3000000" // token amount
    },
    {
      "is_untracked": false, // untracked flag
      "allocation_of_supply": 0.012, // supply percent
      "name": "HIP-2", // allocation name
      "unlock_type": "nonlinear", // unlock type
      "token_amount": "120000", // token amount
      "tge_unlocked_token_amount": "120000", // TGE unlocked
      "unlocked_token_amount": "120000", // total unlocked
      "tge_unlock_percent": 100 // TGE percent
    }
  ],
  "fully_diluted_valuation": 34587740013.671524, // FDV
  "name": "Hyperliquid", // project name
  "max_supply": 1000000000, // max supply
  "chart": [ // chart data
    {
      "date": 1732838400000, // chart time
      "allocations": [ // chart allocations
        {
          "name": "Genesis Distribution", // name
          "unlocked_percent": 31, // unlocked percent
          "token_amount": "310000000", // token amount
          "unlocked_token_amount": "310000000" // unlocked amount
        },
        {
          "name": "Core Contributors", // name
          "unlocked_percent": 0, // unlocked percent
          "token_amount": "238000000", // token amount
          "unlocked_token_amount": "0" // unlocked amount
        },
        {
          "name": "HIP-2", // name
          "unlocked_percent": 0.012, // unlocked percent
          "token_amount": "120000", // token amount
          "unlocked_token_amount": "120000" // unlocked amount
        }
      ],
      "is_tge": true, // is TGE flag
      "unlocked_percent": 31.012, // total percent
      "unlocked_token_amount": "310120000" // total unlocked
    }
    ],
    "untracked_allocation_names": [
      "Community Grants",
      "Future Emissions & Community Rewards",
      "Hyper Foundation"
    ]
  }
}
```

---
  