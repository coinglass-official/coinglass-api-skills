---
name: other
description: Other request using the CoinGlass API. 
metadata:
  version: 1.0.0
  author: CoinGlass
  openclaw:
    requires:
      bins:
        - curl
        - openssl
    homepage: https://github.com/coinglass-official/coinglass-api-skills/tree/main/indic/other/API.md
license: MIT
---

# CoinGlass Other Skill

Other request on CoinGLass API endpoints. Return the result in JSON format.


## Quick Reference

| API                                      | Endpoint                                      | Function                                                                                                                                                                                               |
| ---------------------------------------- | --------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| AHR999                                   | /api/index/ahr999                             | This endpoint provides data for AHR999, including the average value, AHR999 value, and corresponding values for different dates.                                                                       |
| Bull Market Peak Indicators              | /api/bull-market-peak-indicator               | This endpoint provides a list of Bull Market Peak Indicators                                                                                                                                           |
| Puell-Multiple                           | /api/index/puell-multiple                     | This endpoint provides the Puell-Multiple index, which includes data on buy and sell quantities, the price, and the Puell-Multiple value at specific timestamps.                                       |
| Stock-to-Flow Model                      | /api/index/stock-flow                         | This endpoint provides data for the Stock-to-Flow model, including the price and the number of days remaining until the next halving event for specific timestamps.                                    |
| Pi Cycle Top Indicator                   | /api/index/pi-cycle-indicator                 | This endpoint provides data for the Pi Cycle Top Indicator, including the 111-day moving average (ma110), the 350-day moving average multiplied by 2 (ma350Mu2), and the price at specific timestamps. |
| Golden-Ratio-Multiplier                  | /api/index/golden-ratio-multiplier            | This endpoint provides data for the Golden Ratio Multiplier                                                                                                                                            |
| Bitcoin Profitable Days                  | /api/index/bitcoin/profitable-days            | This endpoint provides data for the Bitcoin Profitable Days                                                                                                                                            |
| Bitcoin-Rainbow-Chart                    | /api/index/bitcoin/rainbow-chart              | This endpoint provides data for the Bitcoin Rainbow Chart                                                                                                                                              |
| Crypto Fear & Greed Index                | /api/index/fear-greed-history                 | This endpoint provides data for the Crypto Fear & Greed Index                                                                                                                                          |
| StableCoin MarketCap History             | /api/index/stableCoin-marketCap-history       | This endpoint provides data for the StableCoin MarketCap History                                                                                                                                       |
| Bitcoin Bubble Index                     | /api/index/bitcoin/bubble-index               | This endpoint provides data for the Bitcoin Bubble Index                                                                                                                                               |
| Tow Year Ma Multiplier                   | /api/index/2-year-ma-multiplier               | This endpoint provides data for the Tow Year Ma Multiplier                                                                                                                                             |
| 200-Week Moving Avg Heatmap              | /api/index/200-week-moving-average-heatmap    | This endpoint provides data for the 200-Week Moving Avg Heatmap                                                                                                                                        |
| Altcoin Season Index                     | /api/index/altcoin-season                     | This endpoint provides data for the altcoin season index                                                                                                                                               |
| Bitcoin Short Term Holder SOPR           | /api/index/bitcoin-sth-sopr                   | This endpoint provides data for the bitcoin short term holder sopr                                                                                                                                     |
| Bitcoin Long Term Holder SOPR            | /api/index/bitcoin-lth-sopr                   | This endpoint provides data for the bitcoin long term holder sopr                                                                                                                                      |
| Bitcoin Short Term Holder Realized Price | /api/index/bitcoin-sth-realized-price         | This endpoint provides data for the bitcoin short term holder realized price                                                                                                                           |
| Bitcoin Long Term Holder Realized Price  | /api/index/bitcoin-lth-realized-price         | This endpoint provides data for the bitcoin long term holder realized price                                                                                                                            |
| Bitcoin Short Term Holder Supply         | /api/index/bitcoin-short-term-holder-supply   | This endpoint provides data for the bitcoin short term holder supply                                                                                                                                   |
| Bitcoin Long Term Holder Supply          | /api/index/bitcoin-long-term-holder-supply    | This endpoint provides data for the bitcoin long term holder supply                                                                                                                                    |
| Bitcoin RHODL Ratio                      | /api/index/bitcoin-rhodl-ratio                | This endpoint provides data for the bitcoin rhodl ratio                                                                                                                                                |
| Bitcoin Reserve Risk                     | /api/index/bitcoin-reserve-risk               | This endpoint provides data for the bitcoin reserve risk                                                                                                                                               |
| Bitcoin Active Addresses                 | /api/index/bitcoin-active-addresses           | This endpoint provides data for the bitcoin active addresses                                                                                                                                           |
| Bitcoin New Addresses                    | /api/index/bitcoin-new-addresses              | This endpoint provides data for the bitcoin new addresses                                                                                                                                              |
| Bitcoin Net Unrealized PNL               | /api/index/bitcoin-net-unrealized-profit-loss | This endpoint provides data for the bitcoin net unrealized profit/loss (nupl)                                                                                                                          |
| Bitcoin Correlations                     | /api/index/bitcoin-correlation                | This endpoint provides data for the bitcoin correlations (GLD, IWM, QQQ, SPY, TLT)                                                                                                                     |
| Bitcoin Macro Oscillator (BMO)           | /api/index/bitcoin-macro-oscillator           | This endpoint provides data for the bitcoin macro oscillator (bmo)                                                                                                                                     |
| Options/Futures OI Ratio                 | /api/index/option-vs-futures-oi-ratio         | This endpoint provides data for the options/futures oi ratio                                                                                                                                           |
| Bitcoin vs Global M2 Supply & Growth     | /api/index/bitcoin-vs-global-m2-growth        | This endpoint provides data for the bitcoin vs global m2 supply & growth                                                                                                                               |
| Bitcoin vs US M2 Supply & Growth         | /api/index/bitcoin-vs-us-m2-growth            | This endpoint provides data for the bitcoin vs US m2 supply & growth                                                                                                                                   |
| Bitcoin Dominance                        | /api/index/bitcoin-dominance                  | This endpoint provides data for the bitcoin dominance                                                                                                                                                  |
| Exchanges Assets Transparency            | /api/exchange_assets_transparency/list        | This endpoint provides transparency data of exchange assets, including total balances, inflows, balance changes, open interest, leverage, and trading volume.                                          |
| Futures vs Spot Volume Ratio             | /api/futures_spot_volume_ratio                | This endpoint provides time-series data for the futures-to-spot trading volume ratio, including timestamp, volume ratio, futures trading volume (USD), and spot trading volume (USD).                  |

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
        
