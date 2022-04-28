# api.spacefill.fr changelog


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
