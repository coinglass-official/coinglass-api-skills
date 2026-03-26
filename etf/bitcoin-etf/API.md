---
name: bitcoin-etf
description: Bitcoin ETF request using the CoinGlass API. 
metadata:
  version: 1.0.0
  author: CoinGlass
  openclaw:
    requires:
      bins:
        - curl
        - openssl
    homepage: https://github.com/coinglass-official/coinglass-api-skills/tree/main/etf/bitcoin-etf/API.md
license: MIT
---

# CoinGlass Bitcoin ETF Skill

Bitcoin ETF request on CoinGLass API endpoints. Return the result in JSON format.


## Quick Reference

| API                          | Endpoint                                  | Function                                                                                                                                                                                                                                     |
| ---------------------------- | ----------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Bitcoin ETF List             | /api/etf/bitcoin/list                     | This endpoint provides a list of key status information for Bitcoin Exchange-Traded Funds (ETFs).                                                                                                                                            |
| Hong Kong ETF Flows History  | /api/hk-etf/bitcoin/flow-history          | This endpoint provides historical data on ETF flow activity for Bitcoin ETFs in the Hong Kong market.                                                                                                                                        |
| ETF NetAssets History        | /api/etf/bitcoin/net-assets/history       | This endpoint provides historical data on the net assets of Bitcoin Exchange-Traded Funds (ETFs).                                                                                                                                            |
| ETF Flows History            | /api/etf/bitcoin/flow-history             | This endpoint provides historical flow data for Bitcoin Exchange-Traded Funds (ETFs), including daily net inflows and outflows in USD, closing prices, and flow breakdowns by individual ETF tickers.                                        |
| ETF Premium/Discount History | /api/etf/bitcoin/premium-discount/history | This endpoint provides historical data on the premium or discount rates of Bitcoin Exchange-Traded Funds (ETFs), including Net Asset Value (NAV), market price, and premium/discount percentages for each ETF ticker.                        |
| ETF History                  | /api/etf/bitcoin/history                  | This endpoint provides historical data for Bitcoin Exchange-Traded Funds (ETFs), including key information such as market price, Net Asset Value (NAV), premium/discount percentage, shares outstanding, and net assets for each ETF ticker. |
| ETF Price History            | /api/etf/bitcoin/price/history            | This endpoint provides historical price data for Bitcoin Exchange-Traded Funds (ETFs), including open, high, low, and close (OHLC) prices, along with trading volume for each data point.                                                    |
| ETF Detail                   | /api/etf/bitcoin/detail                   | This endpoint provides detailed information on a Bitcoin Exchange-Traded Fund (ETF), including its key attributes and status.                                                                                                                |
| ETF AUM                      | /api/etf/bitcoin/aum                      | This endpoint provides historical Assets Under Management (AUM) data for Bitcoin ETFs                                                                                                                                                        |

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
        
## API 1: Bitcoin ETF List


**Supported Plans, Intervals, and Historical Data Access**

Hobbyist:Available
Startup:Available
Standard:Available
Professional:Available


### Method: GET

**URL**:
```
https://open-api-v4.coinglass.com//api/etf/bitcoin/list
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

*No parameters required*


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/etf/bitcoin/list' \
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
      "ticker": "GBTC",                                // ETF identifier
      "fund_name": "Grayscale Bitcoin Trust ETF",      // Fund name
      "region": "us",                                  // Region
      "market_status": "early_trading",                // Market status (open/closed/early_trading, etc.)
      "primary_exchange": "ARCX",                      // Primary exchange
      "cik_code": "0001588489",                        // CIK code (unique identifier)
      "fund_type": "Spot",                             // Fund type (Spot/ETF/Futures, etc.)
      "list_date": 1424822400000,                      // Listing date (timestamp in milliseconds)
      "shares_outstanding": "240750100",               // Shares outstanding
      "aum_usd": "16137543152.34",                     // Assets under management (USD)
      "management_fee_percent": "1.5",                 // Management fee (%)
      "last_trade_time": 1745225312958,                // Last trade time (timestamp in milliseconds)
      "last_quote_time": 1745225389483,                // Last quote time (timestamp in milliseconds)
      "volume_quantity": 1068092,                      // Volume quantity
      "volume_usd": 71485902.2312,                     // Volume in USD
      "price_change_usd": 0.47,                        // Price change (USD)
      "price_change_percent": 0.71,                    // Price change (%)
      "asset_details": {
        "net_asset_value_usd": 67.03,                  // Net asset value (USD)
        "premium_discount_percent": 0.09,              // Premium/discount rate (%)
        "btc_holding": 190124.5441,                    // BTC balance
        "btc_change_percent_24h": 0,                   // 24h BTC change (%)
        "btc_change_24h": -7.8136,                     // 24h BTC change amount
        "btc_change_percent_7d": -0.32,                // 7d BTC change (%)
        "btc_change_7d": -615.563,                     // 7d BTC change amount
        "update_date": "2025-04-17"                    // Update date
      },
      "update_timestamp": 1745224505000                // Data update timestamp (milliseconds)
    }
  ]
}
```

