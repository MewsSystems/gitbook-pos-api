<!-- AUTOMATICALLY GENERATED, DO NOT MODIFY -->
# HealthCheck

## Get health check status

Returns a health check object with status message.

### Request

`[PlatformAddress]/api/v2/health-check`

### Response

```javascript
{
  "id": "undefined",
  "type": "health_check",
  "attributes": {
    "message": "Service is operational"
  }
}
```

| Property | Type | Contract | Description |
| :-- | :-- | :-- | :-- |
| `Id` | string | required, max length 1024 characters |  |
| `Type` | string | required, max length 1024 characters |  |
| `Attributes` | [health_check_attributes](healthcheck.md#health_check_attributes) | required |  |

#### health_check_attributes

| Property | Type | Contract | Description |
| :-- | :-- | :-- | :-- |
| `Message` | string | required, max length 1024 characters | Shows the current service status. |
