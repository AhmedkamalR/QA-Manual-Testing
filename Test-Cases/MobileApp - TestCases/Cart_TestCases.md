# 📱 Mobile App – Cart Test Cases

This document contains detailed **Mobile App test cases** for the **Cart module**.  
Covers Valid, Invalid, Edge, Performance, Accessibility scenarios.

---

## ✅ Valid Test Cases

| Step | Action | Expected Result | Attachments |
|------|--------|-----------------|-------------|
| 1 | Tap "Add to Cart" from product list | Mini-cart badge increments; toast confirmation shown | – |
| 2 | Tap "Add to Cart" from product detail after choosing variation | Correct variation added with details | – |
| 3 | View Cart screen | Items listed with qty, price, subtotal, totals | Screenshot |
| 4 | Increase quantity via + button | Quantity increments, totals recalculated | – |
| 5 | Decrease quantity via - button; when 0 → confirm remove | Item removed after confirmation | – |
| 6 | Swipe left on cart line to reveal "Remove" and tap it | Item removed, totals updated | – |
| 7 | Apply coupon in cart UI and hit "Apply" | Coupon applied and totals updated | – |
| 8 | Use "Move to Wishlist" action | Item moved to wishlist and removed from cart | – |
| 9 | Tap "Checkout" | Navigates to checkout with cart preserved | – |
| 10 | Offline: add item to cart (cached) then go online | Item synced to server and appears in web/other devices | – |

---

## ❌ Invalid Test Cases

| Step | Action | Expected Result | Attachments |
|------|--------|-----------------|-------------|
| 1 | Add to cart an inactive product using deep link | Error message "product unavailable" displayed | – |
| 2 | Enter invalid qty via manual input (if allowed) | Validation blocks and displays error | – |
| 3 | Attempt apply expired coupon | Coupon rejected with clear message | – |
| 4 | Add item beyond user's allowed max (e.g., promo limit) | Action blocked with message | – |
| 5 | Loss of internet during quantity update | App shows error and allows retry without data loss | – |

---

## ⚠️ Edge / Advanced Test Cases

| Step | Action | Expected Result | Attachments |
|------|--------|-----------------|-------------|
| 1 | Create cart with 50–100 items on low-end device | App remains responsive; list virtualization used | – |
| 2 | Rotate device while editing qty | UI persists state and updates correctly | – |
| 3 | Rapid add/remove taps on same item | No duplicate lines; debouncing works | – |
| 4 | Cart merge conflict: item X exists in server cart with qty 1 and local cart has qty 3 | Merge policy applied (sum/override) and user informed | – |
| 5 | Use app while switching network types (Wi-Fi → mobile) during cart update | Retry/resume handles correctly | – |
| 6 | Cart with high-resolution images (lazy load) | App shows placeholders and loads progressively | – |
| 7 | Deep link to cart with expired session | Prompt to login and restore cart when authenticated | – |
| 8 | Price recalculation after promo expiry while on cart screen | User notified and totals updated | – |

---

## 🔒 Security & Integrity Tests

| Step | Action | Expected Result | Attachments |
|------|--------|-----------------|-------------|
| 1 | Tamper deep link payload for cart add | Server rejects; app shows safe error | – |
| 2 | Test offline cache tampering (modify local DB) | Server authoritative data overwrites on sync | – |
| 3 | Ensure PII not logged in crash logs (cart notes) | No sensitive data in logs | – |

---

## ⚡ Performance & UX Tests

| Step | Action | Expected Result | Attachments |
|------|--------|-----------------|-------------|
| 1 | Open cart with many items on older Android device | Smooth scroll and acceptable UI responsiveness | – |
| 2 | Check cart badge updates when adding items from quick actions | Badge updates in near real-time | – |
| 3 | Accessibility: VoiceOver/TalkBack reads cart items and totals correctly | Screen reader announces quantity, title, and price | – |
| 4 | Check pull-to-refresh behavior on cart screen | Cart refreshes and shows updated totals | – |

---

## 📌 Coverage Achieved

- **Valid Scenarios**: add/update/remove items, variations, move to wishlist, coupon application, offline add + sync, checkout link.  
- **Invalid Scenarios**: inactive product add, invalid qty, expired coupons, loss of network mid-action.  
- **Edge Scenarios**: large carts on low-end devices, merge conflicts, rapid add/remove debounce, orientation changes, promo expiry while viewing cart.  
- **Security**: server authoritative enforcement on sync, tamper protection for deep links/local cache.  
- **Performance & UX**: virtualization for long lists, lazy-loading images, responsive UI on low-end devices, accessibility compliance (TalkBack/VoiceOver).  
- **Reliability**: graceful retry/resume for network switches and idempotency for repeated user actions.  
