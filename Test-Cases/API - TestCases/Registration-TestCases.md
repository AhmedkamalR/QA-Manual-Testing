# API - Registration Feature Test Cases

This document contains **API-level test cases** for the Registration endpoint, covering valid (positive), invalid (negative), and edge scenarios.

---

## ✅ Valid Test Cases

| Step | Action | Expected Result | Attachments |
|------|--------|----------------|-------------|
| 1 | Send POST `/api/register` with valid `name`, `email`, `password`, `phone` | Response 201 Created, user registered successfully | Response_ValidRegister.json |
| 2 | Register with `"subscribeNewsletter": true` | User flagged as subscribed | Response_Newsletter.json |
| 3 | Register with valid referral code | Referral bonus applied | Response_Referral.json |
| 4 | Register with password = max length (64 chars) | Registration successful | Response_MaxPassword.json |
| 5 | Register with special characters in name (`Ahmed-Kamal`) | Accepted | Response_SpecialCharName.json |
| 6 | Register using OAuth2 (Google/Facebook) | Response 201 with linked provider account | Response_OAuthRegister.json |
| 7 | Register with both email + phone for MFA | Both stored and MFA enabled | Response_MFA.json |
| 8 | Validate response time < 2s | Pass performance criteria | Response_Performance.json |

---

## ❌ Invalid Test Cases

| Step | Action | Expected Result | Attachments |
|------|--------|----------------|-------------|
| 1 | POST `/api/register` with empty body | Response 400 Bad Request | Response_EmptyBody.json |
| 2 | Missing `email` field | Response 400 "Email required" | Response_NoEmail.json |
| 3 | Missing `password` field | Response 400 "Password required" | Response_NoPassword.json |
| 4 | Invalid email format (`abc@com`) | Response 400 Invalid Email | Response_InvalidEmail.json |
| 5 | Password too short (<8 chars) | Response 400 "Password too weak" | Response_ShortPassword.json |
| 6 | Existing email re-used | Response 409 "Email already exists" | Response_DuplicateEmail.json |
| 7 | Existing phone re-used | Response 409 "Phone already exists" | Response_DuplicatePhone.json |
| 8 | Weak password (`123456`) | Response 400 "Weak password" | Response_WeakPassword.json |
| 9 | Register with disposable email (`test@mailinator.com`) | Response 403 Forbidden | Response_Disposable.json |
| 10 | SQL injection in email (`' OR 1=1 --`) | Response 400, sanitized | Response_SQL.json |
| 11 | XSS in name (`<script>alert(1)</script>`) | Response 400, escaped | Response_XSS.json |
| 12 | Oversized profile image (>5MB) | Response 413 Payload Too Large | Response_ImageTooLarge.json |
| 13 | Wrong content type (e.g., text/plain) | Response 415 Unsupported Media Type | Response_WrongContentType.json |
| 14 | Register without HTTPS | Response 403 SSL required | Response_NoSSL.json |
| 15 | Invalid phone format | Response 400 "Invalid phone" | Response_InvalidPhone.json |
| 16 | Too many attempts from one IP | Response 429 Too Many Requests | Response_RateLimit.json |

---

## ⚠️ Edge Test Cases

| Step | Action | Expected Result | Attachments |
|------|--------|----------------|-------------|
| 1 | Email = 256 characters | Response 400 "Email too long" | Response_LongEmail.json |
| 2 | Password = 128 characters | Registration successful (if allowed) | Response_LongPassword.json |
| 3 | Name = empty string | Response 400 "Name required" | Response_EmptyName.json |
| 4 | Register with emoji in name (`Ahmed😊`) | Either accepted or sanitized | Response_EmojiName.json |
| 5 | Register with leading/trailing spaces in email | Trimmed and accepted | Response_Trimmed.json |
| 6 | Register at boundary time (23:59 → 00:00) | Registration successful | Response_BoundaryTime.json |
| 7 | Register with blacklisted domain (`@spam.com`) | Response 403 Forbidden | Response_Blacklist.json |
| 8 | Send 1MB JSON body | Response 413 Payload Too Large | Response_BigPayload.json |
| 9 | Parallel duplicate registration requests | Only first succeeds, others blocked | Response_DuplicateRace.json |
| 10 | Simulate network packet loss during registration | Graceful retry or timeout error | Response_PacketLoss.json |
| 11 | Server crash mid-request | Response 500 (no sensitive info leaked) | Response_ServerCrash.json |

---

## 📌 Coverage Achieved

- **Valid Scenarios**: Standard registration, newsletter opt-in, referral codes, max-length fields, OAuth registration, MFA, response performance.  
- **Invalid Scenarios**: Missing/empty fields, invalid format, duplicate accounts, weak/disposable credentials, injection/XSS, oversized uploads, wrong content type, rate limiting.  
- **Edge Scenarios**: Very long inputs, emojis, trimmed values, boundary timing, blacklisted domains, payload limits, race conditions, network/server instability.  

---