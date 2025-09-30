# 📄 API – Product Catalog Test Cases

This document contains detailed **test cases** for the **Product Catalog API**.  
Covers **Valid, Invalid, and Edge Scenarios** to ensure comprehensive coverage.

---

## ✅ Valid Test Cases

| Step | Action | Expected Result | Attachments |
|------|--------|-----------------|-------------|
| 1 | Send GET request `/products` with valid parameters | API returns list of active products with correct schema | – |
| 2 | Send GET `/products/{id}` with valid product ID | API returns correct product details | – |
| 3 | Send GET `/products?category_id=5` | API returns products under category 5 | – |
| 4 | Send GET `/products?brand=Apple` | API returns all products filtered by brand = Apple | – |
| 5 | Send GET `/products?price_min=100&price_max=500` | API returns products only within price range | – |
| 6 | Send GET `/products?sort=price_asc` | Products are sorted from low to high | – |
| 7 | Send GET `/products?sort=rating_desc` | Products sorted by rating | – |
| 8 | Send GET `/products?page=1&limit=20` | API returns 20 products with pagination info | – |
| 9 | Send GET `/products/related/{id}` | Returns related/upsell/cross-sell products | – |
| 10 | Send GET `/products/featured` | Returns featured products correctly | – |
| 11 | Send GET `/products/best-sellers` | Returns list of best-selling products | – |
| 12 | Send GET `/products/recently-viewed` (with token) | Returns correct recently viewed products | – |
| 13 | Send GET `/products/stock/{id}` | Returns stock availability and quantity | – |
| 14 | Verify response time for product catalog API (< 2s) | API responds within SLA | – |

---

## ❌ Invalid Test Cases

| Step | Action | Expected Result | Attachments |
|------|--------|-----------------|-------------|
| 1 | Send GET `/products/{id}` with non-existing ID | API returns 404 Not Found | – |
| 2 | Send GET `/products/{id}` with invalid ID type (string) | API returns 400 Bad Request | – |
| 3 | Send GET `/products?category_id=9999` | API returns empty list or proper error | – |
| 4 | Send GET `/products?price_min=-100` | API rejects with validation error | – |
| 5 | Send GET `/products?limit=0` | API returns error for invalid pagination | – |
| 6 | Send GET `/products?limit=10000` | API caps results or rejects | – |
| 7 | Send GET `/products` without authentication (if required) | API returns 401 Unauthorized | – |
| 8 | Send GET `/products` with invalid token | API returns 401 Unauthorized | – |
| 9 | Send GET `/products` with expired token | API returns 401/403 | – |
| 10 | Send malformed request (missing headers) | API returns proper error code, not 500 | – |
| 11 | Try to fetch inactive/archived product | API should return proper status (404 or hidden) | – |
| 12 | Request product not available in region | API returns localized error or empty response | – |

---

## ⚠️ Edge Test Cases

| Step | Action | Expected Result | Attachments |
|------|--------|-----------------|-------------|
| 1 | Product with extremely long description (5000 chars) | API handles without truncation errors | – |
| 2 | Product with 0 price (free) | API displays correctly | – |
| 3 | Product with overlapping discounts | API applies correct final price | – |
| 4 | Product without image | API returns default placeholder or null safely | – |
| 5 | Product with 20+ variations | API returns variations correctly | – |
| 6 | Request `/products?limit=1000` | API handles without performance degradation | – |
| 7 | Archived/inactive product requested directly | API hides it or returns 404 | – |
| 8 | Product available only in one language | API returns correct localized data | – |
| 9 | Product with very high price (1,000,000+) | API handles without overflow | – |
| 10 | Product with HTML/JS in description | API escapes/sanitizes (no XSS risk) | – |
| 11 | Stress test: 500 requests in short time | API remains stable | – |
| 12 | Simulate DB connection loss | API returns graceful error, not crash | – |

---

## 📌 Coverage Achieved

- **Valid Scenarios**: Retrieve products, categories, brands, filters, sorting, pagination, stock, featured, related, best-sellers, recently viewed, performance checks.  
- **Invalid Scenarios**: Wrong IDs, invalid pagination, negative prices, missing headers, invalid/expired tokens, unauthorized requests, archived/inactive products, malformed requests.  
- **Edge Scenarios**: Very long descriptions, free products, overlapping discounts, no images, many variations, large pagination, high prices, localization issues, sanitization, stress/performance failures.  
- **Security**: Handled invalid tokens, unauthorized access, XSS in description, SQL injection protection.  
- **Performance**: Verified response time (< 2s), stress tested with high load, DB failure handling.  
- **Usability & Reliability**: Ensures proper defaults, placeholders, and consistent error messages.  
