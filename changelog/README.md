# Changelog
## 11st April 2025
* Change PlatformAddress from https://pos.mews.com/api to https://api.mews.com/pos
* Change API versioning from v2 to v1
* [Environments:](../guidelines/environments.md)
  * Add demo accounts credentials for backend, Open API, connected PMS and Android app
  * Add production PlatformAddress

## 27st February 2025
* [Get bookings:](../operations/bookings.md#get_bookings)
  * Correcting booking JSON example response.
  * Added list of [booking statuses.](../operations/bookings.md#booking_attributes)
  * Extended [booking attributes](../operations/bookings.md#booking_attributes) with `depositAmount` and `isWalkIn`.
  * Extended bookings [filters](../operations/bookings.md#get_bookings) with  `bookingDatetimeGt`, `bookingDatetimeGteq`, `bookingDatetimeLt`, `bookingDatetimeLteq`.
* [Create booking:](../operations/bookings.md#create_booking)
  * Extended [booking attributes](../operations/bookings.md#booking_attributes) with `depositAmount` and `isWalkIn`.
* [Update booking:](../operations/bookings.md#update_booking)
  * Extended [booking attributes](../operations/bookings.md#booking_attributes) with `depositAmount` and `isWalkIn`.
* [Get products:](../operations/products.md#get_products)
  * Added permitted values for [product_attributes status](../operations/products.md#product_attributes) and [modifier_set_attributes selection](../operations/products.md#product_attributes).
* [Get tables:](../operations/tables.md#get_tables)
  * Extended tables relationships, now it is related to `area`.
  * Renamed `number` field to `name`.
* [Create webhook endpoint:](../operations/webhookendpoints.md)
  * General improvements to [webhook endpoints page.](../operations/webhookendpoints.md) Documentation-only, no changes to API.
* [Get areas:](../operations/areas.md)
  * New operation added.
* Added [Table booking](../use-cases/table-booking.md) use case.
* Added [Booking status](../events/webhooks.md#booking-status) values to [Webhooks](../events/webhooks.md).

## 20th February 2025
* Added [API Events](../events/README.md), [Webhooks](../events/webhooks.md) and [Webhook security](../events/wh-security.md)

## 17th February 2025
* Added new API operation [Create webhook endpoint](../operations/webhookendpoints.md#create-webhook-endpoint).
* Corrected booking status in JSON samples in [Bookings](../operations/bookings.md).
* Bookings are now connected to [multiple orders](../operations/bookings.md#booking_relationships) rather than only one.
* Extended [list of supported filters](../guidelines/filtering.md).

## 4th February 2025
* Extended [list of supported filters](../guidelines/filtering.md).
* [Get invoices](../operations/invoices.md#get-invoices): Extended Filters to include `registerIdEq`.

## 23rd January 2025
* New operations added:
  * [Get bookings](../operations/bookings.md#get-bookings)
  * [Create booking](../operations/bookings.md#create-booking)
  * [Update booking](../operations/bookings.md#update-booking)
  * [Get orders](../operations/orders.md#get-orders)
  * [Get customers](../operations/customers.md#get-customers)
  * [Create customer](../operations/customers.md#create-customer)
  * [Get tables](../operations/tables.md#get-tables)
* Updated operations list to match proper inflections.

| Changelog by year |
| :-- |
| [Changelog 2024](changelog2024.md) |
