<!-- AUTOMATICALLY GENERATED, DO NOT MODIFY -->
# Bookings

## Update booking

This operation updates a booking.

**Note:** This operation needs [Authentication](../essential-guide/authentication.md).

### Request

`PATCH` `[PlatformAddress]/api/v2/bookings/{id}`

```javascript
{
  "data": {
    "type": "bookings",
    "id": "83f93e1c-b6e1-4040-90cf-3274b6f3c82d",
    "attributes": {
      "status": "booked",
      "partySize": 6,
      "bookingDatetime": "2024-10-24T08:44:45.409Z"
    },
    "relationships": {
      "customer": {
        "data": {
          "type": "customers",
          "id": "5efa8b3c-b930-4b31-918d-95ab0e212e65"
        }
      },
      "tables": {
        "data": [
          {
            "type": "tables",
            "id": "5efa8b3c-b930-4b31-918d-95ab0e212e78"
          }
        ]
      }
    }
  }
}
```

| Property | Type | Contract | Description |
| :-- | :-- | :-- | :-- |
| `status` | string | required | The initial status of the booking. |
| `partySize` | integer | required | Represents the number of people included in the booking. |
| `bookingDatetime` | string | required, max length 25 characters | The booking's date. |
| `duration` | integer,null | optional | Represents the length of the booking in minutes. |
| `notes` | string,null | optional, max length 10000 characters | Additional notes for the booking. |
| `roomNumber` | string,null | optional, max length 100 characters | The room number of the booking's customer. |
| `promotions` | string,null | optional, max length 100 characters | The promotions of the booking. |
| `bookingReference` | string,null | optional, max length 255 characters | A reference code or identifier associated with the booking. |

### Response

```javascript
{
  "data": {
    "id": "83f93e1c-b6e1-4040-90cf-3274b6f3c82d",
    "type": "bookings",
    "attributes": {
      "status": "booked",
      "bookingDatetime": "2024-10-24T08:44:45.409Z",
      "duration": 90,
      "partySize": 6,
      "notes": "Vegetarian",
      "promotions": "Dinner - 4 courses INC",
      "roomNumber": "11",
      "bookingReference": "R43RdhQ",
      "createdAt": "2024-10-24T08:44:45.409Z",
      "updatedAt": "2024-10-24T08:44:45.409Z"
    },
    "relationships": {
      "order": {
        "data": {
          "id": "5efa8b3c-b930-4b31-918d-95ab0e212e65",
          "type": "orders"
        }
      },
      "customer": {
        "data": {
          "id": "5efa8b3c-b930-4b31-918d-95ab0e212e65",
          "type": "customers"
        }
      },
      "tables": {
        "data": [
          {
            "id": "5efa8b3c-b930-4b31-918d-95ab0e212e78",
            "type": "tables"
          }
        ]
      }
    }
  }
}
```
Below is a list of all possible fields this endpoint can return including relationships fields fetched with include query parameter.

| Property | Type | Contract | Description |
| :-- | :-- | :-- | :-- |
| `status` | string | required | The initial status of the booking. |
| `partySize` | integer | required | Represents the number of people included in the booking. |
| `bookingDatetime` | string | required, max length 25 characters | The booking's date. |
| `duration` | integer,null | optional | Represents the length of the booking in minutes. |
| `notes` | string,null | optional, max length 10000 characters | Additional notes for the booking. |
| `roomNumber` | string,null | optional, max length 100 characters | The room number of the booking's customer. |
| `promotions` | string,null | optional, max length 100 characters | The promotions of the booking. |
| `bookingReference` | string,null | optional, max length 255 characters | A reference code or identifier associated with the booking. |

#### booking_relationships

| Property | Type | Contract | Description |
| :-- | :-- | :-- | :-- |
| `tables` | object | required | Details of the table associated with the booking. |
| `customer` | object | required | Details of the customer associated with the booking. |

## Get bookings

This operation returns a list of bookings.

**Note**: This operation needs [Authentication](../guidelines/authentication.md) and supports the following JSON:API features:

- [Sparse fieldsets](../guidelines/sparse-fieldsets.md) - supports all fields of `booking` query parameter.

### Request

`GET` `[PlatformAddress]/api/v2/bookings`

### Response

```javascript
{
  "data": [
    {
      "id": "31b14937-2524-491f-b0a0-dc0a7393ff33",
      "type": "bookings",
      "attributes": {
        "status": "booked",
        "bookingDatetime": "2024-10-24T08:44:45.409Z",
        "duration": 60,
        "partySize": 2,
        "notes": "Vegetarian",
        "promotions": "Dinner - 4 courses INC",
        "roomNumber": "11",
        "bookingReference": "R43RdhQ",
        "createdAt": "2024-10-24T08:44:45.409Z",
        "updatedAt": "2024-10-24T08:44:45.409Z"
      },
      "relationships": {
        "order": {
          "data": {
            "id": "5efa8b3c-b930-4b31-918d-95ab0e212e65",
            "type": "orders"
          }
        },
        "customer": {
          "data": {
            "id": "5efa8b3c-b930-4b31-918d-95ab0e212e65",
            "type": "customers"
          }
        },
        "tables": {
          "data": [
            {
              "id": "5efa8b3c-b930-4b31-918d-95ab0e212e78",
              "type": "tables"
            }
          ]
        }
      }
    }
  ],
  "links": {
    "prev": "https://pos.mews-demo.com/api/v2/bookings?page%5Bbefore%5D=NA&page%5Bsize%5D=1",
    "next": "https://pos.mews-demo.com/api/v2/bookings?page%5Bafter%5D=NA&page%5Bsize%5D=1"
  }
}
```
Below is a list of all possible fields this endpoint can return including relationships fields fetched with include query parameter.

