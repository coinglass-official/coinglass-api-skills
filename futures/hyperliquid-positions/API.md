---
name: hyperliquid-positions
description: Hyperliquid Positions request using the CoinGlass API. 
metadata:
  version: 1.0.0
  author: CoinGlass
  openclaw:
    requires:
      bins:
        - curl
        - openssl
    homepage: https://github.com/coinglass-official/coinglass-api-skills/tree/main/futures/hyperliquid-positions/API.md
license: MIT
---

# CoinGlass Hyperliquid Positions Skill

Hyperliquid Positions request on CoinGLass API endpoints. Return the result in JSON format.


## Quick Reference

| API                                       | Endpoint                                                 | Function                                                                                                                                                                                                                  |
| ----------------------------------------- | -------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Hyperliquid Whale Alert                   | /api/hyperliquid/whale-alert                             | This endpoint provides real-time whale alerts on Hyperliquid, highlighting positions with a notional value over $1 million.(Returns up to approximately 200 most recent records)                                          |
| Hyperliquid Whale Position                | /api/hyperliquid/whale-position                          | This endpoint provides whale positions on Hyperliquid with a notional value exceeding $1 million.                                                                                                                         |
| Hyperliquid Wallet Positions by Coin      | /api/hyperliquid/position                                | This endpoint provides real-time wallet position data by coin on Hyperliquid, including user addresses, position size, margin balance, and unrealized PnL for each account.                                               |
| Hyperliquid Wallet Positions by Address   | /api/hyperliquid/user-position                           | This endpoint provides Hyperliquid user position data, including margin summaries, withdrawable balance, and open asset positions.                                                                                        |
| Hyperliquid Wallet Positions Distribution | /api/hyperliquid/wallet/position-distribution            | This endpoint provides real-time Hyperliquid wallet position distribution data, grouped by position size tiers, including address counts, long/short position values, sentiment indicators, and profit/loss distribution. |
| Hyperliquid Wallet PNL Distribution       | /api/hyperliquid/wallet/pnl-distribution                 | This endpoint provides real-time Hyperliquid wallet PNL distribution data, grouped by PNL size tiers, including address counts, long/short position values, sentiment indicators, and profit/loss distribution.           |
| Hyperliquid Long/Short Ratio (Accounts)   | /api/hyperliquid/global-long-short-account-ratio/history | This endpoint provides the long/short account ratio history for symbols on Hyperliquid.                                                                                                                                   |

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
        
## API 1: Hyperliquid Whale Alert


**Supported Plans, Intervals, and Historical Data Access**

Hobbyist:Not Available
Startup:Available
Standard:Available
Professional:Available


### Method: GET

**URL**:
```
https://open-api-v4.coinglass.com//api/hyperliquid/whale-alert
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

*No parameters required*


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/hyperliquid/whale-alert' \
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
      "user": "0x3fd4444154242720c0d0c61c74a240d90c127d33", // User address
      "symbol": "ETH",                                     // Symbol
      "position_size": 12700,                              // Position size (positive: long, negative: short)
      "entry_price": 1611.62,                              // Entry price
      "liq_price": 527.2521,                               // Liquidation price
      "position_value_usd": 21003260,                      // Position value (USD)
      "position_action": 2,                                // Position action type (1: open, 2: close)
      "create_time": 1745219517000                         // Entry time (timestamp in milliseconds)
    },
    {
      "user": "0x1cadadf0e884ac5527ae596a4fc1017a4ffd4e2c",
      "symbol": "BTC",
      "position_size": 33.54032,
      "entry_price": 87486.2,
      "liq_price": 44836.8126,
      "position_value_usd": 2936421.4757,
      "position_action": 2,
      "create_time": 1745219477000
    }
  ]
}
```

---
  
  
  ---
        
## API 2: Hyperliquid Whale Position


**Supported Plans, Intervals, and Historical Data Access**

Hobbyist:Not Available
Startup:Available
Standard:Available
Professional:Available


### Method: GET

**URL**:
```
https://open-api-v4.coinglass.com//api/hyperliquid/whale-position
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

*No parameters required*


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/hyperliquid/whale-position' \
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
      "user": "0x20c2d95a3dfdca9e9ad12794d5fa6fad99da44f5", // User address
      "symbol": "ETH",                                   // Token symbol
      "position_size": -44727.1273,                      // Position size (positive: long, negative: short)
      "entry_price": 2249.7,                             // Entry price
      "mark_price": 1645.8,                              // Current mark price
      "liq_price": 2358.2766,                            // Liquidation price
      "leverage": 25,                                    // Leverage
      "margin_balance": 2943581.7019,                    // Margin balance (USD)
      "position_value_usd": 73589542.5467,               // Position value (USD)
      "unrealized_pnl": 27033236.424,                    // Unrealized PnL (USD)
      "funding_fee": -3107520.7373,                      // Funding fee (USD)
      "margin_mode": "cross",                            // Margin mode (e.g., cross / isolated)
      "create_time": 1741680802000,                      // Entry time (timestamp in ms)
      "update_time": 1745219966000                       // Last updated time (timestamp in ms)
    },
    {
      "user": "0xf967239debef10dbc78e9bbbb2d8a16b72a614eb",
      "symbol": "BTC",
      "position_size": -800,
      "entry_price": 84931.3,
      "mark_price": 87427,
      "liq_price": 92263.798,
      "leverage": 15,
      "margin_balance": 4812076.3896,
      "position_value_usd": 69921600,
      "unrealized_pnl": -1976493.6819,
      "funding_fee": 14390.0346,
      "margin_mode": "isolated",
      "create_time": 1743982804000,
      "update_time": 1745219969000
    }
  ]
}
```

