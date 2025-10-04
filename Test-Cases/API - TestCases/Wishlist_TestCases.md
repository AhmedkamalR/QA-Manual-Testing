# 🧩 Wishlist Module - API Test Cases

---

## 📌 Purpose
To validate all wishlist-related API endpoints — including add, remove, list, and sync — ensuring data integrity, user access control, and consistency across sessions and devices.

---

## ✅ Wishlist - Valid Test Cases

| Step | Action | Expected Result | Attachments |
|------|---------|----------------|--------------|
| 1 | GET `/wishlist` with valid user token | Returns list of saved products |  |
| 2 | POST `/wishlist/add` with valid product ID | Product added successfully |  |
| 3 | DELETE `/wishlist/remove/{id}` | Product removed successfully |  |
| 4 | Add multiple products sequentially | All added with correct IDs |  |
| 5 | Add same product again | Returns “Already in wishlist” message |  |
| 6 | Fetch wishlist after adding items | Reflects real-time changes |  |
| 7 | Add item from different device (same user) | Synced correctly |  |
| 8 | Delete item from different device | Updates reflect on all sessions |  |
| 9 | Pagination (`/wishlist?page=2&limit=10`) | Returns proper results with metadata |  |
| 10 | Verify response time under 1 second | Meets API performance benchmark |  |

---

## ❌ Wishlist - Invalid Test Cases

| Step | Action | Expected Result | Attachments |
|------|---------|----------------|--------------|
| 1 | Add product without authentication token | 401 Unauthorized |  |
| 2 | Add invalid product ID | 400 Bad Request |  |
| 3 | Add deleted/out-of-stock product | 409 Conflict |  |
| 4 | Remove product not in wishlist | 404 Not Found |  |
| 5 | GET wishlist with expired token | 403 Forbidden |  |
| 6 | Invalid pagination params (`limit=-5`) | Validation error |  |
| 7 | Try to add product belonging to another user | 403 Forbidden |  |
| 8 | Corrupted JSON payload | 400 Bad Request |  |
| 9 | API server timeout | 504 Gateway Timeout |  |
| 10 | Add product when DB unavailable | Proper error message returned |  |

---

## ⚙️ Wishlist - Edge Test Cases

| Step | Action | Expected Result | Attachments |
|------|---------|----------------|--------------|
| 1 | Add 500+ products to wishlist | API handles volume gracefully |  |
| 2 | Remove item during sync | System prevents race condition |  |
| 3 | Add item with special chars in ID | Validation error |  |
| 4 | Add/remove rapidly via automation | No duplicates or lost entries |  |
| 5 | Simultaneous wishlist update on multiple devices | DB reflects consistent state |  |
| 6 | Verify cache invalidation after update | Updated immediately |  |
| 7 | Product removed from catalog | Auto-removed from wishlist |  |
| 8 | Server restarts mid-request | Data integrity maintained |  |
| 9 | Add item with large payload | Validation rejects properly |  |
| 10 | Test for SQL/XSS injection in payload | Rejected safely |  |

---

## 📌 Coverage Achieved

- **Valid Scenarios**: CRUD operations, multi-device sync, pagination, duplicate handling, response validation.  
- **Invalid Scenarios**: Invalid/missing tokens, bad IDs, unavailable products, malformed payloads, permission violations.  
- **Edge Scenarios**: Volume stress, concurrency, injection attacks, race conditions, server recovery, cache behavior.  

---
