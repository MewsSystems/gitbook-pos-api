<!-- AUTOMATICALLY GENERATED, DO NOT MODIFY -->
# Invoices

## Get invoices

This operation returns a list of invoices.
Note: This operation needs [Authentication](../essential-guide/authentication.md) and supports the following [JSON:API features](../essential-guide/features.md):

- [Relationships](../essential-guide/relationships.md)- `invoiceItems`, `user`, `register`, `originalInvoice` using `include` query parameter.
- [Filters](../essential-guide/filtering.md)- `createdAtGt`.
- [Sparse fieldsets](../essential-guide/sparse-fieldsets.md)- supports all fields of `invoices` and related resources with `fields` query parameter.

### Request

`GET` `[PlatformAddress]/api/v2/invoices`

### Response

```javascript
{
  "data": [
    {
      "id": "5a43b8fa-8029-4093-895b-bddd8c74ebe1",
      "type": "invoices",
      "attributes": {
        "discount": "0.00",
        "tax": "1.67",
        "total": "10.00",
        "subtotal": "8.33",
        "cancelled": false,
        "cancelReason": null,
        "discountAmount": "0.00",
        "description": null,
        "itemDiscountAmount": "0.00",
        "createdAt": "2024-10-24T08:44:45.409Z",
        "updatedAt": "2024-10-24T08:44:45.547Z",
        "tipAmount": "0.00"
      },
      "relationships": {
        "user": {
          "data": {
            "id": "817f7fc3-3dcb-4cb8-9991-af488a497968",
            "type": "users"
          }
        },
        "originalInvoices": {
          "data": null
        },
        "register": {
          "data": {
            "id": "eef23c03-49b9-432b-b1a3-955ea1501557",
            "type": "registers"
          }
        },
        "invoiceItems": {
          "data": [
            {
              "id": "22426614-316e-4654-b567-60d781f9ae37",
              "type": "invoiceItems"
            }
          ]
        }
      }
    }
  ],
  "links": {
    "prev": "https://pos.mews-demo.com/api/v2/invoices?page%5Bbefore%5D=NA&page%5Bsize%5D=1",
    "next": "https://pos.mews-demo.com/api/v2/invoices?page%5Bafter%5D=NA&page%5Bsize%5D=1"
  }
}
```
Below is a list of all possible fields this endpoint can return including relationships fields fetched with include query parameter.

