# 🌐 Website – Cart Test Cases

This document contains detailed **Website test cases** for the **Cart module**.  
Format: Step | Action | Expected Result | Attachments

---

## ✅ Valid Test Cases

| Step | Action | Expected Result | Attachments |
|------|--------|-----------------|-------------|
| 1 | On product listing, click "Add to Cart" for product A | Product added; mini-cart badge increments; toast/confirmation visible | Screenshot |
| 2 | On product details page, select variation (size/color) then Add to Cart | Correct variation added; cart line shows variation info | Screenshot |
| 3 | Open Cart page | All added items listed with price, qty, subtotal, totals | Screenshot |
| 4 | Increase quantity from 1 → 2 in cart UI | Quantity updated, totals recalculated | – |
| 5 | Decrease quantity to 0 via UI (use Remove) | Item removed, totals updated | – |
| 6 | Use "Save for Later" or "Move to Wishlist" (if available) | Item moved accordingly and removed from cart | – |
| 7 | Apply valid coupon code in cart | Discount applied, totals update, coupon summary displayed | – |
| 8 | Apply valid gift card or wallet deduction | Amount deducted, totals updated | – |
| 9 | Estimate shipping by entering postal code | Shipping options and costs are displayed | – |
| 10 | Click "Proceed to Checkout" | Redirect to Checkout with cart preserved | – |
| 11 | Cart persists after logout and login (for logged-in users) | Items remain in user's cart after relogin | – |
| 12 | Mini-cart updates when cart page changed in another tab | Real-time or eventual sync visible (WebSocket/refresh) | – |
| 13 | Display price, tax, shipping breakdown on cart summary | All components shown and math correct | – |

---

## ❌ Invalid Test Cases

| Step | Action | Expected Result | Attachments |
|------|--------|-----------------|-------------|
| 1 | Attempt Add to Cart while product is inactive | Action blocked; message "product unavailable" shown | – |
| 2 | Enter quantity > available stock in cart UI | UI shows validation and restricts increase | – |
| 3 | Apply invalid/expired coupon | Coupon rejected with clear message | – |
| 4 | Tamper client-side price (via dev tools) then submit cart | Server recalculates and enforces correct prices on checkout | – |
| 5 | Try to access /cart URL without session/cookie | Redirect to login or show empty cart per policy | – |
| 6 | Clear cookies mid-session then try to place order | Either preserved via server-side cart or user prompted to re-login | – |
| 7 | Refresh during coupon application | Coupon state consistent; no double-apply | – |
| 8 | Simulate network loss while updating qty | Client shows error and allows retry without data loss | – |

---

## ⚠️ Edge / Advanced Test Cases

| Step | Action | Expected Result | Attachments |
|------|--------|-----------------|-------------|
| 1 | Add maximum allowed distinct SKUs (e.g., 100 items) | Cart page remains performant; totals correct | – |
| 2 | Add product then change region/currency | Currency and shipping recalc correctly or user warned | – |
| 3 | Add item while another user purchases last unit | On checkout, user notified and item removed or quantity adjusted | – |
| 4 | Two browser tabs add same item simultaneously | Cart merge logic prevents duplicates or adjusts quantities predictably | – |
| 5 | Coupon expiring while in cart (simulated clock) | Behavior per policy: coupon accepted if applied timestamp valid or invalidated | – |
| 6 | Cart with fractional quantities (if allowed) | UI supports and totals calculate correctly | – |
| 7 | Price change mid-session (product price updated) | Policy applied (locked price vs live price) and user notified | – |
| 8 | Accessibility: navigate cart using keyboard only | Focus order logical, ARIA attributes present, actions reachable | – |
| 9 | Low bandwidth: image lazy-loading & skeletons for cart | Page loads gracefully and actions functional | – |
| 10 | Cart persisted between devices after login | Items synced and duplicates de-duplicated per policy | – |

---

## 🔒 Security & Integrity Tests

| Step | Action | Expected Result | Attachments |
|------|--------|-----------------|-------------|
| 1 | Attempt client-side price override and place order | Server enforces server-side pricing; order uses server price | – |
| 2 | Try CSRF attack on cart endpoints (simulate) | CSRF tokens validate and request rejected | – |
| 3 | XSS attempt in cart note field | Input sanitized, no script execution | – |
| 4 | Attempt to access another user's cart via URL | 403 Forbidden or redirect | – |

---

## ⚡ Performance & UX Tests

| Step | Action | Expected Result | Attachments |
|------|--------|-----------------|-------------|
| 1 | Open cart with many items (100+) on desktop | Page interaction remains smooth (< defined fps / response thresholds) | – |
| 2 | Observe cart badge update latency on slow connection | Updates visible with spinner & consistent state | – |
| 3 | Usability: CTAs (Checkout, Continue Shopping) visible and clear on mobile & desktop | Buttons accessible and described | – |
| 4 | Visual regressions check (different screen sizes) | Cart layout consistent, no overlap | – |

---

## 📌 Coverage Achieved

- **Valid Scenarios**: add/update/remove, variations, coupon/gift card, shipping estimate, persistence, mini-cart behavior, proceed-to-checkout flow.  
- **Invalid Scenarios**: inactive products, exceed stock, invalid coupons, client-side tampering, session/cookie loss handling.  
- **Edge Scenarios**: large carts, cross-tab sync, price change policies, coupon expiry race, fractional qty, accessibility keyboard/ARIA, low-bandwidth behavior.  
- **Security**: CSRF, XSS sanitization, server-side price enforcement, authorization checks.  
- **Performance & UX**: cart badge latency, lazy-loading images, responsive layout, keyboard-only navigation, clear error states.  
