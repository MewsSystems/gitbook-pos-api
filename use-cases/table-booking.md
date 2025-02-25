# Table booking

This use case is aimed at Restaurant Table Booking Systems, and it describes how to use the __Mews POS API__ to manage table bookings, including:
  * Getting table availability
  * Making and amending bookings
  * Checking booking status

## Contents

* [Checking availability](#checking-availability)
* [Making a table booking](#making-a-table-booking)
* [Working with customers](#working-with-customers)
* [Alternate flows](#alternate-flows)
* [Getting status changes](#getting-status-changes)
* [Getting the customer spend](#getting-the-customer-spend)
* [Frequently Asked Questions](#frequently-asked-questions)
* [Additional help](#additional-help)

## Checking availability

You can check availability at the POS level by correlating active bookings with tables.

### 1. Get tables
First call [Get tables](../operations/tables.md#get-tables) to get information on restaurant tables, including table numbers and quantity of seats.

#### Example request:
```
GET [PlatformAddress]/api/v2/tables
```

### 2. Get bookings
Call [Get bookings](../operations/bookings.md#get-bookings) and filter by the desired booking period, to get the set of all bookings for that period, and the tables they are linked to.
Tables with no bookings are free to book. Note that this API Operation supports pagination, to manage requests in case of large amounts of data.

> #### Booking period filters
> The relevant booking period filters are:
>
> * `bookingDatetimeGt` – greater than
> * `bookingDatetimeGteq`– greater than or equal to
> * `bookingDatetimeLt` – less than
> * `bookingDatetimeLteq` – less than or equal to

#### Booking status
Check the booking status to see if the booking is active or not. The supported statuses are:
* `confirmed` – The booking has been made and confirmed.
* `seated` – The customer has arrived and the party is seated.
* `completed` – The booking has finished.
* `cancelled` – The customer has cancelled the booking.
* `noShow` – The customer did not show up and the booking has been registered by the staff as a 'no show'.

#### Example request:
```
GET [PlatformAddress]/api/v2/bookings?filter[bookingDatetimeGt]=2024-07-25T16%3A29%3A35%2B00%3A00&filter[bookingDatetimeLt]=2024-07-26T16%3A29%3A35%2B00%3A00
```

The response will tell you:
* What table or tables the booking is linked to
* The booking date and time
* The booking duration
* The party size
* The external booking reference, if applicable

See [Get bookings](../operations/bookings.md#get-bookings) for a full list of supported fields.

## Making a table booking

Once you have taken a customer booking, you can set up the booking in __Mews POS__ using [Create booking](../operations/bookings.md#create-booking).
See the API Operation description for a full list of parameters. You must specify the following parameters as a minimum:
* Booking date and time
* Party size
* Table (linked through `booking_relationships`)

In addition, it is helpful to also specify the duration, otherwise we will apply a default value, for example 90 minutes.
* Duration

#### Example request:

```
POST [PlatformAddress]/api/v2/bookings
```
```json
{
  "data": {
    "type": "bookings",
    "attributes": {
      "status": "confirmed",
      "partySize": 5,
      "bookingDatetime": "2024-10-24T08:44:45.409Z",
      "duration": "120"
    },
    "relationships": {
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

## Working with customers

If you wish to attach a named customer to a booking, you can do this by adding a customer relationship and linking to a Mews customer profile with the `id` field.

#### Example request:

```
POST [PlatformAddress]/api/v2/bookings
```
```json
{
  "data": {
    "type": "bookings",
    "attributes": {
      "status": "confirmed",
      "partySize": 5,
      "bookingDatetime": "2024-10-24T08:44:45.409Z",
      "duration": "120"
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

To obtain the profile id, perform a customer look-up using [Get customers](../operations/customers.md#get-customers) with either the `emailEq` or `fullNameEq` filter.
Note that an exact match is required, so care is needed to ensure the search string is correct.

#### Example request:
```
GET [PlatformAddress]/api/v2/customers?filter[emailEq]=john.doe@mews.com
```

If no customer profile exists for the customer, you can create one with [Create customer](../operations/customers.md#create-customer).

## Alternate flows

### Amending a table booking

To amend an existing booking, use [Update booking](../operations/bookings.md#update-booking). You can use this to update any booking parameters, including setting the booking status.

#### Example request:

```
PATCH [PlatformAddress]/api/v2/bookings/31b14937-2524-491f-b0a0-dc0a739
```

### Canceling a table booking

To cancel a booking, use [Update booking](../operations/bookings.md#update-booking) and set the booking status to `Cancelled`.

### Checking on bookings

To check on the details of bookings, use [Get bookings](../operations/bookings.md#get-bookings) (see [Checking availability](#checking-availability) above).

### Changing table assignment

The table assignment is made through the [relationship](../guidelines/relationships.md) between `Booking` and `Table`. To change table, remove the old relationship and set a new relationship. 

#### Example request:

```
PATCH [PlatformAddress]/api/v2/bookings/31b14937-2524-491f-b0a0-dc0a739
```
```json
{
  "data": {
    "type": "bookings",
    "id": "83f93e1c-b6e1-4040-90cf-3274b6f3c82d",
    "attributes": {
      "status": "confirmed",
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
            "id": "7c888ff-b8c30-88bb1-878f-225ab0e38a78"
          }
        ]
      }
    }
  }
}
```

### Walk-in customer scenario

> **Scenario:** A customer arrives without a prior booking and requests a table on-site.

Walk-ins can be created either in the Table Booking System or in __Mews POS__.

* If the restaurant has a host managing table allocations, the walk-in booking is created in the Table Booking System.
* If there is no host, the waiter seats the walk-in guest and opens an order directly from the table plan in __Mews POS__. This automatically creates a walk-in booking linked to the order.

A walk-in booking is identified by the `isWalkIn` flag in [booking_attributes](../operations/bookings.md#booking_attributes). Use this field if creating a walk-in booking. Walk-ins created through __Mews POS__ have the value "pos" for `bookingReference`, otherwise this field contains the booking reference from the Table Booking System. Note that walk-in bookings always have the initial booking status `seated`.

## Getting status changes

If you want to be notified when a booking changes status in near-real-time, for example when customers are seated or when a booking is closed or canceled, use [API Events](../events/README.md).

## Getting the customer spend

Once the booking status is `completed`, you can fetch the total amount of customer spend for the booking. First obtain the `Order` linked to the `Booking`, then obtain the `Invoice` linked to the `Order`.
Normally, a `Booking` will be linked to a single `Order` and a single `Invoice`, however in case of a split bill, a `Booking` will have multiple `Orders`, each with their own `Invoice`.

* `Booking` --> `Order` --> `Invoice`

## Frequently Asked Questions

* [How do I know if there is a no-show?](#how-do-i-know-if-there-is-a-no-show)
* [Do you handle customer preferences?](#do-you-handle-customer-preferences)
* [Do you support restaurant areas?](#do-you-support-restaurant-areas)

### How do I know if there is a no-show?
_How can I be notified of a no-show, where the customer does not turn up for their booking?_

* __Answer__: Look at the booking status within the `Booking` record. To be notified of changes to booking status, use [API Events]().

### Is there a way to specify customer preferences?
_Is there a way to express customer preferences such as table preferences or dietary requirements?_

* __Answer__: You are currently recommended to express customer preferences through the `Notes` field when creating the booking.

### Do you support restaurant areas?
_Do you support a level of organization between restaurant and table?_

* __Answer__: This is not currently supported, but may be added as we develop the API.

## Additional help

You may find these additional resources helpful when working with __Mews POS__ in the demo environment:

> **Help Guides**:
> * [Managing table orders in Mews POS](https://help.mews.com/s/article/managing-table-orders)
> * [How to move an open order to a new table in Mews POS if guests switch tables](https://help.mews.com/s/article/How-to-move-an-open-order-to-a-new-table-in-Mews-POS-if-guests-switch-tables)
> * [Table statuses in Mews POS](https://help.mews.com/s/article/table-statuses)
