# Webhooks

Webhooks provide a streamlined way to receive event notifications about various entities. Register your Webhook endpoints with Mews using API Operation [Create webhook endpoint](../operations/webhookendpoints.md#create-webhook-endpoint).

## Key features

* __POST requests__ – Webhook messages are sent as HTTP `POST` requests with the event details in the JSON body.
* __Authenticated__ – Each webhook request includes an `X-Signature` header, which contains an HMAC SHA-256 signature to verify the authenticity of the webhook. For more details, see [Webhook security](wh-security.md).
* __Unified event delivery__ – Each message encapsulates all simultaneous events related to the entities you’ve subscribed to. For example, subscribing to booking events may result in a webhook containing multiple `booking.status.updated` events, each corresponding to a different booking.
* __Event structure__ – Each event within a message specifies the event type and includes the unique identifier of the associated entity, e.g., `booking.status.updated` events include a `BookingId`. To retrieve detailed information about an entity, use the relevant API Operation along with the entity’s unique identifier.

## Implementation

To implement Webhooks:

1. Define the entities and event types you are interested in via your Webhook subscription.
2. Fetch additional details about entities as needed by using the appropriate API Operations.

## Supported events

| <div style="width:100px">Entity</div> | <div style="width:150px">Event</div> | Description |
| :-- | :-- | :-- |
| `bookings` | `booking.status.updated`  | A booking is updated. This includes any modifications to its properties. |
| `orders` | `order.status.updated`  | An order status is updated. This includes any modifications to order status. |
| `products` | `product.availability.updated`  | A product availability is updated. This includes any modifications to product availability. |

## Request body

```json
{
    "data": {
        "id": "98656c4a-950d-4b19-b7ef-ad1744e92b53",
        "type": "bookings",
        "attributes": {
            "status": "seated",
            "updatedAt": "2025-02-06T09:41:30.465Z"
        }
    },
    "meta": {
        "event_type": "booking.status.updated"
    }
}
```

| Property | Type | Contract | Description |
| :-- | :-- | :-- | :-- |
| `data` | [EventData](#eventdata) | required | Details of the event. |
| `meta` | [MetaData](#metadata) | required | Meta data related to the event. |

### EventData

| Property | Type | Contract | Description |
| :-- | :-- | :-- | :-- |
| `id` | string | required | Unique identifier of the entity related to the event. |
| `type` | string | required | The type of entity related to the event, e.g. `bookings`. |
| `attributes` | [EventAttributes](#eventattributes) | required | Attributes of the event or entity. The contents depend on the event type. |

### MetaData

| Property | Type | Contract | Description |
| :-- | :-- | :-- | :-- |
| `event_type` | string | required | The type of event, e.g. `booking.status.updated`. |

### EventAttributes

#### booking.status.updated properties:

| Property | Type | Contract | Description |
| :-- | :-- | :-- | :-- |
| `status` | string [Booking status](#booking-status) | required | The new status of the booking, e.g. `seated`. |
| `updatedAt` | string | required | Timestamp of when the booking was updated. |

#### Booking status

* `confirmed` – The booking has been made and confirmed.
* `seated` – The customer has arrived and the party is seated.
* `completed` – The booking has finished.
* `cancelled` – The customer has cancelled the booking.
* `noShow` – The customer did not show up and the booking has been registered by the staff as a 'no show'.

#### order.status.updated properties:

| Property | Type | Contract | Description |
| :-- | :-- | :-- | :-- |
| `status` | string [Order status](#order-status) | required | The new status of the order, e.g. `paid`. |
| `updatedAt` | string | required | Timestamp of when the order was updated. |

#### Order status

* `draft` – The order is in draft state.
* `sent` – The order has been sent.
* `paid` – The order has been paid.
* `discarded` – The order has been discarded.
* `cart` – The order is in cart state.
* `pending_payment` – The order is pending payment.
* `open` – The order is open and can be modified.
* `open_web` – The order is open for web processing.

#### product.availability.updated properties:

| Property | Type | Contract | Description |
| :-- | :-- | :-- | :-- |
| `isAvailable` | boolean | required | The new availability status of the product. |
| `updatedAt` | string | required | Timestamp of when the product availability was updated. |
