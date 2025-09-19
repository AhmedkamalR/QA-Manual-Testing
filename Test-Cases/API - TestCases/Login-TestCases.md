# API - Login Feature Test Cases

This document contains **API-level test cases** for the Login endpoint, covering valid (positive), invalid (negative), and edge scenarios.

---

## ✅ Valid Test Cases

| Step | Action | Expected Result | Attachments |
|------|--------|----------------|-------------|
| 1 | Send POST request `/api/login` with valid `email`, `password` | Response 200 OK, returns JWT token + user details | Response_ValidLogin.json |
| 2 | Send request with correct creds + `"rememberMe": true` | Token has longer expiry | Response_RememberMe.json |
| 3 | Send valid login request, then call `/api/logout` | Session token invalidated | Response_Logout.json |
| 4 | Validate response time under 2s for valid login | Pass performance criteria | Response_Performance.json |
| 5 | Login with valid OAuth2 (Google/Facebook) credentials | Response 200 with provider access token + mapped user | Response_OAuthLogin.json |
| 6 | Login with 2FA enabled (valid OTP after password) | Response 200 with JWT token | Response_2FA.json |
| 7 | Login from multiple devices with valid creds | Both sessions created successfully with independent tokens | Response_MultiDevice.json |
| 8 | Login → refresh token flow (`/api/refresh`) | New JWT issued, old one invalidated | Response_Refresh.json |

---

## ❌ Invalid Test Cases

| Step | Action | Expected Result | Attachments |
|------|--------|----------------|-------------|
| 1 | POST `/api/login` with empty body | Response 400 Bad Request | Response_EmptyBody.json |
| 2 | Missing `password` field | Response 400 with error "Password required" | Response_NoPassword.json |
| 3 | Invalid email format (`abc@com`) | Response 400 Invalid Email | Response_InvalidEmail.json |
| 4 | Wrong password | Response 401 Unauthorized | Response_WrongPassword.json |
| 5 | Non-existent account | Response 404 "User not found" | Response_NoUser.json |
| 6 | 5 failed logins in a row | Response 429 "Too many attempts" | Response_TooMany.json |
| 7 | Login with expired password | Response 403 "Password expired" | Response_Expired.json |
| 8 | Login with disabled account | Response 403 "Account disabled" | Response_Disabled.json |
| 9 | Send valid login without `Content-Type: application/json` header | Response 415 Unsupported Media Type | Response_NoContentType.json |
| 10 | Attempt login via GET instead of POST | Response 405 Method Not Allowed | Response_WrongMethod.json |
| 11 | Submit wrong OTP for 2FA | Response 401 Unauthorized | Response_WrongOTP.json |
| 12 | Send request with revoked API key (if API-key protected) | Response 403 Forbidden | Response_RevokedAPIKey.json |

---

## ⚠️ Edge Test Cases

| Step | Action | Expected Result | Attachments |
|------|--------|----------------|-------------|
| 1 | Email field = 256 chars | Response 400 "Email too long" | Response_LongEmail.json |
| 2 | Password field = 100+ chars | System handles gracefully | Response_LongPassword.json |
| 3 | SQL injection payload in email (`' OR 1=1 --`) | Response 400, input sanitized | Response_SQL.json |
| 4 | XSS payload in email (`<script>alert(1)</script>`) | Response 400, script escaped | Response_XSS.json |
| 5 | Send request without HTTPS | Response 403 "SSL required" | Response_NoSSL.json |
| 6 | Send with expired JWT token | Response 401 Unauthorized | Response_ExpiredToken.json |
| 7 | Send with tampered JWT token | Response 401 Unauthorized | Response_TamperedToken.json |
| 8 | Very high load (1000 login req/sec) | API handles load or returns 503 gracefully | Response_LoadTest.json |
| 9 | Simulate network packet loss (50%) during login | Graceful retry or timeout error | Response_PacketLoss.json |
| 10 | Simulate server crash mid-login | API recovers with 500 error (no sensitive info leaked) | Response_ServerCrash.json |
| 11 | Send request with UTF-8 special chars + emojis in email | Response 400 or sanitized input | Response_Emoji.json |
| 12 | Parallel login + logout race condition | Last valid action reflected consistently | Response_RaceCondition.json |
| 13 | Very large payload (1MB JSON body) | Response 413 Payload Too Large | Response_BigPayload.json |
| 14 | Multiple concurrent refresh token requests | Only first valid, others rejected | Response_RefreshRace.json |

---

## 📌 Coverage Achieved

- **Valid Scenarios**: Normal login, remember me, logout, response time validation, OAuth login, 2FA login, multi-device login, refresh token.  
- **Invalid Scenarios**: Empty/missing fields, invalid format, wrong password, non-existent account, too many attempts (rate limiting), expired password, disabled account, missing/invalid headers, wrong method, wrong OTP, revoked API key.  
- **Edge Scenarios**: Very long inputs, large payload, SQL injection, XSS, no SSL, expired/tampered token, load/stress tests, network instability, server crash handling, emojis & UTF-8 chars, concurrency/race conditions, multiple refresh requests.  

---
