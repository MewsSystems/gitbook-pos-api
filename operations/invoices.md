<!-- AUTOMATICALLY GENERATED, DO NOT MODIFY -->
# Invoices

## Get invoices

This operation returns a list of invoices.
Note: This operation needs [Authentication](../essential-guide/authentication.md) and supports the `include` query parameters `invoice_item, user, register, product_variant, invoice_item_modifier` following the [JSON:API specification](../essential-guide/features.md).

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
        "cancel_reason": null,
        "discount_amount": "0.00",
        "description": null,
        "item_discount_amount": "0.00",
        "created_at": "2024-10-24T08:44:45.409Z",
        "updated_at": "2024-10-24T08:44:45.547Z",
        "tip_amount": "0.00"
      },
      "relationships": {
        "user": {
          "data": {
            "id": "817f7fc3-3dcb-4cb8-9991-af488a497968",
            "type": "users"
          }
        },
        "original_invoices": {
          "data": null
        },
        "register": {
          "data": {
            "id": "eef23c03-49b9-432b-b1a3-955ea1501557",
            "type": "registers"
          }
        },
        "items": {
          "data": [
            {
              "id": "22426614-316e-4654-b567-60d781f9ae37",
              "type": "invoice_items"
            }
          ]
        }
      }
    }
  ],
  "included": [
    {
      "id": "817f7fc3-3dcb-4cb8-9991-af488a497968",
      "type": "users",
      "attributes": {
        "name": "Norbert Russel"
      }
    },
    {
      "id": "22426614-316e-4654-b567-60d781f9ae37",
      "type": "invoice_items",
      "attributes": {
        "product_name": "Awesome Rubber Bottle",
        "unit_price_incl_tax": "10.00",
        "quantity": 1,
        "subtotal": "8.33",
        "tax": "1.67",
        "total": "10.00",
        "discount": "0.00",
        "comp": false,
        "void": false,
        "comp_void_reason": null,
        "comp_void_notes": null,
        "discount_amount": "1.00",
        "subtotal_incl_discount": "7.33",
        "tax_incl_discount": "1.47",
        "total_incl_discount": "8.80",
        "created_at": "2024-01-01T12:00:00Z",
        "updated_at": "2024-01-01T12:00:00Z"
      }
    },
    {
      "id": "eef23c03-49b9-432b-b1a3-955ea1501557",
      "type": "registers",
      "attributes": {
        "name": "Cummings and Sons",
        "invoices_count": 1,
        "index": 9,
        "virtual": false,
        "created_at": "2024-10-24T08:44:45.042Z",
        "updated_at": "2024-10-24T08:44:45.042Z"
      },
      "links": {
        "self": "https://pos.mews-demo.com/api/v2/registers/eef23c03-49b9-432b-b1a3-955ea1501557"
      }
    },
    {
      "id": "99a2d9e7-8903-4c45-8f72-d914f38eb44a",
      "type": "product_variants",
      "attributes": {
        "sku": "SKU12345",
        "tax": "1.00",
        "deleted": false,
        "barcode": "012345678912",
        "retail_price_excl_tax": "8.00",
        "retail_price_incl_tax": "10.00",
        "regular_retail_price": "9.00",
        "created_at": "2024-01-01T12:00:00Z",
        "updated_at": "2024-01-01T12:00:00Z"
      }
    },
    {
      "id": "1a6d80c4-7f2e-4d49-9f5a-f279cdaaa87e",
      "type": "invoice_item_modifiers",
      "attributes": {
        "name": "Extra Ice",
        "price": "0.50",
        "created_at": "2024-01-01T12:00:00Z",
        "updated_at": "2024-01-01T12:00:00Z"
      }
    }
  ],
  "links": {
    "prev": "https://pos.mews-demo.com/api/v2/invoices?page%5Bbefore%5D=NA&page%5Bsize%5D=1",
    "next": "https://pos.mews-demo.com/api/v2/invoices?page%5Bafter%5D=NA&page%5Bsize%5D=1"
  }
}
```

| Property | Type | Contract | Description |
| :-- | :-- | :-- | :-- |
| `data` | array of object [invoice](invoices.md#invoice) | required, max 1000 items | The document's "primary data". |
| `included` | array of object [invoice_item](invoices.md#invoice_item),[user](invoices.md#user),[register](invoices.md#register),[product_variant](invoices.md#product_variant),[invoice_item_modifier](invoices.md#invoice_item_modifier) | optional, max 1000 items | Details of the objects to which the invoice is related. |
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
| `tip_amount` | string,null | optional, max length 255 characters | The amount of gratuity or tip added to the invoice. |
| `created_at` | string | required, max length 25 characters | Created at timestamp in RFC 3339 format. |
| `updated_at` | string | required, max length 25 characters | Updated at timestamp in RFC 3339 format. |
| `cancelled` | boolean | required | Indicates whether the invoice has been cancelled (true) or not (false). |
| `cancel_reason` | string,null | optional, max length 255 characters | The reason provided for cancelling the invoice, if applicable. |
| `discount_amount` | string,null | optional, max length 255 characters | The total monetary value of the discount applied to the invoice. |
| `description` | string,null | optional, max length 255 characters | A brief description of the invoice, including details about the transaction. |
| `item_discount_amount` | string,null | optional, max length 255 characters | The total discount amount applied to individual items within the invoice. |

#### invoice_relationships

| Property | Type | Contract | Description |
| :-- | :-- | :-- | :-- |
| `user` | object | required | Details of the user associated with the invoice. |
| `registers` | object | required | Details of the register associated with the invoice. |
| `original_invoice` | object | required | Details of the original invoice associated with the invoice. |
| `items` | object | required | Details of the items associated with the invoice. |

#### invoice_relationships_attributes

| Property | Type | Contract | Description |
| :-- | :-- | :-- | :-- |
| `id` | string | required, max length 36 characters | Universally unique ID (UUID) that identifies the related object. |
| `type` | string | required | The [type](https://jsonapi.org/format/#document-resource-object-identification) member is used to describe resource objects that share common attributes and relationships. |

#### invoice_item

| Property | Type | Contract | Description |
| :-- | :-- | :-- | :-- |
| `id` | string | required, max length 36 characters | Universally unique ID (UUID) that identifies the related object. |
| `type` | string | required | The [type](https://jsonapi.org/format/#document-resource-object-identification) member is used to describe resource objects that share common attributes and relationships. |
| `attributes` | [invoice_item_attributes](invoices.md#invoice_item_attributes) | required | An [attributes object](https://jsonapi.org/format/#document-resource-object-attributes) representing some of the resource's data. |

#### invoice_item_attributes

| Property | Type | Contract | Description |
| :-- | :-- | :-- | :-- |
| `product_name` | string | required, max length 255 characters | The name of the product or item being invoiced. |
| `unit_price_incl_tax` | string | required, max length 255 characters | The price of the product per unit, including applicable taxes. |
| `quantity` | integer | required | The number of units of the product being purchased. |
| `subtotal` | string | required, max length 255 characters | The total price of the product before taxes and discounts are applied. |
| `tax` | string | required, max length 255 characters | The tax amount applicable to the specific item. |
| `total` | string | required, max length 255 characters | The total price of the item after taxes and discounts have been applied. |
| `discount` | string | required, max length 255 characters | The percentage or amount of discount applied specifically to this item. |
| `comp` | boolean | required | Indicates whether the item was provided for free (comped) or not. |
| `void` | boolean | required | Indicates whether the item has been voided from the invoice. |
| `comp_void_reason` | string,null | optional, max length 255 characters | The reason provided for voiding the item, if applicable. |
| `comp_void_notes` | string,null | optional, max length 2048 characters | Additional notes regarding the comping or voiding of the item. |
| `discount_amount` | string,null | optional, max length 255 characters | The total monetary value of the discount applied to this specific item. |
| `subtotal_incl_discount` | string | required, max length 255 characters | The subtotal of the item after applying any discounts. |
| `tax_incl_discount` | string | required, max length 255 characters | The tax amount applicable to the item after applying any discounts. |
| `total_incl_discount` | string | required, max length 255 characters | The tax amount applicable to the item after applying any discounts. |
| `created_at` | string | required, max length 25 characters | Created at timestamp in RFC 3339 format. |
| `updated_at` | string | required, max length 25 characters | Updated at timestamp in RFC 3339 format. |

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
| `invoices_count` | integer | required | Total number of invoices issued from this register. |
| `index` | integer | required | The index of a register within an outlet. |
| `virtual` | boolean | required | A boolean indicating whether the register is virtual `true` or physical `false`. |
| `created_at` | string | required, max length 25 characters | Register created at timestamp in RFC 3339 format. |
| `updated_at` | string | required, max length 25 characters | Register updated at timestamp in RFC 3339 format. |

#### register_relationships

| Property | Type | Contract | Description |
| :-- | :-- | :-- | :-- |
| `outlet` | object | required | Details of the outlet to which the register is associated. |

#### register_relationships_attributes

| Property | Type | Contract | Description |
| :-- | :-- | :-- | :-- |
| `id` | string | required, max length 36 characters | Universally unique ID (UUID) that identifies the related object. |
| `type` | string | required | The [type](https://jsonapi.org/format/#document-resource-object-identification) member is used to describe resource objects that share common attributes and relationships. |

#### product_variant

| Property | Type | Contract | Description |
| :-- | :-- | :-- | :-- |
| `id` | string | required, max length 36 characters | Universally unique ID (UUID) that identifies the related object. |
| `type` | string | required, max length 255 characters | The [type](https://jsonapi.org/format/#document-resource-object-identification) member is used to describe resource objects that share common attributes and relationships. |
| `attributes` | [product_variant_attributes](invoices.md#product_variant_attributes) | required | An [attributes object](https://jsonapi.org/format/#document-resource-object-attributes) representing some of the resource's data. |

#### product_variant_attributes

| Property | Type | Contract | Description |
| :-- | :-- | :-- | :-- |
| `retail_price_excl_tax` | string | required, max length 255 characters | Retail price excluding tax. |
| `retail_price_incl_tax` | string | required, max length 255 characters | Retail price including tax. |
| `regular_retail_price` | string | required, max length 255 characters | Regular retail price. |
| `sku` | string | required, max length 255 characters | SKU of the variant. |
| `barcode` | string | required, max length 255 characters | Barcode of the variant. |
| `created_at` | string | required, max length 25 characters | Created at timestamp in RFC 3339 format. |
| `updated_at` | string | required, max length 25 characters | Updated at timestamp in RFC 3339 format. |

#### invoice_item_modifier

| Property | Type | Contract | Description |
| :-- | :-- | :-- | :-- |
| `id` | string | required, max length 36 characters | Universally unique ID (UUID) that identifies the related object. |
| `type` | string | required | The [type](https://jsonapi.org/format/#document-resource-object-identification) member is used to describe resource objects that share common attributes and relationships. |
| `attributes` | [invoice_item_modifiers_attributes](invoices.md#invoice_item_modifiers_attributes) | required | An [attributes object](https://jsonapi.org/format/#document-resource-object-attributes) representing some of the resource's data. |

#### invoice_item_modifiers_attributes

| Property | Type | Contract | Description |
| :-- | :-- | :-- | :-- |
| `name` | string | required, max length 255 characters | Name of the modifier item. |
| `price` | string | required, max length 255 characters | Price of the modifier item. |

#### invoice_pagination_links

| Property | Type | Contract | Description |
| :-- | :-- | :-- | :-- |
| `prev` | string | required, max length 1024 characters | The link to the previous page of results. |
| `next` | string | required, max length 1024 characters | The link to the next page of results. |
