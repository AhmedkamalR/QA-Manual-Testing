# 🔔 Notifications – Test Scenarios

This document outlines **comprehensive test scenarios** for the **Notifications module** across API, Website, and Mobile App.  
It ensures coverage of valid, invalid, and edge cases for push notifications, in-app messages, SMS, and emails.

---

## 1. API Scenarios

### ✅ Valid Scenarios
- Send push notification to valid user ID/device token.
- Send email notification with valid template ID.
- Send SMS notification with valid phone number.
- Retrieve all notifications for a user.
- Mark notification as read/unread.
- Delete notification from user’s list.
- Support multiple notification channels (Push, Email, SMS).
- Scheduled notification delivered at correct time.
- Notification priority respected (High vs Normal).
- Batch notification sent to multiple users.
- Multilingual notification (EN/AR).
- Notification linked to order status change (e.g., Shipped).
- Retrieve notification history with pagination.
- Retry mechanism on failed delivery.

### ❌ Invalid Scenarios
- Invalid/missing user ID in request.
- Invalid or expired device token.
- Invalid phone number format for SMS.
- Invalid email format.
- Notification template ID not found.
- Exceeding SMS/email sending limit.
- Unauthorized API request (missing/invalid token).
- Sending notification to deleted user account.
- Notification sent with empty body/title.
- Sending to inactive/blocked user.
- Wrong channel parameter (e.g., “fax”).

### ⚠️ Edge Scenarios
- Bulk sending to 10,000+ users simultaneously.
- Notification size exceeds character limit (e.g., SMS > 160).
- Notification with emojis/special characters.
- Multilingual mix (English + Arabic in one message).
- Same notification sent multiple times (deduplication).
- Notification delivery during downtime → queued & retried.
- User opts out of notifications → should not receive.
- Expired scheduled notification (should not send).
- Very high frequency notifications (spam handling).
- Cross-channel sync: read on mobile → marked read on web.

---

## 2. Website Scenarios

### ✅ Valid Scenarios
- Show in-app notification bell with unread count.
- Click notification → navigate to correct page.
- Mark all notifications as read.
- Delete single notification.
- Pagination/scroll for older notifications.
- Real-time notification appears without refresh (WebSocket).
- Email notification received for order confirmation.
- Email includes correct subject, body, and branding.
- Verify unsubscribe link works in email.
- SMS received for delivery update.
- Notifications sync between web & mobile.

### ❌ Invalid Scenarios
- Access notification page without login.
- Broken/missing notification icon.
- Email template missing variables → shows placeholders.
- Notification link broken (404 page).
- SMS not delivered due to carrier issue.
- Duplicate notifications for same event.
- Notification counter not updated after reading.
- HTML tags not escaped in notification body (XSS risk).
- Sending notifications after user disabled them.

### ⚠️ Edge Scenarios
- 100+ notifications in list → scroll/pagination tested.
- Very long notification title breaks UI alignment.
- Multi-language (switch EN/AR → text updates correctly).
- Email received in spam folder (deliverability).
- Expired promo notification still visible.
- Notification arrives when user logged out → visible after login.
- Multiple simultaneous order updates → notifications grouped.
- Accessibility: screen readers announce notifications properly.

---

## 3. Mobile App Scenarios

### ✅ Valid Scenarios
- Receive push notification while app is in foreground.
- Receive push notification while app is in background.
- Notification click opens correct app screen.
- In-app notification center shows list.
- Mark as read/unread in app.
- Delete notification from list.
- Sync notifications with web.
- Push notification includes deep link.
- Receive SMS/email for order updates.
- Push notification badge count updates correctly.
- Offline mode → pending notifications sync after reconnect.
- Silent push received and processed in background.

### ❌ Invalid Scenarios
- Push notification not delivered due to invalid device token.
- App uninstalled → push not delivered.
- Notification click opens wrong screen.
- Notification with missing body.
- Duplicate push received.
- SMS/email not matching language preference.
- Push blocked by user OS permissions.
- User logged out → still receiving notifications.

### ⚠️ Edge Scenarios
- 100+ notifications in app list.
- Push notification with large image/attachment.
- Rich push (image, buttons, deep links) supported.
- App force-closed when notification received.
- App offline during push → delivered after reconnect.
- Push sent during OS-level Do Not Disturb (handled gracefully).
- User receives notification in multiple devices (multi-login).
- Push notification with special characters/emoji.
- Notification arrives during app update/install.

---

## ✅ Key Values / Keywords
- **Channels:** Push, Email, SMS, In-App.  
- **Entities:** User, Notification, Template, Token, Device.  
- **Parameters:** user_id, device_token, notification_id, template_id, channel.  
- **States:** Read, Unread, Delivered, Failed, Queued, Scheduled, Opted-out.  
- **Edge:** Bulk delivery, Multi-device sync, Large message, Network failure, Expired schedule.  

---
