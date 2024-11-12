# Filtering

__Mews POS API__ supports filtering using the JSON:API `filter` query parameter. The `filter` query parameter can be used to filter resources by attributes.
Please note that support for filters is endpoint-specific. Visit the documentation of an endpoint to get more details about the supported filters.

> **Unsafe characters**: We recommend you always URI-encode the values of filter query parameters, because filters can contain unsafe URL characters.

### Supported filters

| Property | Type | Contract | Description |
| :-- | :-- | :-- | :-- |
| `createdAtGt` | string | optional | Date-time the resource was created, in RFC 3339 format. <br> Raw example: <br> `filter[createdAtGt]=2024-07-25T16:29:35+00:00` <br> Encoded example: <br> `filter%5BcreatedAtGt%5D=2024-07-25T16%3A29%3A35%2B00%3A00` |

* We plan to add support for more filters in future.


### Example request and response

In the example request, we will query the `/invoices` endpoint with filter:

`GET` `[PlatformAddress]/api/v2/invoices?filter%createdAtGt%5D=2024-07-25T16%3A29%3A35%2B00%3A00`

#### Response

```javascript

{
    "data": [
        {
            "id": "babcf91e-5930-4b90-b929-0fb2b076bd3b",
            "type": "invoices",
            "attributes": {
                "cancelled": false,
                "cancelReason": null,
                "description": null,
                "createdAt": "2024-07-26T07:35:07.817Z",
                "updatedAt": "2024-07-26T07:35:07.836Z",
                "discount": null,
                "tax": "0.00",
                "total": "10.00",
                "subtotal": "10.00",
                "discountAmount": null,
                "itemDiscountAmount": null,
                "tipAmount": null
            },
            "relationships": {
                "user": {
                    "data": {
                        "id": "918a47d1-6553-42ee-8de4-3b5af5edc8e7",
                        "type": "users"
                    }
                },
                "register": {
                    "data": {
                        "id": "f35693cb-cc0c-4c6f-bf16-eb0547444642",
                        "type": "registers"
                    }
                },
                "invoiceItems": {
                    "data": [
                        {
                            "id": "7d87444b-807a-4ea4-8b69-b0e91f5fa174",
                            "type": "invoiceItems"
                        }
                    ]
                }
            }
        }
    ],
    "links": {
        "prev": "[PlatformAddress]/api/v2/invoices?page[before]=OTMzMw&page[size]=1",
        "next": "[PlatformAddress]/api/v2/invoices?page[after]=OTMzMw&page[size]=1"
    }
}
```