# Markets

Fetch information about markets.

### Get Available Markets

```python
from vexbi import API
api = API(app_id='APP_ID', secret_key='APP_SECRET')

markets = api.get_available_markets()
```

Get all available markets.

##### HTTP Request
`GET https://www.vexbi.com/api/v2/markets`

##### Responses

| Code | Description |
| ---- | ----------- |
| 200 | Get all available markets. |

### Get Tickers

```python
from vexbi import API
api = API(app_id='APP_ID', secret_key='APP_SECRET')

tickers = api.tickers()
```

Get tickers for all markets.

##### HTTP Request
`GET https://www.vexbi.com/api/v2/tickers`

##### Responses

| Code | Description |
| ---- | ----------- |
| 200 | Get tickers for all markets. |
