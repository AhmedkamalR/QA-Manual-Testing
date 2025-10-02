# 🔌 API – Order Management Test Cases

This document contains detailed **API test cases** for the **Order Management module**.  
Covers Valid, Invalid, Edge, Security, and Performance scenarios.

---

## ✅ Valid Test Cases

| Step | Action | Expected Result | Attachments |
|------|--------|-----------------|-------------|
| 1 | POST /orders with valid payload (items + address + payment) | 201 Created, order ID returned | – |
| 2 | GET /orders/{id} with valid token | 200 OK, order details returned | – |
| 3 | GET /orders (list) | Returns list with pagination metadata | – |
| 4 | PUT /orders/{id}/cancel before dispatch | 200 OK, status=Cancelled | – |
| 5 | POST /orders/{id}/return valid item | 200 OK, return initiated | – |
| 6 | POST /orders/{id}/reorder | 200 OK, new cart/session created | – |

---

## ❌ Invalid Test Cases

| Step | Action | Expected Result | Attachments |
|------|--------|-----------------|-------------|
| 1 | POST /orders with empty items array | 400 Bad Request, validation error | – |
| 2 | GET /orders/{id} without token | 401 Unauthorized | – |
| 3 | PUT /orders/{id}/cancel after shipped | 409 Conflict, cannot cancel | – |
| 4 | POST /orders/{id}/return with invalid item ID | 404 Not Found | – |
| 5 | Access another user’s order with valid token | 403 Forbidden | – |

---

## ⚠️ Edge / Advanced Test Cases

| Step | Action | Expected Result | Attachments |
|------|--------|-----------------|-------------|
| 1 | Create order with 1000 items | Server handles and responds within SLA | – |
| 2 | Stress test: 50 requests to reorder endpoint simultaneously | No duplicates, server handles concurrency | – |
| 3 | Cancel order while payment still pending | Status updated consistently | – |
| 4 | GET /orders with invalid page/size params | Returns validation error | – |

---

## 🔒 Security & Integrity Tests

| Step | Action | Expected Result | Attachments |
|------|--------|-----------------|-------------|
| 1 | SQL injection in order ID | Request rejected, no data leakage | – |
| 2 | Modify return payload to refund more than paid | Server rejects, logs alert | – |
| 3 | Replay attack on reorder endpoint | Idempotency key prevents duplication | – |

---

## ⚡ Performance & SLA Tests

| Step | Action | Expected Result | Attachments |
|------|--------|-----------------|-------------|
| 1 | Load test: 1000 requests/minute to GET /orders | Server responds within SLA (e.g., <300ms) | – |
| 2 | Spike test: sudden surge in order placements | System scales, no downtime | – |
| 3 | API returns consistent status under load | No 500 errors | – |

---

## 📌 Coverage Achieved
- **Valid**: Create, view, cancel, return, reorder via API.  
- **Invalid**: Missing tokens, invalid payloads, unauthorized access.  
- **Edge**: Large payloads, concurrency, pending-payment scenarios.  
- **Security**: Injection, tampering, replay attack prevention.  
- **Performance**: Load, stress, spike tests with SLA adherence.  
