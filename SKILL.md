---
name: coinglass-api
description: CoinGlass API skill. Routes to the appropriate sub-skill based on user intent. Covers futures, ETF, options, spots, on-chain, indicators, account, and other market data.
metadata:
  version: 1.0.0
  author: CoinGlass
  openclaw:
    requires:
      bins:
        - curl
        - openssl
    homepage: https://github.com/coinglass-official/coinglass-api-skills
license: MIT
---

# CoinGlass API Skill

This is the root entry point for all CoinGlass API skills. It provides access to comprehensive crypto market data including futures, ETF flows, options, spot markets, on-chain data, indicators, and account information.

When a user request matches a sub-skill, read the corresponding `API.md` for that sub-skill and follow its instructions.

---

## Routing Table

Based on the user's intent, route to the appropriate sub-skill:

### Futures

| User Intent | Sub-skill Path |
|---|---|
| Funding rate, funding history | [futures/funding-rate/API.md](futures/funding-rate/API.md)|
| Liquidation, liquidation heatmap | [futures/liquidation/API.md](futures/liquidation/API.md)|
| Long/short ratio | [futures/long-short-ratio/API.md](futures/long-short-ratio/API.md)|
| Open interest, OI history | [futures/open-interest/API.md](futures/open-interest/API.md)|
| Order book (L2), futures order book | [futures/order-book-l2/API.md](futures/order-book-l2/API.md)|
| Taker buy/sell volume (futures) | [futures/taker-buy-sell/API.md](futures/taker-buy-sell/API.md)|
| Futures trading market, market overview | [futures/trading-market/API.md](futures/trading-market/API.md)|
| Hyperliquid positions | [futures/hyperliquid-positions/API.md](futures/hyperliquid-positions/API.md)|

### ETF

| User Intent | Sub-skill Path |
|---|---|
| Bitcoin ETF, BTC ETF flows | [etf/bitcoin-etf/API.md](etf/bitcoin-etf/API.md)|
| Ethereum ETF, ETH ETF flows | [etf/ethereum-etf/API.md](etf/ethereum-etf/API.md)|
| Solana ETF, SOL ETF flows | [etf/solana-etf/API.md](etf/solana-etf/API.md)|
| XRP ETF flows | [etf/xrp-etf/API.md](etf/xrp-etf/API.md)|
| Grayscale, GBTC, ETHE | [etf/grayscale/API.md](etf/grayscale/API.md)|

### Spots

| User Intent | Sub-skill Path |
|---|---|
| Spot order book | [spots/order-book/API.md](spots/order-book/API.md)|
| Spot taker buy/sell volume | [spots/taker-buy-sell/API.md](spots/taker-buy-sell/API.md)|
| Spot trading market, spot market overview | [spots/trading-market/API.md](spots/trading-market/API.md)|

### Options

| User Intent | Sub-skill Path |
|---|---|
| Options, put/call ratio, options flow, max pain | [options/API.md](options/API.md)|

### On-Chain

| User Intent | Sub-skill Path |
|---|---|
| Exchange inflow/outflow, exchange reserve | [on-chain/exchange-data/API.md](on-chain/exchange-data/API.md)|
| Token on-chain data, holder distribution | [on-chain/token/API.md](on-chain/token/API.md)|
| On-chain transactions, whale transactions | [on-chain/transactions/API.md](on-chain/transactions/API.md)|

### Indicators

| User Intent | Sub-skill Path |
|---|---|
| Futures indicators | [indic/futures/API.md](indic/futures/API.md)|
| Spot indicators | [indic/spots/API.md](indic/spots/API.md)|
| Other indicators, fear & greed, market sentiment | [indic/other/API.md](indic/other/API.md)|

### Other

| User Intent | Sub-skill Path |
|---|---|
| Financial calendar, economic events, FOMC | [other/financial-calendar/API.md](other/financial-calendar/API.md)|
| Crypto news | [other/news/API.md](other/news/API.md)|

### Account

| User Intent | Sub-skill Path |
|---|---|
| API account info, plan details, usage | [account/API.md](account/API.md)|

---

## Rate Limits

**Rate Limits**
HOBBYIST: 30 Rate limit/min
STARTUP: 80 Rate limit/min
STANDARD: 300 Rate limit/min
PROFESSIONAL: 1200 Rate limit/min

**Response Headers**
API-KEY-MAX-LIMIT: Indicates the maximum allowed request limit for your API key (per minute).
API-KEY-USE-LIMIT: Shows the current usage count of your API key (requests made in the current time period).

## Error Codes

For detailed information on error codes, please refer to [Errors](account/references/errors-codes.md).