# CoinGlass API Skills 

CoinGlass API Skills is an open skills marketplace that gives AI agents access to professional-grade crypto market data, analytics, and intelligence through CoinGlass API. It enables agents to retrieve unified real-time and historical data across derivatives, spot, options, ETF, and on-chain markets, and to work with institution-ready datasets such as funding rates, open interest, liquidations, L2/L3 order book depth, order flow, whale activity, ETF flows, and macro market indicators through natural language.

Built by CoinGlass. Built for everyone.  
Originally recognized for its industry-leading crypto derivatives data, CoinGlass has expanded into a broader analytics platform for the full crypto market. CoinGlass API Skills is designed for traders, quantitative teams, institutions, developers, and data platforms that need structured, scalable, and analytics-focused access to crypto market intelligence across futures, spots, options, on-chain data, ETF data, indicators, news,, and realtime streams.

* * *

## About This Repository

Each skill lives in its own folder and contains a `API.md` file.

This repository is designed to help AI agents:

- understand user intent
- select the right skill
- map requests to the correct CoinGlass endpoint
- return structured results with useful explanations

Browse the existing skills to understand patterns and naming conventions before creating new ones.

* * *

## Installation

Get started with CoinGlass API Skills in a single command.

### Prerequisites

Before installing CoinGlass API Skills , ensure you have the following prerequisite:

- Node.js (version 22 or higher)

### Install Skills (npx skills)

Run the following command to add CoinGlass API Skills to your project:

```bash
npx skills add https://github.com/coinglass-official/coinglass-api-skills
```

### Install Skills (via GitHub Download ZIP)

1.Click the Code button in the top right corner and select Download ZIP.

2.Upload the extracted files to the corresponding platform/tool.

3.Follow the platform/tool's instructions for further configuration and installation.

Cursor Skills Installation Guide: https://cursor.com/docs/skills

Claude Skills Installation Guide: https://support.claude.com/en/articles/12512180-use-skills-in-claude

---

## How It Works

1. A user asks a market-data question in natural language
2. The AI agent selects the relevant skill
3. The skill maps the request to the appropriate CoinGlass endpoint
4. The agent returns structured data with a useful explanation

---

## Design Principles

CoinGlass API Skills is designed around a few simple principles:

* one domain, one skill where practical
* explicit routing from user intent to endpoint
* predictable parameter handling
* concise summaries by default
* raw data when requested
* transparent handling of limits, missing data, and errors

---

## Disclaimer

CoinGlass API Skills is an informational and integration tool only. CoinGlass API Skills and its outputs are provided on an “as is” and “as available” basis, without representation or warranty of any kind. It does not constitute investment, financial, trading, or any other form of advice, and does not represent a recommendation to buy, sell, or hold any assets.

Your use of CoinGlass API Skills and any information provided in connection with it is at your own risk, and you are solely responsible for evaluating the information provided and for any decisions made based on it. CoinGlass does not endorse or guarantee any AI-generated information. AI-generated content may include errors, biases, omissions, or outdated information.

CoinGlass is not responsible for any losses or damages incurred as a result of your use of or reliance on CoinGlass API Skills . CoinGlass may modify or discontinue the feature at its discretion, and functionality may vary depending on environment, configuration, or access scope. Market data may be delayed, incomplete, unavailable for certain plans, or subject to API limitations.
