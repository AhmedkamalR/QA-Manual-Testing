# 🛒 Checkout – Test Scenarios

This document outlines **comprehensive test scenarios** for the **Checkout module** across API, Website, and Mobile App.  
It aims to ensure **end-to-end coverage** before writing detailed test cases.

---

## 1. API Scenarios

### ✅ Valid Scenarios
- Create order with valid cart and user.
- Create guest order with valid cart.
- Apply valid coupon/promo code.
- Apply gift card or wallet balance.
- Select valid shipping method (Standard, Express, Pickup).
- Provide valid billing and shipping address.
- Calculate taxes correctly (domestic vs international).
- Confirm order with successful payment gateway callback.
- Fetch order summary before confirmation.
- Ensure idempotency on retry (no duplicate orders).

### ❌ Invalid Scenarios
- Create order with empty cart.
- Apply invalid/expired coupon.
- Apply coupon not applicable to items in cart.
- Provide invalid/missing address fields.
- Select unsupported shipping method.
- Attempt checkout with blocked region/country.
- Payment declined by gateway (invalid card, insufficient funds).
- Payment API timeout or failed callback.
- Create order with invalid JSON payload.
- Retry without idempotency key causing duplicate orders.

### ⚠️ Edge Scenarios
- Simultaneous orders for last item (inventory race condition).
- Order with mixed items (in-stock + out-of-stock).
- Order with zero total (100% discount or free product).
- Order with large quantity (stress inventory check).
- High-value order requiring fraud check.
- Coupon + gift card + wallet combined in one order.
- Partial shipment API response (multi-warehouse).
- Payment gateway returns delayed success after timeout.
- Large payload (100+ items in single order).
- Localization issues (address validation per country).

---

## 2. Website Scenarios

### ✅ Valid Scenarios
- Logged-in user checkout with saved address/payment.
- Guest checkout with new address/payment.
- Add/change shipping address during checkout.
- Add/change billing address during checkout.
- Apply valid coupon and see discount applied.
- Select different shipping methods and verify totals.
- Review order summary (items, totals, tax, shipping, discount).
- Place order successfully and see confirmation page.
- Receive order confirmation email.
- Order appears in “My Orders” with correct details.

### ❌ Invalid Scenarios
- Checkout with empty cart.
- Enter invalid coupon code.
- Enter expired coupon code.
- Use coupon below minimum spend requirement.
- Enter incomplete or invalid address fields.
- Attempt checkout with item that went out-of-stock.
- Incorrect totals displayed after applying multiple discounts.
- Double-click on “Place Order” creates duplicate.
- Session expires mid-checkout → redirect to login.
- Unauthorized user tries to access another user’s order summary.

### ⚠️ Edge Scenarios
- Very long address fields (500+ characters).
- Special characters/emoji in address or name.
- Apply multiple promotions stacking incorrectly.
- Checkout in multiple currencies.
- High-value order (e.g., 1M).
- Item added during checkout (cart updated mid-flow).
- Coupon stack limit exceeded (e.g., more than 3 applied).
- Slow network causing delayed order confirmation.
- Accessibility: keyboard-only navigation through checkout.
- Screen reader reads totals, discounts, and messages correctly.

---

## 3. Mobile App Scenarios

### ✅ Valid Scenarios
- Logged-in checkout using saved payment method.
- Guest checkout via mobile app.
- Use Apple Pay / Google Pay.
- Add/change address during checkout.
- Apply valid coupon in-app.
- Resume checkout after app minimized/reopened.
- Receive push notification after successful order.
- Offline cart syncs when online and allows checkout.
- Order confirmation screen matches order details.
- Order history updated after checkout.

### ❌ Invalid Scenarios
- Checkout without login when required.
- Apply invalid/expired coupon.
- Payment SDK failure (invalid card, canceled).
- Network drops during payment process.
- Wishlist item moved to checkout but goes out-of-stock.
- Force-close app during checkout (resume flow broken).
- Unauthorized checkout attempt with tampered payload.
- Payment gateway error not handled gracefully.

### ⚠️ Edge Scenarios
- Checkout flow interrupted by phone call/notification.
- Very slow network → retry payment option.
- App crash recovery during checkout.
- Large cart (50+ items).
- Payment in multiple currencies.
- App deep link to expired checkout session.
- Switching language (EN ↔ AR) mid-checkout.
- Accessibility: voice-over reads checkout fields.
- Fingerprint/FaceID authentication before payment.
- Push notification deep link to confirmation screen.

---

## ✅ Key Values / Keywords
- **Entities:** Cart, Order, Address, Payment, Shipping, Coupon, Gift Card, Wallet.  
- **Parameters:** cart_id, user_id, address_id, coupon_code, payment_token, shipping_method.  
- **States:** In-Stock, Out-of-Stock, Pending Payment, Paid, Cancelled, Refunded.  
- **Edge:** High-value order, Multi-currency, Large cart, Stacked promotions, Inventory race condition.  

---
