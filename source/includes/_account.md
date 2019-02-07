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
      "balance": "5000.00000000",
      "locked": "0.00000000"
    },
    {
      "currency": "bch",
      "balance": "0.05749850",
      "locked": "0.03150000"
    },
    {
      "currency": "ltc",
      "balance": "3.99000000",
      "locked": "0.00000000"
    },
    {
      "currency": "btc",
      "balance": "0.13012197",
      "locked": "0.05000000"
    },
    {
      "currency": "mxn",
      "balance": "97969.23",
      "locked": "0.00"
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
