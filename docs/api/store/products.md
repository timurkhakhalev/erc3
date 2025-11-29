# Product Management

### List Products
**POST** `/products/list`

Retrieves a paginated list of products.

**Request:**
```json
{
  "tool": "/products/list",
  "offset": 0,
  "limit": 20
}
```

**Response:**
```json
{
  "products": [
    {
      "sku": "PROD-001",
      "name": "Product Name",
      "available": 10,
      "price": 2999
    }
  ],
  "next_offset": 20
}
```