---
  
  
  ---
        
## API 2: Hong Kong ETF Flows History


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
https://open-api-v4.coinglass.com//api/hk-etf/bitcoin/flow-history
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

*No parameters required*


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/hk-etf/bitcoin/flow-history' \
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
      "timestamp": 1714435200000,                     // Date (timestamp in milliseconds)
      "flow_usd": 247866000,                          // Total capital inflow (USD)
      "price_usd": 63842.4,                           // BTC price on that date (USD)
      "etf_flows": [                                  // ETF capital flow details
        {
          "etf_ticker": "CHINAAMC",                   // ETF ticker
          "flow_usd": 123610690                       // Capital inflow for this ETF (USD)
        },
        {
          "etf_ticker": "HARVEST",                    // ETF ticker
          "flow_usd": 63138000                        // Capital inflow for this ETF (USD)
        },
        {
          "etf_ticker": "BOSERA&HASHKEY",             // ETF ticker
          "flow_usd": 61117310                        // Capital inflow for this ETF (USD)
        }
      ]
    }
  ]
}
```

---
  
  
  ---
        
## API 3: ETF NetAssets History


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
https://open-api-v4.coinglass.com//api/etf/bitcoin/net-assets/history
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

| Parameter | Type   | Required | Description                           | Example value |
| --------- | ------ | -------- | ------------------------------------- | ------------- |
| ticker    | string | no       | ETF ticker symbol (e.g., GBTC, IBIT). |               |


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/etf/bitcoin/net-assets/history' \
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
      "price_usd": 46337.8                      // BTC price on that date (USD)
    },
    {
      "net_assets_usd": 51874409241.39,         // Net asset value (USD)
      "change_usd": 203000000,                  // Daily capital change (USD)
      "timestamp": 1705017600000,               // Date (timestamp in milliseconds)
      "price_usd": 42788.9                      // BTC price on that date (USD)
    }
  ]
}
```

---
  
  
  ---
        
## API 4: ETF Flows History


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
https://open-api-v4.coinglass.com//api/etf/bitcoin/flow-history
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

*No parameters required*


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/etf/bitcoin/flow-history' \
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
      "timestamp": 1704931200000,                   // Date (timestamp in milliseconds)
      "flow_usd": 655300000,                         // Total daily capital flow (USD)
      "price_usd": 46663,                            // BTC current price (USD)
      "etf_flows": [                                 // ETF capital flow breakdown
        {
          "etf_ticker": "GBTC",                      // ETF ticker
          "flow_usd": -95100000                      // Capital outflow (USD)
        },
        {
          "etf_ticker": "IBIT",                      // ETF ticker
          "flow_usd": 111700000                      // Capital inflow (USD)
        },
        {
          "etf_ticker": "FBTC",                      // ETF ticker
          "flow_usd": 227000000                      // Capital inflow (USD)
        }
      ]
    }
  ]
}
```

---
  
  
  ---
        
## API 5: ETF Premium/Discount History


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
https://open-api-v4.coinglass.com//api/etf/bitcoin/premium-discount/history
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

| Parameter | Type   | Required | Description                           | Example value |
| --------- | ------ | -------- | ------------------------------------- | ------------- |
| ticker    | string | no       | ETF ticker symbol (e.g., GBTC, IBIT). |               |


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/etf/bitcoin/premium-discount/history' \
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
      "timestamp": 1706227200000,                 // Date (timestamp in milliseconds)
      "list": [
        {
          "ticker": "GBTC",                       // ETF ticker
          "nav_usd": 37.51,                        // Net Asset Value (USD)
          "market_price_usd": 37.51,               // Market price (USD)
          "premium_discount_details": 0            // Premium/Discount percentage
        },
        {
          "ticker": "IBIT",                       // ETF ticker
          "nav_usd": 23.94,                        // Net Asset Value (USD)
          "market_price_usd": 23.99,               // Market price (USD)
          "premium_discount_details": 0.22         // Premium/Discount percentage
        },
        {
          "ticker": "FBTC",                       // ETF ticker
          "nav_usd": 36.720807,                    // Net Asset Value (USD)
          "market_price_usd": 36.75,               // Market price (USD)
          "premium_discount_details": 0.0795       // Premium/Discount percentage
        }
      ]
    }
  ]
}
```

