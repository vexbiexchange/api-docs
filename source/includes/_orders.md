# Orders

Managing orders programatically can be done with the following methods.

## Create Order

```python
# Create Order
from vexbi import API
api = API(app_id='APP_ID', secret_key='APP_SECRET')

order_data = {
  'market': 'btcmxn', 
  'side': 'sell',
  'volume': '0.05',
  'price': '70000.0'
}
order = api.create_order(order_data=order_data)
```

> Response from Vexbi:

```json
{
  "id": 50790,
  "side": "sell",
  "ord_type": "limit",
  "price": "70000.0",
  "avg_price": "0.0",
  "state": "wait",
  "market": "btcmxn",
  "created_at": "2018-12-14T13:19:24-06:00",
  "volume": "0.05",
  "remaining_volume": "0.05",
  "executed_volume": "0.0",
  "trades_count": 0
}
```

Create and place a new sell/buy order.

##### HTTP Request
`POST https://www.vexbi.com/api/v2/orders`

##### Parameters

| Field | Type | Description |
| ----- | ---- | ----------- |
| market | String | Unique market id. It's always in the form of xxxyyy, where xxx is the base currency code, yyy is the quote currency code, e.g. 'btcmxn'. All available markets can be found at /api/v2/markets. | Yes | string |
| side | String | Either 'sell' or 'buy'. |
| volume | String | The amount user want to sell/buy. An order could be partially executed, e.g. an order sell 5 btc can be matched with a buy 3 btc order, left 2 btc to be sold; in this case the order's volume would be '5.0', its remaining_volume would be '2.0', its executed volume is '3.0'. |
| price | String | **Optional.** (Defaults to market price) Price for each unit. e.g. If you want to sell/buy 1 btc at 3000 usd, the price is '3000.0' |

##### Responses

| Code | Description |
| ---- | ----------- |
| 201 | Create a Sell/Buy order. |

## Cancel an Order

```python
# Cancel Order
from vexbi import API
api = API(app_id='APP_ID', secret_key='APP_SECRET')

order = api.delete_order(order_id=10)
```

> Response from Vexbi:

```json
{
  "id": 50790,
  "side": "sell",
  "ord_type": "limit",
  "price": "70000.0",
  "avg_price": "0.0",
  "state": "wait",
  "market": "btcmxn",
  "created_at": "2018-12-14T13:19:24-06:00",
  "volume": "0.05",
  "remaining_volume": "0.05",
  "executed_volume": "0.0",
  "trades_count": 0
}
```

Cancel an order already placed.

##### HTTP Request
`POST https://www.vexbi.com/api/v2/order/delete`

##### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| id | Integer | Unique order id. |

##### Responses

| Code | Description |
| ---- | ----------- |
| 201 | Cancel an order. |

## Cancel All Orders

```python
# Cancel All Orders
from vexbi import API
api = API(app_id='APP_ID', secret_key='APP_SECRET')

clear_selection = { 'side': 'sell' }
result = api.clear_all(data=clear_selection)
```

> Response from Vexbi:

```json
[
  {
    "id": 50789,
    "side": "sell",
    "ord_type": "limit",
    "price": "70000.0",
    "avg_price": "0.0",
    "state": "wait",
    "market": "btcmxn",
    "created_at": "2018-12-14T13:16:34-06:00",
    "volume": "0.05",
    "remaining_volume": "0.05",
    "executed_volume": "0.0",
    "trades_count": 0
  },
  {
    "id": 50853,
    ...
  },
  ...
]
```

Cancel all your existent orders or for a specific side.

##### HTTP Request
`POST https://www.vexbi.com/api/v2/orders/clear`

##### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| side | String | **Optional.** (`sell` or `buy`) If present, only sell orders (asks) or buy orders (bids) will be canncelled. |

##### Responses

| Code | Description |
| ---- | ----------- |
| 201 | Cancel all my orders. |

## Get Order

```python
# Get Order
from vexbi import API
api = API(app_id='APP_ID', secret_key='APP_SECRET')

order = api.get_order(order_id=50792)
order["id"]
order["remaining_volume"]
```

> Response from Vexbi:

```json
{
  "id": 50792,
  "side": "sell",
  "ord_type": "limit",
  "price": "70000.0",
  "avg_price": "0.0",
  "state": "wait",
  "market": "btcmxn",
  "created_at": "2018-12-14T13:19:24-06:00",
  "volume": "0.05",
  "remaining_volume": "0.05",
  "executed_volume": "0.0",
  "trades_count": 0,
  "trades": []
}
```


Get an existent order.

##### HTTP Request
`GET https://www.vexbi.com/api/v2/order?id=_ID_`

##### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| id | String | Unique order id. |

##### Responses

| Code | Description |
| ---- | ----------- |
| 200 | Get an orders. |

## Get Orders (paginated)

```python
# Get Orders (Paginated)
from vexbi import API
api = API(app_id='APP_ID', secret_key='APP_SECRET')

query = { 'limit': 30 }
orders = api.get_orders(market='btcmxn', query=query)
```

> Response from Vexbi:

```json
[
  {
    "id": 50792,
    "side": "sell",
    "ord_type": "limit",
    "price": "70000.0",
    "avg_price": "0.0",
    "state": "wait",
    "market": "btcmxn",
    "created_at": "2018-12-14T13:19:24-06:00",
    "volume": "0.05",
    "remaining_volume": "0.05",
    "executed_volume": "0.0",
    "trades_count": 0
  },
  ...
]
```

Get a list of existent orders.

##### HTTP Request
`GET https://www.vexbi.com/api/v2/orders?market=_MKT_&limit=_LIMIT_`

##### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| market | String | Unique market id. It's always in the form of xxxyyy, where xxx is the base currency code, yyy is the quote currency code, e.g. 'btcmxn'. All available markets can be found at /api/v2/markets. |
| state | String | **Optional.** Filter order by state, default to 'wait' (active orders). |
| limit | Integer | **Optional.** (Defaults to 100) Limit the number of returned orders. |
| page | Integer | **Optional.** Specify the page of paginated results. |
| order_by | String | **Optional.** (Defaults to asc) If set, returned orders will be sorted in specific order. |

##### Responses

| Code | Description |
| ---- | ----------- |
| 200 | Get a list of orders. |
