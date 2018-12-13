# Trades

Fetch information about trades.

### Get Market Trades

```python
from vexbi import API
api = API(app_id='APP_ID', secret_key='APP_SECRET')

trades = api.trades()
```

Get recent trades on market, each trade is included only once. Trades are sorted in reverse creation order.

##### HTTP Request
`GET https://www.vexbi.com/api/v2/trades`

##### Responses

| Code | Description |
| ---- | ----------- |
| 200 | Get recent trades on market. |

### Get My Trades

```python
from vexbi import API
api = API(app_id='APP_ID', secret_key='APP_SECRET')

trades = api.my_trades()
```

Get your executed trades. Trades are sorted in reverse creation order.

##### HTTP Request
`GET https://www.vexbi.com/api/v2/trades/my`

##### Responses

| Code | Description |
| ---- | ----------- |
| 200 | Get your executed trades. |
