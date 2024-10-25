<!-- AUTOMATICALLY GENERATED, DO NOT MODIFY -->
# Products

## Get products

This operation returns a list of products.
Note: This operation needs [Authentication](../essential-guide/authentication.md) and supports the `include` query parameters `product_type, modifier_set, product_variant` following the [JSON:API specification](../essential-guide/features.md).

### Request

`GET` `[PlatformAddress]/api/v2/products`

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
        "created_at": "2022-10-16T11:29:00Z",
        "updated_at": "2022-10-19T11:29:00Z",
        "tax": "2.00",
        "retail_price_incl_tax": "10.00",
        "retail_price_excl_tax": "8.00",
        "regular_retail_price": "10.00",
        "unit_price": "10.00"
      },
      "relationships": {
        "product_type": {
          "data": {
            "id": "c53372e2-9aa1-452a-8965-2ea3fa514fb2",
            "type": "product_types"
          }
        },
        "modifier_sets": {
          "data": [
            {
              "id": "06382148-c76a-489d-b382-72fb7d7ab37b",
              "type": "modifier_sets"
            },
            {
              "id": "e727124a-d2bb-4002-98bd-81af6d788666",
              "type": "modifier_sets"
            }
          ]
        },
        "product_variants": {
          "data": [
            {
              "id": "0907e6d2-62c1-44cd-a886-f403ce9c7145",
              "type": "product_variants"
            },
            {
              "id": "0d4e4ec6-118f-47a6-9040-b68abbec0575",
              "type": "product_variants"
            }
          ]
        }
      }
    }
  ],
  "included": [
    {
      "id": "c53372e2-9aa1-452a-8965-2ea3fa514fb2",
      "type": "product_types",
      "attributes": {
        "name": "Food",
        "created_at": "2022-10-16T11:29:00Z",
        "updated_at": "2022-10-19T11:29:00Z"
      }
    },
    {
      "id": "06382148-c76a-489d-b382-72fb7d7ab37b",
      "type": "modifier_sets",
      "attributes": {
        "name": "Size",
        "selection": "single",
        "maximum_count": 10,
        "minimum_count": 1,
        "created_at": "2022-10-16T11:29:00Z",
        "updated_at": "2022-10-19T11:29:00Z"
      }
    },
    {
      "id": "e727124a-d2bb-4002-98bd-81af6d788666",
      "type": "modifier_sets",
      "attributes": {
        "name": "Toppings",
        "selection": "multiple",
        "maximum_count": 10,
        "minimum_count": 1,
        "created_at": "2022-10-16T11:29:00Z",
        "updated_at": "2022-10-19T11:29:00Z"
      }
    },
    {
      "id": "0907e6d2-62c1-44cd-a886-f403ce9c7145",
      "type": "product_variants",
      "attributes": {
        "sku": "ABD-123-HR-O",
        "barcode": "1234567891",
        "tax": "2.00",
        "retail_price_incl_tax": "10.00",
        "retail_price_excl_tax": "8.00",
        "regular_retail_price": "10.00",
        "created_at": "2022-10-16T11:29:00Z",
        "updated_at": "2022-10-19T11:29:00Z"
      }
    },
    {
      "id": "0d4e4ec6-118f-47a6-9040-b68abbec0575",
      "type": "product_variants",
      "attributes": {
        "sku": "ABD-144-HR-Z",
        "barcode": "1234567777",
        "tax": "2.00",
        "retail_price_incl_tax": "10.00",
        "retail_price_excl_tax": "8.00",
        "regular_retail_price": "10.00",
        "created_at": "2022-10-16T11:29:00Z",
        "updated_at": "2022-10-19T11:29:00Z"
      }
    }
  ],
  "links": {
    "prev": "https://pos.mews-demo.com/api/v2/products?page%5Bbefore%5D=NA&page%5Bsize%5D=1",
    "next": "https://pos.mews-demo.com/api/v2/products?page%5Bafter%5D=NA&page%5Bsize%5D=1"
  }
}
```

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
| `status` | string | required | Status of the product. |
| `tax` | string | required, max length 255 characters | Tax of the product. |
| `retail_price_excl_tax` | string | required, max length 255 characters | Retail price excluding tax. |
| `retail_price_incl_tax` | string | required, max length 255 characters | Retail price including tax. |
| `regular_retail_price` | string | required, max length 255 characters | Regular retail price. |
| `unit_price` | string | required, max length 255 characters | Unit price of the product. |
| `created_at` | string | required, max length 25 characters | Created at timestamp in ISO 8601 format. |
| `updated_at` | string | required, max length 25 characters | Updated at timestamp in ISO 8601 format. |

#### product_relationships

| Property | Type | Contract | Description |
| :-- | :-- | :-- | :-- |
| `product_type` | object | required | Details of the product type associated with the product. |
| `modifier_sets` | object | required | Details of the modifier sets associated with the product. |
| `product_variants` | object | required | Details of the product variants associated with the product. |

#### product_relationships_attributes

| Property | Type | Contract | Description |
| :-- | :-- | :-- | :-- |
| `id` | string | required, max length 36 characters | Universally unique ID (UUID) that identifies the related object. |
| `type` | string | required | The [type](https://jsonapi.org/format/#document-resource-object-identification) member is used to describe resource objects that share common attributes and relationships. |

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
| `created_at` | string | required, max length 25 characters | Created at timestamp in ISO 8601 format. |
| `updated_at` | string | required, max length 25 characters | Updated at timestamp in ISO 8601 format. |

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
| `selection` | string | required | Modifier set selection type. |
| `maximum_count` | integer | required | Maximum number of modifiers that can be selected. |
| `minimum_count` | integer | required | Minimum number of modifiers that must be selected. |
| `created_at` | string | required, max length 25 characters | Created at timestamp in ISO 8601 format. |
| `updated_at` | string | required, max length 25 characters | Updated at timestamp in ISO 8601 format. |

#### product_variant

| Property | Type | Contract | Description |
| :-- | :-- | :-- | :-- |
| `id` | string | required, max length 36 characters | Universally unique ID (UUID) that identifies the related object. |
| `type` | string | required, max length 255 characters | The [type](https://jsonapi.org/format/#document-resource-object-identification) member is used to describe resource objects that share common attributes and relationships. |
| `attributes` | [product_variant_attributes](products.md#product_variant_attributes) | required | An [attributes object](https://jsonapi.org/format/#document-resource-object-attributes) representing some of the resource's data. |

#### product_variant_attributes

| Property | Type | Contract | Description |
| :-- | :-- | :-- | :-- |
| `retail_price_excl_tax` | string | required, max length 255 characters | Retail price excluding tax. |
| `retail_price_incl_tax` | string | required, max length 255 characters | Retail price including tax. |
| `regular_retail_price` | string | required, max length 255 characters | Regular retail price. |
| `sku` | string | required, max length 255 characters | SKU of the variant. |
| `barcode` | string | required, max length 255 characters | Barcode of the variant. |
| `created_at` | string | required, max length 25 characters | Created at timestamp in ISO 8601 format. |
| `updated_at` | string | required, max length 25 characters | Updated at timestamp in ISO 8601 format. |

#### product_pagination_links

| Property | Type | Contract | Description |
| :-- | :-- | :-- | :-- |
| `prev` | string | required, max length 1024 characters | The link to the previous page of results. |
| `next` | string | required, max length 1024 characters | The link to the next page of results. |