## API 1: AHR999


**Supported Plans, Intervals, and Historical Data Access**

Hobbyist:Available
Startup:Available
Standard:Available
Professional:Available


### Method: GET

**URL**:
```
https://open-api-v4.coinglass.com//api/index/ahr999
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

*No parameters required*


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/index/ahr999' \
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
      "date_string": "2011/02/01",            // Date in string format (YYYY/MM/DD)
      "average_price": 0.1365,                // Average price on the given date
      "ahr999_value": 4.441692296429609,      // AHR999 index value
      "current_value": 0.626                  // Current value on the given date
    },
    {
      "date_string": "2011/02/02",            // Date in string format (YYYY/MM/DD)
      "average_price": 0.1383,                // Average price on the given date
      "ahr999_value": 5.642181244439729,      // AHR999 index value
      "current_value": 0.713                  // Current value on the given date
    }
    // More data entries...
  ]
}
```

---
  
  
  ---
        
## API 2: Bull Market Peak Indicators


**Supported Plans, Intervals, and Historical Data Access**

Hobbyist:Available
Startup:Available
Standard:Available
Professional:Available


### Method: GET

**URL**:
```
https://open-api-v4.coinglass.com//api/bull-market-peak-indicator
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

*No parameters required*


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/bull-market-peak-indicator' \
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
      "indicator_name": "Bitcoin Ahr999 Index",  // Indicator name
      "current_value": "0.78",                  // Current value
      "target_value": "4",                      // Target value
      "previous_value": "0.77",                 // Previous value
      "change_value": "0.0009811160359081",     // Change value
      "comparison_type": ">=",                  // Comparison type
      "hit_status": false                       // Hit status (whether the target condition is met)
    },
    {
      "indicator_name": "Pi Cycle Top Indicator",  // Indicator name
      "current_value": "85073.0",                  // Current value
      "target_value": "154582",                    // Target value
      "previous_value": "85127.0",                 // Previous value
      "change_value": "-54.0",                     // Change value
      "comparison_type": ">=",                     // Comparison type
      "hit_status": false                          // Hit status (whether the target condition is met)
    }
  ]
}
```

---
  
  
  ---
        
## API 3: Puell-Multiple


**Supported Plans, Intervals, and Historical Data Access**

Hobbyist:Available
Startup:Available
Standard:Available
Professional:Available


### Method: GET

**URL**:
```
https://open-api-v4.coinglass.com//api/index/puell-multiple
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

*No parameters required*


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/index/puell-multiple' \
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
      "timestamp": 1282003200000,           // Timestamp (in milliseconds)
      "price": 0.07,                         // Price on the given day
      "puell_multiple": 1                   // Puell Multiple value
    },
    {
      "timestamp": 1282089600000,           // Timestamp (in milliseconds)
      "price": 0.068,                        // Price on the given day
      "puell_multiple": 1.0007745933384973  // Puell Multiple value
    }
    ...
  ]
}
```

