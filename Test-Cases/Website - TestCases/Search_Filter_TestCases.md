# 🔍 Website - Search & Filter Test Cases

This document contains **detailed test cases** for the **Search & Filter module (Website)**.  
It ensures full coverage across **Valid, Invalid, and Edge scenarios**.

---

## ✅ Valid Test Cases

| Step | Action | Expected Result | Attachments |
|------|--------|-----------------|-------------|
| 1 | Enter valid keyword (e.g., "Laptop") in search bar. | Search results page displays relevant products. | |
| 2 | Enter exact product name. | Product details page link appears in results. | |
| 3 | Enter partial keyword (e.g., "lap"). | Results show all matching items. | |
| 4 | Apply filter: price range (100–500). | Only products within price range are displayed. | |
| 5 | Apply multiple filters (brand + price + rating). | Products meet all filter criteria. | |
| 6 | Sort results (Price Low → High). | Products displayed in ascending price order. | |
| 7 | Sort results (Newest Arrivals). | Newest products appear first. | |
| 8 | Use category filter (Electronics > Laptops). | Only laptops are displayed. | |
| 9 | Verify pagination (page 1, page 2). | Correct results appear with navigation. | |
| 10 | Change website language (EN → AR) and search. | Results update with localized data. | |

---

## ❌ Invalid Test Cases

| Step | Action | Expected Result | Attachments |
|------|--------|-----------------|-------------|
| 1 | Submit search with empty input. | Validation message or no results page. | |
| 2 | Enter invalid characters (e.g., "@@@@"). | 0 results with handled error state. | |
| 3 | Apply invalid filter values (min > max price). | System shows no results or validation error. | |
| 4 | Modify search URL with invalid product ID. | 404 page displayed gracefully. | |
| 5 | Clear cookies/session and perform search. | Search still works as expected. | |
| 6 | Apply filters on empty results page. | No products found message displayed. | |
| 7 | Perform search without network (offline). | System shows offline error state. | |
| 8 | Tamper with search query string for SQL injection attempt. | Request blocked or sanitized safely. | |

---

## ⚠️ Edge Test Cases

| Step | Action | Expected Result | Attachments |
|------|--------|-----------------|-------------|
| 1 | Enter extremely long keyword (200+ chars). | System trims input and returns valid results or error. | |
| 2 | Enter keyword with emojis (e.g., "📱Laptop"). | Search handles emojis gracefully. | |
| 3 | Enter mixed case ("LAPTOP" vs "laptop"). | Results remain the same (case-insensitive). | |
| 4 | Product exists but out of stock. | Product appears with "Out of Stock" label. | |
| 5 | Apply all filters at once (brand + price + rating + category). | Results update correctly. | |
| 6 | Use back/forward browser navigation after applying filters. | Filters and results remain consistent. | |
| 7 | Switch device viewport (desktop → mobile) mid-search. | Results and filters adapt responsively. | |
| 8 | Load more results with infinite scroll (if supported). | Results load smoothly without duplicates. | |
| 9 | Test with slow internet. | Results load progressively with loading indicators. | |
| 10 | Search in empty database (no products). | Displays "No Products Found" message clearly. | |

---

## 📌 Coverage Achieved

- **Valid Scenarios**: Keyword search, exact/partial matches, filters (price, brand, rating, stock, category), sorting, pagination, language change.  
- **Invalid Scenarios**: Empty input, invalid characters, wrong filter values, broken links, offline mode, tampered queries.  
- **Edge Scenarios**: Very long keywords, emojis/Unicode, case sensitivity, out-of-stock results, multi-filters, responsive checks, infinite scroll, slow internet.  
- **Security**: SQL injection prevention, sanitized query handling, safe error states.  
- **Performance**: Pagination, infinite scroll, slow network, filter performance under load.  
- **Usability**: Consistent filters, back/forward navigation, responsive layouts, multilingual search accuracy.  
- **Accessibility**: Search bar focus, clear error messages, readable "No Products Found" states.  

---
