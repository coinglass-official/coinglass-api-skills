---
name: news
description: News request using the CoinGlass API. 
metadata:
  version: 1.0.0
  author: CoinGlass
  openclaw:
    requires:
      bins:
        - curl
        - openssl
    homepage: https://github.com/coinglass-official/coinglass-api-skills/tree/main/other/news/API.md
license: MIT
---

# CoinGlass News Skill

News request on CoinGLass API endpoints. Return the result in JSON format.


## Quick Reference

| API  | Endpoint          | Function                                                               |
| ---- | ----------------- | ---------------------------------------------------------------------- |
| News | /api/article/list | This endpoint provides an instant news (up to nearly 1000 news items). |

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
        
## API 1: News


**Supported Plans, Intervals, and Historical Data Access**

Hobbyist:Not Available
Startup:Available
Standard:Available
Professional:Available


### Method: GET

**URL**:
```
https://open-api-v4.coinglass.com//api/article/list
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

| Parameter  | Type    | Required | Description                                            | Example value |
| ---------- | ------- | -------- | ------------------------------------------------------ | ------------- |
| start_time | integer | no       | Start timestamp in milliseconds (e.g., 1641522717000). |               |
| end_time   | integer | no       | End timestamp in milliseconds (e.g., 1641522717000).   |               |
| language   | string  | no       | Supported languages: 'en', 'zh', 'zh-tw'               |               |
| page       | integer | no       | Current page number                                    |               |
| per_page   | integer | no       | Number of items returned per page                      |               |


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/article/list' \
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
      "article_picture":  "https://images.cointelegraph.com/images/528_aHR0cHM6Ly9zMy5jb2ludGVsZWdyYXBoLmNvbS91cGxvYWRzLzIwMjUtMDIvMDE5NTNkOTUtOTEyYi03MTE4LWE3NTEtNDRjNDExZWUzNmMy.jpg",  //Article Picture
      "article_title": "Crypto ETFs ‘punching above weight’ as almost half of ETF investers plan buys", // Article Title
      "article_content": "<p>Nearly h \n</blockquote> <!---->",  //Article Content
      "source_name": "COINTELEGRAPH",   // Source Name
      "source_website_logo": "https://cdn.coinglasscdn.com/news/coin_telegraph.png",   //Source Website Logo
      "article_release_time": 1762482358000, //Article Release Time
      "article_description": "<p>Bloomberg ETF analyst Eric Balchunas said it was “shocking” to see Schwab’s findings that crypto ETF investments could be on par with those in bond ETFs.</p>" // Article Description
    },

    {
      "article_picture": "https://images.cointelegraph.com/images/528_aHR0cHM6Ly9zMy5jb2ludGVsZWdyYXBoLmNvbS91cGxvYWRzLzIwMjUtMTEvMDE5YTViM2MtODFkOC03NWFhLTg2MjEtOGEyYmZjMDJhZDk0.jpg",
      "article_title": "Bitcoin at $100K is ‘speed bump’ to $56K, but data signals no signs of panic",
      "article_content": "<p data-ct-non-bby 2030.</p> <!---->",
      "source_name": "COINTELEGRAPH",
      "source_website_logo": "https://cdn.coinglasscdn.com/news/coin_telegraph.png",
      "article_release_time": 1762478945000,
      "article_description": "<p>Bloomberg analyst Mike McGlone says Bitcoin hitting $100,000 is “a speed bump” to $56,000, but other analysts say Bitcoin has bottomed out.</p>"
    },
  ]
}
```

---
  