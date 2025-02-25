<!-- AUTOMATICALLY GENERATED, DO NOT MODIFY -->
# Orders

## Get order

An order represents a single set of items that was ordered by a customer. Each order is uniquely identified and can be associated with an invoice item.

**Note:** This operation needs [Authentication](../guidelines/authentication.md) and supports the following JSON:API features:

- [Relationships](../guidelines/relationships.md) - `invoice`, `customer`, `booking`, `tables` using `include` query parameter.
- [Sparse fieldsets](../guidelines/sparse-fieldsets.md) - supports all fields of `order` and related resources with `fields` query parameter.

### Request

`GET` `[PlatformAddress]/api/v2/orders/{id}`

### Response

```javascript
{
  "data": {
    "id": "2496b6bd-a326-4a5a-95c8-359c943dcee8",
    "type": "orders",
    "attributes": {
      "covers": 1,
      "tableStatus": "seated",
      "notes": "Please make it quick",
      "depositAmount": "20.00",
      "createdAt": "2021-06-29T08:00:00Z",
      "updatedAt": "2021-06-29T08:00:00Z"
    },
    "relationships": {
      "invoice": {
        "data": {
          "id": "4014e105-57d6-4b12-a4fc-164601ec53e9",
          "type": "invoices"
        }
      },
      "customer": {
        "data": {
          "id": "4014e105-57d6-4b12-a4fc-164601ec53e9",
          "type": "customers"
        }
      },
      "register": {
        "data": {
          "id": "a0312dc4-e0bf-4a27-837d-a6cf41f54464",
          "type": "bookings"
        }
      },
      "invoiceItems": {
        "data": [
          {
            "id": "dcd9718c-abb0-4ba2-83c5-ae01505a5391",
            "type": "tables"
          }
        ]
      }
    },
    "links": {
      "self": "https://pos.mews-demo/com/api/v2/orders/2496b6bd-a326-4a5a-95c8-359c943dcee8"
    }
  }
}
```
Below is a list of all possible fields this endpoint can return including relationships fields fetched with include query parameter.

