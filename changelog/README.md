# Changelog

## 21st February 2025
* Get bookings - updated booking [relationship](../operations/bookings.md#booking_relationships) with orders (multiple orders now related to booking instead of one).
* Get bookings - added list of [booking statuses.](../operations/bookings.md#booking_attributes)
* Get bookings - added two new fields, `depositAmount` and `isWalkIn`, for [booking attributes.](../operations/bookings.md#booking_attributes)
* Get bookings - updated bookings list endpoint [filters.](../operations/bookings.md#get_bookings)
* Get products - updated product status [enum list.](../operations/products.md#product_attributes)
* Get tables - updated tables relationships, now it is related to `area`.
* Create webhook endpoint - general improvements for webhook endpoint[ documentation page.](../operations/webhookendpoints.md)

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
