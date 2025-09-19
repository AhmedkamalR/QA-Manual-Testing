# Website - Login Feature Test Cases

This document contains **comprehensive test cases** for the Login functionality, covering positive, negative, and edge scenarios.

---

## ✅ Valid Test Cases

| Step | Action | Expected Result | Attachments |
|------|--------|----------------|-------------|
| 1 | Navigate to Login page | Login form with Email & Password fields is displayed | Screenshot_LoginPage.png |
| 2 | Enter valid email & password then click Login | User is redirected to Homepage/Dashboard | Screenshot_LoginSuccess.png |
| 3 | Enter valid credentials and check "Remember Me" | User remains logged in after browser restart | Screenshot_RememberMe.png |
| 4 | Enter valid credentials, click "Forgot Password", then reset password via email | Password reset is successful and user can log in with new password | Screenshot_PasswordReset.png |
| 5 | Login with valid credentials then click "Logout" | User is redirected back to Login page and session is ended | Screenshot_Logout.png |
| 6 | Login from one browser, then login again from another device | Session handling works correctly, user can access account | Screenshot_MultiDevice.png |
| 7 | Use "Show Password" toggle | Password is displayed in plain text when enabled | Screenshot_ShowPassword.png |
| 8 | Login with valid credentials while language = Arabic | Login successful with correct localization | Screenshot_ArabicLogin.png |
| 9 | Login using valid credentials while cookies enabled | Session persists as expected | Screenshot_CookiesEnabled.png |
| 10 | Login after clearing browser cache | User can still login successfully | Screenshot_ClearCache.png |
| 11 | Login while enabling browser autofill | Credentials autofilled and login successful | Screenshot_Autofill.png |

---

## ❌ Invalid Test Cases

| Step | Action | Expected Result | Attachments |
|------|--------|----------------|-------------|
| 1 | Leave Email and Password empty, click Login | Error: "Email and Password are required" | Screenshot_BlankFields.png |
| 2 | Enter email only without password | Error: "Password is required" | Screenshot_NoPassword.png |
| 3 | Enter password only without email | Error: "Email is required" | Screenshot_NoEmail.png |
| 4 | Enter invalid email format (e.g. `test@com`) | Error: "Invalid email format" | Screenshot_InvalidEmail.png |
| 5 | Enter valid email but wrong password | Error: "Incorrect password" | Screenshot_WrongPassword.png |
| 6 | Enter unregistered email and valid password | Error: "Account does not exist" | Screenshot_NoAccount.png |
| 7 | Enter valid credentials but disable JavaScript | Login fails gracefully with proper message | Screenshot_NoJS.png |
| 8 | Try login with expired password (if policy enforced) | Error: "Password expired, please reset" | Screenshot_ExpiredPassword.png |
| 9 | Enter valid email but use Caps Lock ON for password | Error: "Incorrect password" | Screenshot_CapsLock.png |
| 10 | Attempt login after 5 failed tries | Account locked or CAPTCHA displayed | Screenshot_AccountLock.png |
| 11 | Enter valid credentials but internet is disconnected | Proper error "No internet connection" shown | Screenshot_NoInternet.png |
| 12 | Enter valid credentials but account is inactive | Error: "Account inactive, contact support" | Screenshot_InactiveAccount.png |
| 13 | Enter credentials with leading/trailing spaces ( ` user@test.com ` ) | Error displayed or system trims input | Screenshot_TrimmedInput.png |
| 14 | Attempt login with expired/invalid session cookie | User forced to re-login | Screenshot_InvalidSession.png |
| 15 | Login with correct credentials but from blocked IP | Error: "Access denied" | Screenshot_BlockedIP.png |

---

## ⚠️ Edge Test Cases

| Step | Action | Expected Result | Attachments |
|------|--------|----------------|-------------|
| 1 | Enter email with 256 characters | System restricts or shows error gracefully | Screenshot_LongEmail.png |
| 2 | Enter password with 100+ characters | System handles input without crash | Screenshot_LongPassword.png |
| 3 | Enter password with only spaces | Error: "Password cannot be blank" | Screenshot_EmptyPassword.png |
| 4 | Enter password with special characters only (e.g. `@@@@`) | Error displayed or login prevented | Screenshot_SpecialChars.png |
| 5 | Attempt SQL Injection (`' OR '1'='1`) in email field | System blocks injection and shows error | Screenshot_SQLInjection.png |
| 6 | Attempt XSS (`<script>alert('x')</script>`) in email field | System escapes script and prevents execution | Screenshot_XSS.png |
| 7 | Enter emoji characters in email or password | System rejects invalid characters | Screenshot_Emoji.png |
| 8 | Login with valid credentials but disable cookies | Login works but session not persistent | Screenshot_NoCookies.png |
| 9 | Multiple users try logging in with same account at the same time | System handles concurrency properly | Screenshot_ConcurrentLogin.png |
| 10 | Open multiple tabs and login in one tab | Other tabs are updated to logged-in state or require refresh | Screenshot_MultiTabs.png |
| 11 | Enter mixed case email (`TestUser@Domain.com`) | System accepts and normalizes email (case insensitive) | Screenshot_EmailCase.png |
| 12 | Login using password with leading/trailing spaces (` pass123 `) | System trims input before validation | Screenshot_TrimSpaces.png |
| 13 | Resize browser window during login | Page responsive, no crash | Screenshot_Resize.png |
| 14 | Switch network (Wi-Fi → Mobile Data) during login | Session handled gracefully, no crash | Screenshot_NetworkSwitch.png |
| 15 | Press browser back button immediately after login | User redirected properly without breaking session | Screenshot_BackButton.png |
| 16 | Try login with multiple tabs refreshing simultaneously | System handles requests without crash | Screenshot_MultiRefresh.png |

---

📌 **Coverage Achieved**  
- **Valid Scenarios**: Normal login, remember me, logout, forgot password, multi-device, localization, autofill, clear cache.  
- **Invalid Scenarios**: Empty fields, invalid format, wrong password, unregistered account, inactive/expired account, account lock, no internet, no JS, blocked IP, invalid session, trimmed input.  
- **Edge Scenarios**: Very long inputs, special chars, SQL injection, XSS, emojis, no cookies, concurrency, multi-tabs, input trimming, resize, network switch, back button, multi-refresh.  
