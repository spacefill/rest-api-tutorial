# Orders CRUD

See complete orders API endpoints on https://api.sandbox.spacefill.fr/docs

* [Examples](#examples)
  * [Create](#create)
  * [Get](#get)
* [List](#list)

## Examples

In the following examples, each request uses [`jq`](https://stedolan.github.io/jq/) to parse and render the JSON, don't forget to remove it if you do some copy/paste.

### Create

To create an entry `order` with two items:

```sh
$ curl -sLX 'POST' \
  'https://api.sandbox.spacefill.fr/v1/logistic_management/orders/entry' \
  -H 'accept: application/json' \
  -H 'Authorization: Bearer secret' \
  -H 'Content-Type: application/json' \
  -d '{
  "shipper_order_reference": "REF_01",
  "warehouse_id": "d8bdc728-242b-4039-99a3-0aa239650011",
  "comment": "Additional comment",
  "planned_execution_datetime_range": {
    "datetime_from": "2021-09-28T15:12:41.538Z",
    "datetime_to": "2021-09-28T15:12:41.538Z"
  },
  "carrier_name": "Carrier X",
  "carrier_phone_number": "+33610101010",
  "transport_management_owner": "PROVIDER",
  "entry_expeditor": "Expeditor X",
  "entry_expeditor_address_line1": "123 Boulevard X",
  "entry_expeditor_address_line2": "",
  "entry_expeditor_address_line3": "",
  "entry_expeditor_address_zip": "75020",
  "entry_expeditor_address_city": "Paris",
  "entry_expeditor_address_country": "France",
  "entry_expeditor_planned_datetime_range": {
    "datetime_from": "2021-09-28T15:12:41.538Z",
    "datetime_to": "2021-09-28T15:12:41.538Z"
  }
  "order_items": [
    {
      "master_item_id": "13acc10a-a6ab-4099-b600-fb33fa6c0001",
      "batch_id": "e4f77256-304a-4911-a1eb-9f6d47ca0001",
      "item_packaging_type": "PALLET",
      "expected_quantity": 1
    },
    {
      "master_item_id": "13acc10a-a6ab-4099-b600-fb33fa6c0002",
      "batch_id": "e4f77256-304a-4911-a1eb-9f6d47ca0005",
      "item_packaging_type": "PALLET",
      "expected_quantity": 1
    }
  ]
}' | jq
{
  "id": "78712692-e622-4a9c-a746-3222486c9877",
  "iid": null,
  "shipper_order_reference": "REF_01",
  "customer_id": "1de9c987-08ab-32fe-e218-89c124cd0001",
  "warehouse_id": "d8bdc728-242b-4039-99a3-0aa239650011",
  "order_type": "ENTRY",
  "status": "WAREHOUSE_NEEDS_TO_CONFIRM_PLANNED_EXECUTION_DATE_STATE",
  "comment": "Additional comment",
  "planned_execution_datetime_range": {
    "datetime_from": "2021-09-28T15:12:41.538000+00:00",
    "datetime_to": "2021-09-28T15:12:41.538000+00:00"
  },
  "effective_executed_at": null,
  "carrier_name": "Carrier X",
  "carrier_phone_number": "+33610101010",
  "transport_management_owner": "PROVIDER",
  "entry_expeditor": "Expeditor X",
  "entry_expeditor_address_line1": "123 Boulevard X",
  "entry_expeditor_address_line2": null,
  "entry_expeditor_address_line3": null,
  "entry_expeditor_address_zip": "75020",
  "entry_expeditor_address_city": "Paris",
  "entry_expeditor_address_country": "France",
  "entry_expeditor_planned_datetime_range": {
    "datetime_from": "2021-09-28T15:12:41.538000+00:00",
    "datetime_to": "2021-09-28T15:12:41.538000+00:00"
  },
  "exit_final_recipient": null,
  "exit_final_recipient_address_line1": null,
  "exit_final_recipient_address_line2": null,
  "exit_final_recipient_address_line3": null,
  "exit_final_recipient_address_zip": null,
  "exit_final_recipient_address_city": null,
  "exit_final_recipient_address_country": null,
  "exit_final_recipient_planned_datetime_range": null,
  "created_at": "2021-09-29T13:20:59.286179+00:00",
  "created_by": "4b03020e-007b-4430-86fd-dc409f6a0001",
  "updated_at": "2021-09-29T13:20:59.286179+00:00",
  "updated_by": "4b03020e-007b-4430-86fd-dc409f6a0001",
  "order_items": [
    {
      "id": "107c0bb0-4173-4d86-9685-8f49c4800001",
      "master_item_id": "13acc10a-a6ab-4099-b600-fb33fa6c0001",
      "batch_id": "e4f77256-304a-4911-a1eb-9f6d47ca0001",
      "position": 1,
      "item_packaging_type": "PALLET",
      "expected_quantity": 1,
      "actual_quantity": null
    },
    {
      "id": "107c0bb0-4173-4d86-9685-8f49c4800002",
      "master_item_id": "13acc10a-a6ab-4099-b600-fb33fa6c0002",
      "batch_id": "e4f77256-304a-4911-a1eb-9f6d47ca0005",
      "position": 2,
      "item_packaging_type": "PALLET",
      "expected_quantity": 1,
      "actual_quantity": null
    }
  ]
}
```

To create an exit `order` with two items:

```sh
$ curl -sLX 'POST' \
  'https://api.sandbox.spacefill.fr/v1/logistic_management/orders/exit' \
  -H 'accept: application/json' \
  -H 'Authorization: Bearer secret' \
  -H 'Content-Type: application/json' \
  -d '{
  "shipper_order_reference": "REF_01",
  "warehouse_id": "d8bdc728-242b-4039-99a3-0aa239650011",
  "comment": "Additional comment",
  "planned_execution_datetime_range": {
    "datetime_from": "2021-09-28T15:12:41.538Z",
    "datetime_to": "2021-09-28T15:12:41.538Z"
  },
  "carrier_name": "Carrier X",
  "carrier_phone_number": "+33610101010",
  "transport_management_owner": "PROVIDER",
  "exit_final_recipient": "Recipient X",
  "exit_final_recipient_address_line1": "123 Boulevard X",
  "exit_final_recipient_address_line2": "",
  "exit_final_recipient_address_line3": "",
  "exit_final_recipient_address_zip": "75020",
  "exit_final_recipient_address_city": "Paris",
  "exit_final_recipient_address_country": "France",
  "exit_final_recipient_planned_datetime_range": {
    "datetime_from": "2021-09-28T15:12:41.538Z",
    "datetime_to": "2021-09-28T15:12:41.538Z"
  }
  "order_items": [
    {
      "master_item_id": "13acc10a-a6ab-4099-b600-fb33fa6c0001",
      "batch_id": "e4f77256-304a-4911-a1eb-9f6d47ca0001",
      "item_packaging_type": "PALLET",
      "expected_quantity": 1
    },
    {
      "master_item_id": "13acc10a-a6ab-4099-b600-fb33fa6c0002",
      "batch_id": "e4f77256-304a-4911-a1eb-9f6d47ca0005",
      "item_packaging_type": "PALLET",
      "expected_quantity": 1
    }
  ]
}' | jq
{
  "id": "64116f29-dd39-42df-ba15-23fce520d013",
  "iid": null,
  "shipper_order_reference": "REF_01",
  "customer_id": "1de9c987-08ab-32fe-e218-89c124cd0001",
  "warehouse_id": "d8bdc728-242b-4039-99a3-0aa239650011",
  "order_type": "EXIT",
  "status": "WAREHOUSE_NEEDS_TO_CONFIRM_PLANNED_EXECUTION_DATE_STATE",
  "comment": "Additional comment",
  "planned_execution_datetime_range": {
    "datetime_from": "2021-09-28T15:12:41.538000+00:00",
    "datetime_to": "2021-09-28T15:12:41.538000+00:00"
  },
  "effective_executed_at": null,
  "carrier_name": "Carrier X",
  "carrier_phone_number": "+33610101010",
  "transport_management_owner": "PROVIDER",
  "entry_expeditor": null,
  "entry_expeditor_address_line1": null,
  "entry_expeditor_address_line2": null,
  "entry_expeditor_address_line3": null,
  "entry_expeditor_address_zip": null,
  "entry_expeditor_address_city": null,
  "entry_expeditor_address_country": null,
  "entry_expeditor_planned_datetime_range": null,
  "exit_final_recipient": "Recipient X",
  "exit_final_recipient_address_line1": "123 Boulevard X",
  "exit_final_recipient_address_line2": null,
  "exit_final_recipient_address_line3": null,
  "exit_final_recipient_address_zip": "75020",
  "exit_final_recipient_address_city": "Paris",
  "exit_final_recipient_address_country": "France",
  "exit_final_recipient_planned_datetime_range": {
    "datetime_from": "2021-09-28T15:12:41.538000+00:00",
    "datetime_to": "2021-09-28T15:12:41.538000+00:00"
  },
  "created_at": "2021-09-29T13:24:39.913629+00:00",
  "created_by": "4b03020e-007b-4430-86fd-dc409f6a0001",
  "updated_at": "2021-09-29T13:24:39.913629+00:00",
  "updated_by": "4b03020e-007b-4430-86fd-dc409f6a0001",
  "order_items": [
    {
      "master_item_id": "13acc10a-a6ab-4099-b600-fb33fa6c0001",
      "batch_id": "e4f77256-304a-4911-a1eb-9f6d47ca0001",
      "item_packaging_type": "PALLET",
      "expected_quantity": 1
    },
    {
      "master_item_id": "13acc10a-a6ab-4099-b600-fb33fa6c0002",
      "batch_id": "e4f77256-304a-4911-a1eb-9f6d47ca0005",
      "item_packaging_type": "PALLET",
      "expected_quantity": 1
    }
  ]
}
```

### Get

```sh
$ curl -sLX 'GET' \
  'https://api.sandbox.spacefill.fr/v1/logistic_management/orders/701d1c8e-f77d-4ec1-9242-ad9896d50001' \
  -H 'accept: application/json' \
  -H 'Authorization: Bearer secret'
{
  "id": "701d1c8e-f77d-4ec1-9242-ad9896d50001",
  "iid": "MV-20200105-001",
  "shipper_order_reference": "reference 1 by shipper",
  "customer_id": "1de9c987-08ab-32fe-e218-89c124cd0001",
  "warehouse_id": "d8bdc728-242b-4039-99a3-0aa239650001",
  "order_type": "ENTRY",
  "status": "COMPLETED_ORDER_STATE",
  "comment": "This is a comment 1",
  "planned_execution_datetime_range": {
    "datetime_from": "2020-01-05T07:00:00+00:00",
    "datetime_to": "2020-01-05T11:00:00+00:00"
  },
  "effective_executed_at": "2020-01-04T12:00:00+00:00",
  "carrier_name": "My carrier name",
  "carrier_phone_number": "+33666510584",
  "transport_management_owner": "PROVIDER",
  "entry_expeditor": "Entry expeditor 1",
  "entry_expeditor_address_line1": "33 Rue de la Folie Méricourt",
  "entry_expeditor_address_line2": null,
  "entry_expeditor_address_line3": null,
  "entry_expeditor_address_zip": "75011",
  "entry_expeditor_address_city": "Paris",
  "entry_expeditor_address_country": "France",
  "entry_expeditor_planned_datetime_range": {
    "datetime_from": "2020-01-05T07:00:00+00:00",
    "datetime_to": "2020-01-05T11:00:00+00:00"
  },
  "exit_final_recipient": null,
  "exit_final_recipient_address_line1": null,
  "exit_final_recipient_address_line2": null,
  "exit_final_recipient_address_line3": null,
  "exit_final_recipient_address_zip": null,
  "exit_final_recipient_address_city": null,
  "exit_final_recipient_address_country": null,
  "exit_final_recipient_planned_datetime_range": {
    "datetime_from": null,
    "datetime_to": null
  },
  "created_at": "2020-10-21T12:29:00+00:00",
  "created_by": "4b03020e-007b-4430-86fd-dc409f6a0001",
  "updated_at": "2021-09-29T10:43:13.595771+00:00",
  "updated_by": null,
  "order_items": [
    {
      "id": "107c0bb0-4173-4d86-9685-8f49c4800001",
      "master_item_id": "13acc10a-a6ab-4099-b600-fb33fa6c0001",
      "batch_id": "e4f77256-304a-4911-a1eb-9f6d47ca0001",
      "position": 1,
      "item_packaging_type": "PALLET",
      "expected_quantity": 5,
      "actual_quantity": 5
    },
    {
      "id": "107c0bb0-4173-4d86-9685-8f49c4800002",
      "master_item_id": "13acc10a-a6ab-4099-b600-fb33fa6c0002",
      "batch_id": "e4f77256-304a-4911-a1eb-9f6d47ca0005",
      "position": 2,
      "item_packaging_type": "CARDBOARD_BOX",
      "expected_quantity": 10,
      "actual_quantity": 9
    },
    {
      "id": "107c0bb0-4173-4d86-9685-8f49c4800003",
      "master_item_id": "13acc10a-a6ab-4099-b600-fb33fa6c0008",
      "batch_id": "e4f77256-304a-4911-a1eb-9f6d47ca0013",
      "position": 3,
      "item_packaging_type": "EACH",
      "expected_quantity": 20,
      "actual_quantity": 20
    },
    {
      "id": "107c0bb0-4173-4d86-9685-8f49c4800004",
      "master_item_id": "13acc10a-a6ab-4099-b600-fb33fa6c0009",
      "batch_id": null,
      "position": 4,
      "item_packaging_type": "PALLET",
      "expected_quantity": 30,
      "actual_quantity": 30
    }
  ]
}
```

## List

```sh
$  curl -sLX 'GET' \
  'https://api.sandbox.spacefill.fr/v1/logistic_management/orders' \
  -H 'accept: application/json' \
  -H 'Authorization: Bearer secret' | jq
{
  "total": 2,
  "items": [
    {
      "id": "701d1c8e-f77d-4ec1-9242-ad9896d50001",
      "iid": "MV-20200105-001",
      "shipper_order_reference": "reference 1 by shipper",
      "customer_id": "1de9c987-08ab-32fe-e218-89c124cd0001",
      "warehouse_id": "d8bdc728-242b-4039-99a3-0aa239650001",
      "order_type": "ENTRY",
      "status": "COMPLETED_ORDER_STATE",
      "comment": "This is a comment 1",
      "planned_execution_datetime_range": {
        "datetime_from": "2020-01-05T07:00:00+00:00",
        "datetime_to": "2020-01-05T11:00:00+00:00"
      },
      "effective_executed_at": "2020-01-04T12:00:00+00:00",
      "carrier_name": "My carrier name",
      "carrier_phone_number": "+33666510584",
      "transport_management_owner": "PROVIDER",
      "entry_expeditor": "Entry expeditor 1",
      "entry_expeditor_address_line1": "33 Rue de la Folie Méricourt",
      "entry_expeditor_address_line2": null,
      "entry_expeditor_address_line3": null,
      "entry_expeditor_address_zip": "75011",
      "entry_expeditor_address_city": "Paris",
      "entry_expeditor_address_country": "France",
      "entry_expeditor_planned_datetime_range": {
        "datetime_from": "2020-01-05T07:00:00+00:00",
        "datetime_to": "2020-01-05T11:00:00+00:00"
      },
      "exit_final_recipient": null,
      "exit_final_recipient_address_line1": null,
      "exit_final_recipient_address_line2": null,
      "exit_final_recipient_address_line3": null,
      "exit_final_recipient_address_zip": null,
      "exit_final_recipient_address_city": null,
      "exit_final_recipient_address_country": null,
      "exit_final_recipient_planned_datetime_range": {
        "datetime_from": null,
        "datetime_to": null
      },
      "created_at": "2020-10-21T12:29:00+00:00",
      "created_by": "4b03020e-007b-4430-86fd-dc409f6a0001",
      "updated_at": "2021-09-29T10:43:13.595771+00:00",
      "updated_by": null,
      "order_items": [
        {
          "id": "107c0bb0-4173-4d86-9685-8f49c4800001",
          "master_item_id": "13acc10a-a6ab-4099-b600-fb33fa6c0001",
          "batch_id": "e4f77256-304a-4911-a1eb-9f6d47ca0001",
          "position": 1,
          "item_packaging_type": "PALLET",
          "expected_quantity": 5,
          "actual_quantity": 5
        },
        {
          "id": "107c0bb0-4173-4d86-9685-8f49c4800002",
          "master_item_id": "13acc10a-a6ab-4099-b600-fb33fa6c0002",
          "batch_id": "e4f77256-304a-4911-a1eb-9f6d47ca0005",
          "position": 2,
          "item_packaging_type": "CARDBOARD_BOX",
          "expected_quantity": 10,
          "actual_quantity": 9
        },
        {
          "id": "107c0bb0-4173-4d86-9685-8f49c4800003",
          "master_item_id": "13acc10a-a6ab-4099-b600-fb33fa6c0008",
          "batch_id": "e4f77256-304a-4911-a1eb-9f6d47ca0013",
          "position": 3,
          "item_packaging_type": "EACH",
          "expected_quantity": 20,
          "actual_quantity": 20
        },
        {
          "id": "107c0bb0-4173-4d86-9685-8f49c4800004",
          "master_item_id": "13acc10a-a6ab-4099-b600-fb33fa6c0009",
          "batch_id": null,
          "position": 4,
          "item_packaging_type": "PALLET",
          "expected_quantity": 30,
          "actual_quantity": 30
        }
      ]
    },
    {
      "id": "701d1c8e-f77d-4ec1-9242-ad9896d50002",
      "iid": "MV-20200410-001",
      "shipper_order_reference": "reference 2 by shipper",
      "customer_id": "1de9c987-08ab-32fe-e218-89c124cd0001",
      "warehouse_id": "d8bdc728-242b-4039-99a3-0aa239650002",
      "order_type": "ENTRY",
      "status": "WAREHOUSE_NEEDS_TO_CONFIRM_PLANNED_EXECUTION_DATE_STATE",
      "comment": "This is a comment 2",
      "planned_execution_datetime_range": {
        "datetime_from": "2020-04-10T12:00:00+00:00",
        "datetime_to": "2020-04-10T16:00:00+00:00"
      },
      "effective_executed_at": "2019-02-06T11:00:00+00:00",
      "carrier_name": null,
      "carrier_phone_number": null,
      "transport_management_owner": "SHIPPER",
      "entry_expeditor": "Entry expeditor 2",
      "entry_expeditor_address_line1": null,
      "entry_expeditor_address_line2": null,
      "entry_expeditor_address_line3": null,
      "entry_expeditor_address_zip": null,
      "entry_expeditor_address_city": null,
      "entry_expeditor_address_country": null,
      "entry_expeditor_planned_datetime_range": {
        "datetime_from": null,
        "datetime_to": null
      },
      "exit_final_recipient": null,
      "exit_final_recipient_address_line1": null,
      "exit_final_recipient_address_line2": null,
      "exit_final_recipient_address_line3": null,
      "exit_final_recipient_address_zip": null,
      "exit_final_recipient_address_city": null,
      "exit_final_recipient_address_country": null,
      "exit_final_recipient_planned_datetime_range": {
        "datetime_from": null,
        "datetime_to": null
      },
      "created_at": "2020-11-22T12:16:00+00:00",
      "created_by": "72c27102-1d3b-4a51-9533-b8d1ead743b6",
      "updated_at": "2021-09-29T10:43:13.595771+00:00",
      "updated_by": null,
      "order_items": [
        {
          "id": "107c0bb0-4173-4d86-9685-8f49c4800005",
          "master_item_id": "13acc10a-a6ab-4099-b600-fb33fa6c0001",
          "batch_id": "e4f77256-304a-4911-a1eb-9f6d47ca0001",
          "position": 5,
          "item_packaging_type": "CARDBOARD_BOX",
          "expected_quantity": 40,
          "actual_quantity": 40
        },
        {
          "id": "107c0bb0-4173-4d86-9685-8f49c4800006",
          "master_item_id": "13acc10a-a6ab-4099-b600-fb33fa6c0002",
          "batch_id": "e4f77256-304a-4911-a1eb-9f6d47ca0005",
          "position": 6,
          "item_packaging_type": "EACH",
          "expected_quantity": 5,
          "actual_quantity": 5
        },
        {
          "id": "107c0bb0-4173-4d86-9685-8f49c4800007",
          "master_item_id": "13acc10a-a6ab-4099-b600-fb33fa6c0008",
          "batch_id": "e4f77256-304a-4911-a1eb-9f6d47ca0013",
          "position": 7,
          "item_packaging_type": "PALLET",
          "expected_quantity": 10,
          "actual_quantity": 9
        },
        {
          "id": "107c0bb0-4173-4d86-9685-8f49c4800008",
          "master_item_id": "13acc10a-a6ab-4099-b600-fb33fa6c0009",
          "batch_id": null,
          "position": 8,
          "item_packaging_type": "CARDBOARD_BOX",
          "expected_quantity": 20,
          "actual_quantity": 20
        }
      ]
    }
  ]
}
```