---
  
  
  ---
        
## API 4: Stock-to-Flow Model


**Supported Plans, Intervals, and Historical Data Access**

Hobbyist:Available
Startup:Available
Standard:Available
Professional:Available


### Method: GET

**URL**:
```
https://open-api-v4.coinglass.com//api/index/stock-flow
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

*No parameters required*


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/index/stock-flow' \
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
      "timestamp": 1282003200000,       // Timestamp (in milliseconds)
      "price": 0.07,                     // Price on the given day
      "next_halving": 834               // Days remaining until the next halving
    },
    {
      "timestamp": 1282089600000,       // Timestamp (in milliseconds)
      "price": 0.068,                    // Price on the given day
      "next_halving": 833               // Days remaining until the next halving
    }

  ]
}
```

---
  
  
  ---
        
## API 5: Pi Cycle Top Indicator


**Supported Plans, Intervals, and Historical Data Access**

Hobbyist:Available
Startup:Available
Standard:Available
Professional:Available


### Method: GET

**URL**:
```
https://open-api-v4.coinglass.com//api/index/pi-cycle-indicator
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

*No parameters required*


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/index/pi-cycle-indicator' \
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
      "ma_110": 0.07,                     // 110-day moving average price
      "timestamp": 1282003200000,        // Timestamp (milliseconds)
      "ma_350_mu_2": 0.14,               // 2x value of 350-day moving average
      "price": 0.07                      // Daily price
    },
    {
      "ma_110": 0.069,                   // 110-day moving average price
      "timestamp": 1282089600000,        // Timestamp (milliseconds)
      "ma_350_mu_2": 0.138,              // 2x value of 350-day moving average
      "price": 0.068                     // Daily price
    }
  ]
}
```

---
  
  
  ---
        
## API 6: Golden-Ratio-Multiplier


**Supported Plans, Intervals, and Historical Data Access**

Hobbyist:Available
Startup:Available
Standard:Available
Professional:Available


### Method: GET

**URL**:
```
https://open-api-v4.coinglass.com//api/index/golden-ratio-multiplier
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

*No parameters required*


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/index/golden-ratio-multiplier' \
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
      "low_bull_high_2": 0.14,                       // Bull market low-high ratio coefficient
      "timestamp": 1282003200000,                    // Timestamp (in milliseconds)
      "price": 0.07,                                 // Current price
      "ma_350": 0.07,                                // 350-day moving average
      "accumulation_high_1_6": 0.11200000000000002,  // Accumulation high ratio (1/6 golden ratio)
      "x_3": 0.21000000000000002,                    // Golden ratio multiple x3
      "x_5": 0.35000000000000003,                    // Golden ratio multiple x5
      "x_8": 0.56,                                   // Golden ratio multiple x8
      "x_13": 0.9100000000000001,                    // Golden ratio multiple x13
      "x_21": 1.4700000000000002                     // Golden ratio multiple x21
    },
    ...
  ]
}
```

---
  
  
  ---
        
## API 7: Bitcoin Profitable Days


**Supported Plans, Intervals, and Historical Data Access**

Hobbyist:Available
Startup:Available
Standard:Available
Professional:Available


### Method: GET

**URL**:
```
https://open-api-v4.coinglass.com//api/index/bitcoin/profitable-days
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

*No parameters required*


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/index/bitcoin/profitable-days' \
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
      "side": 1,                              // Trade direction, 1 represents buy, 0 represents sell
      "timestamp": 1282003200000,             // Timestamp (in milliseconds)
      "price": 0.07                           // Price
    },
    {
      "timestamp": 1282089600000,             // Timestamp (in milliseconds)
      "price": 0.068,                         // Price
      "side": 1                               // Trade direction, 1 represents buy, 0 represents sell
    }
  ]
}
```

---
  
  
  ---
        
## API 8: Bitcoin-Rainbow-Chart


**Supported Plans, Intervals, and Historical Data Access**

Hobbyist:Available
Startup:Available
Standard:Available
Professional:Available


### Method: GET

**URL**:
```
https://open-api-v4.coinglass.com//api/index/bitcoin/rainbow-chart
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

*No parameters required*


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/index/bitcoin/rainbow-chart' \
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
    [
      0.07,                                 // Current price
      0.033065,                             // Minimum value of shadow
      0.044064,                             // First layer
      0.059892,                             // Second layer
      0.082219,                             // Third layer
      0.110996,                             // Fourth layer
      0.149845,                             // Fifth layer
      0.205865,                             // Sixth layer
      0.283454,                             // Seventh layer
      0.380525,                             // Eighth layer
      0.517626,                             // Ninth layer
      1282003200000                        // Timestamp
    ]
  ]
}
```

