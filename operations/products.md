<!-- AUTOMATICALLY GENERATED, DO NOT MODIFY -->
# Products

## Get products

This operation returns a list of products.

**Note:** This operation needs [Authentication](../guidelines/authentication.md) and supports the following JSON:API features:

- [Relationships](../guidelines/relationships.md) - `productType`, `modifierSets`, `productVariants` using `include` query parameter.
- [Sparse fieldsets](../guidelines/sparse-fieldsets.md) - supports all fields of `product` and related resources with `fields` query parameter.

### Request

`GET` `[PlatformAddress]/v1/products`

### Response

```javascript
{
  "data": [
    {
      "id": "286ef74f-e37f-477f-bcda-77f8fbfd13ea",
      "type": "products",
      "attributes": {
        "name": "Product Number One",
        "description": "Description of product number one.",
        "sku": "ABC-123-HR-K",
        "status": "active",
        "barcode": "1234567890",
        "createdAt": "2022-10-16T11:29:00Z",
        "updatedAt": "2022-10-19T11:29:00Z",
        "tax": "2.00",
        "retailPriceInclTax": "10.00",
        "retailPriceExclTax": "8.00",
        "regularRetailPrice": "10.00",
        "unitPrice": "10.00"
      },
      "relationships": {
        "productType": {
          "data": {
            "id": "c53372e2-9aa1-452a-8965-2ea3fa514fb2",
            "type": "productTypes"
          }
        },
        "modifierSets": {
          "data": [
            {
              "id": "06382148-c76a-489d-b382-72fb7d7ab37b",
              "type": "modifierSets"
            },
            {
              "id": "e727124a-d2bb-4002-98bd-81af6d788666",
              "type": "modifierSets"
            }
          ]
        },
        "productVariants": {
          "data": [
            {
              "id": "0907e6d2-62c1-44cd-a886-f403ce9c7145",
              "type": "productVariants"
            },
            {
              "id": "0d4e4ec6-118f-47a6-9040-b68abbec0575",
              "type": "productVariants"
            }
          ]
        }
      }
    }
  ],
  "links": {
    "prev": "https://api.mews-demo.com/pos/v1/products?page%5Bbefore%5D=NA&page%5Bsize%5D=1",
    "next": "https://api.mews-demo.com/pos/v1/products?page%5Bafter%5D=NA&page%5Bsize%5D=1"
  }
}
```
Below is a list of all possible fields this endpoint can return including relationships fields fetched with include query parameter.

