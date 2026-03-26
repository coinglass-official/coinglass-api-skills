---
name: trading-market
description: Trading Market request using the CoinGlass API. 
metadata:
  version: 1.0.0
  author: CoinGlass
  openclaw:
    requires:
      bins:
        - curl
        - openssl
    homepage: https://github.com/coinglass-official/coinglass-api-skills/tree/main/futures/trading-market/API.md
license: MIT
---

# CoinGlass Trading Market Skill

Trading Market request on CoinGLass API endpoints. Return the result in JSON format.


## Quick Reference

| API                          | Endpoint                              | Function                                                                                                                       |
| ---------------------------- | ------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------ |
| Supported Coins              | /api/futures/supported-coins          | This endpoint allows you to query all the supported coins on CoinGlass                                                         |
| Supported Exchanges          | /api/futures/supported-exchanges      | This endpoint allows you to query all the supported exchanges on CoinGlass                                                     |
| Supported Exchange and Pairs | /api/futures/supported-exchange-pairs | Check the supported exchange and trading pairs in the API documentation                                                        |
| Coins Markets                | /api/futures/coins-markets            | This endpoint provides performance-related metrics for all available futures coins                                             |
| Pairs Markets                | /api/futures/pairs-markets            | This endpoint provides performance-related metrics for all available futures trading pairs                                     |
| Coins Price Change           | /api/futures/coins-price-change       | This endpoint provides percentage price changes and amplitude data for all supported coins across multiple timeframes.         |
| Price History (OHLC)         | /api/futures/price/history            | This endpoint provides historical open, high, low, and close (OHLC) price data for cryptocurrencies over specified timeframes. |
| Delisted Pairs               | /api/futures/delisted-exchange-pairs  | This endpoint allows you to query all delisted trading pairs.                                                                  |
| Exchange Rank                | /api/futures/exchange-rank            | This endpoint provides a ranking list of futures exchanges on CoinGlass.                                                       |

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
https://open-api-v4.coinglass.com//api/futures/supported-coins
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

*No parameters required*


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/futures/supported-coins' \
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
      "SOL",
      "XRP",
      ...
  ]
}
```

---
  
  
  ---
        
## API 2: Supported Exchanges


**Supported Plans, Intervals, and Historical Data Access**

Hobbyist:Available
Startup:Available
Standard:Available
Professional:Available


### Method: GET

**URL**:
```
https://open-api-v4.coinglass.com//api/futures/supported-exchanges
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

*No parameters required*


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/futures/supported-exchanges' \
-H 'Content-Type: application/json' \
-H 'CG-API-KEY: ${YOUR_API_KEY}' \
-H 'User-Agent: coinglass-skill/1.0.0'
```
        
**Response**:
```json
{"code":"0","data":["OKX","Binance","HTX","Bitmex","Bitfinex","Bybit","Deribit","Gate","Kraken","KuCoin","CME","Bitget","dYdX","CoinEx","BingX","Coinbase","Gemini","Crypto.com","Hyperliquid","Bitunix","MEXC","WhiteBIT","Aster","Lighter","EdgeX","Drift","Paradex","Extended","ApeX Omni"]}
```

---
  
  
  ---
        
## API 3: Supported Exchange and Pairs


**Supported Plans, Intervals, and Historical Data Access**

Hobbyist:Available
Startup:Available
Standard:Available
Professional:Available


### Method: GET

**URL**:
```
https://open-api-v4.coinglass.com//api/futures/supported-exchange-pairs
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