---
  
  
  ---
        
## API 9: Crypto Fear & Greed Index


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
https://open-api-v4.coinglass.com//api/index/fear-greed-history
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

*No parameters required*


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/index/fear-greed-history' \
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
      "data_list": [4611285.1141, ...],         // Fear and Greed Index values
      "price_list": [4788636.51145, ...],         // Corresponding price data
      "time_list": [1636588800, ...]        // Timestamps
    }
  ]
}
```

---
  
  
  ---
        
## API 10: StableCoin MarketCap History


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
https://open-api-v4.coinglass.com//api/index/stableCoin-marketCap-history
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

*No parameters required*


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/index/stableCoin-marketCap-history' \
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
      "data_list": [4611285.1141, ...],         // List of values
      "price_list": [, ...],                    // List of prices
      "time_list": [1636588800, ...]            // List of timestamps
    }
  ]
}
```

---
  
  
  ---
        
## API 11: Bitcoin Bubble Index


**Supported Plans, Intervals, and Historical Data Access**

Hobbyist:Available
Startup:Available
Standard:Available
Professional:Available


### Method: GET

**URL**:
```
https://open-api-v4.coinglass.com//api/index/bitcoin/bubble-index
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

*No parameters required*


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/index/bitcoin/bubble-index' \
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
      "price": 0.0495,                          // Current price
      "bubble_index": -29.59827206,             // Bubble index
      "google_trend_percent": 0.0287,           // Google trend percentage
      "mining_difficulty": 181.543,             // Mining difficulty
      "transaction_count": 235,                 // Transaction count
      "address_send_count": 390,                // Address send count
      "tweet_count": 0,                         // Tweet count
      "date_string": "2010-07-17"               // Date string
    },
    {
      "price": 0.0726,                          // Current price
      "bubble_index": -29.30591863,             // Bubble index
      "google_trend_percent": 0.0365,           // Google trend percentage
      "mining_difficulty": 181.543,             // Mining difficulty
      "transaction_count": 248,                 // Transaction count
      "address_send_count": 424,                // Address send count
      "tweet_count": 0,                         // Tweet count
      "date_string": "2010-07-18"               // Date string
    }
  ]
}
```

---
  
  
  ---
        
## API 12: Tow Year Ma Multiplier


**Supported Plans, Intervals, and Historical Data Access**

Hobbyist:Available
Startup:Available
Standard:Available
Professional:Available


### Method: GET

**URL**:
```
https://open-api-v4.coinglass.com//api/index/2-year-ma-multiplier
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

*No parameters required*


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/index/2-year-ma-multiplier' \
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
      "timestamp": 1282003200000,               // Timestamp (in milliseconds)
      "price": 0.07,                            // Current price
      "moving_average_730": 0.07,               // 2-year moving average (730 represents the period)
      "moving_average_730_multiplier_5": 0.35000000000000003, // 5 times the 2-year moving average (Multiplier)
    }
  ]
}
```

---
  
  
  ---
        
## API 13: 200-Week Moving Avg Heatmap


**Supported Plans, Intervals, and Historical Data Access**

Hobbyist:Available
Startup:Available
Standard:Available
Professional:Available


### Method: GET

**URL**:
```
https://open-api-v4.coinglass.com//api/index/200-week-moving-average-heatmap
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

*No parameters required*


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/index/200-week-moving-average-heatmap' \
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
      "timestamp": 1325203200000,          // Timestamp (in milliseconds)
      "price": 4.31063509000584,           // Current price
      "moving_average_1440": 4.143619070636635, // 200-week moving average (1440 represents the period)
      "moving_average_1440_ip": 0,         // Position of the moving average (IP indicator)
    }
  ]
}
```

---
  
  
  ---
        
## API 14: Altcoin Season Index


**Supported Plans, Intervals, and Historical Data Access**

Hobbyist:Not Available
Startup:Available
Standard:Available
Professional:Available


### Method: GET

**URL**:
```
https://open-api-v4.coinglass.com//api/index/altcoin-season
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

*No parameters required*


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/index/altcoin-season' \
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
      "timestamp": 1491177600000,
      "altcoin_index": 96,
      "altcoin_marketcap": 0
    },
    {
      "timestamp": 1491264000000,
      "altcoin_index": 100,
      "altcoin_marketcap": 0
    },
    {
      "timestamp": 1491350400000,
      "altcoin_index": 96,
      "altcoin_marketcap": 0
    },
}
```

---
  
  
  ---
        
## API 15: Bitcoin Short Term Holder SOPR


**Supported Plans, Intervals, and Historical Data Access**

Hobbyist:Not Available
Startup:Available
Standard:Available
Professional:Available


### Method: GET

