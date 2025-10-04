# 📱 Mobile App – Order Management Test Cases

This document contains **comprehensive Mobile App test cases** for the **Order Management module**.  
Includes Valid, Invalid, Edge, Security, Performance, and UX scenarios.  

---

## ✅ Valid Test Cases

| Step | Action | Expected Result | Attachments |
|------|--------|-----------------|-------------|
| 1 | Place order with Cash on Delivery | Order confirmed, order ID shown | – |
| 2 | Place order with credit card (online payment) | Payment success, order confirmation displayed | Screenshot |
| 3 | Apply discount coupon during order | Discount reflected, total recalculated | – |
| 4 | Use different delivery addresses for multiple orders | Correct address applied to each | – |
| 5 | Place order with saved address | Address auto-filled correctly | – |
| 6 | Place order with multiple items and different sellers | System splits into sub-orders | – |
| 7 | View order list in “My Orders” | Orders sorted by date/status | – |
| 8 | Tap an order → open order details | Items, totals, payment info shown | – |
| 9 | Track shipment | Opens tracking page, live status visible | – |
| 10 | Cancel unshipped order | Order status updates to “Cancelled” | – |
| 11 | Request return within allowed window | Return initiated, message displayed | – |
| 12 | Submit review for delivered order | Review saved and shown in product page | – |
| 13 | Reorder completed order | Items added to cart with correct quantities | – |
| 14 | Download invoice | PDF opens/downloads successfully | PDF |
| 15 | Check push notification for order status updates | Notifications appear with correct content | Screenshot |
| 16 | Reopen app after placing order | Order persists in history (synced) | – |
| 17 | Check estimated delivery date on details page | ETA displayed correctly | – |
| 18 | Change delivery address before shipping | Address updated successfully | – |

---

## ❌ Invalid Test Cases

| Step | Action | Expected Result | Attachments |
|------|--------|-----------------|-------------|
| 1 | Place order without selecting payment method | Error shown: “Select payment method” | – |
| 2 | Try to cancel order after shipped | Error message: “Cannot cancel shipped order” | – |
| 3 | Attempt reorder for deleted product | Error: “Product unavailable” | – |
| 4 | Return request after return window expired | Validation prevents submission | – |
| 5 | Tap order ID not belonging to user (via deeplink) | Unauthorized error | – |
| 6 | Modify order address after dispatch | Action blocked, message displayed | – |
| 7 | Submit review for cancelled order | Action not allowed | – |
| 8 | Try to reorder with insufficient wallet balance | Payment failure message displayed | – |
| 9 | Network lost during order confirmation | Safe retry or message shown | – |

---

## ⚠️ Edge / Advanced Test Cases

| Step | Action | Expected Result | Attachments |
|------|--------|-----------------|-------------|
| 1 | Place order with 100+ SKUs | Order handled smoothly without crash | – |
| 2 | Order with one digital and one physical item | Correct flow for mixed fulfillment | – |
| 3 | Edit address while placing order | Updates reflected immediately | – |
| 4 | Rapidly tap “Place Order” button | Debounce prevents duplicate orders | – |
| 5 | Order item with limited-time promo | Price locked at checkout | – |
| 6 | Switch network during confirmation | Retry resumes properly | – |
| 7 | Offline cache sync: place offline order → reconnect | Order synced successfully | – |
| 8 | Return part of multi-item order | Only selected items returned | – |
| 9 | Refund initiated to wallet | Refund reflected correctly | – |
| 10 | Retry payment after failed attempt | Retry successful | – |
| 11 | Device rotation during tracking | UI maintains order context | – |
| 12 | Receive multiple status push updates in sequence | All updates appear in correct order | – |
| 13 | Combine return + exchange in one request (if allowed) | Both flows handled properly | – |

---

## 🔒 Security & Integrity Tests

| Step | Action | Expected Result | Attachments |
|------|--------|-----------------|-------------|
| 1 | Manipulate API call to cancel another user’s order | Server rejects unauthorized access | – |
| 2 | Edit local DB to mark order as “Delivered” | Server sync restores real status | – |
| 3 | Replay payment confirmation | System prevents duplicate payment | – |
| 4 | Inspect logs for card info | No sensitive data stored | – |

---

## ⚡ Performance & UX Tests

| Step | Action | Expected Result | Attachments |
|------|--------|-----------------|-------------|
| 1 | Load 100 orders on low-end device | Smooth scrolling | – |
| 2 | Track shipment on poor connection | Graceful loading & retry option | – |
| 3 | VoiceOver/TalkBack reads order details | Accessible labels & reading order | – |
| 4 | Pull-to-refresh “My Orders” | Data refreshes without duplication | – |
| 5 | Reorder 10+ previous orders in quick sequence | No duplication or crashes | – |

---

## 📌 Coverage Achieved
Covers:
- **Order placement (COD, online, split orders, promos)**  
- **Viewing, tracking, cancelling, returning, reviewing, reordering**  
- **Security: prevention of tampering, unauthorized access**  
- **Performance & UX: pagination, retry, accessibility, notifications**