---
  
  
  ---
        
## API 6: ETF History


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
https://open-api-v4.coinglass.com//api/etf/bitcoin/history
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

| Parameter | Type   | Required | Description                           | Example value |
| --------- | ------ | -------- | ------------------------------------- | ------------- |
| ticker    | string | yes      | ETF ticker symbol (e.g., GBTC, IBIT). | GBTC          |


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/etf/bitcoin/history?ticker=GBTC' \
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
      "assets_date": 1706486400000,           // Net asset date (timestamp in milliseconds)
      "btc_holdings": 496573.8166,            // BTC holdings
      "market_date": 1706486400000,           // Market price date (timestamp in milliseconds)
      "market_price": 38.51,                  // Market price (USD)
      "name": "Grayscale Bitcoin Trust",      // ETF name
      "nav": 38.57,                           // Net Asset Value per share (USD)
      "net_assets": 21431132778.35,           // Total net assets (USD)
      "premium_discount": -0.16,              // Premium/discount percentage
      "shares_outstanding": 555700100,        // Total shares outstanding
      "ticker": "GBTC"                        // ETF ticker
    }
  ]
}
```

---
  
  
  ---
        
## API 7: ETF Price History


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
https://open-api-v4.coinglass.com//api/etf/bitcoin/price/history
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

| Parameter | Type   | Required | Description                                | Example value |
| --------- | ------ | -------- | ------------------------------------------ | ------------- |
| ticker    | string | yes      | ETF ticker symbol (e.g., GBTC, IBIT).      | GBTC          |
| range     | string | yes      | Time range for the data (e.g., 1d,7d,all). | 1d            |


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/etf/bitcoin/price/history?ticker=GBTC&range=1d' \
-H 'Content-Type: application/json' \
-H 'CG-API-KEY: ${YOUR_API_KEY}' \
-H 'User-Agent: coinglass-skill/1.0.0'
```
        
**Response**:
```json
{
  "code": "0",
  "message": "success",
  "data": [
    {
      "time": 1731056460000,   // timestamp in milliseconds
      "open": 60.47,                // Opening price
      "high": 60.47,                // Highest price
      "low": 60.47,                 // Lowest price
      "close": 60.47,               // Closing price
      "volume": 100                // Trading volume
    },
    ...
  ]
}
```

---
  
  
  ---
        
## API 8: ETF Detail


**Supported Plans, Intervals, and Historical Data Access**

Hobbyist:Available
Startup:Available
Standard:Available
Professional:Available


### Method: GET

**URL**:
```
https://open-api-v4.coinglass.com//api/etf/bitcoin/detail
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

| Parameter | Type   | Required | Description                           | Example value |
| --------- | ------ | -------- | ------------------------------------- | ------------- |
| ticker    | string | yes      | ETF ticker symbol (e.g., GBTC, IBIT). | GBTC          |


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/etf/bitcoin/detail?ticker=GBTC' \
-H 'Content-Type: application/json' \
-H 'CG-API-KEY: ${YOUR_API_KEY}' \
-H 'User-Agent: coinglass-skill/1.0.0'
```
        
