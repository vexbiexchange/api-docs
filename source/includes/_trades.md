# Trades

Fetch information about trades.

### Get Market Trades

```python
# Get Market Trades
from vexbi import API
api = API(app_id='APP_ID', secret_key='APP_SECRET')

query = {
  'limit': 80,
  'from': 10
}
trades = api.trades(market='btcmxn', query=query)
```

Get recent trades on market, each trade is included only once. Trades are sorted in reverse creation order.

##### HTTP Request
`GET https://www.vexbi.com/api/v2/trades`

##### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| market | String | Unique market id. It's always in the form of xxxyyy, where xxx is the base currency code, yyy is the quote currency code, e.g. 'btcmxn'. All available markets can be found at /api/v2/markets. |
| limit | Integer | **Optional.** Limit the number of returned trades. Default to 50. |
| timestamp | Integer | **Optional.** An integer represents the seconds elapsed since Unix epoch. If set, only trades executed before the time will be returned. |
| from | Integer | **Optional.** Trade id. If set, only trades created AFTER the trade will be returned. |
| to | Integer | **Optional.** Trade id. If set, only trades created BEFORE the trade will be returned. |
| order_by | String | **Optional.** If set, returned trades will be sorted in specific order, default to 'desc'. |

##### Responses

| Code | Description |
| ---- | ----------- |
| 200 | Get recent trades on market. |

### Get My Trades

```python
# Get My Trades
from vexbi import API
api = API(app_id='APP_ID', secret_key='APP_SECRET')

query = {
  'from': 10,
  'to': 120
}
trades = api.my_trades(market='btcmxn', query=query)
```

Get your executed trades. Trades are sorted in reverse creation order.

##### HTTP Request
`GET https://www.vexbi.com/api/v2/trades/my`

##### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| market | String | Unique market id. It's always in the form of xxxyyy, where xxx is the base currency code, yyy is the quote currency code, e.g. 'btcmxn'. All available markets can be found at /api/v2/markets. |
| limit | Integer | **Optional.** Limit the number of returned trades. Default to 50. |
| timestamp | Integer | **Optional.** An integer represents the seconds elapsed since Unix epoch. If set, only trades executed before the time will be returned. |
| from | Integer | **Optional.** Trade id. If set, only trades created AFTER the trade will be returned. |
| to | Integer | **Optional.** Trade id. If set, only trades created BEFORE the trade will be returned. |
| order_by | String | **Optional.** If set, returned trades will be sorted in specific order, default to 'desc'. |

##### Responses

| Code | Description |
| ---- | ----------- |
| 200 | Get your executed trades. |
