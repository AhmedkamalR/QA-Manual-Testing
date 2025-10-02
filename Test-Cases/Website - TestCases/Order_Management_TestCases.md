# 💻 Website – Order Management Test Cases

This document contains detailed **Website test cases** for the **Order Management module**.  
Covers Valid, Invalid, Edge, Security, and Performance scenarios.

---

## ✅ Valid Test Cases

| Step | Action | Expected Result | Attachments |
|------|--------|-----------------|-------------|
| 1 | Place order via checkout with saved card | Order confirmed, order ID shown | Screenshot |
| 2 | Place order with guest checkout (if supported) | Order placed, guest confirmation email sent | – |
| 3 | View order history in profile | Orders listed with correct status and totals | – |
| 4 | Download invoice PDF | Invoice generated correctly | PDF |
| 5 | Cancel order before shipment | Status updates to "Cancelled", refund processed | – |
| 6 | Initiate return from order details | Return request submitted successfully | – |
| 7 | Apply gift card during reorder | Gift card balance applied correctly | – |

---

## ❌ Invalid Test Cases

| Step | Action | Expected Result | Attachments |
|------|--------|-----------------|-------------|
| 1 | Cancel after dispatch | Error message: "Cannot cancel after dispatch" | – |
| 2 | Reorder item no longer in catalog | Error: "Product unavailable" | – |
| 3 | Access other user’s order by changing URL ID | Unauthorized error | – |
| 4 | Place order without terms & conditions checkbox (if required) | Validation blocks | – |
| 5 | Try to return item after return window expired | Blocked with message | – |

---

## ⚠️ Edge / Advanced Test Cases

| Step | Action | Expected Result | Attachments |
|------|--------|-----------------|-------------|
| 1 | Place order with mixed shipping methods | Correctly split shipments shown | – |
| 2 | Reorder multiple orders rapidly | Cart merges correctly without duplicates | – |
| 3 | Open same order in 2 browser tabs, cancel in one | Other tab shows updated status after refresh | – |
| 4 | Apply multiple vouchers at checkout | Only valid stacking allowed | – |

---

## 🔒 Security & Integrity Tests

| Step | Action | Expected Result | Attachments |
|------|--------|-----------------|-------------|
| 1 | Modify order amount in dev tools | Server rejects manipulation | – |
| 2 | Access API call of another user’s order | Unauthorized error | – |
| 3 | Check caching in browser history (invoice page) | Sensitive data not cached | – |

---

## ⚡ Performance & UX Tests

| Step | Action | Expected Result | Attachments |
|------|--------|-----------------|-------------|
| 1 | Load 100+ orders in order history | Pagination/infinite scroll works | – |
| 2 | Cancel order with poor internet | Retry/loader shown, no duplicate cancellation | – |
| 3 | Accessibility: Tab + screen reader navigation | Proper focus order and labels | – |

---

## 📌 Coverage Achieved
- **Valid**: Checkout, guest orders, invoice, reorder, returns.  
- **Invalid**: Expired returns, unauthorized access, unavailable products.  
- **Edge**: Multi-shipment, duplicate reorders, parallel actions.  
- **Security**: Unauthorized blocked, sensitive data protected.  
- **Performance/UX**: Pagination, accessibility, retry on poor network.  