| Property | Type | Contract | Description |
| :-- | :-- | :-- | :-- |
| `status` | string | required | The initial status of the booking. |
| `partySize` | integer | required | Represents the number of people included in the booking. |
| `bookingDatetime` | string | required, max length 25 characters | The booking's date. |
| `duration` | integer,null | optional | Represents the length of the booking in minutes. |
| `notes` | string,null | optional, max length 10000 characters | Additional notes for the booking. |
| `roomNumber` | string,null | optional, max length 100 characters | The room number of the booking's customer. |
| `promotions` | string,null | optional, max length 100 characters | The promotions of the booking. |
| `bookingReference` | string,null | optional, max length 255 characters | A reference code or identifier associated with the booking. |

#### booking_pagination_links

| Property | Type | Contract | Description |
| :-- | :-- | :-- | :-- |
| `prev` | string | required, max length 1024 characters | The link to the previous page of results. |
| `next` | string | required, max length 1024 characters | The link to the next page of results. |

## Create booking

A booking represents a reservation made by a booking for goods or services, such as a table at a restaurant.

**Note:** This operation needs [Authentication](../essential-guide/authentication.md).

### Request

`POST` `[PlatformAddress]/api/v2/bookings`

```javascript
{
  "data": {
    "type": "bookings",
    "attributes": {
      "status": "booked",
      "partySize": 5,
      "bookingDatetime": "2024-10-24T08:44:45.409Z"
    },
    "relationships": {
      "customer": {
        "data": {
          "type": "customers",
          "id": "5efa8b3c-b930-4b31-918d-95ab0e212e65"
        }
      },
      "tables": {
        "data": [
          {
            "type": "tables",
            "id": "5efa8b3c-b930-4b31-918d-95ab0e212e78"
          }
        ]
      }
    }
  }
}
```

| Property | Type | Contract | Description |
| :-- | :-- | :-- | :-- |
| `status` | string | required | The initial status of the booking. |
| `partySize` | integer | required | Represents the number of people included in the booking. |
| `bookingDatetime` | string | required, max length 25 characters | The booking's date. |
| `duration` | integer,null | optional | Represents the length of the booking in minutes. |
| `notes` | string,null | optional, max length 10000 characters | Additional notes for the booking. |
| `roomNumber` | string,null | optional, max length 100 characters | The room number of the booking's customer. |
| `promotions` | string,null | optional, max length 100 characters | The promotions of the booking. |
| `bookingReference` | string,null | optional, max length 255 characters | A reference code or identifier associated with the booking. |

### Response

```javascript
{
  "data": {
    "id": "83f93e1c-b6e1-4040-90cf-3274b6f3c82d",
    "type": "bookings",
    "attributes": {
      "status": "booked",
      "bookingDatetime": "2024-10-24T08:44:45.409Z",
      "duration": 60,
      "partySize": 2,
      "notes": "Vegetarian",
      "promotions": "Dinner - 4 courses INC",
      "roomNumber": "11",
      "bookingReference": "R43RdhQ",
      "createdAt": "2024-10-24T08:44:45.409Z",
      "updatedAt": "2024-10-24T08:44:45.409Z"
    },
    "relationships": {
      "customer": {
        "data": {
          "id": "5efa8b3c-b930-4b31-918d-95ab0e212e65",
          "type": "customers"
        }
      },
      "tables": {
        "data": [
          {
            "id": "5efa8b3c-b930-4b31-918d-95ab0e212e78",
            "type": "tables"
          }
        ]
      }
    }
  }
}
```
Below is a list of all possible fields this endpoint can return including relationships fields fetched with include query parameter.

| Property | Type | Contract | Description |
| :-- | :-- | :-- | :-- |
| `status` | string | required | The initial status of the booking. |
| `partySize` | integer | required | Represents the number of people included in the booking. |
| `bookingDatetime` | string | required, max length 25 characters | The booking's date. |
| `duration` | integer,null | optional | Represents the length of the booking in minutes. |
| `notes` | string,null | optional, max length 10000 characters | Additional notes for the booking. |
| `roomNumber` | string,null | optional, max length 100 characters | The room number of the booking's customer. |
| `promotions` | string,null | optional, max length 100 characters | The promotions of the booking. |
| `bookingReference` | string,null | optional, max length 255 characters | A reference code or identifier associated with the booking. |