---
  
  
  ---
        
## API 3: Hyperliquid Wallet Positions by Coin


**Supported Plans, Intervals, and Historical Data Access**

Hobbyist:Not Available
Startup:Not Available
Standard:Available
Professional:Available


### Method: GET

**URL**:
```
https://open-api-v4.coinglass.com//api/hyperliquid/position
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

| Parameter    | Type   | Required | Description                                                                       | Example value |
| ------------ | ------ | -------- | --------------------------------------------------------------------------------- | ------------- |
| symbol       | string | yes      | Trading coin (e.g., BTC). Retrieve supported coins via the 'supported-coins' API. | BTC           |
| current_page | string | no       | Current page number being returned                                                | 1             |


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/hyperliquid/position?symbol=BTC' \
-H 'Content-Type: application/json' \
-H 'CG-API-KEY: ${YOUR_API_KEY}' \
-H 'User-Agent: coinglass-skill/1.0.0'
```
        
**Response**:
```json
{
  "code": "0",                     // Status code (0 = success)
  "data": {
    "total_pages": 10,          // Total pages of position data
    "current_page":1,   // Current page number being returned
    "list": [
      {
        "user": "0x5b5d51203a0f9079f8aeb098a6523a13f298c060",           //User Wallet address
        "symbol": "BTC",           // Symbol
        "position_size": -2683.14, // Position size (positive = long, negative = short)
        "entry_price": 111459.6,   // Entry price
        "mark_price": 116638,      // Current price
        "liq_price": 150629.52,    // Liquidation price
        "leverage": 10,            // Leverage
        "margin_balance": 31263482.07,        // Margin balance (USD)
        "position_value_usd": 312634820.77,   // Position value (USD)
        "unrealized_pnl": -13572345.06,       // Unrealized profit/loss (USD)
        "funding_fee": -12534553.66,          // Funding fee (USD)
        "margin_mode": "cross",               // Margin mode ("cross" or "isolated")
        "create_time": 1752152867098,         // Open time (timestamp)
        "update_time": 1758162698266          // Last update (timestamp)
      }
    ]
  }
}
```

---
  
  
  ---
        
## API 4: Hyperliquid Wallet Positions by Address


**Supported Plans, Intervals, and Historical Data Access**

Hobbyist:Not Available
Startup:Available
Standard:Available
Professional:Available


### Method: GET

**URL**:
```
https://open-api-v4.coinglass.com//api/hyperliquid/user-position
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

| Parameter    | Type   | Required | Description  | Example value |
| ------------ | ------ | -------- | ------------ | ------------- |
| user_address | string | yes      | User Address |               |


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/hyperliquid/user-position?user_address=' \
-H 'Content-Type: application/json' \
-H 'CG-API-KEY: ${YOUR_API_KEY}' \
-H 'User-Agent: coinglass-skill/1.0.0'
```
        
**Response**:
```json
{
  "code": "0",
  "data": {
    "margin_summary": {
      "account_value": 179250588.896754,
      "total_ntl_pos": 679947383.29435,
      "total_raw_usd": -500696794.397596,
      "total_margin_used": 131236726.65887
    },
    "cross_margin_summary": {
      "account_value": 179250588.896754,
      "total_ntl_pos": 679947383.29435,
      "total_raw_usd": -500696794.397596,
      "total_margin_used": 131236726.65887
    },
    "cross_maintenance_margin_used": 19278725.276478,
    "withdrawable": 46429612.237884,
    "asset_positions": [
      {
        "type": "oneWay",
        "position": {
          "coin": "BTC",
          "szi": 1000,
          "leverage": {
            "type": "cross",
            "value": 5
          },
          "entry_px": 91506.7,
          "position_value": 86265000,
          "unrealized_pnl": -5643767.29312,
          "return_on_equity": -0.3083797767,
          "max_leverage": 5,
          "cum_funding": {
            "all_time": -104732.177706,
            "since_open": 87958.233078,
            "since_change": 84811.539668
          }
        }
      },
      }
    ]
  }
}
```

---
  
  
  ---
        
## API 5: Hyperliquid Wallet Positions Distribution


