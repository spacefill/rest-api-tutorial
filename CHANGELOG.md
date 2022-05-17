# api.spacefill.fr changelog

## 2022-05-18

Updated endpoints:

- `GET /v1/logistic_management/master_items/{master_item_id/}`: new `include_forecasted_quantity_at` url query parameter ([more informations](https://api.spacefill.fr/docs#/logistic-management/get_v1_logistic_management_master_item_v1_logistic_management_master_items__master_item_id___get))


## 2022-05-17

Updated endpoints:

- `GET /v1/logistic_management/master_items/`:
  - accept these new url query filters:
    - `edi_erp_id`
    - `edi_wms_id`
    - `edi_tms_id`
  - return these new fields in response:
    - `edi_erp_id`
    - `edi_wms_id`
    - `edi_tms_id`
- `POST /v1/logistic_management/master_items/`:
  - accept these new fields in request input:
    - `edi_erp_id`
    - `edi_wms_id`
    - `edi_tms_id`
  - return these new fields in response:
    - `edi_erp_id`
    - `edi_wms_id`
    - `edi_tms_id`
- `GET /v1/logistic_management/master_items/{master_item_id}/`: return these new fields in response:
  - `edi_erp_id`
  - `edi_wms_id`
  - `edi_tms_id`
- `PUT /v1/logistic_management/master_items/{master_item_id}/`:
  - accept these new fields in request input:
    - `edi_erp_id`
    - `edi_wms_id`
    - `edi_tms_id`
  - return these new fields in response:
    - `edi_erp_id`
    - `edi_wms_id`
    - `edi_tms_id`
- `PATCH /v1/logistic_management/master_items/{master_item_id}/`:
  - accept these new fields in request input:
    - `edi_erp_id`
    - `edi_wms_id`
    - `edi_tms_id`
  - return these new fields in response:
    - `edi_erp_id`
    - `edi_wms_id`
    - `edi_tms_id`
- `GET /v1/logistic_management/orders/`:
  - accept these new url query filters:
    - `edi_erp_id`
    - `edi_wms_id`
    - `edi_tms_id`
  - return these new fields in response:
    - `edi_erp_id`
    - `edi_wms_id`
    - `edi_tms_id`
- `GET /v1/logistic_management/orders/{order_id}/`: return these new fields in response:
  - `edi_erp_id`
  - `edi_wms_id`
  - `edi_tms_id`
- `POST /v1/logistic_management/orders/entry/`:
  - accept these new fields in request input:
    - `edi_erp_id`
    - `edi_wms_id`
    - `edi_tms_id`
  - return these new fields in response:
    - `edi_erp_id`
    - `edi_wms_id`
    - `edi_tms_id`
- `POST /v1/logistic_management/orders/exit/`:
  - accept these new fields in request input:
    - `edi_erp_id`
    - `edi_wms_id`
    - `edi_tms_id`
  - return these new fields in response:
    - `edi_erp_id`
    - `edi_wms_id`
    - `edi_tms_id`
- `PATCH /v1/logistic_management/orders/{order_id}/`: return these new fields in response:
  - `edi_erp_id`
  - `edi_wms_id`
  - `edi_tms_id`


## 2022-05-10

- Endpoint that is now implemented:
  - `POST /v1/logistic_management/orders/{order_id}/shipper_updates_order_action`, more info see [Swagger documentation](https://api.spacefill.fr/docs#/logistic-management/post_v1_logistic_management_shipper_updates_order_action_v1_logistic_management_orders__order_id__shipper_updates_order_action_post)

- New endpoint not implemented:
  - `POST /v1/logistic_management/inventory_adjustments/`, more info see [Swagger documentation](https://api.spacefill.fr/docs#/logistic-management%20(not%20implemented)/post_v1_logistic_management_inventory_adjustement_v1_logistic_management_inventory_adjustments__post)


## 2022-05-03

- `master_items.transfered_to_erp_at`, `master_items.transfered_to_wms_at` and `master_items.transfered_to_tms_at` fields
   are automatically reset (set to `null`) on each API or Web interface `master_items` update events
- `orders.transfered_to_erp_at`, `orders.transfered_to_wms_at` and `orders.transfered_to_tms_at` fields
   are automatically reset (set to `null`) on each API or Web interface `orders` update events

## 2022-04-27

New endpoints:

- `PATCH /v1/logistic_management/master_items/{master_item_id}/`
- `PATCH /v1/logistic_management/orders/{order_id}/`

Updated endpoints:

- `GET /v1/logistic_management/master_items/`]
  - accept this new url query filters:
    - `is_transfered_to_erp`
    - `is_transfered_to_wms`
    - `is_transfered_to_tms`
  - return this news fields in response:
    - `transfered_to_erp_at`
    - `transfered_to_wms_at`
    - `transfered_to_tms_at`
- `POST /v1/logistic_management/master_items/`:
  - accept this new fields in request input:
    - `transfered_to_erp_at`
    - `transfered_to_wms_at`
    - `transfered_to_tms_at`
  - return this news fields in response:
    - `transfered_to_erp_at`
    - `transfered_to_wms_at`
    - `transfered_to_tms_at`
- `GET /v1/logistic_management/master_items/{master_item_id}/`: return this news fields in response:
  - `transfered_to_erp_at`
  - `transfered_to_wms_at`
  - `transfered_to_tms_at`
- `PUT /v1/logistic_management/master_items/{master_item_id}/`:
  - accept this new fields in request input:
    - `transfered_to_erp_at`
    - `transfered_to_wms_at`
    - `transfered_to_tms_at`
  - return this news fields in response:
    - `transfered_to_erp_at`
    - `transfered_to_wms_at`
    - `transfered_to_tms_at`
- `GET /v1/logistic_management/orders/`:
  - accept this new url query filters:
    - `is_transfered_to_erp`
    - `is_transfered_to_wms`
    - `is_transfered_to_tms`
  - return this news fields in response:
    - `transfered_to_erp_at`
    - `transfered_to_wms_at`
    - `transfered_to_tms_at`
- `GET /v1/logistic_management/orders/{order_id}/`: return this news fields in response:
  - `transfered_to_erp_at`
  - `transfered_to_wms_at`
  - `transfered_to_tms_at`
- `POST /v1/logistic_management/orders/entry/`:
  - accept this new fields in request input:
    - `transfered_to_erp_at`
    - `transfered_to_wms_at`
    - `transfered_to_tms_at`
  - return this news fields in response:
    - `transfered_to_erp_at`
    - `transfered_to_wms_at`
    - `transfered_to_tms_at`
- `POST /v1/logistic_management/orders/exit/`:
  - accept this new fields in request input:
    - `transfered_to_erp_at`
    - `transfered_to_wms_at`
    - `transfered_to_tms_at`
  - return this news fields in response:
    - `transfered_to_erp_at`
    - `transfered_to_wms_at`
    - `transfered_to_tms_at`
- `POST /v1/logistic_management/orders/{order_id}/warehouse_acknowledges_receipt_of_order_action`: return this news fields in response:
  - `transfered_to_erp_at`
  - `transfered_to_wms_at`
  - `transfered_to_tms_at`
- `POST /v1/logistic_management/orders/{order_id}/shipper_cancels_order_action`: return this news fields in response:
  - `transfered_to_erp_at`
  - `transfered_to_wms_at`
  - `transfered_to_tms_at`
- `POST /v1/logistic_management/orders/{order_id}/warehouse_emits_order_receipt_error_action`: return this news fields in response:
  - `transfered_to_erp_at`
  - `transfered_to_wms_at`
  - `transfered_to_tms_at`


## 2022-04-26

Updated endpoints:

- `GET /v1/logistic_management/master_items/`
  - accept this new url query filter: `archived`
  - return this new field in response: `archived_at`
- `GET /v1/logistic_management/master_items/{master_item_id}/`: return this new field in response: `archived_at`
