<!-- AUTOMATICALLY GENERATED, DO NOT MODIFY -->
# Tables

## Get tables

This operation returns a list of tables.

**Note:** This operation needs [Authentication](../guidelines/authentication.md) and supports the following JSON:API features:

- [Sparse fieldsets](../guidelines/sparse-fieldsets.md) - supports all fields of `table` with `fields` query parameter.

### Request

`GET` `[PlatformAddress]/api/v2/tables`

### Response

```javascript
{
  "data": [
    {
      "id": "286ef74f-e37f-477f-bcda-77f8fbfd13ea",
      "type": "tables",
      "attributes": {
        "number": "Table number 1",
        "numberOfSeats": 4,
        "createdAt": "2024-11-13T11:29:00Z",
        "updatedAt": "2024-11-15T11:29:00Z"
      }
    }
  ],
  "links": {
    "prev": "https://pos.mews-demo.com/api/v2/tables?page%5Bbefore%5D=NA&page%5Bsize%5D=1",
    "next": "https://pos.mews-demo.com/api/v2/tables?page%5Bafter%5D=NA&page%5Bsize%5D=1"
  }
}
```
Below is a list of all possible fields this endpoint can return including relationships fields fetched with include query parameter.

| Property | Type | Contract | Description |
| :-- | :-- | :-- | :-- |
| `number` | string | required, max length 255 characters | Number of the table. |
| `numberOfSeats` | integer | required | Number of seats for the table. |
| `createdAt` | string | required, max length 25 characters | Created at timestamp in RFC 3339 format. |
| `updatedAt` | string | required, max length 25 characters | Updated at timestamp in RFC 3339 format. |

#### table_pagination_links

| Property | Type | Contract | Description |
| :-- | :-- | :-- | :-- |
| `prev` | string | required, max length 1024 characters | The link to the previous page of results. |
| `next` | string | required, max length 1024 characters | The link to the next page of results. |
