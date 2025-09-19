# Mobile App - Login Feature Test Cases

This document contains **comprehensive test cases** for the Mobile App Login functionality, covering valid, invalid, and edge scenarios.

---

## ✅ Valid Test Cases

| Step | Action | Expected Result | Attachments |
|------|--------|----------------|-------------|
| 1 | Open the app, navigate to Login screen | Login form with Email/Username & Password is displayed | Screenshot_AppLoginPage.png |
| 2 | Enter valid email & password, tap Login | User is redirected to Home/Dashboard | Screenshot_AppLoginSuccess.png |
| 3 | Enter valid credentials and enable "Remember Me" | User remains logged in after app restart | Screenshot_AppRememberMe.png |
| 4 | Tap "Forgot Password" → receive reset link → reset successfully | User logs in with new password | Screenshot_AppPasswordReset.png |
| 5 | Enter valid credentials → enable Face ID/Touch ID | Next login via biometrics successful | Screenshot_BiometricLogin.png |
| 6 | Enter valid credentials, then Logout | User session ends, redirected to Login | Screenshot_AppLogout.png |
| 7 | Login offline mode (if supported) | App shows offline error or cached mode | Screenshot_AppOffline.png |
| 8 | Login with valid credentials in different device | Session syncs correctly | Screenshot_AppMultiDevice.png |
| 9 | Login using Social Login (Google/Facebook/Apple) | Successful login via provider with valid token | Screenshot_AppSocialLogin.png |
| 10 | Login with localization set to Arabic/English | App shows correct localized messages | Screenshot_AppLocalization.png |
| 11 | Login after updating the app | App continues session or requests re-login without issues | Screenshot_AppUpdateLogin.png |

---

## ❌ Invalid Test Cases

| Step | Action | Expected Result | Attachments |
|------|--------|----------------|-------------|
| 1 | Leave fields blank, tap Login | Error: "Email and Password are required" | Screenshot_AppBlankFields.png |
| 2 | Enter email only, no password | Error: "Password required" | Screenshot_AppNoPassword.png |
| 3 | Enter invalid email format (abc@com) | Error: "Invalid email" | Screenshot_AppInvalidEmail.png |
| 4 | Enter valid email + wrong password | Error: "Incorrect password" | Screenshot_AppWrongPassword.png |
| 5 | Enter unregistered email | Error: "Account not found" | Screenshot_AppNoAccount.png |
| 6 | Exceed max failed attempts (e.g. 5 tries) | Account locked / CAPTCHA prompt | Screenshot_AppLock.png |
| 7 | Try login with disabled account | Error: "Account inactive" | Screenshot_AppInactive.png |
| 8 | Enter valid credentials but revoke app permissions (network) | Error: "No internet connection" | Screenshot_AppNoInternet.png |
| 9 | Enter valid password + email with trailing/leading spaces | System trims and processes correctly | Screenshot_AppTrimSpaces.png |
| 10 | Enter case-sensitive password incorrectly (Pass123 vs pass123) | Error: "Incorrect password" | Screenshot_AppCaseSensitive.png |
| 11 | Enter password containing emojis | System rejects unsupported characters | Screenshot_AppEmojiPassword.png |
| 12 | Use expired password reset link | Error: "Reset link expired" | Screenshot_AppExpiredLink.png |
| 13 | Try login during server maintenance mode | Error: "Service unavailable, try later" | Screenshot_AppMaintenance.png |

---

## ⚠️ Edge Test Cases

| Step | Action | Expected Result | Attachments |
|------|--------|----------------|-------------|
| 1 | Enter very long email (>256 chars) | System rejects input | Screenshot_AppLongEmail.png |
| 2 | Enter password >100 chars | Input accepted, login handled properly | Screenshot_AppLongPassword.png |
| 3 | Enter password with only spaces | Error: "Password cannot be blank" | Screenshot_AppSpacePassword.png |
| 4 | Input SQL Injection string | App prevents injection | Screenshot_AppSQL.png |
| 5 | Input XSS string in email field | App sanitizes input | Screenshot_AppXSS.png |
| 6 | Enable airplane mode during login | App shows proper offline error | Screenshot_AppAirplane.png |
| 7 | Multiple users login simultaneously on different devices | Session handled correctly | Screenshot_AppConcurrent.png |
| 8 | Rotate screen during login | Fields remain stable, no crash | Screenshot_AppRotate.png |
| 9 | Kill app during login process | App recovers gracefully | Screenshot_AppKill.png |
| 10 | Login on device with very low memory/battery | App handles without crashing | Screenshot_AppLowResources.png |
| 11 | Login while switching network (WiFi ⇆ Mobile Data) | Session handled, no crash | Screenshot_AppNetworkSwitch.png |
| 12 | Login with VPN/Proxy enabled | App detects and handles per security policy | Screenshot_AppVPN.png |
| 13 | Lock device screen during login process | App resumes or restarts login properly | Screenshot_AppLockScreen.png |
| 14 | Concurrent login from 3+ devices with same account | App handles session rules (allow or restrict) | Screenshot_AppMultiDeviceConcurrent.png |

---

## 📌 Coverage Achieved  

- **Valid Scenarios**: Standard login, remember me, forgot password, logout, biometric login, multi-device login, offline handling, localization, social login, post-update login.  
- **Invalid Scenarios**: Blank fields, missing creds, invalid format, wrong password, unregistered user, disabled account, too many failed attempts (lockout), revoked network, expired reset link, server maintenance, spaces/emoji in password, case-sensitive mismatch.  
- **Edge Scenarios**: Long inputs, SQL injection, XSS, airplane mode, crash/kill recovery, device rotation, concurrency, VPN/proxy, network switch, low device resources, screen lock during login.  

---
