# SpaceFill OMS REST API usage tutorial

For more information about OMS (Order Management System) see this Wikipedia article: https://en.wikipedia.org/wiki/Order_management_system

This tutorial is based on [`curl`](https://en.wikipedia.org/wiki/CURL) command line tool.

Before building and executing any HTTP request, you need to retrieve some data from https://app.spacefill.fr

- Your API Token
- The warehouse id where you want store your merchandises

Before creating an `orders`, we need to create some `master-items`:

```sh
curl -X 'POST' \
  'https://api.spacefill.fr/v1/logistic_management/master_items/' \
  -H 'accept: application/json' \
  -H 'x_token: secret' \
  -H 'Content-Type: application/json' \
  -d '{
  "item_reference": "POTATOES2KG",
  "designation": "Potatoes 2Kg",
  "each_barcode_type": "EAN",
  "each_barcode": "5901234123457",
  "each_quantity_by_pallet": 50,
  "each_is_stackable": true,
  "pallet_is_stackable": false,
  "each_width_in_cm": 30,
  "each_length_in_cm": 30,
  "each_height_in_cm": 30,
  "pallet_width_in_cm": 80,
  "pallet_length_in_cm": 120,
  "pallet_height_in_cm": 100,
  "pallet_gross_weight_in_kg": null,
  "pallet_net_weight_in_kg": 100,
  "each_gross_weight_in_kg": 2
}'
```

```sh
curl -X 'POST' \
  'https://api.spacefill.fr/v1/logistic_management/master_items/' \
  -H 'accept: application/json' \
  -H 'x_token: secret' \
  -H 'Content-Type: application/json' \
  -d '{
  "item_reference": "CARROT1KG",
  "designation": "Carrot 1Kg",
  "each_barcode_type": "EAN",
  "each_barcode": "5901834823459",
  "each_quantity_by_pallet": 100,
  "each_is_stackable": true,
  "pallet_is_stackable": false,
  "each_width_in_cm": 15,
  "each_length_in_cm": 10,
  "each_height_in_cm": 20,
  "pallet_width_in_cm": 80,
  "pallet_length_in_cm": 120,
  "pallet_height_in_cm": 100,
  "pallet_gross_weight_in_kg": null,
  "pallet_net_weight_in_kg": 70,
  "each_gross_weight_in_kg": 1
}'
```

After these `master-items` creation, we can create an `orders` entry with those items:

```sh
curl -X 'POST' \
  'https://api.spacefill.fr/v1/logistic_management/orders/' \
  -H 'accept: application/json' \
  -H 'x_token: secret' \
  -H 'Content-Type: application/json' \
  -d '{
  "shipper_order_reference": "BL20210818001",
  "warehouse_id": "3fa85f64-5717-4562-b3fc-2c963f66afa6",
  "order_type": "ENTRY",
  "planned_execution_datetime_range": {
    "datetime_from": "2021-08-20T08:00:00",
    "datetime_to": "2021-08-20T12:00:00"
  },
  "items": [
    {
      "item_reference": "POTATOES2KG",
      "item_packaging_type": "PALLET",
      "expected_quantity": 10
    },
    {
      "item_reference": "CARROT1KG",
      "item_packaging_type": "PALLET",
      "expected_quantity": 15
    },
  ]
}'
```

## How can a client get orders.status update (events) information?

Two implementations are possible: « Pull method ([polling](https://en.wikipedia.org/wiki/Polling_(computer_science))) » or « [Push method](https://en.wikipedia.org/wiki/Push_technology) ([with Webhook](https://en.wikipedia.org/wiki/Webhook)) »

### Client pull method

Client execute for instance all 5min this HTTP request with `since` parameter with value `NOW - 6mins` :

```sh
curl -X 'POST' \
  'https://api.spacefill.fr/v1/logistic_management/orders/?since=20210910201000' \
  -H 'accept: application/json' \
  -H 'x_token: secret' \
{
  "total": 0,
  "items": [
  ]
}
```

If the result is empty, the client has nothing to do.

5 minutes later, the client executes the same request again:

```sh
curl -X 'POST' \
  'https://api.spacefill.fr/v1/logistic_management/orders/?since=20210910201000' \
  -H 'accept: application/json' \
  -H 'x_token: secret' \
{
  "total": 1,
  "items": [
    {
      "id": "3fa85f64-5717-4562-b3fc-2c963f66afa6",
      ...
      "status": "COMPLETED_ORDER_STATE",
      ...
    }
  ]
}
```

Now, in this example, there is one item in response, so the client can handle this item, read the new status value...

### Server push method with webhook

The client can set up a webhook with the following HTTP request:

```sh
$ curl -X 'POST' \
  'http://127.0.0.1:5004/v1/logistic_management/orders/hooks' \
  -H 'accept: application/json' \
  -H 'x_token: secret' \
  -H 'Content-Type: application/json' \
  -d '{
  "target_url": "https://example.com/foobar/"
}'
{
  "result": "ok"
}
```

Then, with this webhook configured, every order update will send a POST HTTP request to https://example.com/foobar/ url with the order's data in POST payload, so that the client can handle all order update events in "real time".
