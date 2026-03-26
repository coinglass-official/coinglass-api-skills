---
name: financial-calendar
description: Financial Calendar request using the CoinGlass API. 
metadata:
  version: 1.0.0
  author: CoinGlass
  openclaw:
    requires:
      bins:
        - curl
        - openssl
    homepage: https://github.com/coinglass-official/coinglass-api-skills/tree/main/other/financial-calendar/API.md
license: MIT
---

# CoinGlass Financial Calendar Skill

Financial Calendar request on CoinGLass API endpoints. Return the result in JSON format.


## Quick Reference

| API           | Endpoint                    | Function                                          |
| ------------- | --------------------------- | ------------------------------------------------- |
| Economic Data | /api/calendar/economic-data | This endpoint provides data for the economic data |

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
        
## API 1: Economic Data


**Supported Plans, Intervals, and Historical Data Access**

Hobbyist:Not Available
Startup:Available
Standard:Available
Professional:Available


### Method: GET

**URL**:
```
https://open-api-v4.coinglass.com//api/calendar/economic-data
```


**Headers**: `Content-Type: application/json`,`CG-API-KEY: ${YOUR_API_KEY}`


**Request Parameters**:

| Parameter  | Type    | Required | Description                                                                                            | Example value |
| ---------- | ------- | -------- | ------------------------------------------------------------------------------------------------------ | ------------- |
| start_time | integer | no       | Start timestamp in milliseconds. The maximum supported range is up to 15 days before the current time. |               |
| end_time   | integer | no       | End timestamp in milliseconds. The maximum supported range is up to 15 days after the current time.    |               |
| language   | string  | no       | Supported language :  'en' or  'zh'                                                                    |               |


**Example**:
```bash
curl 'https://open-api-v4.coinglass.com/api/calendar/economic-data' \
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
      "calendar_name": "Seasonally adjusted industrial output (MoM)(May)",
      "country_code": "SK",
      "country_name": "Korea",
      "data_effect": "Minor Impact",
      "forecast_value": "-0.1%",
      "revised_previous_value": "",
      "previous_value": "-0.9%",
      "publish_timestamp": 1751238000000,
      "published_value": "-2.9%",
      "importance_level": 1, //1,2,3
      "has_exact_publish_time": 1
    },
    {
      "calendar_name": "Industrial Output(YoY)(May)",
      "country_code": "SK",
      "country_name": "Korea",
      "data_effect": "Minor Impact",
      "forecast_value": "2.6%",
      "revised_previous_value": "",
      "previous_value": "4.9%",
      "publish_timestamp": 1751238000000,
      "published_value": "0.2%",
      "importance_level": 1,  //1,2,3
      "has_exact_publish_time": 1
    },
}
```

---
  