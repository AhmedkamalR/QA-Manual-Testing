# 🚨 Critical Bug Reports  

This file contains **critical/high severity bugs** that directly impact core business functions, user data, or application stability.  

---

## 🐞 Bug #1 – Payment Gateway Not Processing Orders  
- **Type:** Backend + Web/Mobile  
- **Title:** Payment requests fail on all platforms.  
- **Steps:**  
  1. Add item to cart.  
  2. Proceed to payment.  
  3. Enter valid credit card.  
- **Expected:** Payment should process successfully.  
- **Actual:** Error message: "Unable to process payment".  
- **Attachments:** API logs + screenshot.  

---

## 🐞 Bug #2 – App Crash on Launch (iOS 17)  
- **Type:** Frontend / iOS App  
- **Title:** App closes immediately after opening.  
- **Steps:**  
  1. Install app on iOS 17 device.  
  2. Tap to open.  
- **Expected:** App should launch normally.  
- **Actual:** App crashes instantly.  
- **Attachments:** Crash log + video.  

---

## 🐞 Bug #3 – User Data Leak via API (Security Issue)  
- **Type:** Backend  
- **Title:** Unauthorized API endpoint exposing user data.  
- **Steps:**  
  1. Call API `/user/details` without authentication.  
- **Expected:** Endpoint should reject unauthorized access.  
- **Actual:** Returns full user data (name, email, address).  
- **Attachments:** API response dump.  

---

## 🐞 Bug #4 – Orders Not Syncing Between Mobile & Web  
- **Type:** Backend + Integration  
- **Title:** Orders placed on mobile not visible on web.  
- **Steps:**  
  1. Place order using mobile app.  
  2. Log into same account on web.  
- **Expected:** Order should be visible on both.  
- **Actual:** Web order history empty.  
- **Attachments:** Screenshots from both platforms.  

---

## 🐞 Bug #5 – Admin Cannot Access Dashboard  
- **Type:** Backend + Web  
- **Title:** Admin login blocked due to authentication loop.  
- **Steps:**  
  1. Go to Admin panel.  
  2. Enter valid credentials.  
- **Expected:** Admin should access dashboard.  
- **Actual:** Login page reloads in infinite loop.  
- **Attachments:** Screen recording.  

---

## 🎯 Summary  
- Payment failures: **1**  
- App stability: **1**  
- Security risks: **1**  
- Order sync issues: **1**  
- Admin access issues: **1**  

Total: **5 Critical bugs documented**  
