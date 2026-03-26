---
name: transactions
description: Transactions request using the CoinGlass API. 
metadata:
  version: 1.0.0
  author: CoinGlass
  openclaw:
    requires:
      bins:
        - curl
        - openssl
    homepage: https://github.com/coinglass-official/coinglass-api-skills/tree/main/on-chain/transactions/API.md
license: MIT
---

# CoinGlass Transactions Skill

Transactions request on CoinGLass API endpoints. Return the result in JSON format.


## Quick Reference

| API                                  | Endpoint                     | Function                                                                                                                                                                                                                        |
| ------------------------------------ | ---------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Exchange On-chain Transfers (ERC-20) | /api/exchange/chain/tx/list  | This endpoint provides on-chain transfer records (ERC-20) for exchanges.                                                                                                                                                        |
| Whale Transfer                       | /api/chain/v2/whale-transfer | This endpoint provides large on-chain transfers (minimum $10M) within the past six months across major blockchains, including Bitcoin, Ethereum, Tron, Ripple, Dogecoin, Litecoin, Polygon, Algorand, Bitcoin Cash, and Solana. |

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
        
## API 1: Exchange On-chain Transfers (ERC-20)


**Supported Plans, Intervals, and Historical Data Access**

Hobbyist:Available
Startup:Available
Standard:Available
Professional:Available


### Method: GET

**URL**:
```
https://open-api-v4.coinglass.com//api/exchange/chain/tx/list
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

| Parameter  | Type    | Required | Description                                                                            | Example value |
| ---------- | ------- | -------- | -------------------------------------------------------------------------------------- | ------------- |
| symbol     | string  | no       | Must be a token symbol supported by the ERC-20 protocol on the Ethereum (ETH) network. |               |
| start_time | integer | no       | Start timestamp in milliseconds (e.g., 1706089927315).                                 | 1706089927315 |
| min_usd    | number  | no       | Minimum transfer amount filter, specified in USD.                                      |               |
| per_page   | integer | no       | Number of results per page.  Max:100                                                   | 10            |
| page       | integer | no       | Page number for pagination, default: 1.                                                | 1             |


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/exchange/chain/tx/list' \
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
      "transaction_hash": "0xb8d08182d2de176ac42dceba9ff82a7a5fe650c1e56285d6810daac9561ff9dc", // Transaction hash
      "asset_symbol": "USDT",                       // Asset symbol
      "amount_usd": 9998.5,                         // Amount in USD
      "asset_quantity": 9998.5,                     // Quantity
      "exchange_name": "Coinbase",                 // Exchange name
      "transfer_type": 1,                           // Transfer type: 1 = Inflow, 2 = Outflow, 3 = Internal transfer
      "from_address": "0x16c6897438c4f0c7894862d884549e8564c4025f", // From address
      "to_address": "0xa9d1e08c7793af67e9d92fe308d5697fb81d3e43",   // To address
      "transaction_time": 1745224211                // Transaction time (timestamp in seconds)
    },
    {
      "transaction_hash": "0x033c56cb05654f2c360235eff99c84f0eee9c6330fc7012930adfe0a88789c0f", // Transaction hash
      "asset_symbol": "MANA",                       // Asset symbol
      "amount_usd": 6368.95196834,                  // Amount in USD
      "asset_quantity": 20091.33113044,             // Quantity
      "exchange_name": "Binance",                  // Exchange name
      "transfer_type": 1,                           // Transfer type: 1 = Inflow, 2 = Outflow, 3 = Internal transfer
      "from_address": "0x06fd4ba7973a0d39a91734bbc35bc2bcaa99e3b0", // From address
      "to_address": "0x28c6c06298d514db089934071355e5743bf21d60",   // To address
      "transaction_time": 1745224211                // Transaction time (timestamp in seconds)
    }
  ]
}
```

---
  
  
  ---
        
## API 2: Whale Transfer


**Supported Plans, Intervals, and Historical Data Access**

Hobbyist:Not Available
Startup:Available
Standard:Available
Professional:Available


### Method: GET

**URL**:
```
https://open-api-v4.coinglass.com//api/chain/v2/whale-transfer
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

| Parameter  | Type   | Required | Description                                                                       | Example value |
| ---------- | ------ | -------- | --------------------------------------------------------------------------------- | ------------- |
| symbol     | string | no       | Trading coin (e.g., BTC). Retrieve supported coins via the 'supported-coins' API. |               |
| start_time | string | no       | Start timestamp in milliseconds (e.g., 1641522717000).                            |               |
| end_time   | string | no       | End timestamp in milliseconds (e.g., 1641522717000).                              |               |


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/chain/v2/whale-transfer' \
-H 'Content-Type: application/json' \
-H 'CG-API-KEY: ${YOUR_API_KEY}' \
-H 'User-Agent: coinglass-skill/1.0.0'
```
        
**Response**:
```json
{
  "code": "0", // status: "0" = success
  "data": [
    {
      "transaction_hash": "0x910ade7323eae57017c1894078ff1ce319fe908709ba185d81147588ceb06dcc",//transaction hash
      "amount_usd": "18403606.873493258", // transfer value in USD
      "asset_quantity": "10081.791421235566", // transferred amount
      "asset_symbol": "WETH", // asset symbol
      "from": "unknown wallet", // sender 
      "to": "unknown wallet", // receiver 
      "blockchain_name": "ethereum", // blockchain name
      "block_height": 22402402, // block number
      "block_timestamp": 1746265043 // block time (unix)
    },
    {
      "transaction_hash": "7b1fa0327a1e68fbcc397eee0a75ae8ced8c19c08d32f5cfd2ec5d3ba04e59fe",//transaction hash
      "amount_usd": "18413630.94247512", // transfer value in USD
      "asset_quantity": "10087.28276721801", // transferred amount
      "asset_symbol": "WETH", // asset symbol
      "from": "unknown wallet", // sender 
      "to": "unknown wallet", // receiver 
      "blockchain_name": "ethereum", // blockchain name
      "block_height": 22402402, // block number
      "block_timestamp": 1746265043 // block time (unix)
    }
    ....
  ]
}
```

---
  