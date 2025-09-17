# API - Login Feature Test Cases

This document contains **API-level test cases** for the Login endpoint, covering positive, negative, and edge scenarios.

---

## ✅ Valid Test Cases

| Step | Action | Expected Result | Attachments |
|------|--------|----------------|-------------|
| 1 | Send POST request `/api/login` with valid `email`, `password` | Response 200 OK, returns JWT token + user details | Response_ValidLogin.json |
| 2 | Send request with correct creds + "rememberMe=true" | Token has longer expiry | Response_RememberMe.json |
| 3 | Send valid login request, then call `/api/logout` | Session token invalidated | Response_Logout.json |
| 4 | Validate response time under 2s for valid login | Pass performance criteria | Response_Performance.json |

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

---
