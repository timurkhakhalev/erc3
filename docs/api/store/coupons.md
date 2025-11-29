# Coupon Management

### Apply Coupon
**POST** `/coupon/apply`

Applies a discount coupon to the current basket.

**Request:**
```json
{
  "tool": "/coupon/apply",
  "coupon": "SAVE10"
}
```

**Response:**
```json
{}
```

### Remove Coupon
**POST** `/coupon/remove`

Removes the currently applied coupon.

**Request:**
```json
{
  "tool": "/coupon/remove"
}
```

**Response:**
```json
{}
```

## Demo API Endpoints

**Base URL Pattern**: `{base_url}/demo/{task_id}`

Demo endpoints use the same tool-based dispatch pattern as store endpoints.