| Parameter | Type   | Required | Description                                                                   | Example value |
| --------- | ------ | -------- | ----------------------------------------------------------------------------- | ------------- |
| exchange  | string | no       | Filters the results to return only trading pairs from the specified exchange. |               |


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/futures/supported-exchange-pairs' \
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
        "instrument_id": "BTCUSD_PERP",// futures pair
        "base_asset": "BTC",// base asset
        "quote_asset": "USD"// quote asset
        "settlement_currency": "USDT", // Settlement currency
        "max_leverage": 100, // Maximum supported leverage
        "funding_interval": 1, // Funding rate settlement interval
        "price_tick_size": 0.1 // Price precision & minimum price increment
      },
      {
        "instrument_id": "BTCUSD_250627",
        "base_asset": "BTC",
        "quote_asset": "USD"
        "settlement_currency": "USDT",
        "max_leverage": 100,
        "funding_interval": 1,
        "price_tick_size": 0.1
      },
      ....
      ],
    "Bitget": [
      {
        "instrument_id": "BTCUSDT_UMCBL",
        "base_asset": "BTC",
        "quote_asset": "USDT"
        "settlement_currency": "USDT",
        "max_leverage": 100,
        "funding_interval": 1,
        "price_tick_size": 0.1
      },
      {
        "instrument_id": "ETHUSDT_UMCBL",
        "base_asset": "ETH",
        "quote_asset": "USDT"
        "settlement_currency": "USDT",
        "max_leverage": 100,
        "funding_interval": 1,
        "price_tick_size": 0.1
      },
      ...
      ]
      ...
   }
}
```

---
  
  
  ---
        
## API 4: Coins Markets


**Supported Plans, Intervals, and Historical Data Access**

Hobbyist:Not Available
Startup:Not Available
Standard:Available
Professional:Available


### Method: GET

**URL**:
```
https://open-api-v4.coinglass.com//api/futures/coins-markets
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

