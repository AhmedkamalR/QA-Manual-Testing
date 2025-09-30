# 🔍 API - Search & Filter Test Cases

This document contains **detailed test cases** for the **Search & Filter module (API level)**.  
It ensures full coverage across **Valid, Invalid, and Edge scenarios**.

---

## ✅ Valid Test Cases

| Step | Action | Expected Result | Attachments |
|------|--------|-----------------|-------------|
| 1 | Send a search request with a valid keyword (e.g., "iPhone"). | Returns a list of products matching the keyword. | |
| 2 | Search using exact product name. | Returns that specific product. | |
| 3 | Search using partial keyword (e.g., "iph"). | Returns all products starting with or containing "iph". | |
| 4 | Apply price filter (min=100, max=500). | Only products within range are returned. | |
| 5 | Apply multiple filters (brand + price + rating). | Products match all applied filters. | |
| 6 | Search with sorting (price low → high). | Results are correctly sorted. | |
| 7 | Verify pagination (page=1, limit=20). | Returns 20 results with pagination metadata. | |
| 8 | Fetch search results in different languages (EN/AR). | Returns localized product data. | |
| 9 | Search with special category filter (e.g., "On Sale"). | Returns discounted products. | |
| 10 | Apply stock filter (In Stock only). | Only available products are returned. | |

---

## ❌ Invalid Test Cases

| Step | Action | Expected Result | Attachments |
|------|--------|-----------------|-------------|
| 1 | Search with an empty keyword. | Returns error or validation message. | |
| 2 | Search with invalid characters (e.g., "!@#$"). | Returns 0 results with handled error. | |
| 3 | Invalid filter values (negative price, invalid brand ID). | Returns validation error. | |
| 4 | Invalid pagination (page=-1, limit=0). | Returns error response. | |
| 5 | Search request without required parameters. | API returns 400 Bad Request. | |
| 6 | Search endpoint called without authentication (if required). | Returns 401 Unauthorized. | |
| 7 | SQL injection attempt in keyword (e.g., "iPhone'; DROP TABLE"). | Request blocked or sanitized. | |
| 8 | XSS injection attempt in keyword (e.g., `<script>alert(1)</script>`). | Request blocked or sanitized. | |

---

## ⚠️ Edge Test Cases

| Step | Action | Expected Result | Attachments |
|------|--------|-----------------|-------------|
| 1 | Search with extremely long keyword (500+ chars). | API trims/handles gracefully. | |
| 2 | Search with emojis or special Unicode characters. | API handles input correctly. | |
| 3 | Search with different case ("IPHONE" vs "iphone"). | Results remain the same (case-insensitive). | |
| 4 | Search for product with no stock but exists in DB. | Returns product but with "Out of Stock". | |
| 5 | Request with very high limit (e.g., 1000). | Returns limited results with proper response time. | |
| 6 | Search during high load (performance). | API responds within SLA. | |
| 7 | Product exists only in Arabic but searched in English. | Returns 0 results or fallback. | |
| 8 | Search when DB has 0 products. | Returns empty list gracefully. | |

---

## 📌 Coverage Achieved

- **Valid Scenarios**: Keyword search, exact/partial matches, filters (price, brand, rating, stock), sorting, pagination, multi-language, special categories.  
- **Invalid Scenarios**: Empty keyword, invalid characters, invalid filters/pagination, missing parameters, unauthorized access, SQL/XSS attempts.  
- **Edge Scenarios**: Very long keywords, Unicode/emojis, case sensitivity, out-of-stock results, large pagination, DB empty state, high load performance, localization gaps.  
- **Security**: SQL injection prevention, XSS sanitization, authentication/authorization checks.  
- **Performance**: Pagination handling, stress with large result sets, SLA compliance.  
- **Usability**: Multi-language, localized search accuracy, filters consistency across regions.  

---
