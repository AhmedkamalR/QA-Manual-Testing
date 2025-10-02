# 💻 Website – Payment Test Cases

This document contains detailed **Website test cases** for the **Payment module**.  
Covers Valid, Invalid, Edge, Security, Performance, Accessibility scenarios.

---

## ✅ Valid Test Cases

| Step | Action | Expected Result | Attachments |
|------|--------|-----------------|-------------|
| 1 | Checkout with "Cash on Delivery" | Order confirmed | – |
| 2 | Checkout with valid Visa/MasterCard | Payment succeeds | – |
| 3 | Save card via browser autofill | Autofill works, payment succeeds | – |
| 4 | Use PayPal / 3rd party wallet | Payment succeeds | – |
| 5 | Apply valid coupon | Discount applied | – |
| 6 | Retry payment after timeout | Success; no duplicate | – |
| 7 | Split payment (points + card) | Works correctly | – |
| 8 | Complete 3D Secure page redirect | Success, return to site | – |
| 9 | Cancel at bank page | Order not created | – |
| 10 | Refund processed in order history | Shown correctly | Screenshot |

---

## ❌ Invalid Test Cases

| Step | Action | Expected Result | Attachments |
|------|--------|-----------------|-------------|
| 1 | Invalid card number | Error | – |
| 2 | Expired card date | Declined | – |
| 3 | Wrong CVV | Declined | – |
| 4 | Apply expired promo | Rejected | – |
| 5 | Duplicate tab payment attempt | Blocked | – |
| 6 | Browser refresh mid-payment | Safe recovery | – |
| 7 | Session expired on checkout | Redirect to login | – |
| 8 | Stolen/blocked card | Declined | – |
| 9 | JS disabled during checkout | Payment blocked | – |
| 10 | Unsupported currency | Error displayed | – |

---

## ⚠️ Edge / Advanced Test Cases

| Step | Action | Expected Result | Attachments |
|------|--------|-----------------|-------------|
| 1 | 100+ items checkout | Payment smooth | – |
| 2 | Slow internet checkout | Graceful error | – |
| 3 | Browser back button on payment | Order safe | – |
| 4 | Multiple coupon stack attempt | Validation error | – |
| 5 | OTP received on mobile, entered late | Payment success if valid | – |
| 6 | PayPal redirect abandoned | Order cancelled | – |
| 7 | Browser crash during payment | No duplicate order | – |
| 8 | Large promo discount near 100% | Works correctly | – |
| 9 | Retry with different method | Success | – |
| 10 | Refund after time limit | Blocked | – |

---

## 🔒 Security & Integrity Tests

| Step | Action | Expected Result | Attachments |
|------|--------|-----------------|-------------|
| 1 | Edit payment request in browser DevTools | Rejected | – |
| 2 | Replay form submission | Prevented | – |
| 3 | Session hijacking attempt | Forced logout | – |
| 4 | Check logs for card data | None stored | – |
| 5 | MITM attempt | Data encrypted | – |
| 6 | PCI-DSS audit checks | Compliant | – |

---

## ⚡ Performance & UX Tests

| Step | Action | Expected Result | Attachments |
|------|--------|-----------------|-------------|
| 1 | Payment page loads <3s | Good UX | – |
| 2 | Handle 1000 concurrent users | Stable | – |
| 3 | Browser autofill in forms | Works | – |
| 4 | Refund processing SLA | On-time | – |
| 5 | Accessibility form labels visible | Clear input guidance | – |

---

## ♿ Accessibility Tests

| Step | Action | Expected Result | Attachments |
|------|--------|-----------------|-------------|
| 1 | Screen reader announces fields | Clear | – |
| 2 | Keyboard tab navigation | Possible | – |
| 3 | High contrast theme | Supported | – |
| 4 | Error messages read aloud | Accessible | – |

---

## 📌 Coverage Achieved

- **Valid**: COD, cards, wallets, PayPal, coupons, refunds.  
- **Invalid**: expired cards, wrong CVV, expired promos, disabled JS.  
- **Edge**: concurrency, browser crash, PayPal redirect, back button, slow internet.  
- **Security**: payload tampering, replay attacks, PCI-DSS.  
- **Performance**: SLA, concurrency, browser autofill.  
- **Accessibility**: forms accessible, screen readers.  
