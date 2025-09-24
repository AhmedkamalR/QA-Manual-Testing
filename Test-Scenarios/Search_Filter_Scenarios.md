# 🔎 Search & Filter – Test Scenarios

This document covers **search and filtering functionalities** across  
**Website, Mobile App, and API** for the e-commerce project.

---

## 🌐 Website – Search & Filter Scenarios

1. **Search by Exact Product Name**
2. **Search by Partial Product Name**
3. **Search with Arabic Characters**
4. **Search with Special Characters**
5. **Search with Upper/Lower Case**
6. **Search with Non-Existing Product**
7. **Search with Category Filter Applied**
8. **Combine Multiple Filters**
9. **Clear Filters**
10. **Pagination in Search Results**

---

## 📱 Mobile App – Search & Filter Scenarios

1. **Search with Auto-Suggestions**
2. **Voice Search**
3. **Search Recent History**
4. **Search with Poor/No Internet**
5. **Filter by Toggle (e.g., In-Stock Only)**
6. **Apply Multiple Filters on App**
7. **Reset Filters**

---

## 🔌 API – Search & Filter Scenarios

1. **Valid Search Query**
2. **Invalid / Empty Search Query**
3. **Search with Arabic Characters**
4. **Search with Special Characters**
5. **Filter Parameters**
6. **Sorting Parameters**
7. **Pagination**
8. **Invalid Filter Values**
9. **Response Time**

---

## ⚠️ Edge Cases & Negative Scenarios

### Website
- **SQL Injection Attempt**
  - Input: `"Laptop'; DROP TABLE Products;--"`
  - Verify system escapes input and shows safe "no results" instead of DB error.
  
- **Cross-Site Scripting (XSS)**
  - Input: `<script>alert('xss')</script>`
  - Verify script is sanitized and no popup executes.

- **Very Long Input**
  - Enter 500+ characters in search bar.
  - Verify system trims or shows "too long query" gracefully.

- **Emoji & Non-Latin Characters**
  - Input: `😊🌍`
  - Verify no crash, safe handling, and user-friendly message.

- **Simultaneous Filters**
  - Apply all filters (Price, Brand, Rating, Availability).
  - Verify no performance degradation or crash.

---

### Mobile App
- **Offline Search**
  - Search without connection.
  - Verify "No internet" message appears, not app crash.

- **Interrupted Network**
  - Start search, turn off internet midway.
  - Verify retry/cancel options appear.

- **App Crash Resilience**
  - Rapidly apply/clear filters repeatedly.
  - Verify app stability.

---

### API
- **SQL Injection / XSS in Query Params**
  - `/search?q=<script>alert(1)</script>`
  - Verify response safely encoded, no script executed.

- **High Load / Stress Test**
  - Send 1000 search requests in short time.
  - Verify API responds within SLA and no downtime.

- **Invalid Encoding**
  - `/search?q=%ZZ`
  - Verify 400 Bad Request returned.

- **Empty Filters with Values**
  - `/search?brand=&price_min=&price_max=`
  - Verify response handles gracefully.

---

## ✅ Summary

- Covered **functional search cases** (valid, invalid, edge).
- Verified **filters combination and reset**.
- Ensured **API coverage** (valid/invalid/pagination/performance).
- Added **security & robustness testing** (SQL injection, XSS, very long input).
- Included **mobile-specific resilience scenarios** (offline, network interruptions).

