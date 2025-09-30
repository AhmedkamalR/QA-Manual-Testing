# 💻 Website – Checkout Test Cases

This document contains detailed **Website test cases** for the **Checkout module**.  
Covers Valid, Invalid, Edge, Security, and Performance scenarios.

---

## ✅ Valid Test Cases

| Step | Action | Expected Result | Attachments |
|------|--------|-----------------|-------------|
| 1 | Click "Checkout" from cart with valid items | Checkout page loads with item summary | – |
| 2 | Fill in shipping form with valid data | Address saved and reflected | – |
| 3 | Select delivery option | Correct fee and ETA shown | – |
| 4 | Apply valid promo code | Totals updated with discount | – |
| 5 | Select payment method (COD, card, PayPal) | Stored and displayed correctly | – |
| 6 | Place order with stable connection | Success page shown; confirmation email sent | Screenshot |
| 7 | Verify order appears in Order History | Data persists | – |
| 8 | Guest checkout flow works correctly | Confirmation via email | – |
| 9 | Change address before submitting | Totals recalculated | – |
| 10 | Checkout with saved profile data | Auto-filled form works | – |

---

## ❌ Invalid Test Cases

| Step | Action | Expected Result | Attachments |
|------|--------|-----------------|-------------|
| 1 | Submit empty mandatory fields | Inline validation messages displayed | – |
| 2 | Enter invalid email format | Validation error shown | – |
| 3 | Use expired or invalid coupon | Coupon rejected | – |
| 4 | Checkout with out-of-stock item still in cart | Blocked with error | – |
| 5 | Payment gateway timeout | Retry prompt shown; order not created | – |
| 6 | Checkout without agreeing to Terms | Blocked until checkbox ticked | – |
| 7 | Session expired during checkout | Redirect to login; cart preserved | – |

---

## ⚠️ Edge / Advanced Test Cases

| Step | Action | Expected Result | Attachments |
|------|--------|-----------------|-------------|
| 1 | Checkout with 100+ items in cart | Totals correct, page responsive | – |
| 2 | Multiple browser tabs with same cart | Idempotent order creation | – |
| 3 | Apply multiple promo codes | Only valid one applies | – |
| 4 | Switch languages mid-checkout | Data persists; translations applied | – |
| 5 | Checkout at 11:59 PM, delivery shows correct next-day slots | Correct slot assignment | – |
| 6 | Add gift note with emojis | Stored correctly | – |
| 7 | User cancels payment midway | Redirect back to checkout with cart intact | – |

---

## 🔒 Security & Integrity Tests

| Step | Action | Expected Result | Attachments |
|------|--------|-----------------|-------------|
| 1 | Modify totals using browser dev tools | Server rejects manipulated values | – |
| 2 | Inject script in address field | XSS prevented | – |
| 3 | Replay payment request | Server blocks duplicate transaction | – |
| 4 | Test checkout over HTTPS only | All data encrypted | – |

---

## ⚡ Performance & UX Tests

| Step | Action | Expected Result | Attachments |
|------|--------|-----------------|-------------|
| 1 | Load checkout page on low bandwidth | Optimized assets load progressively | – |
| 2 | Autofill browser saves address and card | Works without breaking validation | – |
| 3 | Accessibility: Tab order works correctly | Screen reader support functional | – |
| 4 | Load testing: 1000 simultaneous checkouts | Server scales properly | – |

---

## 📌 Coverage Achieved

- **Valid Scenarios**: full checkout flow, guest and logged-in, multiple payment methods, auto-fill data.  
- **Invalid Scenarios**: missing fields, invalid email, expired coupons, stock issues, payment failures.  
- **Edge Scenarios**: huge carts, multi-tab handling, language switch, edge timing, gift notes.  
- **Security**: HTTPS enforcement, server authoritative data, replay protection, XSS prevention.  
- **Performance & UX**: scalability, browser autofill, accessibility compliance, smooth experience.  
