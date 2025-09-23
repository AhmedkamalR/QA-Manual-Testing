# Registration Feature - Test Scenarios

This document contains **comprehensive test scenarios** for the Registration (Sign Up) functionality of the E-Commerce system, covering **positive, negative, edge, security, and performance scenarios** for both Web and Mobile platforms.

---

## ✅ Positive Scenarios

1. User opens Registration page/screen successfully.  
2. User fills all mandatory fields (First Name, Last Name, Email, Password, Confirm Password, Phone, Address) with valid data.  
3. User registers using valid email & strong password.  
4. User registers with mobile number (if supported).  
5. User registers with valid referral/invite code.  
6. User selects country & region correctly during registration.  
7. User receives account activation email and activates successfully.  
8. User registers and receives SMS OTP verification code (if enabled).  
9. User registers and is auto-logged in after successful signup.  
10. User registers and is redirected to Welcome/Dashboard page.  
11. User accepts Terms & Conditions and registration is completed.  
12. User registers in Arabic language version successfully.  
13. User registers using social login (Google, Facebook, Apple).  
14. User uploads valid profile picture during registration.  
15. User can navigate back to Login page from Registration.  

---

## ❌ Negative Scenarios

1. User leaves all fields blank and clicks Register → Error messages displayed.  
2. User enters invalid email format (e.g., `test@com`).  
3. User enters password less than minimum required length.  
4. User enters password without special characters / numbers (weak password).  
5. Password and Confirm Password do not match.  
6. User enters phone number in invalid format.  
7. User enters already registered email.  
8. User enters already registered phone number.  
9. User submits registration without accepting Terms & Conditions.  
10. User enters invalid referral code.  
11. User disables JavaScript and tries to register (Web).  
12. User attempts to bypass validation using browser DevTools.  
13. User closes app during registration flow (Mobile).  
14. User tries to register with expired OTP code.  
15. User tries to register with wrong OTP multiple times.  
16. User tries to register but backend API is down.  
17. User registers with email domain that is blacklisted (e.g., temporary mail).  
18. User enters script injection in fields (XSS attempt).  
19. User attempts SQL Injection in input fields.  
20. User tries registering without internet connection.  
21. User tries registering with inactive/disabled social login provider.  

---

## ⚠️ Edge Scenarios

1. User enters maximum length email (256 characters).  
2. User enters maximum length password (100+ characters).  
3. User enters password containing emojis.  
4. User enters name fields with numeric values (should be rejected).  
5. User enters multi-language characters (Arabic, Chinese, etc.) in name field.  
6. User enters leading/trailing spaces in email or password.  
7. User opens multiple tabs and tries registering with same email simultaneously.  
8. User registers on Web and Mobile at the same time.  
9. User rotates device during registration (Mobile).  
10. User switches between apps during registration (Mobile).  
11. User uploads unsupported file format as profile picture.  
12. User uploads large image file as profile picture (size limit exceeded).  
13. User pastes long text (over 500 chars) in address field.  
14. User tries registering using VPN/proxy (geo-restricted).  
15. User tries registering with different locale/timezone settings.  

---

## 🔒 Security Scenarios

1. Ensure registration API uses HTTPS (no plain HTTP).  
2. Ensure passwords are hashed (not stored in plain text).  
3. Ensure strong password policies enforced (min length, upper/lower case, special chars, numbers).  
4. Check rate limiting / throttling after multiple failed attempts.  
5. Verify account lock after too many failed OTP entries.  
6. Ensure CAPTCHA is shown after suspicious registration attempts (bot prevention).  
7. Validate CSRF protection on registration form.  
8. Validate that sensitive data (password, OTP) is not logged in system logs.  
9. Ensure JWT/session tokens are securely generated after registration.  
10. Check email verification links expire after a defined period.  
11. Ensure user cannot register with admin/reserved usernames.  
12. Ensure SQL Injection attempts are blocked.  
13. Ensure XSS payloads in name/email fields are sanitized.  
14. Ensure phone/email OTP is not reused after success.  
15. Validate that concurrent registration attempts with same email/phone are blocked properly.  

---

## ⚡ Performance & Load Scenarios

1. Register 1000 users simultaneously (stress test).  
2. Register users in peak load conditions (e.g., Black Friday).  
3. Register while API response is slow (simulate network latency).  
4. Register while internet disconnects & reconnects mid-process.  
5. Validate system behavior under heavy OTP SMS/email traffic.  
6. Validate registration with large concurrent requests does not crash DB.  
7. Measure response time for registration API under 100 TPS (transactions/sec).  
8. Ensure registration form loads within acceptable time (<2 sec) on Web.  
9. Ensure registration flow completes within <5 sec on Mobile (normal conditions).  
10. Test registration on low-end mobile devices with limited memory.  
11. Test registration on slow 3G/edge network.  
12. Validate system recovers after sudden server restart during registration load.  

---

📌 **Coverage Achieved**  
- **Positive**: Full valid registration flow including email, phone, OTP, social logins, profile upload, localization.  
- **Negative**: Invalid inputs, duplicate accounts, missing fields, weak passwords, expired OTP, API failures, injection attacks.  
- **Edge**: Maximum input lengths, special chars, emojis, large uploads, concurrency, device orientation, locale variations.  
- **Security**: HTTPS, password hashing, brute-force protection, CSRF, SQLi/XSS, OTP security.  
- **Performance**: Load, stress, latency, concurrency, device/network variations.  