**URL**:
```
https://open-api-v4.coinglass.com//api/index/bitcoin-sth-sopr
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

*No parameters required*


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/index/bitcoin-sth-sopr' \
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
      "timestamp": 1255305600000,
      "price": 0.00110205,
      "sth_sopr": 45.98748129
    },
    {
      "timestamp": 1255651200000,
      "price": 0.00124491,
      "sth_sopr": 1.24312355
    },
    {
      "timestamp": 1255824000000,
      "price": 0.00122546,
      "sth_sopr": 1.04147332
    },
}
```

---
  
  
  ---
        
## API 16: Bitcoin Long Term Holder SOPR


**Supported Plans, Intervals, and Historical Data Access**

Hobbyist:Not Available
Startup:Available
Standard:Available
Professional:Available


### Method: GET

**URL**:
```
https://open-api-v4.coinglass.com//api/index/bitcoin-lth-sopr
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

*No parameters required*


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/index/bitcoin-lth-sopr' \
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
      "timestamp": 1255305600000,
      "price": 0.00110205,
      "lth_sopr": 45.98748129
    },
    {
      "timestamp": 1255651200000,
      "price": 0.00124491,
      "lth_sopr": 1.24312355
    },
    {
      "timestamp": 1255824000000,
      "price": 0.00122546,
      "lth_sopr": 1.04147332
    },
}
```

---
  
  
  ---
        
## API 17: Bitcoin Short Term Holder Realized Price


**Supported Plans, Intervals, and Historical Data Access**

Hobbyist:Not Available
Startup:Available
Standard:Available
Professional:Available


### Method: GET

**URL**:
```
https://open-api-v4.coinglass.com//api/index/bitcoin-sth-realized-price
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

*No parameters required*


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/index/bitcoin-sth-realized-price' \
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
      "timestamp": 1325376000000,
      "price": 4.61211781,
      "sth_realized_price": 4.8958766225
    },
    {
      "timestamp": 1325462400000,
      "price": 5.13201225,
      "sth_realized_price": 4.8806352365
    },
    {
      "timestamp": 1325548800000,
      "price": 5.21773083,
      "sth_realized_price": 4.8736945702
    },
}
```

---
  
  
  ---
        
## API 18: Bitcoin Long Term Holder Realized Price


**Supported Plans, Intervals, and Historical Data Access**

Hobbyist:Not Available
Startup:Available
Standard:Available
Professional:Available


### Method: GET

**URL**:
```
https://open-api-v4.coinglass.com//api/index/bitcoin-lth-realized-price
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

*No parameters required*


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/index/bitcoin-lth-realized-price' \
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
      "timestamp": 1325376000000,
      "price": 4.61211781,
      "lth_realized_price": 4.8958766225
    },
    {
      "timestamp": 1325462400000,
      "price": 5.13201225,
      "lth_realized_price": 4.8806352365
    },
    {
      "timestamp": 1325548800000,
      "price": 5.21773083,
      "lth_realized_price": 4.8736945702
    },
}
```

---
  
  
  ---
        
## API 19: Bitcoin Short Term Holder Supply


**Supported Plans, Intervals, and Historical Data Access**

Hobbyist:Not Available
Startup:Available
Standard:Available
Professional:Available


### Method: GET

**URL**:
```
https://open-api-v4.coinglass.com//api/index/bitcoin-short-term-holder-supply
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

*No parameters required*


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/index/bitcoin-short-term-holder-supply' \
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
      "price": 10.8584714558738,
      "short_term_holder_supply": 3682358,
      "timestamp": 1313625600000
    },
    {
      "price": 11.6704730432496,
      "short_term_holder_supply": 3682497,
      "timestamp": 1313712000000
    },
    {
      "price": 11.4597317393337,
      "short_term_holder_supply": 3680156,
      "timestamp": 1313798400000
    },
    {
      "price": 11.3544813407364,
      "short_term_holder_supply": 3684825,
      "timestamp": 1313884800000
    },
}
```

---
  
  
  ---
        
## API 20: Bitcoin Long Term Holder Supply


**Supported Plans, Intervals, and Historical Data Access**

Hobbyist:Not Available
Startup:Available
Standard:Available
Professional:Available


### Method: GET

**URL**:
```
https://open-api-v4.coinglass.com//api/index/bitcoin-long-term-holder-supply
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

*No parameters required*


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/index/bitcoin-long-term-holder-supply' \
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
      "price": 10.8584714558738,
      "long_term_holder_supply": 3395092,
      "timestamp": 1313625600000
    },
    {
      "price": 11.6704730432496,
      "long_term_holder_supply": 3401503,
      "timestamp": 1313712000000
    },
    {
      "price": 11.4597317393337,
      "long_term_holder_supply": 3411444,
      "timestamp": 1313798400000
    },
}
```

