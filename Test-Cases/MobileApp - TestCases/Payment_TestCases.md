# 📱 Mobile App – Payment Test Cases

This document contains detailed **Mobile App test cases** for the **Payment module**.  
Covers Valid, Invalid, Edge, Security, Performance, Accessibility scenarios.

---

## ✅ Valid Test Cases

| Step | Action | Expected Result | Attachments |
|------|--------|-----------------|-------------|
| 1 | Select "Cash on Delivery" and confirm order | Order placed without online payment | – |
| 2 | Pay with valid Visa/MasterCard | Payment succeeds, order confirmed | – |
| 3 | Save card → checkout again | Card visible in saved list, payment successful | – |
| 4 | Use valid mobile wallet (Apple Pay/Google Pay) | Payment processed, order confirmed | – |
| 5 | Apply promo code that reduces total to 0 | Order confirmed without payment | – |
| 6 | Retry payment after gateway timeout | Second attempt succeeds; no duplicate | – |
| 7 | Use loyalty points + card split payment | Correct calculation and success | – |
| 8 | Complete 3D Secure (OTP) verification | OTP accepted, payment confirmed | – |
| 9 | Cancel transaction on bank page → return | Order not created, safe redirection | – |
| 10 | Refund request from order history | Refund processed and visible | Screenshot |

---

## ❌ Invalid Test Cases

| Step | Action | Expected Result | Attachments |
|------|--------|-----------------|-------------|
| 1 | Enter invalid card number | Error "Invalid card" displayed | – |
| 2 | Enter expired card | Transaction rejected | – |
| 3 | Enter incorrect CVV | Declined with error | – |
| 4 | Wallet balance insufficient | Error displayed | – |
| 5 | Apply expired coupon | Coupon rejected | – |
| 6 | Disconnect internet mid-payment | Error displayed, no order | – |
| 7 | Force quit app during payment | Payment aborted | – |
| 8 | Use blocked/stolen card | Declined | – |
| 9 | Duplicate click on "Pay" | Only one transaction processed | – |
| 10 | Unsupported currency selection | Payment blocked | – |

---

## ⚠️ Edge / Advanced Test Cases

| Step | Action | Expected Result | Attachments |
|------|--------|-----------------|-------------|
| 1 | Very high transaction amount | Processed or rejected gracefully | – |
| 2 | Very small amount | Accepted if allowed | – |
| 3 | Split payment across multiple cards | Totals applied correctly | – |
| 4 | Switch from Wi-Fi → 4G mid-payment | Resume or fail gracefully | – |
| 5 | Rapid double-tap pay button | Only one transaction created | – |
| 6 | OTP delay (resend OTP) | Payment succeeds with valid OTP | – |
| 7 | Cardholder name with emojis/special chars | Error if invalid | – |
| 8 | Gateway maintenance | User notified | – |
| 9 | Retry payment with new method | Order confirmed | – |
| 10 | Refund after expiry | Refund blocked with error | – |

---

## 🔒 Security & Integrity Tests

| Step | Action | Expected Result | Attachments |
|------|--------|-----------------|-------------|
| 1 | Tamper payment payload | Server rejects | – |
| 2 | Replay old payment request | Blocked | – |
| 3 | Use expired session token | Forced login | – |
| 4 | Inspect crash logs | No card data stored | – |
| 5 | MITM attack attempt | Data encrypted TLS | – |
| 6 | Multiple stolen cards attempt | Flagged, blocked | – |

---

## ⚡ Performance & UX Tests

| Step | Action | Expected Result | Attachments |
|------|--------|-----------------|-------------|
| 1 | Gateway load <3 sec | Smooth UX | – |
| 2 | Retry failed transaction | Works | – |
| 3 | Test low-end Android device | App responsive | – |
| 4 | 100 concurrent payments | No degradation | – |
| 5 | Refund time SLA | Within limit | – |

---

## ♿ Accessibility Tests

| Step | Action | Expected Result | Attachments |
|------|--------|-----------------|-------------|
| 1 | Screen reader on card form | Reads fields | – |
| 2 | High contrast mode | UI usable | – |
| 3 | Keyboard navigation | Works | – |
| 4 | Error message read aloud | Compliant | – |

---

## 📌 Coverage Achieved

- **Valid**: COD, card, wallet, split payments, refunds, OTP.  
- **Invalid**: wrong card, expired, CVV, insufficient funds, expired coupons.  
- **Edge**: high/low amounts, concurrency, OTP delay, network switch, maintenance.  
- **Security**: payload tampering, replay, encryption, fraud detection.  
- **Performance**: SLA checks, concurrency, responsiveness.  
- **Accessibility**: screen readers, contrast, keyboard navigation.  
