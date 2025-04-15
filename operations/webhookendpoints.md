<!-- AUTOMATICALLY GENERATED, DO NOT MODIFY -->
# Webhook endpoints

## Create Webhook endpoint

Use this operation to register a Webhook with Mews to receive notification events that you subscribed to.
For more information, including details about supported events, see [API Events](../events/README.md).

**Note:** This operation needs [Authentication](../guidelines/authentication.md).

### Request

`POST` `[PlatformAddress]/v1/webhook-endpoints`

```javascript
{
  "data": {
    "type": "webhookEndpoints",
    "attributes": {
      "targetUrl": "https://example.com/webhooks/receive"
    }
  }
}
```

| Property | Type | Contract | Description |
| :-- | :-- | :-- | :-- |
| `data` | [webhook_endpoint_create](webhookendpoints.md#webhook_endpoint_create) | required | The document's "primary data". |

#### webhook_endpoint_create

| Property | Type | Contract | Description |
| :-- | :-- | :-- | :-- |
| `type` | string | required | The [type](https://jsonapi.org/format/#document-resource-object-identification) member is used to describe resource objects that share common attributes and relationships. |
| `attributes` | [webhook_endpoint_attributes](webhookendpoints.md#webhook_endpoint_attributes) | required | An [attributes object](https://jsonapi.org/format/#document-resource-object-attributes) representing some of the resource's data. |

### Response

```javascript
{
  "data": {
    "id": "83f93e1c-b6e1-4040-90cf-3274b6f3c82d",
    "type": "webhookEndpoints",
    "attributes": {
      "targetUrl": "https://example.com/webhooks/receive",
      "secret": "secret",
      "createdAt": "2024-10-24T08:44:45.409Z",
      "updatedAt": "2024-10-24T08:44:45.409Z"
    }
  }
}
```
Below is a list of all possible fields this endpoint can return including relationships fields fetched with include query parameter.

| Property | Type | Contract | Description |
| :-- | :-- | :-- | :-- |
| `targetUrl` | string | required, max length 100 characters | The Webhook URL configured to receive event notifications from Mews. |
| `secret` | string | required, max length 100 characters | A string generated to ensure the authenticity of the webhook. It is used to verify that the webhook request comes from a trusted source. |
| `createdAt` | string | required, max length 25 characters | Created at timestamp in RFC 3339 format. |
| `updatedAt` | string | required, max length 25 characters | Updated at timestamp in RFC 3339 format. |
