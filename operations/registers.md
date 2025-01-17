<!-- AUTOMATICALLY GENERATED, DO NOT MODIFY -->
# Registers

## Get registers

A register represents a terminal or cash register within an outlet, used to issue invoices. Each register is uniquely identified within its outlet and can either be physical or virtual.

**Note:** This operation needs [Authentication](../guidelines/authentication.md) and supports the following JSON:API features:

- [Relationships](../guidelines/relationships.md) - `outlet` using `include` query parameter.
- [Sparse fieldsets](../guidelines/sparse-fieldsets.md) - supports all fields of `register` and related resources with `fields` query parameter.

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
      "invoicesCount": 1200,
      "index": 3,
      "virtual": false,
      "createdAt": "2023-10-16T14:30:00Z",
      "updatedAt": "2023-10-19T14:30:00Z"
    },
    "relationships": {
      "outlet": {
        "data": {
          "id": "5efa8b3c-b930-4b31-918d-95ab0e212e64",
          "type": "outlets"
        }
      }
    },
    "links": {
      "self": "https://pos.mews-demo/com/api/v2/registers/31b14937-2524-491f-b0a0-dc0a7393ff3f"
    }
  }
}
```
Below is a list of all possible fields this endpoint can return including relationships fields fetched with include query parameter.

| Property | Type | Contract | Description |
| :-- | :-- | :-- | :-- |
| `name` | string | required, max length 255 characters | Name of the register. |
| `invoicesCount` | integer | required | Total number of invoices issued from this register. |
| `index` | integer | required | The index of a register within an outlet. |
| `virtual` | boolean | required | A boolean indicating whether the register is virtual `true` or physical `false`. |
| `createdAt` | string | required, max length 25 characters | Register created at timestamp in RFC 3339 format. |
| `updatedAt` | string | required, max length 25 characters | Register updated at timestamp in RFC 3339 format. |

#### register_relationships

| Property | Type | Contract | Description |
| :-- | :-- | :-- | :-- |
| `outlet` | object | required | Details of the outlet to which the register is associated. |

#### outlet_attributes

| Property | Type | Contract | Description |
| :-- | :-- | :-- | :-- |
| `name` | string | required, max length 255 characters | The name of the outlet, representing the business or location. |
| `address1` | string | required, max length 255 characters | The first line of the outlet's street address, typically including the street number and name. |
| `address2` | string | required, max length 255 characters | The second line of outlet's address. |
| `city` | string | required, max length 86 characters | The city where the outlet is located. |
| `state` | string | required, max length 54 characters | The state or region where the outlet is located. |
| `postalCode` | string,null | optional, max length 10 characters | The postal or ZIP code for outlet's location. |
| `index` | integer | required | A unique sequential number representing the outlet number within the establishment. |
| `createdAt` | string | required, max length 25 characters | Outlet created at timestamp in RFC 3339 format. |
| `updatedAt` | string | required, max length 25 characters | Outlet updated at timestamp in RFC 3339 format. |