---
  
  
  ---
        
## API 21: Bitcoin RHODL Ratio


**Supported Plans, Intervals, and Historical Data Access**

Hobbyist:Not Available
Startup:Available
Standard:Available
Professional:Available


### Method: GET

**URL**:
```
https://open-api-v4.coinglass.com//api/index/bitcoin-rhodl-ratio
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

*No parameters required*


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/index/bitcoin-rhodl-ratio' \
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
      "price": 0.07,
      "rhodl_ratio": 0.19768584894587235,
      "timestamp": 1282003200000
    },
    {
      "price": 0.068,
      "rhodl_ratio": 0.3765371066876411,
      "timestamp": 1282089600000
    },
    {
      "price": 0.0667,
      "rhodl_ratio": 0.55947437296653,
      "timestamp": 1282176000000
    },
}
```

---
  
  
  ---
        
## API 22: Bitcoin Reserve Risk


**Supported Plans, Intervals, and Historical Data Access**

Hobbyist:Not Available
Startup:Available
Standard:Available
Professional:Available


### Method: GET

**URL**:
```
https://open-api-v4.coinglass.com//api/index/bitcoin-reserve-risk
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

*No parameters required*


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/index/bitcoin-reserve-risk' \
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
      "price": 0.07,
      "reserve_risk_index": 1.0463483830080946,
      "movcd": 0.0031006755142484214,
      "hodl_bank": 0.06689932448575159,
      "vocd": 0.0031006755142484214,
      "timestamp": 1282003200000
    },
    {
      "price": 0.068,
      "reserve_risk_index": 0.5285777367358181,
      "movcd": 0.006252211158717467,
      "hodl_bank": 0.12864711332703413,
      "vocd": 0.009403746803186513,
      "timestamp": 1282089600000
    },
    {
      "price": 0.0667,
      "reserve_risk_index": 0.3469505118474761,
      "movcd": 0.0031006755142484214,
      "hodl_bank": 0.19224643781278572,
      "vocd": 0.0018287503434234224,
      "timestamp": 1282176000000
    },
}
```

---
  
  
  ---
        
## API 23: Bitcoin Active Addresses


**Supported Plans, Intervals, and Historical Data Access**

Hobbyist:Not Available
Startup:Available
Standard:Available
Professional:Available


### Method: GET

**URL**:
```
https://open-api-v4.coinglass.com//api/index/bitcoin-active-addresses
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

*No parameters required*


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/index/bitcoin-active-addresses' \
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
      "timestamp": 1282003200000,
      "price": 0.07,
      "active_address_count": 494
    },
    {
      "timestamp": 1282089600000,
      "price": 0.068,
      "active_address_count": 726
    },
    {
      "timestamp": 1282176000000,
      "price": 0.0667,
      "active_address_count": 470
    },
}
```

---
  
  
  ---
        
## API 24: Bitcoin New Addresses


**Supported Plans, Intervals, and Historical Data Access**

Hobbyist:Not Available
Startup:Available
Standard:Available
Professional:Available


### Method: GET

**URL**:
```
https://open-api-v4.coinglass.com//api/index/bitcoin-new-addresses
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

*No parameters required*


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/index/bitcoin-new-addresses' \
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
      "timestamp": 1282003200000,
      "price": 0.07,
      "new_address_count": 331
    },
    {
      "timestamp": 1282089600000,
      "price": 0.068,
      "new_address_count": 415
    },
    {
      "timestamp": 1282176000000,
      "price": 0.0667,
      "new_address_count": 316
    },
}
```

---
  
  
  ---
        
## API 25: Bitcoin Net Unrealized PNL


**Supported Plans, Intervals, and Historical Data Access**

Hobbyist:Not Available
Startup:Available
Standard:Available
Professional:Available


### Method: GET

**URL**:
```
https://open-api-v4.coinglass.com//api/index/bitcoin-net-unrealized-profit-loss
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

*No parameters required*


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/index/bitcoin-net-unrealized-profit-loss' \
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
      "price": 0,
      "net_unpnl": 0,
      "timestamp": 1230940800000
    },
    {
      "price": 0,
      "net_unpnl": 0,
      "timestamp": 1231027200000
    },
    {
      "price": 0,
      "net_unpnl": 0,
      "timestamp": 1231113600000
    },
}
```

---
  
  
  ---
        
## API 26: Bitcoin Correlations


**Supported Plans, Intervals, and Historical Data Access**

Hobbyist:Not Available
Startup:Available
Standard:Available
Professional:Available


### Method: GET

