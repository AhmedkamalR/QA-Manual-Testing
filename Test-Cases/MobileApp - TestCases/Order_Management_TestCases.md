# 📱 Mobile App – Order Management Test Cases

This document contains detailed **Mobile App test cases** for the **Order Management module**.  
Covers Valid, Invalid, Edge, Security, and Performance scenarios.

---

## ✅ Valid Test Cases

| Step | Action | Expected Result | Attachments |
|------|--------|-----------------|-------------|
| 1 | Place order from cart with COD payment | Order placed successfully, confirmation screen + order ID shown | Screenshot |
| 2 | Place order with saved address + online payment | Order placed, payment captured, confirmation displayed | – |
| 3 | View "My Orders" screen | Orders listed with status, date, total | Screenshot |
| 4 | Tap order → open details | Order details with items, price, delivery info displayed | – |
| 5 | Track shipment (tap "Track") | Opens tracking screen with real-time status | – |
| 6 | Cancel order before shipping | Order status changes to "Cancelled" and refund initiated if prepaid | – |
| 7 | Request return/refund from order details | Return flow starts, confirmation displayed | – |
| 8 | Reorder previous order | Items re-added to cart successfully | – |

---

## ❌ Invalid Test Cases

| Step | Action | Expected Result | Attachments |
|------|--------|-----------------|-------------|
| 1 | Try to cancel after order is shipped | Cancellation blocked, proper message shown | – |
| 2 | Place order without valid address | Error: "Please add a delivery address" | – |
| 3 | Tap order ID not belonging to logged-in user (via deeplink) | Access denied / error shown | – |
| 4 | Retry payment with expired session | Payment blocked, user asked to retry | – |
| 5 | Submit return request twice for same item | System blocks duplicate return | – |

---

## ⚠️ Edge / Advanced Test Cases

| Step | Action | Expected Result | Attachments |
|------|--------|-----------------|-------------|
| 1 | Place order with 100+ items | Order placed; app handles large payload smoothly | – |
| 2 | Switch network (Wi-Fi → mobile) while placing order | Order processed correctly or retried | – |
| 3 | Refresh "My Orders" rapidly | No duplicate calls or crashes | – |
| 4 | Deep link to order details with expired login | Redirect to login, then show order after auth | – |
| 5 | Return partial items from multi-item order | Only selected items marked for return | – |

---

## 🔒 Security & Integrity Tests

| Step | Action | Expected Result | Attachments |
|------|--------|-----------------|-------------|
| 1 | Manipulate API call to cancel someone else’s order | Server rejects, unauthorized error | – |
| 2 | Modify order total in local storage before placing | Server ignores tampered values | – |
| 3 | Check PII in order logs | No sensitive data stored in crash logs | – |

---

## ⚡ Performance & UX Tests

| Step | Action | Expected Result | Attachments |
|------|--------|-----------------|-------------|
| 1 | Load 50+ orders in "My Orders" screen | Infinite scroll / pagination works smoothly | – |
| 2 | Track shipment with slow API response | App shows loader & retry gracefully | – |
| 3 | Accessibility: Screen reader on order details | Reads order ID, status, total, item names | – |

---

## 📌 Coverage Achieved
- **Valid**: Place, view, track, cancel, return, reorder.  
- **Invalid**: Blocked cancellations, invalid addresses, unauthorized access.  
- **Edge**: Large payloads, partial returns, deep links, network switch.  
- **Security**: No unauthorized access, server authoritative.  
- **Performance/UX**: Pagination, retry, accessibility compliant.  
