# 💖 Wishlist – Test Scenarios

This document outlines **comprehensive test scenarios** for the **Wishlist module** across API, Website, and Mobile App.  
It ensures coverage of valid, invalid, and edge cases for saving, managing, and syncing wishlist items.

---

## 1. API Scenarios

### ✅ Valid Scenarios
- Add product to wishlist by valid product ID.
- Remove product from wishlist.
- Retrieve wishlist items by user ID.
- Add multiple products to wishlist.
- Verify wishlist count updates correctly.
- Support pagination for large wishlists.
- Add product to wishlist when logged in.
- Share wishlist API (if supported).
- Clear all items from wishlist.

### ❌ Invalid Scenarios
- Add to wishlist without authentication.
- Add invalid product ID (string instead of int).
- Add product not available in region.
- Add inactive/archived product.
- Duplicate product added → should not duplicate.
- Remove product not in wishlist.
- Fetch wishlist with invalid user ID.
- Unauthorized API token used.
- API returns error when DB unreachable.
- Wishlist retrieval for deleted account.

### ⚠️ Edge Scenarios
- Wishlist with 0 items → empty state.
- Wishlist with 100+ items.
- Add/remove product rapidly (stress test).
- Concurrent wishlist updates from multiple devices.
- Multi-language product names in wishlist.
- Wishlist API under heavy load (1000 requests).
- Add bundled/combo product.
- Add product with variations (size/color).
- Wishlist sync conflict (API + Web + Mobile).

---

## 2. Website Scenarios

### ✅ Valid Scenarios
- Add product to wishlist from product details page.
- Add product from listing page.
- View wishlist from “My Account”.
- Remove product from wishlist.
- Move product from wishlist to cart.
- Wishlist persists after logout/login.
- Wishlist visible only to logged-in user.
- Wishlist syncs across devices.
- Product details in wishlist update (price, stock).
- Share wishlist via link/email (if available).

### ❌ Invalid Scenarios
- Add to wishlist without login (if restricted).
- Try to add inactive/out-of-stock product.
- Add same product multiple times.
- Broken image in wishlist item.
- Wishlist page accessible without login (security).
- Wishlist not updating count after add/remove.
- Session expired while adding to wishlist.
- Add to wishlist with ad-blockers interfering (UI).

### ⚠️ Edge Scenarios
- Wishlist with long product names → UI wrap.
- Wishlist with products in different languages.
- Wishlist with products from multiple regions.
- 50+ products in wishlist scroll pagination.
- Price changes after product saved → reflect correctly.
- Product becomes unavailable → show “Out of stock”.
- Accessibility: screen readers read wishlist items.

---

## 3. Mobile App Scenarios

### ✅ Valid Scenarios
- Add product to wishlist from product page.
- Add product from search results.
- View wishlist in “My Account”.
- Remove product from wishlist.
- Move product from wishlist to cart.
- Wishlist syncs with website.
- Wishlist persists after reinstall/login.
- Wishlist accessible offline (cached).
- Push notification for wishlist item discount.

### ❌ Invalid Scenarios
- Add to wishlist without login.
- Add invalid product (removed/archived).
- Wishlist not syncing with web.
- Remove product not in wishlist.
- Product image missing in wishlist.
- Wishlist crashes when too many items.

### ⚠️ Edge Scenarios
- Very large wishlist (100+ items).
- Add/remove products in quick succession.
- Switch app language → wishlist localized.
- Offline add to wishlist → sync later.
- Wishlist with combo/variant products.
- Wishlist shared via deep link → invalid ID.
- Force-close app during wishlist update.
- Stress test: multiple taps on "Add to Wishlist".

---

## ✅ Key Values / Keywords
- **Entities:** Wishlist, Product, User, Cart, Session.  
- **Parameters:** user_id, product_id, wishlist_id, auth_token.  
- **States:** Empty, Filled, Out of Stock, Archived, Synced, Shared.  
- **Edge:** Large wishlist, Multi-language, Variants, Sync conflicts, Network interruptions.  

---
