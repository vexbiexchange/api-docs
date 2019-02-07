# Trades

Fetch information about trades.

## Get Market Trades

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
> Response from Vexbi
```json
[
  {
    "id": 563,
    "price": "71285.84",
    "volume": "0.1",
    "funds": "7128.58",
    "market": "btcmxn",
    "created_at": "2018-12-14T12:46:15-06:00",
    "side": null,
    "type": "buy"
  },
  {
    "id": 562,
    "price": "68668.71",
    "volume": "0.00343854",
    "funds": "236.12",
    "market": "btcmxn",
    "created_at": "2018-12-12T16:48:18-06:00",
    "side": null,
    "type": "sell"
  },
  ...
]
```

Get recent trades (each trade is included only once). Trades are sorted in order of most recent to least recent.

##### HTTP Request
`GET https://www.vexbi.com/api/v2/trades`

##### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| market | String | Unique market id. It's always in the form of xxxyyy, where xxx is the base currency code, yyy is the quote currency code, for example 'BTCMXN'. All available markets can be found at /api/v2/markets. |
| limit | Integer | **Optional.** Limit the number of returned trades. Default to 50. |
| timestamp | Integer | **Optional.** An integer represents the seconds elapsed since UNIX Epoch. If set, only trades executed before the time will be returned. |
| from | Integer | **Optional.** Trade id. If set, only trades created AFTER this will be returned. |
| to | Integer | **Optional.** Trade id. If set, only trades created BEFORE this will be returned. |
| order_by | String | **Optional.** If set, returned trades will be sorted in a specific order, defaulting to ‘desc’ (descending). |

##### Responses

| Code | Description |
| ---- | ----------- |
| 200 | Get recent trades on market. |

## Get My Trades

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

> Response from Vexbi:

```json
[
  {
    "id": 563,
    "price": "71285.84",
    "volume": "0.1",
    "funds": "7128.58",
    "market": "btcmxn",
    "created_at": "2018-12-14T12:46:15-06:00",
    "side": "bid",
    "order_id": 50787,
    "type": "buy"
  },
  {
    "id": 46,
    "price": "185000.00",
    "volume": "0.001",
    "funds": "185.00",
    "market": "btcmxn",
    "created_at": "2018-11-06T18:48:50-06:00",
    "side": "ask",
    "order_id": 1605,
    "type": "buy"
  },
  ...
]
```

Get your executed trades. Trades are sorted in order of most to least recent.

##### HTTP Request
`GET https://www.vexbi.com/api/v2/trades/my`

##### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| market | String | Unique market id. It's always in the form of xxxyyy, where xxx is the base currency code, yyy is the quote currency code, for example 'BTCMXN'. All available markets can be found at /api/v2/markets. |
| limit | Integer | **Optional.** Limit the number of returned trades. Default to 50. |
| timestamp | Integer | **Optional.** An integer represents the seconds elapsed since UNIX Epoch. If set, only trades executed before the time will be returned. |
| from | Integer | **Optional.** Trade id. If set, only trades created AFTER this will be returned. |
| to | Integer | **Optional.** Trade id. If set, only trades created BEFORE this will be returned. |
| order_by | String | **Optional.** If set, returned trades will be sorted in a specific order, defaulting to ‘desc’ (descending). |

##### Responses

| Code | Description |
| ---- | ----------- |
| 200 | Get your executed trades. |
