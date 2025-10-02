# 🔌 API – Payment Test Cases

This document contains detailed **API test cases** for the **Payment module**.  
Covers Valid, Invalid, Edge, Security, Performance scenarios.

---

## ✅ Valid Test Cases

| Step | Action | Expected Result | Attachments |
|------|--------|-----------------|-------------|
| 1 | POST `/payment` with valid card JSON | 200 OK, payment success | – |
| 2 | Use tokenized saved card | 200 OK | – |
| 3 | Use valid wallet token | Success | – |
| 4 | Apply promo in request body | Discount applied | – |
| 5 | Partial refund API call | Refund processed | – |
| 6 | Full refund API call | Refund completed | – |
| 7 | 3D Secure API flow | Success after OTP | – |
| 8 | Retry payment with new token | Success | – |
| 9 | Query `/payment/status` after success | Status = Paid | – |
| 10 | Cancel API call before capture | Payment voided | – |

---

## ❌ Invalid Test Cases

| Step | Action | Expected Result | Attachments |
|------|--------|-----------------|-------------|
| 1 | Invalid card number in payload | 400 Bad Request | – |
| 2 | Expired card date | 422 Unprocessable | – |
| 3 | Wrong CVV | 402 Declined | – |
| 4 | Insufficient wallet balance | 402 Declined | – |
| 5 | Expired promo code | 400 Invalid Promo | – |
| 6 | Missing mandatory fields | 400 Bad Request | – |
| 7 | Invalid JWT token | 401 Unauthorized | – |
| 8 | Replay old transaction ID | 409 Conflict | – |
| 9 | Duplicate request with same `orderId` | Idempotency enforced | – |
| 10 | Unsupported currency in payload | 422 Unsupported | – |

---

## ⚠️ Edge / Advanced Test Cases

| Step | Action | Expected Result | Attachments |
|------|--------|-----------------|-------------|
| 1 | Payment with max amount limit | Success/fail gracefully | – |
| 2 | Micro transaction (0.01) | Success if allowed | – |
| 3 | Concurrent 50 API calls same order | Only 1 success | – |
| 4 | Switch tokens mid-transaction | New token processed | – |
| 5 | Long payload injection test | Handled safely | – |
| 6 | Invalid charset encoding in request | Error response | – |
| 7 | Network timeout simulation | 504 Gateway Timeout | – |
| 8 | Refund after time expiry | Blocked | – |
| 9 | Multi-currency with FX conversion | Correctly processed | – |
| 10 | Retry after failed OTP | Success with valid OTP | – |

---

## 🔒 Security & Integrity Tests

| Step | Action | Expected Result | Attachments |
|------|--------|-----------------|-------------|
| 1 | Modify request amount | Rejected | – |
| 2 | Replay attack with same payload | Blocked | – |
| 3 | SQL injection in JSON field | Rejected | – |
| 4 | XSS injection in "cardholderName" | Sanitized | – |
| 5 | Invalid JWT signature | 401 Unauthorized | – |
| 6 | TLS downgrade attack | Connection refused | – |
| 7 | PCI-DSS compliance check | No sensitive storage | – |

---

## ⚡ Performance & Load Tests

| Step | Action | Expected Result | Attachments |
|------|--------|-----------------|-------------|
| 1 | 1000 payment requests/min | API stable | – |
| 2 | Latency under load test | <500ms avg | – |
| 3 | Refund SLA test | Completed on time | – |
| 4 | Idempotency check under load | Only 1 order created | – |
| 5 | Circuit breaker retry | Works correctly | – |

---

## 📌 Coverage Achieved

- **Valid**: cards, wallets, promos, refunds, OTP, cancel flows.  
- **Invalid**: wrong cards, expired, insufficient balance, missing fields, invalid tokens.  
- **Edge**: high/low amounts, concurrency, encoding issues, timeouts, FX conversions.  
- **Security**: replay, tampering, SQLi/XSS injection, JWT validation.  
- **Performance**: load handling, latency, idempotency, SLA.  