| Parameter     | Type    | Required | Description                                                                                                                        | Example value |
| ------------- | ------- | -------- | ---------------------------------------------------------------------------------------------------------------------------------- | ------------- |
| exchange_list | string  | no       | Comma-separated exchange names (e.g., "binance, okx, bybit"). Retrieve supported exchanges via the 'supported-exchange-pairs' API. | Binance,OKX   |
| per_page      | integer | no       | Number of results per page.                                                                                                        | 10            |
| page          | integer | no       | Page number for pagination, default: 1.                                                                                            | 1             |


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/futures/coins-markets' \
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
      "symbol": "BTC",  // Cryptocurrency symbol
      "current_price": 84773.6,  // Current price (in USD)
      "avg_funding_rate_by_oi": 0.00196,  // Average funding rate weighted by open interest
      "avg_funding_rate_by_vol": 0.002647,  // Average funding rate weighted by volume
      "market_cap_usd": 1683310500117.051,  // Market capitalization (in USD)
      "open_interest_market_cap_ratio": 0.0327,  // Ratio of open interest to market capitalization
      "open_interest_usd": 55002072334.9376,  // Open interest (in USD)
      "open_interest_quantity": 648525.0328,  // Open interest quantity (number of contracts)
      "open_interest_volume_ratio": 0.7936,  // Ratio of open interest to volume
      "price_change_percent_5m": -0.02,  // Price change percentage in the last 5 minutes
      "price_change_percent_15m": 0.06,  // Price change percentage in the last 15 minutes
      "price_change_percent_30m": 0.03,  // Price change percentage in the last 30 minutes
      "price_change_percent_1h": -0.1,  // Price change percentage in the last 1 hour
      "price_change_percent_4h": -0.15,  // Price change percentage in the last 4 hours
      "price_change_percent_12h": 0.15,  // Price change percentage in the last 12 hours
      "price_change_percent_24h": 1.06,  // Price change percentage in the last 24 hours
      "open_interest_change_percent_5m": 0,  // Open interest change percentage in the last 5 minutes
      "open_interest_change_percent_15m": 0.04,  // Open interest change percentage in the last 15 minutes
      "open_interest_change_percent_30m": 0,  // Open interest change percentage in the last 30 minutes
      "open_interest_change_percent_1h": -0.01,  // Open interest change percentage in the last 1 hour
      "open_interest_change_percent_4h": 0.17,  // Open interest change percentage in the last 4 hours
      "open_interest_change_percent_24h": 4.58,  // Open interest change percentage in the last 24 hours
      "volume_change_percent_5m": -0.03,  // Volume change percentage in the last 5 minutes
      "volume_change_percent_15m": -0.73,  // Volume change percentage in the last 15 minutes
      "volume_change_percent_30m": -1.13,  // Volume change percentage in the last 30 minutes
      "volume_change_percent_1h": -2.33,  // Volume change percentage in the last 1 hour
      "volume_change_percent_4h": -5.83,  // Volume change percentage in the last 4 hours
      "volume_change_percent_24h": -26.38,  // Volume change percentage in the last 24 hours
      "volume_change_usd_1h": 69310404660.3795,  // Volume change in USD in the last 1 hour
      "volume_change_usd_4h": -4290959532.4414644,  // Volume change in USD in the last 4 hours
      "volume_change_usd_24h": -24835757605.82467,  // Volume change in USD in the last 24 hours
      "long_short_ratio_5m": 1.2523,  // Long/short ratio in the last 5 minutes
      "long_short_ratio_15m": 0.9928,  // Long/short ratio in the last 15 minutes
      "long_short_ratio_30m": 1.0695,  // Long/short ratio in the last 30 minutes
      "long_short_ratio_1h": 1.0068,  // Long/short ratio in the last 1 hour
      "long_short_ratio_4h": 1.0504,  // Long/short ratio in the last 4 hours
      "long_short_ratio_12h": 1.0317,  // Long/short ratio in the last 12 hours
      "long_short_ratio_24h": 1.0313,  // Long/short ratio in the last 24 hours
      "liquidation_usd_1h": 33621.85192,  // Total liquidation amount in USD in the last 1 hour
      "long_liquidation_usd_1h": 22178.4681,  // Long liquidation amount in USD in the last 1 hour
      "short_liquidation_usd_1h": 11443.38382,  // Short liquidation amount in USD in the last 1 hour
      "liquidation_usd_4h": 222210.47117,  // Total liquidation amount in USD in the last 4 hours
      "long_liquidation_usd_4h": 179415.77249,  // Long liquidation amount in USD in the last 4 hours
      "short_liquidation_usd_4h": 42794.69868,  // Short liquidation amount in USD in the last 4 hours
      "liquidation_usd_12h": 11895453.392145,  // Total liquidation amount in USD in the last 12 hours
      "long_liquidation_usd_12h": 10223351.23772,  // Long liquidation amount in USD in the last 12 hours
      "short_liquidation_usd_12h": 1672102.154425,  // Short liquidation amount in USD in the last 12 hours
      "liquidation_usd_24h": 27519292.973646,  // Total liquidation amount in USD in the last 24 hours
      "long_liquidation_usd_24h": 17793322.595016,  // Long liquidation amount in USD in the last 24 hours
      "short_liquidation_usd_24h": 9725970.37863  // Short liquidation amount in USD in the last 24 hours
    },
    {
      "symbol": "ETH",  // Cryptocurrency symbol
      "current_price": 1582.55,  // Current price (in USD)
      "avg_funding_rate_by_oi": 0.001631,  // Average funding rate weighted by open interest
      "avg_funding_rate_by_vol": -0.000601,  // Average funding rate weighted by volume
      "market_cap_usd": 190821695398.62064,  // Market capitalization (in USD)
      "open_interest_market_cap_ratio": 0.0925,  // Ratio of open interest to market capitalization
      "open_interest_usd": 17657693967.0459,  // Open interest (in USD)
      "open_interest_quantity": 11160428.5065,  // Open interest quantity (number of contracts)
      "open_interest_volume_ratio": 0.5398,  // Ratio of open interest to volume
      "price_change_percent_5m": 0.07,  // Price change percentage in the last 5 minutes
      "price_change_percent_15m": 0.25,  // Price change percentage in the last 15 minutes
      "price_change_percent_30m": 0.07,  // Price change percentage in the last 30 minutes
      "price_change_percent_1h": -0.11,  // Price change percentage in the last 1 hour
      "price_change_percent_4h": -0.05,  // Price change percentage in the last 4 hours
      "price_change_percent_12h": -0.02,  // Price change percentage in the last 12 hours
      "price_change_percent_24h": 0.16  // Price change percentage in the last 24 hours
      // ... subsequent fields follow in a similar manner
    }
  ]
}
```

---
  
  
  ---
        
## API 5: Pairs Markets


**Supported Plans, Intervals, and Historical Data Access**

Hobbyist:Available
Startup:Available
Standard:Available
Professional:Available


### Method: GET

**URL**:
```
https://open-api-v4.coinglass.com//api/futures/pairs-markets
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

