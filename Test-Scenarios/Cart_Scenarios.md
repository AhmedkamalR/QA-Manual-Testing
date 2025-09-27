# 🛒 Cart Scenarios 

This document covers **all possible test scenarios** for the **Shopping Cart module** in the E-commerce project.  
Scenarios are structured by **platform** (Website, Mobile App, API) and grouped into **Valid, Invalid, and Edge cases**.

---

## 🌐 Website

### ✅ Valid Scenarios
1. Add single product to cart from product detail page.  
2. Add product to cart from listing/search page.  
3. Add multiple different products → totals update correctly.  
4. Increase product quantity from cart.  
5. Decrease product quantity from cart.  
6. Remove a single product.  
7. Clear all products from cart.  
8. Cart badge counter updates after add/remove.  
9. Cart persists after page refresh.  
10. Cart persists after login (guest → logged user).  
11. Add variant product (color/size) → correct variant appears in cart.  
12. Price, discount, and tax displayed correctly.  
13. Coupon applied successfully → discount reflected.  
14. Cart updated correctly after removing applied coupon.  
15. Add product directly from wishlist to cart.  
16. Navigate to checkout from cart successfully.  

### ❌ Invalid Scenarios
1. Add out-of-stock product → error message displayed.  
2. Increase product quantity beyond stock → validation error.  
3. Add restricted product (age/location) → blocked.  
4. Apply invalid coupon code → error message shown.  
5. Enter expired coupon code → rejected with proper message.  
6. Try to checkout with empty cart → blocked.  
7. Cart price mismatch vs. product page → flagged.  
8. Attempt to edit cart while logged out unexpectedly → handled gracefully.  
9. Session expired while updating cart → should not lose data.  

### 🧪 Edge Scenarios
1. Add maximum allowed items (e.g., 50).  
2. Add same product multiple times from different tabs → cart sync check.  
3. Update cart in one tab → reflected in another tab.  
4. Change product price in backend → verify cart auto-updates.  
5. Currency switch while products in cart → totals recalc.  
6. Network disconnect while adding product → retry or error message.  
7. Large product images in cart → UI performance.  
8. Cart loaded with very high number of products → pagination or scroll check.  

---

## 📱 Mobile App

### ✅ Valid Scenarios
1. Add/remove products from detail page.  
2. Add/remove products from listing page.  
3. Swipe-to-remove item in cart.  
4. Update product quantity via + / – buttons.  
5. Cart persists after app restart.  
6. Cart syncs after login on multiple devices.  
7. Add product from wishlist to cart.  
8. Apply coupon successfully.  
9. Proceed to checkout from cart.  

### ❌ Invalid Scenarios
1. Add out-of-stock product → error.  
2. Increase quantity above stock limit.  
3. Checkout with empty cart → blocked.  
4. Apply invalid/expired coupon.  
5. Session timeout → cart should recover after re-login.  
6. Remove product not in cart → handled gracefully.  

### 🧪 Edge Scenarios
1. Cart with max allowed products.  
2. Rapid add/remove stress test.  
3. Offline mode → show cached cart (if supported).  
4. Price update in backend while app open → auto update cart.  
5. Switch between Android/iOS devices logged in same account → cart sync.  

---

## 🔗 API

### ✅ Valid Scenarios
1. `POST /api/cart/add` with valid product_id & qty → item added.  
2. `PUT /api/cart/update` with valid qty → item updated.  
3. `DELETE /api/cart/remove` with valid product_id → item removed.  
4. `GET /api/cart` returns correct schema (items, subtotal, discount, taxes).  
5. Add multiple products and validate totals.  

### ❌ Invalid Scenarios
1. Add product with invalid `product_id` → 404 error.  
2. Add product with qty = 0 or negative → 400 error.  
3. Update/remove non-existing product → error handled.  
4. Apply invalid/expired coupon code via API → rejected.  
5. Unauthorized request (missing token) → 401 error.  

### 🧪 Edge Scenarios
1. Add max allowed items in single request.  
2. Bulk add/remove operations rapidly → API stability.  
3. Multiple sessions updating cart at same time.  
4. API response under network latency simulation.  
5. Validate response time < 200ms under load.  
6. Schema validation against OpenAPI spec.  

---

## 🗝️ Key Values / Keywords
- Cart persistence  
- Multi-device sync  
- Guest vs. logged-in flow  
- Stock validation  
- Coupon/discount validation  
- Real-time updates  
- Session handling  
- API schema & response codes  
- Performance under stress  

---