**Response**:
```json
{
  "code": "0",
  "msg": "success",
  "data": {
    "ticker_info": {
      "id": 1,                                         // ETF ID
      "ticker": "GBTC",                                // ETF ticker symbol
      "name": "Grayscale Bitcoin Trust ETF",           // ETF name
      "market": "stocks",                              // Market type
      "region": "us",                                  // Region
      "primary_exchange": "ARCX",                      // Primary exchange
      "fund_type": "ETV",                              // Fund type
      "active": "true",                                // Whether the ETF is active
      "currency_name": "usd",                          // Currency name
      "cik_code": "0001588489",                        // CIK code
      "composite_figi": "BBG008748J88",                // Composite FIGI
      "share_class_figi": "BBG008748J97",              // Share class FIGI
      "phone_number": "212-668-1427",                  // Contact phone number
      "tag": "BTC",                                    // Asset tag
      "type2": "Spot",                                 // Additional product type
      "address": {
        "address_1": "{\"address2\":\"4TH FLOOR\",\"city\":\"STAMFORD\",\"address1\":\"290 HARBOR DRIVE\",\"state\":\"CT\",\"postal_code\":\"06902\"}"
      },                                               // Company address (as a JSON string)
      "sic_code": "6221",                              // SIC code
      "sic_description": "COMMODITY CONTRACTS BROKERS & DEALERS", // Industry description
      "ticker_root": "GBTC",                           // Ticker root
      "list_date": 1424822400000,                      // Listing date (timestamp in ms)
      "share_class_shares_outstanding": "240750100",   // Shares outstanding
      "round_lot": "100",                              // Round lot size
      "status": 1,                                     // Status
      "update_time": 1745224505000                     // Last update time (timestamp in ms)
    },
    "market_status": "early_trading",                  // Market status
    "name": "Grayscale Bitcoin Trust ETF",             // ETF name
    "ticker": "GBTC",                                  // ETF ticker
    "type": "stocks",                                  // Market type
    "session": {
      "change": 2.22,                                  // Price change
      "change_percent": 3.309,                         // Change percentage (%)
      "early_trading_change": 2.22,                    // Pre-market change
      "early_trading_change_percent": 3.309,           // Pre-market change percentage (%)
      "close": 67.09,                                  // Previous closing price
      "high": 67.56,                                   // Highest price
      "low": 66.15,                                    // Lowest price
      "open": 66.86,                                   // Opening price
      "volume": 1068092,                               // Trading volume
      "previous_close": 67.09,                         // Previous close
      "price": 69.31                                   // Latest price
    },
    "last_quote": {
      "last_updated": 1745226801708029700,             // Last update time (timestamp in nanoseconds)
      "timeframe": "REAL-TIME",                        // Timeframe type
      "ask": 69.29,                                    // Ask price
      "ask_size": 34,                                  // Ask size
      "ask_exchange": 8,                               // Ask exchange code
      "bid": 69.18,                                    // Bid price
      "bid_size": 3,                                   // Bid size
      "bid_exchange": 11                               // Bid exchange code
    },
    "last_trade": {
      "last_updated": 1745226730467043600,             // Last trade update time (timestamp in nanoseconds)
      "timeframe": "REAL-TIME",                        // Timeframe type
      "id": "62879131651684",                          // Trade ID
      "price": 69.31,                                  // Trade price
      "size": 30,                                      // Trade volume
      "exchange": 12,                                  // Exchange code
      "conditions": [12, 37]                           // Trade condition codes
    },
    "performance": {
      "low_price_52week": 39.56,                       // 52-week low
      "high_price_52week": 86.11,                      // 52-week high
      "high_price_52week_date": 1734238800000,         // 52-week high date (timestamp)
      "low_price_52week_date": 1722744000000,          // 52-week low date (timestamp)
      "ydt_change_percent": -12.23,                    // Year-to-date change (%)
      "year_change_percent": 13.98,                    // 1-year change (%)
      "avg_vol_usd_10d": 518227                        // 10-day average trading value (USD)
    }
  }
}
```

---
  
  
  ---
        
## API 9: ETF AUM


**Supported Plans, Intervals, and Historical Data Access**

Hobbyist:Available
Startup:Available
Standard:Available
Professional:Available


### Method: GET

**URL**:
```
https://open-api-v4.coinglass.com//api/etf/bitcoin/aum
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

| Parameter | Type   | Required | Description                           | Example value |
| --------- | ------ | -------- | ------------------------------------- | ------------- |
| ticker    | string | no       | ETF ticker symbol (e.g., GBTC, IBIT). |               |


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/etf/bitcoin/aum' \
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
      "time": 1704153600000,
      "aum_usd": 0
    },
    {
      "time": 1704240000000,
      "aum_usd": 0
    },
    ....
  ]
}
```

---
  