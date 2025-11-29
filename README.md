# ERC3 API Documentation

REST API documentation for the ERC3 benchmark evaluation platform.

## Documentation

- [API Overview](docs/api/overview.md) - Base URL, authentication, request/response patterns
- [Core API](docs/api/core/index.md) - Benchmarks, sessions, tasks
- [Store API](docs/api/store/index.md) - Store operations (products, cart, coupons)
- [ERC3-Dev Benchmark](docs/api/erc3-dev/index.md) - Identity system, time tracking, agent communication
- [Examples](docs/api/examples/index.md) - curl examples

**Base URL**: `https://erc.timetoact-group.at`

## Quick Start

All endpoints use POST with JSON payloads. Authentication via API key in request body:

```bash
curl -X POST https://erc.timetoact-group.at/start_session \
  -H "Content-Type: application/json" \
  -d '{"account_key": "key-your-api-key", "benchmark": "store"}'
```

See [full documentation](docs/api/index.md) for details.