**URL**:
```
https://open-api-v4.coinglass.com//api/index/bitcoin-correlation
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

*No parameters required*


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/index/bitcoin-correlation' \
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
      "timestamp": 1284508800000,
      "price": 0.06080235,
      "gld": -0.5150866328682138,
      "iwm": -0.4464952558926045,
      "qqq": 0,
      "spy": -0.38000905719099726,
      "tlt": 0.32525293786188403
    },
    {
      "timestamp": 1284595200000,
      "price": 0.0805732,
      "gld": -0.1441145695322488,
      "iwm": -0.390257896507018,
      "qqq": 0,
      "spy": -0.3562006006485584,
      "tlt": 0.25421749956089384
    },
    {
      "timestamp": 1284681600000,
      "price": 0.09079794,
      "gld": 0.18856803587350612,
      "iwm": -0.06826869030058404,
      "qqq": 0,
      "spy": -0.03849870412867858,
      "tlt": -0.02643535666282007
    },
}
```

---
  
  
  ---
        
## API 27: Bitcoin Macro Oscillator (BMO)


**Supported Plans, Intervals, and Historical Data Access**

Hobbyist:Not Available
Startup:Available
Standard:Available
Professional:Available


### Method: GET

**URL**:
```
https://open-api-v4.coinglass.com//api/index/bitcoin-macro-oscillator
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

*No parameters required*


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/index/bitcoin-macro-oscillator' \
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
      "price": 6.3162949999999976,
      "bmo_value": -0.25927286591542786,
      "timestamp": 1326067200000
    },
    {
      "price": 6.449687599999999,
      "bmo_value": -0.23528273675333555,
      "timestamp": 1326153600000
    },
    {
      "price": 6.899966666666668,
      "bmo_value": -0.17373343317542636,
      "timestamp": 1326240000000
    },
}
```

---
  
  
  ---
        
## API 28: Options/Futures OI Ratio


**Supported Plans, Intervals, and Historical Data Access**

Hobbyist:Not Available
Startup:Available
Standard:Available
Professional:Available


### Method: GET

**URL**:
```
https://open-api-v4.coinglass.com//api/index/option-vs-futures-oi-ratio
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

*No parameters required*


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/index/option-vs-futures-oi-ratio' \
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
      "btc_option_vs_futures_radio": 45.1,
      "eth_option_vs_futures_radio": 21.92,
      "timestamp": 1592956800000
    },
    {
      "btc_option_vs_futures_radio": 45.15,
      "eth_option_vs_futures_radio": 23.16,
      "timestamp": 1593043200000
    },
    {
      "btc_option_vs_futures_radio": 47.27,
      "eth_option_vs_futures_radio": 23.65,
      "timestamp": 1593129600000
    },
}
```

---
  
  
  ---
        
## API 29: Bitcoin vs Global M2 Supply & Growth


**Supported Plans, Intervals, and Historical Data Access**

Hobbyist:Not Available
Startup:Available
Standard:Available
Professional:Available


### Method: GET

**URL**:
```
https://open-api-v4.coinglass.com//api/index/bitcoin-vs-global-m2-growth
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

*No parameters required*


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/index/bitcoin-vs-global-m2-growth' \
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
      "timestamp": 1369008000000,
      "price": 117.8186364699,
      "global_m2_yoy_growth": 5.5654014717,
      "global_m2_supply": 59166686473105
    },
    {
      "timestamp": 1369612800000,
      "price": 126.392905903,
      "global_m2_yoy_growth": 5.8571414345,
      "global_m2_supply": 59490171457382
    },
    {
      "timestamp": 1370217600000,
      "price": 122.9491879018,
      "global_m2_yoy_growth": 6.7670545757,
      "global_m2_supply": 60072386054198
    },
}
```

---
  
  
  ---
        
## API 30: Bitcoin vs US M2 Supply & Growth


**Supported Plans, Intervals, and Historical Data Access**

Hobbyist:Not Available
Startup:Available
Standard:Available
Professional:Available


### Method: GET

**URL**:
```
https://open-api-v4.coinglass.com//api/index/bitcoin-vs-us-m2-growth
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

*No parameters required*


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/index/bitcoin-vs-us-m2-growth' \
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
      "timestamp": 1278979200000,
      "price": 0.06183332,
      "us_m2_yoy_growth": 0.1321,
      "us_m2_supply": 8639800000000
    },
    {
      "timestamp": 1279065600000,
      "price": 0.05815725,
      "us_m2_yoy_growth": 0.1321,
      "us_m2_supply": 8639800000000
    },
    {
      "timestamp": 1279152000000,
      "price": 0.05640261,
      "us_m2_yoy_growth": 0.1321,
      "us_m2_supply": 8639800000000
    },
}
```

---
  
  
  ---
        
## API 31: Bitcoin Dominance


**Supported Plans, Intervals, and Historical Data Access**

Hobbyist:Not Available
Startup:Available
Standard:Available
Professional:Available


### Method: GET

