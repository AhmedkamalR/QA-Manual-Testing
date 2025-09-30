# 🔌 API – Cart Test Cases

This document contains detailed **API test cases** for the **Cart module**.  
Covers **Valid, Invalid, Edge, Security, Concurrency and Performance** scenarios.

---

## ✅ Valid Test Cases

| Step | Action | Expected Result | Attachments |
|------|--------|-----------------|-------------|
| 1 | POST `/cart/add` with valid product_id and quantity=1 | 200 OK, item added; response contains cart_id, items[], totals | – |
| 2 | POST `/cart/add` with product variation (size/color) | 200 OK, correct SKU/variation added | – |
| 3 | GET `/cart/{cart_id}` | 200 OK, returns cart items, totals, tax, discounts, currency | – |
| 4 | PUT `/cart/item/{item_id}` change quantity from 1 → 3 | 200 OK, item quantity updated, totals recalculated | – |
| 5 | DELETE `/cart/item/{item_id}` | 200 OK, item removed, totals updated | – |
| 6 | POST `/cart/apply-coupon` with valid coupon | 200 OK, discount applied, totals updated | – |
| 7 | POST `/cart/apply-giftcard` with valid code | 200 OK, gift card balance applied, totals updated | – |
| 8 | POST `/cart/merge` after login (guest -> user) | 200 OK, carts merged per merge policy, no duplicates | – |
| 9 | POST `/cart/clear` | 200 OK, cart emptied | – |
| 10 | GET `/cart/estimate-shipping?address_id=X` | 200 OK, returns shipping options and costs | – |
| 11 | POST `/cart/lock` (reserve stock) then POST `/order/create` | lock succeeds, order creation succeeds and reserved stock reduced | – |
| 12 | GET `/cart` with Authorization header (user) | 200 OK, cart persisted per user account | – |
| 13 | Verify currency handling: cart created in USD then queried with ?currency=EUR | 200 OK, totals converted using current rates | – |
| 14 | GET `/cart` after product price update in catalog | Cart reflects price policy (locked price or dynamic per policy) | – |

---

## ❌ Invalid Test Cases

| Step | Action | Expected Result | Attachments |
|------|--------|-----------------|-------------|
| 1 | POST `/cart/add` with invalid product_id (string or non-existing) | 400 Bad Request or 404 Not Found | – |
| 2 | POST `/cart/add` with negative quantity (-1) | 400 Validation error | – |
| 3 | PUT `/cart/item/{item_id}` with quantity=0 | 400 Validation or behavior defined (remove vs error) | – |
| 4 | POST `/cart/add` product that is inactive/archived | 409 Conflict or 400 with message "product unavailable" | – |
| 5 | POST `/cart/apply-coupon` with expired/invalid coupon | 400/422 with descriptive error | – |
| 6 | POST `/cart/add` exceeding max per-order limit | 409 / 400 with appropriate message | – |
| 7 | POST `/cart/merge` with invalid user token | 401 Unauthorized | – |
| 8 | GET `/cart` without auth when auth required | 401 Unauthorized | – |
| 9 | Send malformed JSON body | 400 Bad Request (not 500) | – |
| 10 | Attempt to modify another user’s cart (user A token modifies cart B) | 403 Forbidden | – |

---

## ⚠️ Edge / Advanced Test Cases

| Step | Action | Expected Result | Attachments |
|------|--------|-----------------|-------------|
| 1 | Create cart with 100 distinct items | 200 OK; response contains all items; totals correct; performance acceptable | – |
| 2 | Add extremely large quantity for single SKU (e.g., 10,000) | 409 / validation; check inventory boundaries | – |
| 3 | Add bundle/kit product containing multiple SKUs | 200 OK; bundle expands or treated as single line with components | – |
| 4 | Create cart while one item is out-of-stock mid-session | API returns item flagged as out-of-stock and advises alternatives | – |
| 5 | Apply coupon + gift card + wallet (stacking rules) | Discounts applied per business rules; totals match expectation | – |
| 6 | Two concurrent POST `/cart/add` requests for last item (concurrency) | Only one request succeeds in reserving; other gets out-of-stock/409 | – |
| 7 | POST `/cart/add` then DB connection lost before response | API returns graceful error; client can retry with idempotency | – |
| 8 | Cart created in one region then accessed from blocked region | Proper error or empty cart per geo-policy | – |
| 9 | Cart totals rounding checks with multiple discounts and taxes | Totals consistent and documented (no cent mismatch) | – |
| 10 | Export cart (large) as JSON/CSV | Successful export; size acceptable; streaming used if required | – |
| 11 | Cart with multi-currency items (marketplace) | Totals converted per currency rules and fees applied | – |
| 12 | Create cart via API while rate limit exceeded | 429 Too Many Requests with Retry-After header | – |

---

## 🔒 Security & Data Integrity Tests

| Step | Action | Expected Result | Attachments |
|------|--------|-----------------|-------------|
| 1 | Attempt parameter tampering (product_id modified on client) | Server verifies product ownership/validity and rejects tampered requests | – |
| 2 | Replay attack: resending same add request without idempotency | If idempotency header present: no duplicate; else server handles duplicates safely | – |
| 3 | SQL injection attempt in any string field (notes, promo code) | Input sanitized; no DB error; return 400 if invalid | – |
| 4 | Access control: attempt to read another user's cart | 403 Forbidden and audit logged | – |

---

## ⚡ Performance & Reliability Tests

| Step | Action | Expected Result | Attachments |
|------|--------|-----------------|-------------|
| 1 | Burst test: 1000 cart-add requests / minute | System stays within SLA (no crash); acceptable error rate; 95% responses < defined latency | – |
| 2 | Long-running carts: carts not used for 30 days | System archives/cleans per retention policy; user notified if necessary | – |
| 3 | Test fallback when shipping estimate service is slow | Cart API returns cached or default shipping with warning | – |

---

## 📌 Coverage Achieved

- **Valid Scenarios**: add/update/remove items, variations, view cart, apply coupons/giftcards, estimate shipping, merge carts, currency handling, reservations.  
- **Invalid Scenarios**: invalid IDs, negative quantities, inactive products, expired coupons, unauthorized access, malformed payloads.  
- **Edge Scenarios**: large carts, very large quantities, bundles/kits, concurrency on last item, cart merging conflicts, rounding edge cases, multi-currency marketplace.  
- **Security**: parameter tampering, SQL injection sanitization, access control and idempotency handling.  
- **Performance**: burst/stress behavior, rate limiting (429), shipping-service fallback, export large cart handling.  
- **Reliability**: graceful handling on DB or downstream failure, idempotent retry recommendations.  
