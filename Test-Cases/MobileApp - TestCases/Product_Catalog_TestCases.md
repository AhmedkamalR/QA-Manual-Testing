# 📱 Mobile App – Product Catalog Test Cases

This document contains detailed **test cases** for the **Product Catalog on Mobile Application**.  
Covers **Valid, Invalid, and Edge Scenarios** to ensure comprehensive QA coverage.

---

## ✅ Valid Test Cases

| Step | Action | Expected Result | Attachments |
|------|--------|-----------------|-------------|
| 1 | Open app → go to catalog from homepage | Products are listed correctly | – |
| 2 | Swipe between categories (Electronics → Fashion) | Correct category products displayed | – |
| 3 | Apply filter by **brand** (Samsung) | Only Samsung products shown | – |
| 4 | Apply filter by **price range** (100–500) | Products displayed within range | – |
| 5 | Apply filter by **availability: In Stock** | Only available items displayed | – |
| 6 | Combine filters (brand + price + stock) | All filters applied correctly | – |
| 7 | Sort by **Price: Low to High** | Sorted ascending | – |
| 8 | Sort by **Top Rated** | Highest rated products displayed first | – |
| 9 | Tap product to open details | Product details page opens | Screenshot |
| 10 | Swipe product images in details view | Gallery scrolls smoothly | – |
| 11 | Select variations (size/color) | Correct SKU, price, and image update | – |
| 12 | Add to cart from listing | Success confirmation shown | – |
| 13 | Add to cart from details page | Product added successfully | – |
| 14 | Add to wishlist (logged in) | Product added to wishlist | – |
| 15 | Pull to refresh on catalog page | List refreshes correctly | – |
| 16 | Offline mode → open cached catalog | Last cached products displayed | – |

---

## ❌ Invalid Test Cases

| Step | Action | Expected Result | Attachments |
|------|--------|-----------------|-------------|
| 1 | Open product with invalid ID (tampered deep link) | Error or 404 page shown | – |
| 2 | Open inactive product via push notification | “Product not available” message shown | – |
| 3 | Wishlist action without login | Redirect to login screen | – |
| 4 | Apply filter with invalid values (price -100) | Safe handling or no results | – |
| 5 | Force add out-of-stock product to cart (via deeplink) | System blocks action | – |
| 6 | Tap broken product image | Placeholder image displayed | – |
| 7 | Open product with missing description | Fallback text shown | – |
| 8 | Sorting parameter invalid in API call | Default sorting applied | – |
| 9 | Open unauthorized product (region restricted) | Blocked with error | – |
| 10 | Apply empty filters → submit | No crash, handled gracefully | – |

---

## ⚠️ Edge Test Cases

| Step | Action | Expected Result | Attachments |
|------|--------|-----------------|-------------|
| 1 | Product with **15+ images** → swipe gallery | Gallery scroll stable | – |
| 2 | Product with **10+ variations** (size/color/material) | All options selectable | – |
| 3 | Product with **long name (100+ chars)** | Text wraps properly, no cut-off | Screenshot |
| 4 | Product with **multi-language description** | App displays localized content correctly | – |
| 5 | Product with **special characters/emoji in name** | Displays without crash | – |
| 6 | Product with **very high price (1M+)** | Displayed correctly | – |
| 7 | Product with **discount timer expired** | Correct fallback after expiry | – |
| 8 | Product with **cross-sell/upsell items** | Related products displayed | – |
| 9 | Pagination last page (empty state) | “No more products” shown | – |
| 10 | Switch app orientation (portrait ↔ landscape) | Layout adjusts without UI break | – |
| 11 | Repeated fast scroll + filter apply | Stable performance, no freeze | – |
| 12 | Load testing: category with 500+ products | App performance remains acceptable | – |
| 13 | Weak/unstable internet while loading catalog | Retry or offline message shown | – |
| 14 | Resume app from background on product details | Data refreshes properly | – |

---

## 📌 Coverage Achieved

- **Valid Scenarios**: Category navigation, filters, sorting, product details, images, variations, add to cart, wishlist, pull-to-refresh, offline cached data.  
- **Invalid Scenarios**: Invalid deep links, inactive products, unauthorized wishlist/cart, broken images, missing translations, invalid filters, restricted products.  
- **Edge Scenarios**: Long names, emojis, multiple variations, multi-language, high prices, countdown timers, pagination limits, orientation switch, unstable network, load testing.  
- **Security**: Unauthorized wishlist/cart actions blocked, tampered deep link validation, restricted region products handled.  
- **Performance**: Verified smooth scrolling, catalog loads under SLA with high-volume products and filters.  
- **Usability & Reliability**: Ensured clear messages, fallback placeholders, responsive UI handling for long inputs, and offline-first support.  
