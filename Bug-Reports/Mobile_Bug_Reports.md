# 📱 Mobile Bug Reports  

This file contains **documented bugs** found during testing the Mobile Applications (Android & iOS).  
Each bug is reported in a **consistent format** for clarity and easy tracking.  

---

## 🐞 Bug #1 – Registration Allows Weak Password  
- **Type:** Frontend / Mobile App (Android & iOS)  
- **Title:** Weak password is accepted during registration.  
- **Steps:**  
  1. Open the app on Android/iOS.  
  2. Navigate to **Registration**.  
  3. Enter a password `"12345"`.  
- **Expected:** App should reject weak password with clear validation message.  
- **Actual:** User account created successfully with weak password.  
- **Attachments:** Screenshot of successful registration.  

---

## 🐞 Bug #2 – Facebook Login Fails on iOS Safari Redirect  
- **Type:** Frontend / iOS App  
- **Title:** FB login redirects to a blank page on iOS Safari.  
- **Steps:**  
  1. Open the app on iOS 17 (real device).  
  2. Tap on **Continue with Facebook**.  
  3. Complete FB login.  
- **Expected:** User should be logged in successfully.  
- **Actual:** Redirects to blank Safari page.  
- **Attachments:** Screen recording of failed FB login.  

---

## 🐞 Bug #3 – Cart Sync Issue Across Devices  
- **Type:** Backend + Mobile App  
- **Title:** Cart not syncing between mobile and web.  
- **Steps:**  
  1. Add products to cart on the mobile app.  
  2. Log in with the same account on web.  
- **Expected:** Cart should sync across devices.  
- **Actual:** Web cart shows empty while mobile cart has products.  
- **Attachments:** Screenshots from both platforms.  

---

## 🐞 Bug #4 – App Crashes on Product Image Zoom (Android)  
- **Type:** Frontend / Android App  
- **Title:** App crashes when zooming product image on Android.  
- **Steps:**  
  1. Open app on Android 14 (Samsung).  
  2. Go to any product detail page.  
  3. Try to zoom product image (pinch gesture).  
- **Expected:** Image should zoom in/out smoothly.  
- **Actual:** App crashes immediately.  
- **Attachments:** Crash log & screen recording.  

---

## 🐞 Bug #5 – Push Notifications Not Received on iOS  
- **Type:** Backend / iOS App  
- **Title:** Push notifications not working on iOS.  
- **Steps:**  
  1. Install the app on iOS 17.  
  2. Enable push notifications in settings.  
  3. Trigger order status update from backend.  
- **Expected:** Push notification should be received.  
- **Actual:** No notification received on iOS device.  
- **Attachments:** Backend logs + iOS screenshots.  

---

## 🐞 Bug #6 – Biometric Login Disabled After Update  
- **Type:** Frontend / Mobile App (Android & iOS)  
- **Title:** FaceID/Fingerprint option disappears after updating the app.  
- **Steps:**  
  1. Enable biometric login in settings.  
  2. Update the app from store.  
  3. Open the app again.  
- **Expected:** Biometric login option should remain available.  
- **Actual:** Option is removed and user forced to re-login manually.  
- **Attachments:** Screen recording showing missing option.  

---

## 🎯 Summary  
- Authentication bugs: **3**  
- Cart/Sync issues: **1**  
- Crashes & Stability: **1**  
- Notifications: **1**  

Total: **6 Mobile bugs documented**  
