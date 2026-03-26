---
name: trading-market
description: Trading market request using the CoinGlass API. 
metadata:
  version: 1.0.0
  author: CoinGlass
  openclaw:
    requires:
      bins:
        - curl
        - openssl
    homepage: https://github.com/coinglass-official/coinglass-api-skills/tree/main/spots/trading-market/API.md
license: MIT
---

# CoinGlass Trading market Skill

Trading market request on CoinGLass API endpoints. Return the result in JSON format.


## Quick Reference

| API                         | Endpoint                           | Function                                                                                                                       |
| --------------------------- | ---------------------------------- | ------------------------------------------------------------------------------------------------------------------------------ |
| Supported Coins             | /api/spot/supported-coins          | This endpoint allows you to query all the supported spot coins on CoinGlass.                                                   |
| Suported Exchange and Pairs | /api/spot/supported-exchange-pairs | This endpoint allows you to query all supported spot trading exchanges and their corresponding trading pairs on CoinGlass.     |
| Coins Markets               | /api/spot/coins-markets            | This endpoint provides performance-related metrics for all available spot coins                                                |
| Pairs Markets               | /api/spot/pairs-markets            | This endpoint provides performance-related metrics for all available spot trading pairs                                        |
| Price OHLC History          | /api/spot/price/history            | This endpoint provides historical open, high, low, and close (OHLC) price data for cryptocurrencies over specified timeframes. |

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
        
## API 1: Supported Coins


**Supported Plans, Intervals, and Historical Data Access**

Hobbyist:Available
Startup:Available
Standard:Available
Professional:Available


### Method: GET

**URL**:
```
https://open-api-v4.coinglass.com//api/spot/supported-coins
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

*No parameters required*


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/spot/supported-coins' \
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
    "BTC",
    "ETH",
    "USDT",
    "BNB",
    "SOL",
    "USDC",
    ...
  ]
}
```

---
  
  
  ---
        
## API 2: Suported Exchange and Pairs


**Supported Plans, Intervals, and Historical Data Access**

Hobbyist:Available
Startup:Available
Standard:Available
Professional:Available


### Method: GET

**URL**:
```
https://open-api-v4.coinglass.com//api/spot/supported-exchange-pairs
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

*No parameters required*


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/spot/supported-exchange-pairs' \
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
    "Binance": [ // exchange name
      {
        "instrument_id": "BTCUSD_USDT",// Spot pair
        "base_asset": "BTC",// base asset
        "quote_asset": "USDT"// quote asset
      },
      {
        "instrument_id": "ETHUSD_USDT",
        "base_asset": "ETH",
        "quote_asset": "USDT"
      },
      ....
      ],
    "Bitget": [
      {
        "instrument_id": "AAVE:USD",
        "base_asset": "AAVE",
        "quote_asset": "USD"
      },
      {
        "instrument_id": "ADAUSD",
        "base_asset": "ADA",
        "quote_asset": "USD"
      },
      ...
      ]
      ...
   }
}
```

---
  
  
  ---
        
## API 3: Coins Markets


**Supported Plans, Intervals, and Historical Data Access**

Hobbyist:Not Available
Startup:Not Available
Standard:Available
Professional:Available


### Method: GET

