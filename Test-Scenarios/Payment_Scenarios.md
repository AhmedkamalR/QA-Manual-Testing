# 💳 Payment – Test Scenarios

This document outlines **comprehensive test scenarios** for the **Payment module** across API, Website, and Mobile App.  
It ensures **functional, negative, edge, and security coverage** before writing detailed test cases.

---

## 1. API Scenarios

### ✅ Valid Scenarios
- Initiate payment with valid order and payment token.
- Payment success via credit/debit card.
- Payment success via digital wallet (Apple Pay, Google Pay).
- Payment success via PayPal or 3rd-party gateway.
- Payment with saved card (tokenized).
- Payment with COD (Cash on Delivery) option.
- Partial payment with gift card + card.
- Retry payment after previous failure with new token.
- Refund API for full amount.
- Refund API for partial amount.
- Capture API for pre-authorized payments.
- Verify callback/notification from payment gateway.

### ❌ Invalid Scenarios
- Initiate payment with missing/invalid order ID.
- Payment with expired card.
- Payment with invalid card number (Luhn check fail).
- Payment with incorrect CVV.
- Payment with expired token/session.
- Payment with insufficient funds.
- Payment with blocked card / blacklisted BIN.
- Invalid currency not supported.
- Payment attempt for cancelled order.
- Duplicate payment request for same order without idempotency.
- Refund for non-existent transaction.
- Refund exceeding original transaction amount.
- Tampered callback signature (invalid).

### ⚠️ Edge Scenarios
- Very high-value transaction (fraud/risk rules).
- Payment gateway timeout → delayed success callback.
- User cancels transaction mid-flow.
- Concurrent payments for same order (race condition).
- Multi-currency conversion during payment.
- Payment with rounding differences (e.g., 2 decimals vs 3 decimals).
- Handling of 3D Secure (OTP/biometric step).
- Payment reversal (chargeback).
- Payment attempted after session expiry.
- Stress test: 1000+ payment requests per minute.

---

## 2. Website Scenarios

### ✅ Valid Scenarios
- Proceed to payment with valid cart.
- Pay with credit/debit card successfully.
- Pay with saved card details.
- Pay with COD option.
- Apply gift card/wallet balance during payment.
- Pay with valid coupon reducing total.
- Redirect to gateway page and return to success page.
- Payment confirmation email received.
- Payment status shown in Order History as “Paid”.
- Retry option available after failed payment.

### ❌ Invalid Scenarios
- Enter invalid card number.
- Enter expired card.
- Enter invalid CVV.
- Enter cardholder name with invalid characters.
- Use unsupported card type.
- Attempt payment with empty fields.
- Cancel payment at gateway and return to site.
- Payment fails due to insufficient funds.
- Duplicate click on “Pay Now” creates duplicate attempt.
- Refresh browser on payment screen.
- Close browser tab mid-payment.
- Checkout blocked when payment gateway unreachable.

### ⚠️ Edge Scenarios
- Very slow gateway response (spinner shown correctly).
- Payment confirmation delayed but user sees pending status.
- User pays in currency different from account default.
- Switching tabs during 3D Secure OTP entry.
- Browser autofill inserts invalid card details.
- Accessibility: screen reader reads card form properly.
- Payment with discount = zero total (no payment required).
- Order with split payment (wallet + card).
- Simultaneous coupon + gift card + card combination.
- Load testing with 100 concurrent checkout users.

---

## 3. Mobile App Scenarios

### ✅ Valid Scenarios
- Pay with card via in-app form.
- Pay with saved card (tokenized).
- Pay using Apple Pay / Google Pay.
- Use biometric authentication (FaceID, Fingerprint).
- Apply gift card/wallet + card in mobile checkout.
- Successful redirect to in-app browser for 3DS step.
- Resume payment flow after app minimized.
- Push notification after payment success.
- Payment status updated in order history.

### ❌ Invalid Scenarios
- Invalid card entry on mobile keypad.
- Network drop during payment process.
- Cancel during Apple Pay / Google Pay flow.
- Payment SDK crash handled gracefully.
- Retry payment with wrong OTP for 3DS.
- Attempt payment after order already paid.
- Double tap “Pay” button → only one charge applied.
- Tampered payment deep link from notification.

### ⚠️ Edge Scenarios
- App force-closed mid-payment → resume safe state.
- Poor network during gateway redirect.
- Switching device language during payment.
- Very large cart amount triggering fraud check.
- Split payments across multiple methods.
- App offline → payment initiation blocked with proper error.
- Long session idle on payment page (timeout).
- Stress test: rapid add/remove cards before pay.

---

## ✅ Key Values / Keywords
- **Entities:** Order, Payment, Card, Wallet, Gift Card, Coupon, Gateway, Refund, Chargeback.  
- **Parameters:** order_id, payment_token, card_number, cvv, expiry_date, currency, amount.  
- **States:** Pending, Paid, Failed, Refunded, Chargeback, Cancelled.  
- **Edge:** High-value transaction, Multi-currency, Gateway timeout, 3DS, Duplicate request, Stress load.  

---
