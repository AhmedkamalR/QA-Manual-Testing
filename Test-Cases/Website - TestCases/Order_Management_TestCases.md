# 💻 Website – Order Management Test Cases

Comprehensive **Website test coverage** for the **Order Management module**, covering full order lifecycle, user actions, and integrations.

---

## ✅ Valid Test Cases

| Step | Action | Expected Result | Attachments |
|------|--------|-----------------|-------------|
| 1 | Place order via checkout (COD) | Confirmation page + order ID shown | Screenshot |
| 2 | Place order with saved card | Payment processed, order created | – |
| 3 | Place order with wallet + card split payment | Both payment methods recorded | – |
| 4 | Apply coupon and gift card | Totals recalculated correctly | – |
| 5 | Edit address in checkout | Updated address reflected | – |
| 6 | Place order with multiple sellers | Orders split properly | – |
| 7 | Access “My Orders” from profile | All recent orders shown | – |
| 8 | Open order details | Products, totals, shipping data visible | – |
| 9 | Track order via carrier tracking link | Redirects to tracking page | – |
| 10 | Cancel order before dispatch | Status updates, refund processed | – |
| 11 | Download invoice | PDF generated correctly | PDF |
| 12 | Initiate return/exchange request | Request logged & confirmation email sent | – |
| 13 | Submit product review after delivery | Review saved successfully | – |
| 14 | Reorder from order details | Cart populated successfully | – |
| 15 | Check email confirmation for placed order | Email received with order summary | – |
| 16 | Apply multiple discount tiers | Correct stacking logic applied | – |

---

## ❌ Invalid Test Cases

| Step | Action | Expected Result | Attachments |
|------|--------|-----------------|-------------|
| 1 | Place order without accepting terms | Validation blocks submission | – |
| 2 | Try cancel order after shipped | Error “Already shipped” | – |
| 3 | Reorder unavailable product | Product unavailable message | – |
| 4 | Return after return period | Error: “Return window expired” | – |
| 5 | Change order status from browser dev tools | No effect; server validation applies | – |
| 6 | Access other user’s order link | 403 Forbidden | – |
| 7 | Duplicate reorder clicks | One order created only | – |
| 8 | Retry payment after timeout | Prevent duplicate charge | – |

---

## ⚠️ Edge / Advanced Test Cases

| Step | Action | Expected Result | Attachments |
|------|--------|-----------------|-------------|
| 1 | Place bulk order (50+ SKUs) | Checkout handles successfully | – |
| 2 | Mixed items: physical + digital | Both fulfillments handled correctly | – |
| 3 | Apply coupon expired during checkout | Coupon rejected gracefully | – |
| 4 | Open order page on multiple tabs | Syncs latest state | – |
| 5 | Network disconnect during cancel | Retry option displayed | – |
| 6 | Apply refund to wallet and card | Split refunds handled correctly | – |
| 7 | Use browser back after placing order | No duplicate submission | – |
| 8 | Switch user account mid-session | Orders list updates correctly | – |

---

## 🔒 Security Tests

| Step | Action | Expected Result | Attachments |
|------|--------|-----------------|-------------|
| 1 | Inject SQL in order ID param | Request sanitized | – |
| 2 | Modify order total in console | Server rejects invalid payload | – |
| 3 | Access invoice without auth | Redirect to login | – |
| 4 | Verify HTTPS enforced during payment | Secure connection only | – |

---

## ⚡ Performance & UX Tests

| Step | Action | Expected Result | Attachments |
|------|--------|-----------------|-------------|
| 1 | Load order history (200+ orders) | Pagination works smoothly | – |
| 2 | Simulate slow backend response | UI shows loading, no crash | – |
| 3 | Accessibility (Tab + screen reader) | Focus order correct | – |
| 4 | Refresh order list repeatedly | No duplication | – |
| 5 | Track order updates auto-refresh every 10s | Real-time updates visible | – |

---

## 📌 Coverage Achieved
Covers:
- **Order creation, tracking, return, reorder, refund**
- **Edge handling: concurrency, timeouts, expired coupons**
- **Security: URL tampering, session isolation, HTTPS**
- **Performance: pagination, stability under large datasets**
