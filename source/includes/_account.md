# Account

Interact with your profile and accounts.

### Get Account Info

```python
from vexbi import Vexbi
client = Client(app_id='APP_ID', secret_key='APP_SECRET')

order = Vexbi.get_account_info(client)
```

Get your profile and accounts info.

##### HTTP Request
`GET https://www.vexbi.com/api/v2/members/me`

##### Responses

| Code | Description |
| ---- | ----------- |
| 200 | Get your profile and accounts info. |
