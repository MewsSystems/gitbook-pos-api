# Inventory management

This use case is aimed at external Inventory Management Systems, and it describes how to use the __Mews POS API__ to managing inventory across multiple point-of-sale locations or outlets.

## Contents

* [Product synchronization](#product-synchronization)
* [Fetching sales data](#fetching-sales-data)
* [Fetching the location or outlet](#fetching-the-location-or-outlet)
* [Frequently Asked Questions](#frequently-asked-questions)
* [Additional help](#additional-help)

## Product synchronization

In order to synchronize products with Mews POS, use the [Get products](../operations/products.md#get-products) endpoint `GET /api/v2/products`. You can call this API operation periodically to refresh the product catalogue and make sure it is in sync with your system. The product attributes in the response include name, description, [SKU](https://en.wikipedia.org/wiki/Stock_keeping_unit), barcode, and price information.

#### Example Request:

```
GET /api/v2/products
Authorization: Basic <base64-encoded-credentials>
Content-Type: application/vnd.api+json
```

Further detail can be obtained via linked entities such as `product_type` (e.g. food or beverage), `modifier_set` (product qualifiers, such as pizza toppings) and `product_variant`. These can be included in the response by using the same request but specifying the relevant include query parameters, as per the [JSON:API specification](https://jsonapi.org/).

#### Example Request:

```
GET /api/v2/products?include=product_type,modifier_set,product_variant
Authorization: Basic <base64-encoded-credentials>
Content-Type: application/vnd.api+json
```

### Pagination

The response is paginated using cursor pagination. Use the `next` link to request the next page of data.

## Fetching sales data

Use the [Get invoices](../operations/invoices.md#get-invoices) endpoint `GET /api/v2/invoices` to fetch invoices, containing order item data. Invoice attributes in the response include a description field and information about amounts, including `tax`, `total`, `subtotal`, `discount` and `tip_amount`.

#### Example Request:

```
GET /api/v2/invoices
Authorization: Basic <base64-encoded-credentials>
Content-Type: application/vnd.api+json
```

Filter the invoices by date using the `filter` query parameter.

#### Example Request:

```
GET /api/v2/invoices?filter=XXX
Authorization: Basic <base64-encoded-credentials>
Content-Type: application/vnd.api+json
```

Linked to the invoice entity are:

* __User__ – the customer
* __Register__ – the cash register or outlet terminal used for the transaction
* __Items__ – an array of invoice order items

These can be selectively included in the response by using the same request but specifying the relevant include query parameters, as per the [JSON:API specification](https://jsonapi.org/). Item attributes include `product_name`, `quantity`, `total` and amount breakdowns for tax and discounts. Use the register `self` link to obtain the full register information, including outlet name.

#### Example Request:

```
GET /api/v2/invoices?include=invoice_item,user,register
Authorization: Basic <base64-encoded-credentials>
Content-Type: application/vnd.api+json
```

#### Example Response:

```json
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
  ],
  "links": {
    "prev": "https://pos.mews-demo.com/api/v2/invoices?page%5Bbefore%5D=NA&page%5Bsize%5D=1",
    "next": "https://pos.mews-demo.com/api/v2/invoices?page%5Bafter%5D=NA&page%5Bsize%5D=1"
  }
}
```

### Pagination

The response is paginated using cursor pagination. Use the `next` link to request the next page of data.

## Fetching the location or outlet

It is helpful to first understand the domain entities and their relationships. POS locations, such as a named bar or restaurant, are called __outlets__ in Mews POS. POS terminals or cash registers are called __registers__. __Invoices__ are linked to a register, which is the terminal used for making the financial transaction.

* So the entity relationship is `Venue` –> `Outlet` –> `Register` –> `Invoice`

To obtain the outlet for an invoice, follow these steps:

1. Fetch the invoice, including related register information
2. Fetch the register, including related outlet information

### Fetch the invoice, including related register information

To fetch the invoice and register, use `GET /api/v2/invoices?include=register`. The register information returned will include the register resource in the `self` field.

### Fetch the register, including related outlet information

Use the register identifier to obtain the register and outlet, e.g. `GET /api/v2/registers?id=eef23c03-49b9-432b-b1a3-955ea1501557,include=outlet`.

## Frequently Asked Questions

<!-- * [What does the fieldset query parameter do?]() -->
<!-- * [Where is Product ID in invoice items?]() -->
<!-- * [Why are you using snake_case when JSON:API recommends camelCase?]() -->
* [How do you represent returns and cancellations?](#how-do-you-represent-returns-and-cancellations)
* [How do you represent waste?](#how-do-you-represent-waste)
* [Are open orders included in the API?](#are-open-orders-included-in-the-API)
* [How do you represent modifiers and add-ons?](#how-do-you-represent-modifiers-and-add-ons)
* [How do you represent combo deals?](#how-do-you-represent-combo-deals)

### How do you represent returns and cancellations?
_How do you represent returns and cancellations, e.g. wrong order, or customer changed their mind?_

* __Answer__: TBD

### How do you represent waste?
_How do you represent waste, e.g. a dropped plate in the kitchen, or a spoiled item?_

* __Answer__: We currently don't support this feature.

### Are open orders included in the API?
_Are open orders included in the API as well, or is the state of every order final?_

* __Answer__: No, only final orders are represented.

### How do you represent modifiers and add-ons?
_How do you represent modifiers and add-ons, e.g. extra cheese, no tomatoes?_

* __Answer__: TBD

### How do you represent combo deals?
_How do you represent menu items and combo deals, e.g. Lunch combo Burger+Cola+Fries?_

* __Answer__: TBD

## Additional help

You may find these additional resources helpful when working with __Mews POS__ in the demo environment.

> **Help Guides**:
> * [Adding product variants in Mews POS](https://help.mews.com/s/article/adding-product-variants-in-the-mews-pos?language=en_US)
> * [How to create a product modifier in Mews POS](https://help.mews.com/s/article/creating-a-modifier?language=en_US)
> * [Managing product modifiers in Mews POS](https://help.mews.com/s/article/managing-product-modifiers-in-the-mews-pos?language=en_US)