**Supported Plans, Intervals, and Historical Data Access**

Hobbyist:Not Available
Startup:Not Available
Standard:Available
Professional:Available


### Method: GET

**URL**:
```
https://open-api-v4.coinglass.com//api/hyperliquid/wallet/position-distribution
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

*No parameters required*


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/hyperliquid/wallet/position-distribution' \
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
    "group_name": "Shrimp", // position tier label
    // shrimp | fish | dolphin | apex_predator | small_whale | whale | tidal_whale | leviathan

    "all_address_count": 260180, // total addresses
    "position_address_count": 20966, // addresses with positions
    "position_address_percent": 8.06, // position address %

    "bias_score": 0.99, // long/short bias score

    "bias_remark": "very_bullish", // sentiment label
    // bearish | slightly_bearish | indecisive | bullish | very_bullish

    "minimum_amount": 0, // min position range
    "maximum_amount": 250, // max position range

    "long_position_usd": 6270051.698175, // long position value
    "short_position_usd": 2382603.196539, // short position value
    "long_position_usd_percent": 72.46, // long value %
    "short_position_usd_percent": 27.54, // short value %

    "position_usd": 8652654.894714, // total position value

    "profit_address_count": 6680, // profitable addresses
    "loss_address_count": 14276, // losing addresses
    "profit_address_percent": 31.88, // profit %
    "loss_address_percent": 68.12 // loss %
   }
  ]
}
```

---
  
  
  ---
        
## API 6: Hyperliquid Wallet PNL Distribution


**Supported Plans, Intervals, and Historical Data Access**

Hobbyist:Not Available
Startup:Not Available
Standard:Available
Professional:Available


### Method: GET

**URL**:
```
https://open-api-v4.coinglass.com//api/hyperliquid/wallet/pnl-distribution
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

*No parameters required*


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/hyperliquid/wallet/pnl-distribution' \
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
    "group_name": "Money_Printer", // PnL tier label
    // money_printer | smart_money | grinder | humble_earner
    // exit_liquidity | semi_rekt | full_rekt | giga_rekt

    "all_address_count": 518, // total addresses
    "position_address_count": 286, // addresses with positions
    "position_address_percent": 55.22, // position address %

    "bias_score": -0.42, // long/short bias score

    "bias_remark": "bearish", // sentiment label
    // bearish | slightly_bearish | indecisive | bullish | very_bullish

    "minimum_amount": 100000, // min PnL range
    "maximum_amount": 1000000, // max PnL range

    "long_position_usd": 1624390818.866083999, // long position value
    "short_position_usd": 2374121810.5067759868, // short position value
    "long_position_usd_percent": 40.62, // long value %
    "short_position_usd_percent": 59.38, // short value %

    "position_usd": 3998512629.3728599858, // total position value

    "profit_address_count": 211, // profitable addresses
    "loss_address_count": 75, // losing addresses
    "profit_address_percent": 73.78, // profit %
    "loss_address_percent": 26.22 // loss %
    }
  ]

}
```

---
  
  
  ---
        
## API 7: Hyperliquid Long/Short Ratio (Accounts)


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
https://open-api-v4.coinglass.com//api/hyperliquid/global-long-short-account-ratio/history
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

| Parameter  | Type    | Required | Description                                                                                                                                          | Example value |
| ---------- | ------- | -------- | ---------------------------------------------------------------------------------------------------------------------------------------------------- | ------------- |
| symbol     | string  | yes      | Trading coin (e.g., BTC).  Retrieve supported coins via the 'supported-coins' API. If not provided, data for all supported symbols will be returned. | BTC           |
| interval   | string  | yes      | Time interval for data aggregation.  Supported values: 5m, 1h,1d                                                                                     | 1d            |
| limit      | integer | no       | Number of results per request.  Default: 1000, Maximum: 1000                                                                                         |               |
| start_time | integer | no       | Start timestamp in milliseconds (e.g., 1641522717000).                                                                                               |               |
| end_time   | integer | no       | End timestamp in milliseconds (e.g., 1641522717000).                                                                                                 |               |


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/hyperliquid/global-long-short-account-ratio/history?symbol=BTC&interval=1d' \
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
      "time": 1751414400000,// Timestamp (in milliseconds)
      "global_account_long_count": 5347,// Long account count
      "global_account_short_count": 3766,// Short account count
      "global_account_total_count": 9113,// Total account count
      "global_account_long_percent": 58.67,// Long percentage (%)
      "global_account_short_percent": 41.33,// Short percentage (%)
      "global_account_long_short_ratio": 1.4195// Long/Short ratio
    },
    {
      "time": 1751500800000,
      "global_account_long_count": 4644,
      "global_account_short_count": 4719,
      "global_account_total_count": 9363,
      "global_account_long_percent": 49.6,
      "global_account_short_percent": 50.4,
      "global_account_long_short_ratio": 0.9841
    },
    {
   ]
}
```

---
  