# Orders

Managing orders programatically can be done with the following methods.

### Create Order

```python
from vexbi import API
api = API(app_id='APP_ID', secret_key='APP_SECRET')

order = api.create_order(
  market='btcusd', 
  side='sell',
  volume='3.0',
  price='5000.0'
)
```

Create and place a new sell/buy order.

##### HTTP Request
`POST https://www.vexbi.com/api/v2/orders`

##### Parameters

| Field | Type | Description |
| ----- | ---- | ----------- |
| market | String | Unique market id. It's always in the form of xxxyyy, where xxx is the base currency code, yyy is the quote currency code, e.g. 'btcusd'. All available markets can be found at /api/v2/markets. | Yes | string |
| side | String | Either 'sell' or 'buy'. |
| volume | String | The amount user want to sell/buy. An order could be partially executed, e.g. an order sell 5 btc can be matched with a buy 3 btc order, left 2 btc to be sold; in this case the order's volume would be '5.0', its remaining_volume would be '2.0', its executed volume is '3.0'. |
| price | String | **Optional.** (Defaults to market price) Price for each unit. e.g. If you want to sell/buy 1 btc at 3000 usd, the price is '3000.0' |

##### Responses

| Code | Description |
| ---- | ----------- |
| 201 | Create a Sell/Buy order. |

### Cancel an Order

```python
from vexbi import API
api = API(app_id='APP_ID', secret_key='APP_SECRET')

order = api.delete_order(10)
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

### Cancel All Orders

```python
from vexbi import API
api = API(app_id='APP_ID', secret_key='APP_SECRET')

result = api.clear_all('sell')
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

### Get Order

```python
from vexbi import API
api = API(app_id='APP_ID', secret_key='APP_SECRET')

order = api.get_order(10)
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

### Get Orders (paginated)

```python
from vexbi import API
api = API(app_id='APP_ID', secret_key='APP_SECRET')

orders = api.get_orders(
  market='btcusd',
  limit='30',
)
```

Get a list of existent orders.

##### HTTP Request
`GET https://www.vexbi.com/api/v2/orders?market=_MKT_&limit=_LIMIT_`

##### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| market | String | Unique market id. It's always in the form of xxxyyy, where xxx is the base currency code, yyy is the quote currency code, e.g. 'btcusd'. All available markets can be found at /api/v2/markets. |
| state | String | **Optional.** Filter order by state, default to 'wait' (active orders). |
| limit | Integer | **Optional.** (Defaults to 100) Limit the number of returned orders. |
| page | Integer | **Optional.** Specify the page of paginated results. |
| order_by | String | **Optional.** (Defaults to asc) If set, returned orders will be sorted in specific order. |

##### Responses

| Code | Description |
| ---- | ----------- |
| 200 | Get a list of orders. |
