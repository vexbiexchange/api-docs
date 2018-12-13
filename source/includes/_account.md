# Account

Interact with your profile and accounts.

### Get Account Info

```python
from vexbi import API
api = API(app_id='APP_ID', secret_key='APP_SECRET')

account_info = api.get_account_info()
email = account_info.email
```

Get your profile and accounts info.

##### HTTP Request
`GET https://www.vexbi.com/api/v2/members/me`

##### Responses

| Code | Description |
| ---- | ----------- |
| 200 | Get your profile and accounts info. |