| Property | Type | Contract | Description |
| :-- | :-- | :-- | :-- |
| `data` | array of object [product](products.md#product) | required, max 1000 items | The document's "primary data". |
| `included` | array of object [product_type](products.md#product_type),[modifier_set](products.md#modifier_set),[product_variant](products.md#product_variant) | optional, max 1000 items | Details of the objects to which the product is related. |
| `links` | [product_pagination_links](products.md#product_pagination_links) | required | A [links object](https://jsonapi.org/profiles/ethanresnick/cursor-pagination/#auto-id-links) describing cursor pagination links. |

#### product

| Property | Type | Contract | Description |
| :-- | :-- | :-- | :-- |
| `id` | string | required, max length 36 characters | Universally unique ID (UUID) that identifies the related object. |
| `type` | string | required | The [type](https://jsonapi.org/format/#document-resource-object-identification) member is used to describe resource objects that share common attributes and relationships. |
| `attributes` | [product_attributes](products.md#product_attributes) | required | An [attributes object](https://jsonapi.org/format/#document-resource-object-attributes) representing some of the resource's data. |
| `relationships` | [product_relationships](products.md#product_relationships) | required | A [relationships object](https://jsonapi.org/format/#document-resource-object-relationships) describing relationships between the resource and other JSON:API resources. |

#### product_attributes

| Property | Type | Contract | Description |
| :-- | :-- | :-- | :-- |
| `name` | string | required, max length 255 characters | Name of the product. |
| `description` | string | required, max length 10000 characters | Description of the product. |
| `sku` | string | required, max length 255 characters | SKU of the product. |
| `barcode` | string | required, max length 255 characters | Barcode of the product. |
| `status` | string | required | Status of the product. Possible values are "active" and "inactive". |
| `tax` | string | required, max length 255 characters | Tax of the product. |
| `retailPriceExclTax` | string | required, max length 255 characters | Retail price excluding tax. |
| `retailPriceInclTax` | string | required, max length 255 characters | Retail price including tax. |
| `regularRetailPrice` | string | required, max length 255 characters | Regular retail price. |
| `unitPrice` | string | required, max length 255 characters | Unit price of the product. |
| `createdAt` | string | required, max length 25 characters | Created at timestamp in RFC 3339 format. |
| `updatedAt` | string | required, max length 25 characters | Updated at timestamp in RFC 3339 format. |

#### product_relationships

| Property | Type | Contract | Description |
| :-- | :-- | :-- | :-- |
| `productType` | object | required | Details of the product type associated with the product. |
| `modifierSets` | object | required | Details of the modifier sets associated with the product. |
| `productVariants` | object | required | Details of the product variants associated with the product. |

#### product_type

| Property | Type | Contract | Description |
| :-- | :-- | :-- | :-- |
| `id` | string | required, max length 36 characters | Universally unique ID (UUID) that identifies the related object. |
| `type` | string | required | The [type](https://jsonapi.org/format/#document-resource-object-identification) member is used to describe resource objects that share common attributes and relationships. |
| `attributes` | [product_type_attributes](products.md#product_type_attributes) | required | An [attributes object](https://jsonapi.org/format/#document-resource-object-attributes) representing some of the resource's data. |

#### product_type_attributes

| Property | Type | Contract | Description |
| :-- | :-- | :-- | :-- |
| `name` | string | required, max length 255 characters | Name of the product type. |
| `createdAt` | string | required, max length 25 characters | Created at timestamp in RFC 3339 format. |
| `updatedAt` | string | required, max length 25 characters | Updated at timestamp in RFC 3339 format. |

#### modifier_set

| Property | Type | Contract | Description |
| :-- | :-- | :-- | :-- |
| `id` | string | required, max length 36 characters | Universally unique ID (UUID) that identifies the related object. |
| `type` | string | required | The [type](https://jsonapi.org/format/#document-resource-object-identification) member is used to describe resource objects that share common attributes and relationships. |
| `attributes` | [modifier_set_attributes](products.md#modifier_set_attributes) | required | An [attributes object](https://jsonapi.org/format/#document-resource-object-attributes) representing some of the resource's data. |

#### modifier_set_attributes

| Property | Type | Contract | Description |
| :-- | :-- | :-- | :-- |
| `name` | string | required, max length 255 characters | Name of the modifier set. |
| `selection` | string | required | Modifier set selection type. Possible values are "single" and "multiple". |
| `maximumCount` | integer | required | Maximum number of modifiers that can be selected. |
| `minimumCount` | integer | required | Minimum number of modifiers that must be selected. |
| `createdAt` | string | required, max length 25 characters | Created at timestamp in RFC 3339 format. |
| `updatedAt` | string | required, max length 25 characters | Updated at timestamp in RFC 3339 format. |

#### product_variant

| Property | Type | Contract | Description |
| :-- | :-- | :-- | :-- |
| `id` | string | required, max length 36 characters | Universally unique ID (UUID) that identifies the related object. |
| `type` | string | required, max length 255 characters | The [type](https://jsonapi.org/format/#document-resource-object-identification) member is used to describe resource objects that share common attributes and relationships. |
| `attributes` | [product_variant_attributes](products.md#product_variant_attributes) | required | An [attributes object](https://jsonapi.org/format/#document-resource-object-attributes) representing some of the resource's data. |

#### product_variant_attributes

| Property | Type | Contract | Description |
| :-- | :-- | :-- | :-- |
| `retailPriceExclTax` | string | required, max length 255 characters | Retail price excluding tax. |
| `retailPriceInclTax` | string | required, max length 255 characters | Retail price including tax. |
| `regularRetailPrice` | string | required, max length 255 characters | Regular retail price. |
| `sku` | string | required, max length 255 characters | SKU of the variant. |
| `barcode` | string | required, max length 255 characters | Barcode of the variant. |
| `createdAt` | string | required, max length 25 characters | Created at timestamp in RFC 3339 format. |
| `updatedAt` | string | required, max length 25 characters | Updated at timestamp in RFC 3339 format. |

#### product_pagination_links

| Property | Type | Contract | Description |
| :-- | :-- | :-- | :-- |
| `prev` | string | required, max length 1024 characters | The link to the previous page of results. |
| `next` | string | required, max length 1024 characters | The link to the next page of results. |
