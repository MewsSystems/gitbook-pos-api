<!-- AUTOMATICALLY GENERATED, DO NOT MODIFY -->
# Registers

## A register within an outlet.

A register represents a terminal within an outlet, used to issue invoices. Each register is
uniquely identified within its outlet and can either be physical or virtual.
Note: This operation needs [Authentication](../essential-guide/authentication.md) and 
supports the `include` query parameter `outlet` following the [JSON:API specification](../essential-guide/features.md).

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

A related resource object from type registers.

| Property | Type | Contract | Description |
| :-- | :-- | :-- | :-- |
| `Data` | [register](registers.md#register) | required |  |
| `Included` | array of [outlet](registers.md#outlet) | optional, max 1 item |  |

#### register

| Property | Type | Contract | Description |
| :-- | :-- | :-- | :-- |
| `Id` | undefined | required, max length 36 characters | globally unique ID (UUID) that identifies the related object. |
| `Type` | string | required | The [type](https://jsonapi.org/format/#document-resource-object-identification) member is used to describe resource objects that share common attributes and relationships. |
| `Attributes` | [register_attributes](registers.md#register_attributes) | required |  |
| `Relationships` | [register_relationships](registers.md#register_relationships) | required |  |

#### register_attributes

| Property | Type | Contract | Description |
| :-- | :-- | :-- | :-- |
| `Name` | string | required, max length 255 characters | Name of the register. |
| `Invoices_count` | integer | required | Total number of invoices issued from this register. |
| `Index` | integer | required | The index of a register within an outlet. |
| `Virtual` | boolean | required | A boolean indicating whether the register is virtual `true` or physical `false`. |
| `Created_at` | string | required, max length 25 characters | Register created at timestamp in ISO 8601 format. |
| `Updated_at` | string | required, max length 25 characters | Register updated at timestamp in ISO 8601 format. |

#### register_relationships

| Property | Type | Contract | Description |
| :-- | :-- | :-- | :-- |
| `Outlets` | object | required | A related resource object from type registers. |

#### relationships_attributes

| Property | Type | Contract | Description |
| :-- | :-- | :-- | :-- |
| `Id` | undefined | required, max length 36 characters | globally unique ID (UUID) that identifies the related object. |
| `Type` | string | required | The [type](https://jsonapi.org/format/#document-resource-object-identification) member is used to describe resource objects that share common attributes and relationships. |
