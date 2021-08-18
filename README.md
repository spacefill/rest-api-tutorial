# SpaceFill OMS REST API usage tutorial

For more information about OMS (Order Management System) see this Wikipedia article: https://en.wikipedia.org/wiki/Order_management_system

This tutorial is based on [`curl`](https://en.wikipedia.org/wiki/CURL) command line tool.

Before to build and execute HTTP request, you need to take some data in https://app.spacefill.fr

- Your API Token

Before create a `orders`, we need to create some `master-items`:

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