| Property | Type | Contract | Description |
| :-- | :-- | :-- | :-- |
| `data` | [order](orders.md#order) | required | The document's "primary data". |
| `included` | array of object [invoice](orders.md#invoice),[table](orders.md#table),[booking](orders.md#booking),[customer](orders.md#customer) | optional, max 100 items | Details of the objects to which the order is associated. |

#### order

| Property | Type | Contract | Description |
| :-- | :-- | :-- | :-- |
| `id` | string | required, max length 36 characters | Universally unique ID (UUID) that identifies the related object. |
| `type` | string | required | The [type](https://jsonapi.org/format/#document-resource-object-identification) member is used to describe resource objects that share common attributes and relationships. |
| `attributes` | [order_attributes](orders.md#order_attributes) | required | An [attributes object](https://jsonapi.org/format/#document-resource-object-attributes) representing some of the resource's data. |
| `links` | object | required | A [links object](https://jsonapi.org/format/#document-resource-object-links) containing links related to the resource. |
| `relationships` | [order_relationships](orders.md#order_relationships) | required | A [relationships object](https://jsonapi.org/format/#document-resource-object-relationships) describing relationships between the resource and other JSON:API resources. |

#### order_attributes

| Property | Type | Contract | Description |
| :-- | :-- | :-- | :-- |
| `notes` | string,null | optional, max length 500 characters | Notes about the order. |
| `covers` | undefined | required | How many people are seated at the table. |
| `depositAmount` | string,null | optional, max length 255 characters | The amount of discount applied to the invoice. |
| `tableStatus` | string,null | optional | Status of the table. Possible values are "noTable", "seated", "cleaning", and "free". |
| `createdAt` | string | required, max length 25 characters | Order created at timestamp in RFC 3339 format. |
| `updatedAt` | string | required, max length 25 characters | Order updated at timestamp in RFC 3339 format. |

#### order_relationships

| Property | Type | Contract | Description |
| :-- | :-- | :-- | :-- |
| `invoice` | object | required | Details of the invoice associated with the order. |
| `customer` | object | required | Details of the customer associated with the order. |
| `booking` | object | required | Details of the booking associated with the order. |
| `tables` | object | required | Details of the tables associated with the order. |

#### invoice

| Property | Type | Contract | Description |
| :-- | :-- | :-- | :-- |
| `id` | string | required, max length 36 characters | Universally unique ID (UUID) that identifies the related object. |
| `type` | string | required | The [type](https://jsonapi.org/format/#document-resource-object-identification) member is used to describe resource objects that share common attributes and relationships. |
| `attributes` | [invoice_attributes](orders.md#invoice_attributes) | required | An [attributes object](https://jsonapi.org/format/#document-resource-object-attributes) representing some of the resource's data. |
| `relationships` | [invoice_relationships](orders.md#invoice_relationships) | required | A [relationships object](https://jsonapi.org/format/#document-resource-object-relationships) describing relationships between the resource and other JSON:API resources. |

#### invoice_attributes

| Property | Type | Contract | Description |
| :-- | :-- | :-- | :-- |
| `discount` | string,null | optional, max length 255 characters | The amount of discount applied to the invoice. |
| `tax` | string | required, max length 255 characters | The total tax amount applicable to the invoice. |
| `total` | string | required, max length 255 characters | The final amount due on the invoice after all discounts and taxes. |
| `subtotal` | string | required, max length 255 characters | The total amount of the invoice before taxes and additional charges. |
| `tipAmount` | string,null | optional, max length 255 characters | The amount of gratuity or tip added to the invoice. |
| `createdAt` | string | required, max length 25 characters | Created at timestamp in RFC 3339 format. |
| `updatedAt` | string | required, max length 25 characters | Updated at timestamp in RFC 3339 format. |
| `cancelled` | boolean | required | Indicates whether the invoice has been cancelled (true) or not (false). |
| `cancelReason` | string,null | optional, max length 255 characters | The reason provided for cancelling the invoice, if applicable. |
| `discountAmount` | string,null | optional, max length 255 characters | The total monetary value of the discount applied to the invoice. |
| `description` | string,null | optional, max length 255 characters | A brief description of the invoice, including details about the transaction. |
| `itemDiscountAmount` | string,null | optional, max length 255 characters | The total discount amount applied to individual items within the invoice. |

#### invoice_relationships

| Property | Type | Contract | Description |
| :-- | :-- | :-- | :-- |
| `user` | object | required | Details of the user associated with the invoice. |
| `registers` | object | required | Details of the register associated with the invoice. |
| `originalInvoice` | object | required | Details of the original invoice associated with the invoice. |
| `items` | object | required | Details of the items associated with the invoice. |

#### table

| Property | Type | Contract | Description |
| :-- | :-- | :-- | :-- |
| `id` | string | required, max length 36 characters | Universally unique ID (UUID) that identifies the related object. |
| `type` | string | required | The [type](https://jsonapi.org/format/#document-resource-object-identification) member is used to describe resource objects that share common attributes and relationships. |
| `attributes` | [table_attributes](orders.md#table_attributes) | required | An [attributes object](https://jsonapi.org/format/#document-resource-object-attributes) representing some of the resource's data. |
| `relationships` | [table_relationships](orders.md#table_relationships) | required | A [relationships object](https://jsonapi.org/format/#document-resource-object-relationships) describing relationships between the resource and other JSON:API resources. |

#### table_attributes

| Property | Type | Contract | Description |
| :-- | :-- | :-- | :-- |
| `name` | string | required, max length 255 characters | The name of the table. |
| `numberOfSeats` | integer | required | Number of people that can be seated at this table. |
| `createdAt` | string | required, max length 25 characters | Created at timestamp in RFC 3339 format. |
| `updatedAt` | string | required, max length 25 characters | Updated at timestamp in RFC 3339 format. |

#### table_relationships

| Property | Type | Contract | Description |
| :-- | :-- | :-- | :-- |
| `area` | object | required | Details of the table area. |

#### booking

| Property | Type | Contract | Description |
| :-- | :-- | :-- | :-- |
| `id` | string | required, max length 36 characters | Universally unique ID (UUID) that identifies the related object. |
| `type` | string | required | The [type](https://jsonapi.org/format/#document-resource-object-identification) member is used to describe resource objects that share common attributes and relationships. |
| `attributes` | [booking_attributes](orders.md#booking_attributes) | required | An [attributes object](https://jsonapi.org/format/#document-resource-object-attributes) representing some of the resource's data. |
| `relationships` | [booking_relationships](orders.md#booking_relationships) | required | A [relationships object](https://jsonapi.org/format/#document-resource-object-relationships) describing relationships between the resource and other JSON:API resources. |

#### booking_attributes

| Property | Type | Contract | Description |
| :-- | :-- | :-- | :-- |
| `createdAt` | string | required, max length 25 characters | Created at timestamp in RFC 3339 format. |
| `updatedAt` | string | required, max length 25 characters | Updated at timestamp in RFC 3339 format. |
| `required` | undefined | required |  |
| `status` | string,null | optional | The initial status of the booking. Possible values are "confirmed", "seated", "completed", "cancelled", and "noShow". |
| `partySize` | integer | required | Represents the number of people included in the booking. |
| `bookingDatetime` | string | required, max length 25 characters | The booking's date. |
| `duration` | integer,null | optional | Represents the length of the booking in minutes. |
| `notes` | string,null | optional, max length 10000 characters | Additional notes for the booking. |
| `roomNumber` | string,null | optional, max length 100 characters | The room number of the booking's customer. |
| `promotions` | string,null | optional, max length 100 characters | The promotions of the booking. |
| `bookingReference` | string,null | optional, max length 255 characters | A reference code or identifier associated with the booking. |
| `isWalkIn` | boolean | required | Indicates if the booking is a walk-in. |
| `depositAmount` | string,null | optional, max length 255 characters | The amount of the deposit. |

#### booking_relationships

| Property | Type | Contract | Description |
| :-- | :-- | :-- | :-- |
| `tables` | object | required | Details of the tables associated with the booking. |
| `customer` | object | required | Details of the customer associated with the booking. |
| `orders` | object | required | Details of the orders associated with the booking. |

#### customer

| Property | Type | Contract | Description |
| :-- | :-- | :-- | :-- |
| `id` | string | required, max length 36 characters | Universally unique ID (UUID) that identifies the related object. |
| `type` | string | required | The [type](https://jsonapi.org/format/#document-resource-object-identification) member is used to describe resource objects that share common attributes and relationships. |
| `attributes` | [customer_attributes](orders.md#customer_attributes) | required | An [attributes object](https://jsonapi.org/format/#document-resource-object-attributes) representing some of the resource's data. |

#### customer_attributes

| Property | Type | Contract | Description |
| :-- | :-- | :-- | :-- |
| `fullName` | string,null | optional, max length 255 characters | The full name of the customer. This can be either a personal name or a company name. |
| `companyName` | string,null | optional, max length 255 characters | The name of the company associated with the customer. |
| `taxNumber` | string,null | optional, max length 40 characters | The customer's tax identification number. |
| `email` | string,null | optional, max length 320 characters | The customer's email address. |
| `address1` | string,null | optional, max length 255 characters | The first line of the customer's address. |
| `address2` | string,null | optional, max length 255 characters | The second line of the customer's address. |
| `city` | string,null | optional, max length 100 characters | The city of the customer's address. |
| `state` | string,null | optional, max length 100 characters | The state or province of the customer's address. |
| `postalCode` | string,null | optional, max length 20 characters | The postal or ZIP code of the customer's address. |
| `country` | string,null | optional, max length 100 characters | The country of the customer's address. |
| `notes` | string,null | optional, max length 500 characters | Additional notes about the customer. |
| `phone` | string,null | optional, max length 20 characters | The customer's phone number. |
| `mobile` | string,null | optional, max length 20 characters | The customer's mobile phone number. |
| `countrySpecificCode` | string,null | optional, max length 50 characters | A unique country specific code assigned to the customer. Lottery code, for example, in Italy. |
| `dateOfBirth` | string,null | optional, max length 10 characters | The customer's date of birth in YYYY-MM-DD format. |
| `createdAt` | string | required, max length 25 characters | Created at timestamp in RFC 3339 format. |
| `updatedAt` | string | required, max length 25 characters | Updated at timestamp in RFC 3339 format. |
