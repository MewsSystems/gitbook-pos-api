# Requests

The **Mews POS API** follows the [JSON:API specification](https://jsonapi.org/) for formatting HTTP requests. `Content-Type` is set to the JSON:API media type `application/vnd.api+json`.

## Address pattern

All operations follow this address pattern:

```text
[PlatformAddress]/api/pos/v1/[Resource]/TBD
```

* **PlatformAddress** - Base address of the Mews POS API, this depends on the environment \(e.g. test, demo, production\)
* **Resource** - Resource or domain entity which is the target of the action, always pluralized \(e.g. bills, reservations\)
* **Action** - Name of the action to be performed on the resource \(e.g. getAll, add, delete\)

## Request body

Each request will include a payload consisting of a header with authentication information, and a body with the data needed to perform the operation. For example:

```json
{
  "method": "POST",
  "url": "/api/v1/invoices/",
  "headers": {
    "Content-Type": "application/vnd.api+json",
    "X-ClientToken": "<client_token>",
    "X-AccessToken": "<login_access_token>"
  },
  "body": {
    "data": {
      "type": "invoices",
      "attributes": {
        "customer_uuid": "<customer_uuid>",
        "order_uuid": "<order_uuid>",
        "register_uuid": "<register_uuid>",
        "payment_ids": ["<payment_1_cash_uuid>"]
      }
    }
  }
}
```