**URL**:
```
https://open-api-v4.coinglass.com//api/spot/coins-markets
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

| Parameter | Type    | Required | Description                             | Example value |
| --------- | ------- | -------- | --------------------------------------- | ------------- |
| per_page  | integer | no       |  Number of results per page.            | 10            |
| page      | integer | no       | Page number for pagination, default: 1. | 1             |


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/spot/coins-markets' \
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
      "symbol": "BTC", // Token symbol, e.g., BTC for Bitcoin
      "current_price": 87500, // Current price in USD

      "market_cap": 1735007745495.3037, // Market capitalization in USD

      // Price changes in USD over various time intervals
      "price_change_5m": 101.5, // Price change in last 5 minutes
      "price_change_15m": 46.18, // Price change in last 15 minutes
      "price_change_30m": -77.22, // Price change in last 30 minutes
      "price_change_1h": 12.56, // Price change in last 1 hour
      "price_change_4h": 147.75, // Price change in last 4 hours
      "price_change_12h": 147.75, // Price change in last 12 hours
      "price_change_24h": 2799.99, // Price change in last 24 hours
      "price_change_1w": 2989.69, // Price change in last 1 week

      // Price changes in percentage over various time intervals
      "price_change_percent_5m": 0.12, // % change in last 5 minutes
      "price_change_percent_15m": 0.05, // % change in last 15 minutes
      "price_change_percent_30m": -0.09, // % change in last 30 minutes
      "price_change_percent_1h": 0.01, // % change in last 1 hour
      "price_change_percent_4h": 0.17, // % change in last 4 hours
      "price_change_percent_12h": 0.17, // % change in last 12 hours
      "price_change_percent_24h": 3.31, // % change in last 24 hours
      "price_change_percent_1w": 3.54, // % change in last 1 week

      // Total trading volume in USD over various time intervals
      "volume_usd_1h": 129491564.6994, // Total volume in last 1 hour
      "volume_usd_5m": 11056683.8336, // Total volume in last 5 minutes
      "volume_usd_15m": 50625331.2542, // Total volume in last 15 minutes
      "volume_usd_30m": 80070296.0794, // Total volume in last 30 minutes
      "volume_usd_4h": 580775143.5162, // Total volume in last 4 hours
      "volume_usd_12h": 2663308247.353, // Total volume in last 12 hours
      "volume_usd_24h": 3719093876.3834, // Total volume in last 24 hours
      "volume_usd_1w": 16801739001.0272, // Total volume in last 1 week

      // Trading volume change in USD compared to the previous same interval
      "volume_change_usd_1h": -35317032.6336,
      "volume_change_usd_5m": -110911976.2243,
      "volume_change_usd_15m": -59017725.7105,
      "volume_change_usd_30m": -39864985.2519,
      "volume_change_usd_4h": -1084757627.3629,
      "volume_change_usd_12h": 1624238611.116,
      "volume_change_usd_24h": 1967797576.5416,
      "volume_change_usd_1w": -23396586539.5365,

      // Percentage change in trading volume over various time intervals
      "volume_change_percent_1h": -21.43,
      "volume_change_percent_5m": -90.93,
      "volume_change_percent_15m": -53.83,
      "volume_change_percent_30m": -33.24,
      "volume_change_percent_4h": -65.13,
      "volume_change_percent_12h": 156.32,
      "volume_change_percent_24h": 112.36,
      "volume_change_percent_1w": 3.54,

      // Buy-side trading volume in USD (aggressive buy orders)
      "buy_volume_usd_1h": 55687151.2164,
      "buy_volume_usd_5m": 4634327.6087,
      "buy_volume_usd_15m": 20222399.059,
      "buy_volume_usd_30m": 33140975.4441,
      "buy_volume_usd_4h": 278174843.6339,
      "buy_volume_usd_12h": 1410854413.4688,
      "buy_volume_usd_24h": 1923920264.0666,
      "buy_volume_usd_1w": 8116673333.4846,

      // Sell-side trading volume in USD (aggressive sell orders)
      "sell_volume_usd_1h": 73804413.4829,
      "sell_volume_usd_5m": 6422356.2248,
      "sell_volume_usd_15m": 30402932.1951,
      "sell_volume_usd_30m": 46929320.6352,
      "sell_volume_usd_4h": 302600299.8822,
      "sell_volume_usd_12h": 1252453833.8841,
      "sell_volume_usd_24h": 1795173612.3167,
      "sell_volume_usd_1w": 8685065667.5425,

      // Net flow (buy volume - sell volume), representing market sentiment
      "volume_flow_usd_1h": -18117262.2665,
      "volume_flow_usd_5m": -1788028.6161,
      "volume_flow_usd_15m": -10180533.1361,
      "volume_flow_usd_30m": -13788345.1911,
      "volume_flow_usd_4h": -24425456.2483,
      "volume_flow_usd_12h": 158400579.5847,
      "volume_flow_usd_24h": 128746651.7499,
      "volume_flow_usd_1w": -568392334.0579
    }
  ]
}
```

---
  
  
  ---
        
## API 4: Pairs Markets


**Supported Plans, Intervals, and Historical Data Access**

Hobbyist:Available
Startup:Available
Standard:Available
Professional:Available


### Method: GET