| Parameter | Type   | Required | Description                                                                      | Example value |
| --------- | ------ | -------- | -------------------------------------------------------------------------------- | ------------- |
| symbol    | string | yes      | Trading coin (e.g., BTC).Retrieve supported coins via the 'supported-coins' API. | BTC           |


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/futures/pairs-markets?symbol=BTC' \
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
      "instrument_id": "BTCUSDT", // Futures trading pair
      "exchange_name": "Binance", // Exchange name
      "symbol": "BTC/USDT", // Trading pair symbol

      "current_price": 84604.3, // Current price
      "index_price": 84646.66222222, // Index price
      "price_change_percent_24h": 0.67, // 24h price change (%)

      "volume_usd": 11317580109.5041, // 24h trading volume (USD)
      "volume_usd_change_percent_24h": -32.13, // 24h volume change (%)

      "long_volume_usd": 5800829746.047, // Long trade volume (USD)
      "short_volume_usd": 5516750363.4571, // Short trade volume (USD)
      "long_volume_quantity": 1130850, // Number of long trades
      "short_volume_quantity": 1162710, // Number of short trades

      "open_interest_quantity": 77881.234, // Open interest quantity (contracts)
      "open_interest_usd": 6589095073.8296, // Open interest value (USD)
      "open_interest_change_percent_24h": 1.9, // 24h open interest change (%)

      "long_liquidation_usd_24h": 3654182.12, // Long liquidations in past 24h (USD)
      "short_liquidation_usd_24h": 4099047.79, // Short liquidations in past 24h (USD)

      "funding_rate": 0.002007, // Current funding rate
      "next_funding_time": 1744963200000, // Next funding time (timestamp)

      "open_interest_volume_radio": 0.5822, // Open interest to volume ratio
      "oi_vol_ratio_change_percent_24h": 50.13 // 24h ratio change (%)
    },
    {
      "instrument_id": "BTC_USDT", // Futures trading pair
      "exchange_name": "Gate.io", // Exchange name
      "symbol": "BTC/USDT", // Trading pair symbol

      "current_price": 84616.3, // Current price
      "index_price": 84643.36, // Index price
      "price_change_percent_24h": 0.69, // 24h price change (%)

      "volume_usd": 1711484049.255, // 24h trading volume (USD)
      "volume_usd_change_percent_24h": -67.03, // 24h volume change (%)

      "long_volume_usd": 870432407.5966, // Long trade volume (USD)
      "short_volume_usd": 841051641.6584, // Short trade volume (USD)
      "long_volume_quantity": 210027, // Number of long trades
      "short_volume_quantity": 218777, // Number of short trades

      "open_interest_quantity": 69477.278, // Open interest quantity (contracts)
      "open_interest_usd": 5878785139.331, // Open interest value (USD)
      "open_interest_change_percent_24h": 3.82, // 24h open interest change (%)

      "long_liquidation_usd_24h": 1502896.68, // Long liquidations in past 24h (USD)
      "short_liquidation_usd_24h": 1037959.7, // Short liquidations in past 24h (USD)

      "funding_rate": 0.0022, // Current funding rate

      "open_interest_volume_radio": 3.4349, // Open interest to volume ratio
      "oi_vol_ratio_change_percent_24h": 214.93 // 24h ratio change (%)
    }
  ]
}
```

---
  
  
  ---
        
## API 6: Coins Price Change


**Supported Plans, Intervals, and Historical Data Access**

Hobbyist:Not Available
Startup:Not Available
Standard:Available
Professional:Available


### Method: GET

**URL**:
```
https://open-api-v4.coinglass.com//api/futures/coins-price-change
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

