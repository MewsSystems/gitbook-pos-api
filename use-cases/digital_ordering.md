# Digital ordering

This use case is aimed at Digital Ordering Systems and it describes how to use the __Mews POS API__ to manage digital orders, including:
  * Browsing the product catalog
  * Creating and managing orders
  * Processing payments

## Contents

* [Products endpoint polling to get availability updates](#products-endpoint-polling-to-get-availability-updates)
* [Orders endpoint polling to get most recent order status changes](#orders-endpoint-polling-to-get-most-recent-order-status-changes)

## Products endpoint polling to get availability updates

Digital ordering systems need to stay synchronized with real-time product availability changes. Use the [Get products](../operations/products.md#get-products) endpoint with filtering and sparse fieldsets to efficiently poll for availability updates.

### Polling strategy

Poll the products endpoint using the `updatedAtGteq` or `updatedAtGt` filters to retrieve only products that have been updated since your last check. Use sparse fieldsets to minimize bandwidth by requesting only the `isAvailable` field.

#### Example request:
```
GET https://api.pos.mews-demo.com/v1/products?filter[updatedAtGteq]=2025-03-12&fields[products]=isAvailable
```

#### Example response:
```json
{
  "data": [
    {
      "id": "139a7f7a-591f-4797-ba23-08c9bee0d044",
      "type": "products",
      "attributes": {
        "isAvailable": false
      }
    },
    {
      "id": "2a8b9c1d-4e5f-6789-abcd-ef1234567890",
      "type": "products",
      "attributes": {
        "isAvailable": true
      }
    }
  ]
}
```


## Orders endpoint polling to get most recent order status changes

Track order status changes in real-time by polling the [Get orders](../operations/orders.md#get-orders) endpoint with filtering and sparse fieldsets to monitor order lifecycle updates.

### Polling strategy

Poll the orders endpoint using the `updatedAtGteq` or `updatedAtGt` filters to retrieve only orders that have been updated since your last check. Use sparse fieldsets to request only the `status` field for efficient bandwidth usage.

#### Example request:
```
GET https://api.pos.mews-demo.com/v1/orders?filter[updatedAtGteq]=2025-05-16&fields[orders]=status
```

#### Example response:
```json
{
  "data": [
    {
      "id": "5624013b-5293-48b1-a07a-e7ee01cbde6a",
      "type": "orders",
      "attributes": {
        "status": "closed"
      }
    },
    {
      "id": "7c8d9e0f-1234-5678-9abc-def012345678",
      "type": "orders",
      "attributes": {
        "status": "open"
      }
    }
  ]
}
```

## Fetch covers for a table at a specific table

### Polling strategy

To retrieve the actual covers (guests seated) for a table, you have to poll the [Get orders](../operations/orders.md#get-orders) and include the `filter[tableIdEq]` query parameter.

#### Example request:
```
GET https://api.pos.mews-demo.com/v1/orders?filter[tableIdEq]=6d5e100c-5bf9-4781-85ec-cdf183e9486f
```

#### Example response:
```json
{
  "data": [
    {
      "id": "e194c497-f601-49c7-b952-08f329a5779e",
      "type": "orders",
      "attributes": {
        "notes": null,
        "createdAt": "2025-09-25T11:23:18.367Z",
        "updatedAt": "2025-09-25T11:24:24.344Z",
        "depositAmount": null,
        "tableStatus": "seated",
        "status": "paid",
        "covers": 4
      },
      "relationships": {
        "tables": {
          "data": [
            {
              "id": "6d5e100c-5bf9-4781-85ec-cdf183e9486f",
              "type": "tables"
            }
          ]
        }
      }
    }
  ]
}
```
