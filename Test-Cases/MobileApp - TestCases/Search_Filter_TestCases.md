# 📱 Mobile App - Search & Filter Test Cases

This document contains **detailed test cases** for the **Search & Filter module (Mobile App)**.  
It ensures full coverage across **Valid, Invalid, and Edge scenarios**.

---

## ✅ Valid Test Cases

| Step | Action | Expected Result | Attachments |
|------|--------|-----------------|-------------|
| 1 | Enter valid keyword (e.g., "Shoes") in search bar. | Matching products are displayed. | |
| 2 | Use auto-suggestions dropdown. | Suggestions update dynamically and can be tapped to search. | |
| 3 | Perform voice search (microphone input). | Products relevant to spoken keyword appear. | |
| 4 | Apply filter (In-Stock toggle). | Only available products are displayed. | |
| 5 | Apply multiple filters (brand + price + size). | Results match all applied filters. | |
| 6 | Sort products (Popularity, Price Low → High). | Products rearranged accordingly. | |
| 7 | Use search history (recent queries). | Past queries can be re-searched easily. | |
| 8 | Change app language (EN → AR) and search again. | Localized results are displayed. | |
| 9 | Scroll through paginated results. | Next set of products load smoothly. | |
| 10 | Tap on product from search results. | Product details page opens correctly. | |

---

## ❌ Invalid Test Cases

| Step | Action | Expected Result | Attachments |
|------|--------|-----------------|-------------|
| 1 | Submit search with empty input. | Validation message shown or no results state. | |
| 2 | Enter invalid characters (e.g., "####"). | App shows no results but remains stable. | |
| 3 | Apply invalid filter range (e.g., min > max). | System handles gracefully with no crash. | |
| 4 | Turn off internet before search. | "No Internet Connection" message appears. | |
| 5 | Interrupt network mid-search (switch Wi-Fi → Data). | Retry or cancel option displayed. | |
| 6 | Apply filters on an empty results set. | Shows "No Products Found". | |
| 7 | Tamper with deep link search query. | App handles safely with no crash. | |
| 8 | Use invalid voice input (background noise). | Displays "No Results Found" message. | |

---

## ⚠️ Edge Test Cases

| Step | Action | Expected Result | Attachments |
|------|--------|-----------------|-------------|
| 1 | Enter very long keyword (200+ chars). | Input trimmed or error message shown gracefully. | |
| 2 | Enter emojis in search (e.g., " Shoes"). | Search executes without crash. | |
| 3 | Enter mixed language query ("حذاء Shoes"). | Results handle multilingual query properly. | |
| 4 | Case sensitivity check ("SHOES" vs "shoes"). | Results remain the same. | |
| 5 | Rapidly apply/clear filters repeatedly. | App remains stable without crash. | |
| 6 | Use offline search with cached products. | Cached products appear with offline indicator. | |
| 7 | Rotate device screen during search. | Search results adapt to orientation correctly. | |
| 8 | Switch theme (Light/Dark mode) mid-search. | Results adapt correctly without UI glitches. | |
| 9 | Test on low-end device with large result set. | App remains responsive without freezing. | |
| 10 | Search in empty catalog database. | "No Products Found" message displayed clearly. | |

---

## 📌 Coverage Achieved

- **Valid Scenarios**: Keyword, auto-suggestions, voice search, filters (stock, brand, price, size), sorting, history, language switch, pagination, product navigation.  
- **Invalid Scenarios**: Empty queries, invalid characters, wrong filter values, no internet, interrupted network, empty results, invalid deep links, noisy voice input.  
- **Edge Scenarios**: Long queries, emojis/multilingual input, case sensitivity, rapid filter toggling, offline mode, orientation changes, theme switching, low device performance.  
- **Security**: Prevents crashes from invalid queries, safe handling of malformed deep links.  
- **Performance**: Pagination, infinite scroll, network interruption, low-end device testing.  
- **Usability**: Clear error messages, stable UI with rotation & theme changes, consistent results with multilingual inputs.  
- **Accessibility**: Voice search, dark mode support, error states with readable feedback.  

---