*No parameters required*


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/futures/coins-price-change' \
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
      "symbol": "BTC", // Symbol
      "current_price": 84518.4, // Current price

      "price_change_percent_5m": -0.04, // 5m change (%)
      "price_change_percent_15m": -0.09, // 15m change (%)
      "price_change_percent_30m": -0.11, // 30m change (%)
      "price_change_percent_1h": -0.17, // 1h change (%)
      "price_change_percent_4h": -0.54, // 4h change (%)
      "price_change_percent_12h": -0.6, // 12h change (%)
      "price_change_percent_24h": 0.24, // 24h change (%)

      "price_amplitude_percent_5m": 0.07, // 5m amplitude (%)
      "price_amplitude_percent_15m": 0.16, // 15m amplitude (%)
      "price_amplitude_percent_30m": 0.18, // 30m amplitude (%)
      "price_amplitude_percent_1h": 0.26, // 1h amplitude (%)
      "price_amplitude_percent_4h": 0.63, // 4h amplitude (%)
      "price_amplitude_percent_12h": 1.17, // 12h amplitude (%)
      "price_amplitude_percent_24h": 2.06 // 24h amplitude (%)
    },
    {
      "symbol": "ETH", // Symbol
      "current_price": 1573.45, // Current price

      "price_change_percent_5m": -0.04, // 5m change (%)
      "price_change_percent_15m": -0.34, // 15m change (%)
      "price_change_percent_30m": -0.38, // 30m change (%)
      "price_change_percent_1h": -0.54, // 1h change (%)
      "price_change_percent_4h": -0.77, // 4h change (%)
      "price_change_percent_12h": -1.99, // 12h change (%)
      "price_change_percent_24h": -1.41, // 24h change (%)

      "price_amplitude_percent_5m": 0.13, // 5m amplitude (%)
      "price_amplitude_percent_15m": 0.4, // 15m amplitude (%)
      "price_amplitude_percent_30m": 0.47, // 30m amplitude (%)
      "price_amplitude_percent_1h": 0.66, // 1h amplitude (%)
      "price_amplitude_percent_4h": 0.9, // 4h amplitude (%)
      "price_amplitude_percent_12h": 2.74, // 12h amplitude (%)
      "price_amplitude_percent_24h": 3.47 // 24h amplitude (%)
    }
  ]
}
```

---
  
  
  ---
        
## API 7: Price History (OHLC)


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
https://open-api-v4.coinglass.com//api/futures/price/history
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

| Parameter  | Type    | Required | Description                                                                                                       | Example value |
| ---------- | ------- | -------- | ----------------------------------------------------------------------------------------------------------------- | ------------- |
| exchange   | string  | yes      |  Futures exchange names (e.g., Binance, OKX) .Retrieve supported exchanges via the 'supported-exchange-pair' API. | Binance       |
| symbol     | string  | yes      | Trading pair (e.g., BTCUSDT). Check supported pairs through the 'supported-exchange-pair' API.                    | BTCUSDT       |
| interval   | string  | yes      | Data aggregation time interval. Supported values: 1m, 3m, 5m, 15m, 30m, 1h, 4h, 6h, 8h, 12h, 1d, 1w.              | 1h            |
| limit      | integer | yes      | Number of results per request. Default: 1000, Maximum: 1000.                                                      | 10            |
| start_time | integer | no       | Start timestamp in milliseconds (e.g., 1641522717000).                                                            |               |
| end_time   | integer | no       | End timestamp in milliseconds (e.g., 1641522717000).                                                              |               |


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/futures/price/history?exchange=Binance&symbol=BTCUSDT&interval=1h&limit=10' \
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
      "time": 1745366400000,
      "open": "93404.9",
      "high": "93864.9",
      "low": "92730",
      "close": "92858.2",
      "volume_usd": "1166471854.3026"
    },
    {
      "time": 1745370000000,
      "open": "92858.2",
      "high": "93464.8",
      "low": "92552",
      "close": "92603.8",
      "volume_usd": "871812560.3437"
    },
    ...
 ]
}
```

---
  
  
  ---
        
## API 8: Delisted Pairs


**Supported Plans, Intervals, and Historical Data Access**

Hobbyist:Available
Startup:Available
Standard:Available
Professional:Available


### Method: GET

**URL**:
```
https://open-api-v4.coinglass.com//api/futures/delisted-exchange-pairs
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

*No parameters required*


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/futures/delisted-exchange-pairs' \
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
        "instrument_id": "BTCUSD_PERP",// futures pair
        "base_asset": "BTC",// base asset
        "quote_asset": "USD"// quote asset
      },
      {
        "instrument_id": "BTCUSD_250627",
        "base_asset": "BTC",
        "quote_asset": "USD"
      },
      ....
      ],
    "Bitget": [
      {
        "instrument_id": "BTCUSDT_UMCBL",
        "base_asset": "BTC",
        "quote_asset": "USDT"
      },
      {
        "instrument_id": "ETHUSDT_UMCBL",
        "base_asset": "ETH",
        "quote_asset": "USDT"
      },
      ...
      ]
      ...
   }
}
```

---
  
  
  ---
        
## API 9: Exchange Rank


**Supported Plans, Intervals, and Historical Data Access**

Hobbyist:Available
Startup:Available
Standard:Available
Professional:Available


### Method: GET

**URL**:
```
https://open-api-v4.coinglass.com//api/futures/exchange-rank
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

*No parameters required*


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/futures/exchange-rank' \
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
      "exchange": "Binance",
      "open_interest_usd": 27564494330,
      "volume_usd": 54150896832,
      "liquidation_usd_24h": 58774453.06516198
    },
    {
      "exchange": "OKX",
      "open_interest_usd": 8586569027,
      "volume_usd": 22670494849,
      "liquidation_usd_24h": 19276388.77685
    },
  ]
}
```

---
  