| Property | Type | Contract | Description |
| :-- | :-- | :-- | :-- |
| `data` | array of object [invoice](invoices.md#invoice) | required, max 1000 items | The document's "primary data". |
| `included` | array of object [invoice_item](invoices.md#invoice_item),[user](invoices.md#user),[register](invoices.md#register) | optional, max 1000 items | Details of the objects to which the invoice is related. |
| `links` | [invoice_pagination_links](invoices.md#invoice_pagination_links) | required | A [links object](https://jsonapi.org/profiles/ethanresnick/cursor-pagination/#auto-id-links) describing cursor pagination links. |

#### invoice

| Property | Type | Contract | Description |
| :-- | :-- | :-- | :-- |
| `id` | string | required, max length 36 characters | Universally unique ID (UUID) that identifies the related object. |
| `type` | string | required | The [type](https://jsonapi.org/format/#document-resource-object-identification) member is used to describe resource objects that share common attributes and relationships. |
| `attributes` | [invoice_attributes](invoices.md#invoice_attributes) | required | An [attributes object](https://jsonapi.org/format/#document-resource-object-attributes) representing some of the resource's data. |
| `relationships` | [invoice_relationships](invoices.md#invoice_relationships) | required | A [relationships object](https://jsonapi.org/format/#document-resource-object-relationships) describing relationships between the resource and other JSON:API resources. |

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

#### invoice_item

| Property | Type | Contract | Description |
| :-- | :-- | :-- | :-- |
| `id` | string | required, max length 36 characters | Universally unique ID (UUID) that identifies the related object. |
| `type` | string | required | The [type](https://jsonapi.org/format/#document-resource-object-identification) member is used to describe resource objects that share common attributes and relationships. |
| `attributes` | [invoice_item_attributes](invoices.md#invoice_item_attributes) | required | An [attributes object](https://jsonapi.org/format/#document-resource-object-attributes) representing some of the resource's data. |

#### invoice_item_attributes

| Property | Type | Contract | Description |
| :-- | :-- | :-- | :-- |
| `productName` | string | required, max length 255 characters | The name of the product or item being invoiced. |
| `unitPriceInclTax` | string | required, max length 255 characters | The price of the product per unit, including applicable taxes. |
| `quantity` | integer | required | The number of units of the product being purchased. |
| `subtotal` | string | required, max length 255 characters | The total price of the product before taxes and discounts are applied. |
| `tax` | string | required, max length 255 characters | The tax amount applicable to the specific item. |
| `total` | string | required, max length 255 characters | The total price of the item after taxes and discounts have been applied. |
| `discount` | string | required, max length 255 characters | The percentage or amount of discount applied specifically to this item. |
| `comp` | boolean | required | Indicates whether the item was provided for free (comped) or not. |
| `void` | boolean | required | Indicates whether the item has been voided from the invoice. |
| `compVoidReason` | string,null | optional, max length 255 characters | The reason provided for voiding the item, if applicable. |
| `compVoidNotes` | string,null | optional, max length 2048 characters | Additional notes regarding the comping or voiding of the item. |
| `discountAmount` | string,null | optional, max length 255 characters | The total monetary value of the discount applied to this specific item. |
| `subtotalInclDiscount` | string | required, max length 255 characters | The subtotal of the item after applying any discounts. |
| `taxInclDiscount` | string | required, max length 255 characters | The tax amount applicable to the item after applying any discounts. |
| `totalInclDiscount` | string | required, max length 255 characters | The tax amount applicable to the item after applying any discounts. |
| `createdAt` | string | required, max length 25 characters | Created at timestamp in RFC 3339 format. |
| `updatedAt` | string | required, max length 25 characters | Updated at timestamp in RFC 3339 format. |

#### user

| Property | Type | Contract | Description |
| :-- | :-- | :-- | :-- |
| `id` | string | required, max length 36 characters | Universally unique ID (UUID) that identifies the related object. |
| `type` | string | required | The [type](https://jsonapi.org/format/#document-resource-object-identification) member is used to describe resource objects that share common attributes and relationships. |
| `attributes` | [user_attributes](invoices.md#user_attributes) | required | An [attributes object](https://jsonapi.org/format/#document-resource-object-attributes) representing some of the resource's data. |

#### user_attributes

| Property | Type | Contract | Description |
| :-- | :-- | :-- | :-- |
| `name` | string | required, max length 255 characters | Full name of the user. |

#### register

| Property | Type | Contract | Description |
| :-- | :-- | :-- | :-- |
| `id` | string | required, max length 36 characters | Universally unique ID (UUID) that identifies the related object. |
| `type` | string | required | The [type](https://jsonapi.org/format/#document-resource-object-identification) member is used to describe resource objects that share common attributes and relationships. |
| `attributes` | [register_attributes](invoices.md#register_attributes) | required | An [attributes object](https://jsonapi.org/format/#document-resource-object-attributes) representing some of the resource's data. |
| `links` | object | required | A [links object](https://jsonapi.org/format/#document-resource-object-links) containing links related to the resource. |
| `relationships` | [register_relationships](invoices.md#register_relationships) | required | A [relationships object](https://jsonapi.org/format/#document-resource-object-relationships) describing relationships between the resource and other JSON:API resources. |

#### register_attributes

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

#### invoice_pagination_links

| Property | Type | Contract | Description |
| :-- | :-- | :-- | :-- |
| `prev` | string | required, max length 1024 characters | The link to the previous page of results. |
| `next` | string | required, max length 1024 characters | The link to the next page of results. |
