# Shopping Cart Management

### View Basket
**POST** `/basket/view`

Retrieves current shopping cart contents.

**Request:**
```json
{
  "tool": "/basket/view"
}
```

**Response:**
```json
{
  "items": [
    {
      "sku": "PROD-001",
      "quantity": 2,
      "price": 2999
    }
  ],
  "subtotal": 5998,
  "coupon": "SAVE10",
  "discount": 600,
  "total": 5398
}
```

### Add to Basket
**POST** `/basket/add`

Adds items to the shopping cart.

**Request:**
```json
{
  "tool": "/basket/add",
  "sku": "PROD-001",
  "quantity": 1
}
```

**Response:**
```json
{
  "line_count": 2,
  "item_count": 3
}
```

### Remove from Basket
**POST** `/basket/remove`

Removes items from the shopping cart.

**Request:**
```json
{
  "tool": "/basket/remove",
  "sku": "PROD-001",
  "quantity": 1
}
```

**Response:**
```json
{
  "line_count": 1,
  "item_count": 1
}
```

### Checkout
**POST** `/basket/checkout`

Processes the current shopping cart for checkout.

**Request:**
```json
{
  "tool": "/basket/checkout"
}
```

**Response:**
```json
{
  "items": [
    {
      "sku": "PROD-001",
      "quantity": 1,
      "price": 2999
    }
  ],
  "subtotal": 2999,
  "coupon": null,
  "discount": 0,
  "total": 2999
}
```
