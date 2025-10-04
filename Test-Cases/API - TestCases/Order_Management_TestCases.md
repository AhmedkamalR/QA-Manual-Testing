# 🔌 API – Order Management Test Cases

Extensive **API test coverage** for the **Order Management module**, including validation, security, performance, and integration scenarios.

---

## ✅ Valid Test Cases

| Step | Action | Expected Result | Attachments |
|------|--------|-----------------|-------------|
| 1 | POST /orders with valid payload | 201 Created, order ID returned | – |
| 2 | GET /orders/{id} (auth user) | 200 OK with full details | – |
| 3 | GET /orders (paginated) | 200 OK + metadata (page, total, limit) | – |
| 4 | PUT /orders/{id}/cancel (before dispatch) | 200 OK, status=Cancelled | – |
| 5 | POST /orders/{id}/return | 200 OK, return initiated | – |
| 6 | POST /orders/{id}/reorder | 201 Created, new cart returned | – |
| 7 | PATCH /orders/{id}/update-address | 200 OK, address updated | – |
| 8 | POST /orders/{id}/review | 201 Created, review stored | – |
| 9 | GET /orders/{id}/invoice | 200 OK, PDF binary returned | – |
| 10 | GET /orders/track/{trackingId} | 200 OK, real-time status | – |

---

## ❌ Invalid Test Cases

| Step | Action | Expected Result | Attachments |
|------|--------|-----------------|-------------|
| 1 | POST /orders with empty payload | 400 Bad Request | – |
| 2 | GET /orders/{id} without auth token | 401 Unauthorized | – |
| 3 | PUT /orders/{id}/cancel after shipped | 409 Conflict | – |
| 4 | POST /orders/{id}/return invalid item ID | 404 Not Found | – |
| 5 | GET /orders of another user | 403 Forbidden | – |
| 6 | POST /orders/{id}/review before delivery | 422 Validation Error | – |
| 7 | PATCH /orders/{id}/update-address post-dispatch | 400 Validation Error | – |
| 8 | Invalid date filters in GET /orders | 400 Bad Request | – |

---

## ⚠️ Edge / Advanced Test Cases

| Step | Action | Expected Result | Attachments |
|------|--------|-----------------|-------------|
| 1 | POST /orders with 500 items | 201 Created, handled within SLA | – |
| 2 | GET /orders?page=1000 | Empty list, no error | – |
| 3 | Simultaneous cancel + return on same ID | Proper lock & consistency | – |
| 4 | Payment confirmation delayed | Order marked pending → paid | – |
| 5 | Retry same POST /orders with idempotency key | No duplicate orders created | – |
| 6 | Stress: 100 concurrent reorder requests | Server handles gracefully | – |
| 7 | GET /orders with filter (date, status, seller) | Proper filtered results | – |
| 8 | PATCH address while tracking active | Prevented; returns 409 | – |

---

## 🔒 Security Tests

| Step | Action | Expected Result | Attachments |
|------|--------|-----------------|-------------|
| 1 | SQL injection in order ID | Request blocked | – |
| 2 | Modify amount in request body | Server ignores client-side value | – |
| 3 | Replay payment event | Rejected (idempotency enforced) | – |
| 4 | Access /orders via invalid JWT | 401 Unauthorized | – |
| 5 | Cross-tenant data access attempt | 403 Forbidden | – |

---

## ⚡ Performance & SLA Tests

| Step | Action | Expected Result | Attachments |
|------|--------|-----------------|-------------|
| 1 | Load test 1000 req/min to GET /orders | SLA <300ms maintained | – |
| 2 | Stress 500 concurrent order creations | No downtime, queueing applied | – |
| 3 | Spike test (peak traffic 2x normal) | Autoscale triggers correctly | – |
| 4 | GET /orders/{id} latency under load | <200ms avg | – |

---

## 📌 Coverage Achieved
- **Full CRUD coverage for orders, cancel, return, reorder**
- **Validation, pagination, concurrency, idempotency**
- **Security: auth, replay, tampering, injection**
- **Performance: load, stress, spike resilience**
