<!-- AUTOMATICALLY GENERATED, DO NOT MODIFY -->
# Registers

## Get registers

A register represents a terminal or cash register within an outlet, used to issue invoices. Each register is uniquely identified within its outlet and can either be physical or virtual.
Note: This operation needs [Authentication](../essential-guide/authentication.md) and supports the `include` query parameter `outlet` following the [JSON:API specification](../essential-guide/features.md).

### Request

`GET` `[PlatformAddress]/api/v2/registers/{id}`

### Response

```javascript
{
  "data": {
    "id": "31b14937-2524-491f-b0a0-dc0a7393ff3f",
    "type": "registers",
    "attributes": {
      "name": "Main Register",
      "invoices_count": 1200,
      "index": 3,
      "virtual": false,
      "created_at": "2023-10-16T14:30:00Z",
      "updated_at": "2023-10-19T14:30:00Z"
    },
    "relationships": {
      "outlet": {
        "data": {
          "id": "5efa8b3c-b930-4b31-918d-95ab0e212e64",
          "type": "outlets"
        }
      }
    }
  },
  "included": [
    {
      "id": "5efa8b3c-b930-4b31-918d-95ab0e212e64",
      "type": "outlets",
      "attributes": {
        "name": "Downtown Cafe",
        "address1": "123 Main Street",
        "address2": "Suite 4B",
        "city": "New York",
        "State": "New York",
        "postal_code": "10001",
        "index": 5,
        "created_at": "2023-10-16T13:30:00Z",
        "updated_at": "2023-10-16T15:30:00Z"
      }
    }
  ]
}
```

| Property | Type | Contract | Description |
| :-- | :-- | :-- | :-- |
| `data` | [register](registers.md#register) | required | The document's "primary data". |
| `included` | array of object [outlet](registers.md#outlet) | optional, max 1 item | Details of the outlet to which the register is associated. |

#### register

| Property | Type | Contract | Description |
| :-- | :-- | :-- | :-- |
| `id` | string | required, max length 36 characters | Universally unique ID (UUID) that identifies the related object. |
| `type` | string | required | The [type](https://jsonapi.org/format/#document-resource-object-identification) member is used to describe resource objects that share common attributes and relationships. |
| `attributes` | [register_attributes](registers.md#register_attributes) | required | An [attributes object](https://jsonapi.org/format/#document-resource-object-attributes) representing some of the resource's data. |
| `relationships` | [register_relationships](registers.md#register_relationships) | required | A [relationships object](https://jsonapi.org/format/#document-resource-object-relationships) describing relationships between the resource and other JSON:API resources. |

#### register_attributes

| Property | Type | Contract | Description |
| :-- | :-- | :-- | :-- |
| `name` | string | required, max length 255 characters | Name of the register. |
| `invoices_count` | integer | required | Total number of invoices issued from this register. |
| `index` | integer | required | The index of a register within an outlet. |
| `virtual` | boolean | required | A boolean indicating whether the register is virtual `true` or physical `false`. |
| `created_at` | string | required, max length 25 characters | Register created at timestamp in ISO 8601 format. |
| `updated_at` | string | required, max length 25 characters | Register updated at timestamp in ISO 8601 format. |

#### register_relationships

| Property | Type | Contract | Description |
| :-- | :-- | :-- | :-- |
| `outlet` | object | required | Details of the outlet to which the register is associated. |

#### relationship_attributes

| Property | Type | Contract | Description |
| :-- | :-- | :-- | :-- |
| `id` | string | required, max length 36 characters | Universally unique ID (UUID) that identifies the related object. |
| `type` | string | required | The [type](https://jsonapi.org/format/#document-resource-object-identification) member is used to describe resource objects that share common attributes and relationships. |

#### outlet

| Property | Type | Contract | Description |
| :-- | :-- | :-- | :-- |
| `id` | string | required, max length 36 characters | Universally unique ID (UUID) that identifies the related object. |
| `type` | string | required | The [type](https://jsonapi.org/format/#document-resource-object-identification) member is used to describe resource objects that share common attributes and relationships. |
| `attributes` | [outlet_attributes](registers.md#outlet_attributes) | required | An [attributes object](https://jsonapi.org/format/#document-resource-object-attributes) representing some of the resource's data. |

#### outlet_attributes

| Property | Type | Contract | Description |
| :-- | :-- | :-- | :-- |
| `name` | string | required, max length 255 characters | The name of the outlet, representing the business or location. |
| `address1` | string | required, max length 255 characters | The first line of the outlet's street address, typically including the street number and name. |
| `address2` | string | required, max length 255 characters | The second line of outlet's address. |
| `city` | string | required, max length 86 characters | The city where the outlet is located. |
| `state` | string | required, max length 54 characters | The state or region where the outlet is located. |
| `postal_code` | string | required, max length 10 characters | The postal or ZIP code for outlet's location. |
| `index` | integer | required | A unique sequential number representing the outlet number within the establishment. |
| `created_at` | string | required, max length 25 characters | Outlet created at timestamp in ISO 8601 format. |
| `updated_at` | string | required, max length 25 characters | Outlet updated at timestamp in ISO 8601 format. |
