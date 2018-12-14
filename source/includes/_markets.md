# Markets

Fetch information about markets.

## Get Available Markets

```python
# Get Available Markets
from vexbi import API
api = API(app_id='APP_ID', secret_key='APP_SECRET')

markets = api.get_available_markets()
```

> Response from Vexbi:

```json
[
  {
    "id": "btcmxn",
    "name": "BTC/MXN"
  },
  {
    "id": "ltcmxn",
    "name": "LTC/MXN"
  },
  {
    "id": "bchmxn",
    "name": "BCH/MXN"
  },
  {
    "id": "xrpmxn",
    "name": "XRP/MXN"
  }
]
```

Get all available markets.

##### HTTP Request
`GET https://www.vexbi.com/api/v2/markets`

##### Responses

| Code | Description |
| ---- | ----------- |
| 200 | Get all available markets. |

## Get Tickers

```python
# Get Tickers
from vexbi import API
api = API(app_id='APP_ID', secret_key='APP_SECRET')

tickers = api.tickers()
```

> Response from Vexbi:

```json

  "btcmxn": {
    "at": 1544814469,
    "ticker": {
      "buy": "68668.714434",
      "sell": "70000.0",
      "low": "71285.84813089",
      "high": "71285.84813089",
      "last": "71285.84813089",
      "vol": "0.1"
    }
  },
  "ltcmxn": {
    "at": 1544814469,
    "ticker": {
      ...
    }
  },
  "bchmxn": {
    "at": 1544814469,
    "ticker": {
      ...
    }
  },
  "xrpmxn": {
    "at": 1544814469,
    "ticker": {
      ...
    }
  }
}
```

Get tickers for all markets.

##### HTTP Request
`GET https://www.vexbi.com/api/v2/tickers`

##### Responses

| Code | Description |
| ---- | ----------- |
| 200 | Get tickers for all markets. |
