# 📱 Mobile App – Checkout Test Cases

This document contains detailed **Mobile App test cases** for the **Checkout module**.  
Covers Valid, Invalid, Edge, Security, Performance, and Accessibility scenarios.

---

## ✅ Valid Test Cases

| Step | Action | Expected Result | Attachments |
|------|--------|-----------------|-------------|
| 1 | Tap "Checkout" from Cart with valid items | Checkout page opens with items summary | – |
| 2 | Enter valid shipping address | Address saved and reflected in order summary | – |
| 3 | Select delivery method (Standard/Express) | Correct fee and ETA displayed | – |
| 4 | Apply valid discount code | Discount applied and totals updated | – |
| 5 | Choose payment method (COD/Card/Wallet) | Selected payment stored and displayed | – |
| 6 | Place order with stable internet | Order created successfully; confirmation screen shown | Screenshot |
| 7 | Verify order synced across devices | Same order visible in Order History | – |
| 8 | Guest checkout with valid details | Order placed; guest gets email/SMS confirmation | – |
| 9 | Change delivery address during checkout | Totals update correctly with new address | – |
| 10 | Checkout with saved address & card | One-tap checkout works seamlessly | – |

---

## ❌ Invalid Test Cases

| Step | Action | Expected Result | Attachments |
|------|--------|-----------------|-------------|
| 1 | Leave mandatory fields empty (address, phone) | Validation error displayed | – |
| 2 | Enter invalid phone number | Error shown; cannot proceed | – |
| 3 | Apply expired coupon | Coupon rejected with clear message | – |
| 4 | Choose unavailable delivery method (service area not supported) | Blocked with error message | – |
| 5 | Attempt to checkout with empty cart | Checkout blocked; error displayed | – |
| 6 | Simulate payment failure (card declined) | Clear error message; retry option shown | – |
| 7 | Loss of internet mid-checkout | App shows error and retains cart state | – |

---

## ⚠️ Edge / Advanced Test Cases

| Step | Action | Expected Result | Attachments |
|------|--------|-----------------|-------------|
| 1 | Checkout with 50+ items | App remains responsive; totals calculated correctly | – |
| 2 | Rotate device during checkout | Data persists; layout adapts | – |
| 3 | Rapidly tap “Place Order” multiple times | Only one order created (idempotent) | – |
| 4 | Apply multiple coupons (stacking not allowed) | Only valid single coupon applied | – |
| 5 | Switch network (Wi-Fi → Mobile Data) during payment | Payment continues/resumes without duplication | – |
| 6 | Checkout at midnight (edge of date/time) | Correct delivery slots and timestamps recorded | – |
| 7 | Use emojis/special chars in address field | System accepts if valid; rejects harmful input | – |
| 8 | Cancel checkout at last step and retry | Cart preserved; user can restart smoothly | – |

---

## 🔒 Security & Integrity Tests

| Step | Action | Expected Result | Attachments |
|------|--------|-----------------|-------------|
| 1 | Tamper discount code via API interception | Server rejects unauthorized code | – |
| 2 | Manipulate delivery fee client-side | Server authoritative totals override | – |
| 3 | Attempt checkout with expired session token | Prompted to re-login; checkout blocked | – |
| 4 | Check sensitive data (card details) not stored in logs | No PII stored locally | – |

---

## ⚡ Performance & UX Tests

| Step | Action | Expected Result | Attachments |
|------|--------|-----------------|-------------|
| 1 | Checkout flow on low-end Android device | Flow completes within acceptable time | – |
| 2 | Validate screen reader reads checkout fields | VoiceOver/TalkBack announces properly | – |
| 3 | Stress test with 100 concurrent orders from same account | Server processes safely; no duplication | – |
| 4 | Pull-to-refresh on checkout summary | Updates totals and delivery info | – |

---

## 📌 Coverage Achieved

- **Valid Scenarios**: checkout flow with address, delivery, coupon, payment, guest, sync across devices.  
- **Invalid Scenarios**: empty fields, invalid phone, expired coupons, unavailable delivery, failed payment, network loss.  
- **Edge Scenarios**: bulk checkout, orientation change, idempotency, stacked coupons, midnight edge cases, special inputs.  
- **Security**: token/session handling, server-authoritative pricing, safe error handling, no sensitive logs.  
- **Performance & UX**: accessibility, low-end device support, concurrent stress handling, smooth pull-to-refresh.  
