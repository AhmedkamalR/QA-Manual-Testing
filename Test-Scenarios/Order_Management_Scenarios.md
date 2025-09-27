# 📦 Order Management – Test Scenarios

This document outlines **comprehensive test scenarios** for the **Order Management module** across API, Website, and Mobile App.  
It covers valid, invalid, edge, and security scenarios ensuring end-to-end coverage.

---

## 1. API Scenarios

### ✅ Valid Scenarios
- Create order with valid cart + user ID.
- Place order with all mandatory fields (shipping, billing, payment).
- Place order with guest checkout.
- Place order with saved address.
- Order creation with valid coupon/discount.
- Order creation with multiple products and quantities.
- Update order status: Placed → Processing → Shipped → Delivered.
- Cancel order before shipment.
- Cancel order partially (if multiple items).
- Return order request for eligible product.
- Refund API triggered for returned product.
- Get order details by order ID.
- List all orders by customer ID.
- Admin updates order status via API.
- Track order status via API.
- Resend order confirmation email trigger.
- Split shipment order (if products from multiple warehouses).

### ❌ Invalid Scenarios
- Place order with empty cart.
- Place order with invalid/missing user ID.
- Order creation with invalid product ID.
- Order creation with product out of stock.
- Order creation with invalid shipping address.
- Apply expired or invalid coupon.
- Apply coupon not applicable for products.
- Place order with invalid payment reference.
- Update order with invalid status transition (e.g., Delivered → Placed).
- Cancel already delivered order.
- Return request beyond return period.
- Refund request for non-refundable item.
- Duplicate API call without idempotency → duplicate order created.
- Fetch order with invalid order ID.
- Access order with unauthorized user token.

### ⚠️ Edge Scenarios
- Large order with 100+ items.
- Order with mixed stock availability (some available, some not).
- Order placed at midnight (date boundary).
- Order with different currencies.
- Partial shipment split across multiple warehouses.
- Network timeout during order creation.
- Payment success but order API fails (reconciliation needed).
- Order created then immediately cancelled (rapid transition).
- High load: 1000+ orders created concurrently.
- Order ID collision (very rare but possible under stress).
- Multi-device login → one user places/cancels order while another updates profile.

---

## 2. Website Scenarios

### ✅ Valid Scenarios
- Place order with single product.
- Place order with multiple products.
- Place order with saved address.
- Place order with new address.
- Place order with different shipping + billing addresses.
- Apply coupon and see discount reflected.
- Apply gift card/wallet balance in checkout.
- See order confirmation page after successful order.
- Receive order confirmation email/SMS.
- Track order status from “My Orders”.
- Cancel order before it is shipped.
- Initiate return from order details page.
- View updated status in order history.
- Reorder past order from history.
- Download invoice PDF.

### ❌ Invalid Scenarios
- Checkout with empty cart.
- Checkout without selecting address.
- Checkout without selecting payment method.
- Apply invalid/expired coupon code.
- Try to reorder unavailable product.
- Try to cancel delivered order.
- Try to return ineligible product.
- Session timeout during order placement.
- Refresh page during final confirmation.
- Multiple clicks on “Place Order” → only one order should be created.
- Cross-user access: trying to see another user’s order.
- Payment failed but order still attempted.

### ⚠️ Edge Scenarios
- Place order with very high cart total.
- Place order at same time from two browser tabs.
- Place order during site maintenance.
- Cancel order seconds before shipment status updates.
- Split shipment → multiple tracking numbers.
- Order with free product (0 value).
- Apply coupon + gift card + wallet together.
- Accessibility: Order details screen readable by screen reader.
- Large order history → pagination works.

---

## 3. Mobile App Scenarios

### ✅ Valid Scenarios
- Place order with valid cart.
- Place order using saved address.
- Place order with biometric payment confirmation.
- Place order via Apple Pay/Google Pay.
- Place order with COD option.
- Track order status from mobile app.
- Cancel order before shipment.
- Initiate return from mobile app.
- Push notification on status updates.
- View invoice inside app.

### ❌ Invalid Scenarios
- Invalid cart (empty).
- Place order with no internet connection.
- App crash recovery after order placed.
- Duplicate tap on “Place Order” button.
- Cancel non-cancellable order.
- Unauthorized user accessing order.
- Return after expiry period.
- Payment SDK failed but order attempted.

### ⚠️ Edge Scenarios
- App force-closed during checkout → order integrity check.
- Place order in poor network (2G).
- Multi-language switch during checkout.
- Order with multiple currencies.
- Large quantity order from app.
- Order created while app in background.
- Order notifications received while app closed.
- Stress test: 100 orders placed in 1 min via mobile.

---

## ✅ Key Values / Keywords
- **Entities:** Cart, Order, Product, User, Address, Coupon, Shipment, Return, Refund.  
- **Parameters:** order_id, user_id, product_id, address_id, coupon_code, payment_id, status.  
- **States:** Placed, Processing, Shipped, Delivered, Cancelled, Returned, Refunded.  
- **Edge:** Large order, Multi-currency, Split shipment, Timeout, Duplicate clicks, High load.  

---
