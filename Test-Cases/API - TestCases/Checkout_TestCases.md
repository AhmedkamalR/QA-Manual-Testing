# 🔌 API – Checkout Test Cases

This document contains detailed **API-level test cases** for the **Checkout module**.  
Covers Valid, Invalid, Edge, Security, and Performance scenarios.

---

## ✅ Valid Test Cases

| Step | Action | Expected Result | Attachments |
|------|--------|-----------------|-------------|
| 1 | POST /checkout with valid payload | 200 OK, order created with ID | – |
| 2 | Include valid shipping address JSON | Address accepted | – |
| 3 | Apply valid coupon via API payload | Discount applied | – |
| 4 | Choose valid delivery option | Fee added to totals | – |
| 5 | Payment success callback processed | Order status → "Paid" | – |
| 6 | Guest checkout with valid email | Order created, confirmation sent | – |
| 7 | Saved profile checkout (auth token) | Auto-fills profile data | – |
| 8 | Verify GET /order/{id} returns correct details | Data consistent | – |

---

## ❌ Invalid Test Cases

| Step | Action | Expected Result | Attachments |
|------|--------|-----------------|-------------|
| 1 | POST /checkout with missing required fields | 400 Bad Request | – |
| 2 | Invalid coupon in payload | Error code 422 with message | – |
| 3 | Use invalid delivery method ID | Error response | – |
| 4 | Send expired session token | 401 Unauthorized | – |
| 5 | Duplicate payment callback | Only one order marked Paid | – |
| 6 | Checkout with out-of-stock item ID | Error returned | – |

---

## ⚠️ Edge / Advanced Test Cases

| Step | Action | Expected Result | Attachments |
|------|--------|-----------------|-------------|
| 1 | Large payload with 100+ items | Processed successfully within SLA | – |
| 2 | Concurrent requests for same cart | Only one order created | – |
| 3 | Coupon applied at same time by multiple users | Consistent validation | – |
| 4 | Order created across different time zones | Timestamp consistent (UTC) | – |
| 5 | Special chars in address JSON | Accepted or safely escaped | – |

---

## 🔒 Security & Integrity Tests

| Step | Action | Expected Result | Attachments |
|------|--------|-----------------|-------------|
| 1 | Modify order totals in request payload | Server recalculates correctly | – |
| 2 | SQL injection attempt in fields | Query sanitized | – |
| 3 | XSS attempt in JSON payload | Escaped safely | – |
| 4 | Replay POST /checkout with same payload | Duplicate rejected | – |
| 5 | Check HTTPS enforced | Only secure requests accepted | – |

---

## ⚡ Performance & UX Tests

| Step | Action | Expected Result | Attachments |
|------|--------|-----------------|-------------|
| 1 | Stress test: 1000 checkout requests/min | API handles load with acceptable response time | – |
| 2 | Response payload size validation | Within expected limits | – |
| 3 | Latency under 200ms with 50 concurrent users | SLA achieved | – |
| 4 | Retry after network interruption | Idempotent and safe | – |

---

## 📌 Coverage Achieved

- **Valid Scenarios**: full checkout API flow with address, coupon, delivery, payment, guest and logged-in.  
- **Invalid Scenarios**: missing/invalid fields, wrong IDs, expired tokens, duplicates, stock errors.  
- **Edge Scenarios**: large payloads, concurrent requests, coupon race conditions, time zone handling.  
- **Security**: HTTPS enforced, SQLi/XSS prevented, server authoritative totals, replay protection.  
- **Performance**: stress/load test, response size limits, low latency, idempotent retries.  