**URL**:
```
https://open-api-v4.coinglass.com//api/spot/pairs-markets
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

| Parameter | Type   | Required | Description                                                                       | Example value |
| --------- | ------ | -------- | --------------------------------------------------------------------------------- | ------------- |
| symbol    | string | yes      | Trading coin (e.g., BTC). Retrieve supported coins via the 'supported-coins' API. | BTC           |


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/spot/pairs-markets?symbol=BTC' \
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
      "symbol": "BTC/USDT",                // Trading pair
      "exchange_name": "Binance",          // Exchange name
      "current_price": 87503.55,           // Current price

      "price_change_1h": 99.55,            // Price change in the past 1 hour
      "price_change_percent_1h": 0.11,     // Price change percentage in the past 1 hour
      "volume_usd_1h": 54425251.2426,      // Trading volume in the past 1 hour (USD)
      "buy_volume_usd_1h": 29304086.0661,  // Buy volume in the past 1 hour (USD)
      "sell_volume_usd_1h": 25121165.1759, // Sell volume in the past 1 hour (USD)
      "volume_change_usd_1h": -24851651.918,   // Volume change in the past 1 hour (USD)
      "volume_change_percent_1h": -31.35,  // Volume change percentage in the past 1 hour
      "net_flows_usd_1h": 4182920.8902,    // Net inflow in the past 1 hour (USD)

      "price_change_4h": 209.56,           // Price change in the past 4 hours
      "price_change_percent_4h": 0.24,     // Price change percentage in the past 4 hours
      "volume_usd_4h": 264625587.5144,     // Trading volume in the past 4 hours (USD)
      "buy_volume_usd_4h": 137768056.2376, // Buy volume in the past 4 hours (USD)
      "sell_volume_usd_4h": 126857531.2762, // Sell volume in the past 4 hours (USD)
      "volume_change_4h": -526166190.0218, // Volume change in the past 4 hours (USD)
      "volume_change_percent_4h": -66.54,  // Volume change percentage in the past 4 hours
      "net_flows_usd_4h": 10910524.9614,   // Net inflow in the past 4 hours (USD)

      "price_change_12h": 2925.55,         // Price change in the past 12 hours
      "price_change_percent_12h": 3.46,    // Price change percentage in the past 12 hours
      "volume_usd_12h": 1212930000.2011,   // Trading volume in the past 12 hours (USD)
      "buy_volume_usd_12h": 662857153.6506, // Buy volume in the past 12 hours (USD)
      "sell_volume_usd_12h": 550072846.5499, // Sell volume in the past 12 hours (USD)
      "volume_change_12h": 842092388.1946, // Volume change in the past 12 hours (USD)
      "volume_change_percent_12h": 227.08, // Volume change percentage in the past 12 hours
      "net_flows_usd_12h": 112784307.1007, // Net inflow in the past 12 hours (USD)

      "price_change_24h": 2735.79,         // Price change in the past 24 hours
      "price_change_percent_24h": 3.23,    // Price change percentage in the past 24 hours
      "volume_usd_24h": 1585522232.603,    // Trading volume in the past 24 hours (USD)
      "buy_volume_usd_24h": 843617569.7248, // Buy volume in the past 24 hours (USD)
      "sell_volume_usd_24h": 741904662.8776, // Sell volume in the past 24 hours (USD)
      "volume_change_24h": 873336140.8197, // Volume change in the past 24 hours (USD)
      "volume_change_percent_24h": 122.63, // Volume change percentage in the past 24 hours
      "net_flows_usd_24h": 101712906.8472, // Net inflow in the past 24 hours (USD)

      "price_change_1w": 3057.83,          // Price change in the past 1 week
      "price_change_percent_1w": 3.62,     // Price change percentage in the past 1 week
      "volume_usd_1w": 6808077059.7062,    // Trading volume in the past 1 week (USD)
      "buy_volume_usd_1w": 3374037733.8429, // Buy volume in the past 1 week (USD)
      "sell_volume_usd_1w": 3434039325.8627, // Sell volume in the past 1 week (USD)
      "volume_change_usd_1w": -11208235126.1193, // Volume change in the past 1 week (USD)
      "volume_change_percent_1w": -62.21,  // Volume change percentage in the past 1 week
      "net_flows_usd_1w": -60001592.0198   // Net inflow in the past 1 week (USD)
    }
  ]
}
```

---
  
  
  ---
        
## API 5: Price OHLC History


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
https://open-api-v4.coinglass.com//api/spot/price/history
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

| Parameter  | Type   | Required | Description                                                                                                   | Example value |
| ---------- | ------ | -------- | ------------------------------------------------------------------------------------------------------------- | ------------- |
| exchange   | string | yes      | spot exchange names (e.g., Binance, OKX) .Retrieve supported exchanges via the 'supported-exchange-pair' API. | Binance       |
| symbol     | string | yes      | Trading pair (e.g., BTCUSDT). Retrieve supported pairs via the 'supported-exchange-pair' API.                 | BTCUSDT       |
| interval   | string | yes      | Data aggregation time interval. Supported values: 1m, 3m, 5m, 15m, 30m, 1h, 4h, 6h, 8h, 12h, 1d, 1w.          | 1h            |
| limit      | string | no       | Number of results per request. Default: 1000, Maximum: 1000.                                                  | 10            |
| start_time | string | no       | Start timestamp in milliseconds (e.g., 1641522717000).                                                        |               |
| end_time   | string | no       | End timestamp in milliseconds (e.g., 1641522717000).                                                          |               |


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/spot/price/history?exchange=Binance&symbol=BTCUSDT&interval=1h' \
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
      "time": 1741690800000,
      "open": 81808.25,//open price
      "high": 82092.34, //high price
      "low": 81400,//low price
      "close": 81720.34,//close price
      "volume_usd": 96823535.5724
    },
    {
      "time": 1741694400000,
      "open": 81720.33,
      "high": 81909.69,
      "low": 81017,
      "close": 81225.5,
      "volume_usd": 150660424.1863
    },
```

---
  