**URL**:
```
https://open-api-v4.coinglass.com//api/index/bitcoin-dominance
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

*No parameters required*


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/index/bitcoin-dominance' \
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
      "timestamp": 1367366400000,
      "price": 139,
      "bitcoin_dominance": 94.3595,
      "market_cap": 1545031856
    },
    {
      "timestamp": 1367625600000,
      "price": 98.0999984741,
      "bitcoin_dominance": 93.8787,
      "market_cap": 1097883152
    },
    {
      "timestamp": 1367884800000,
      "price": 112.25,
      "bitcoin_dominance": 94.3851,
      "market_cap": 1240126128
    },
}
```

---
  
  
  ---
        
## API 32: Exchanges Assets Transparency


**Supported Plans, Intervals, and Historical Data Access**

Hobbyist:Not Available
Startup:Available
Standard:Available
Professional:Available


### Method: GET

**URL**:
```
https://open-api-v4.coinglass.com//api/exchange_assets_transparency/list
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

*No parameters required*


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/exchange_assets_transparency/list' \
-H 'Content-Type: application/json' \
-H 'CG-API-KEY: ${YOUR_API_KEY}' \
-H 'User-Agent: coinglass-skill/1.0.0'
```
        
**Response**:
```json
{
  "code": "0",                         // Status code
  "data": [
    {
      "exchange_name": "Binance",       //Exchange name
      "exchange_logo_url": "https://cdn.coinglasscdn.com/static/exchanges/270.png",  //Exchange Logo
      "balance_usd": 178382444198.04,   // Total balance
      "balance_change_usd_24h": -4244709940.9,  // 24h change
      "balance_change_usd_7d": 183489103818.63, // 7d change
      "inflow_usd_24h": 1104357008.908988,      // 24h inflow
      "inflow_usd_7d": 870098130.1614555,       // 7d inflow
      "open_interest": 28940016260,             // Open interest
      "average_leverage": 0.1622,               // Avg leverage
      "volume_usd": 114901619432                // Volume
    },
    {
      "exchange_name": "Bitfinex",              //Exchange Name
      "exchange_logo_url": "https://cdn.coinglasscdn.com/static/exchanges/bitfinex.jpg", //Exchange Logo
      "balance_usd": 25836820506.17,            // Total balance
      "balance_change_usd_24h": -164420313.45,  // 24h change
      "balance_change_usd_7d": 26135897993.59,  // 7d change
      "inflow_usd_24h": 225181636.35856062,     // 24h inflow
      "inflow_usd_7d": 706172180.891416,        // 7d inflow
      "open_interest": 732439767,               // Open interest
      "average_leverage": 0.0283,               // Avg leverage
      "volume_usd": 68891576                    // Volume
    }
  ]
}
```

---
  
  
  ---
        
## API 33: Futures vs Spot Volume Ratio


**Supported Plans, Intervals, and Historical Data Access**

Hobbyist:Not Available
Startup:Available
Standard:Available
Professional:Available


### Method: GET

**URL**:
```
https://open-api-v4.coinglass.com//api/futures_spot_volume_ratio
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

| Parameter     | Type    | Required | Description                                                                                             | Example value |
| ------------- | ------- | -------- | ------------------------------------------------------------------------------------------------------- | ------------- |
| exchange_list | string  | yes      | List of exchange names to retrieve data from (e.g.,  'Binance, OKX, Bybit')                             | Binance       |
| symbol        | string  | yes      | Trading coin (e.g., BTC).Retrieve supported coins via the 'support-coins' API.                          | BTC           |
| interval      | string  | yes      | Time interval for data aggregation.Supported values: 1m, 3m, 5m, 15m, 30m, 1h, 4h, 6h, 8h, 12h, 1d, 1w. | 1h            |
| limit         | integer | no       | Number of results per request.Default: 1000, Maximum: 1000.                                             |               |
| start_time    | integer | no       | Start timestamp in milliseconds (e.g., 1641522717000).                                                  |               |
| end_time      | integer | no       | End timestamp in milliseconds (e.g., 1641522717000).                                                    |               |


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/futures_spot_volume_ratio?exchange_list=Binance&symbol=BTC&interval=1h' \
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
    "time": 1766588040000,        // timestamp (ms)
    "futures_spot_vol_ratio": 16.9974, // futures / spot volume ratio
    "futures_vol_usd": 59900899.685,   // futures volume (USD)
    "spot_vol_usd": 3524120.4165       // spot volume (USD)
  },
  {
    "time": 1766588100000,        // timestamp (ms)
    "futures_spot_vol_ratio": 9.0887,  // futures / spot volume ratio
    "futures_vol_usd": 24469968.832,   // futures volume (USD)
    "spot_vol_usd": 2692346.1708       // spot volume (USD)
  }
]
}
```

---
  