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

---
