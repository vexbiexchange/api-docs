# Account

Interact with your profile and accounts.

## Get Account Info

```python
# Get Account Info
from vexbi import API
api = API(app_id='APP_ID', secret_key='APP_SECRET')

account_info = api.get_account_info()
email = account_info["email"]
```

> Response from Vexbi:

```json
{
  "sn": "SNDF3EF88F00",
  "email": "your@email.com",
  "accounts": [
    {
      "currency": "xrp",
      "balance": "5000.0",
      "locked": "0.0"
    },
    {
      "currency": "bch",
      "balance": "0.0574985",
      "locked": "0.0315"
    },
    {
      "currency": "ltc",
      "balance": "3.99",
      "locked": "0.0"
    },
    {
      "currency": "btc",
      "balance": "0.13012197",
      "locked": "0.05"
    },
    {
      "currency": "mxn",
      "balance": "97969.238561911",
      "locked": "0.0"
    }
  ]
}
```
Get your profile and accounts info.

##### HTTP Request
`GET https://www.vexbi.com/api/v2/members/me`

##### Responses

| Code | Description |
| ---- | ----------- |
| 200 | Get your profile and accounts info. |
