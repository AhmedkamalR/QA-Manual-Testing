# Login - Test Scenarios (Web & Mobile)

This document contains **test scenarios** for the Login feature across **Web** and **Mobile** platforms, covering functional, negative, edge, performance, and security flows.

---

## 1. Positive Scenarios

1. User logs in successfully with valid email & password (Web & Mobile).
2. User logs in with "Remember Me" option → session expiry extended (Web).
3. User logs in successfully and then logs out → token/session becomes invalid (Web & Mobile).
4. User can access protected pages/APIs with a valid token/session (Web & Mobile).
5. Login using biometric authentication (fingerprint/Face ID) (Mobile).
6. Login using social media accounts (Google, Facebook, Apple ID) (Mobile).
7. Response time for valid login under 2s (Web & Mobile).
8. User remains logged in when reopening the app if session is valid (Mobile).

---

## 2. Negative Scenarios

9. Login with empty body → proper validation error (Web & Mobile).
10. Missing `password` field → "Password required" (Web).
11. Invalid email format (e.g., `abc@com`) (Web & Mobile).
12. Wrong password for existing account → `401 Unauthorized` (Web & Mobile).
13. Non-existent account → "User not found" (Web & Mobile).
14. Multiple failed login attempts → "Too many attempts" (Web & Mobile).
15. Login with expired password → blocked + reset prompt (Web & Mobile).
16. Login with disabled account → "Account disabled" (Web & Mobile).
17. Login with locked account (after policy lockout) → "Account locked" (Web & Mobile).
18. Login attempt with deleted account → "Account does not exist" (Web & Mobile).
19. Login with revoked access for social media login → "Access denied" (Mobile).
20. Biometric login attempt with invalid fingerprint/face → denied access (Mobile).
21. Network disconnected during login → appropriate error message (Mobile).

---

## 3. Edge Scenarios

22. Email field = 256 characters (Web & Mobile).
23. Password field > 100 characters (Web & Mobile).
24. Login with SQL Injection payload (`' OR 1=1 --`) → sanitized input (Web).
25. Login with XSS payload (`<script>alert(1)</script>`) → escaped input (Web).
26. Login without HTTPS → "SSL required" (Web).
27. Expired JWT token used → "Unauthorized" (Web & Mobile).
28. Tampered JWT token → "Unauthorized" (Web & Mobile).
29. Login with mixed-case email (e.g., `TestUser@Mail.Com`) → should authenticate (Web & Mobile).
30. Login with leading/trailing spaces in email → trimmed (Web & Mobile).
31. Login with special characters in password → accepted (Web & Mobile).
32. Login with Unicode characters in password (e.g., Arabic, emojis) (Web & Mobile).
33. Reusing session after logout → access denied (Web & Mobile).
34. Login on multiple devices simultaneously → sessions handled correctly (Web & Mobile).
35. Password changed in another session → old token/session invalid (Web & Mobile).
36. App opened after long inactivity → session expires gracefully (Mobile).
37. Switching from Wi-Fi to mobile data during login → retry flow works (Mobile).

---

## 4. Security Scenarios

38. Rate-limiting applied against brute-force attacks (Web & Mobile).
39. Login request without CSRF token → blocked (Web).
40. Replay attack with same login request → rejected (Web & Mobile).
41. Password field not logged in request/response logs (Web & Mobile).
42. Error messages are generic and do not expose sensitive info (Web & Mobile).
43. Password transmitted only over HTTPS (never in plain text) (Web & Mobile).
44. Session hijacking attempt (stolen token) → blocked (Web & Mobile).
45. Token expiry & refresh token flow validated (Web & Mobile).
46. Login endpoint secured against SQL injection, XSS, and code injection (Web).
47. Biometric data never leaves device (Mobile).
48. App blocks rooted/jailbroken devices from bypassing login (Mobile).

---

## 5. Performance & Load Scenarios

49. 1000 concurrent login requests handled gracefully (Web).
50. App tested under slow 2G/3G network during login (Mobile).
51. API login response validated under high server load (Web).
52. App behavior tested under airplane mode (Mobile).

---

## Coverage Achieved

* **Functional coverage**: Valid login, logout, Remember Me, biometric login, and social login.
* **Validation coverage**: Field validation, missing/invalid inputs, long inputs, multi-device login.
* **Security coverage**: Brute force, SQL injection, XSS, CSRF, HTTPS, token tampering, replay attacks.
* **Performance coverage**: Response time, concurrent logins, weak networks, offline mode.
* **Session coverage**: Expired, tampered, reused, revoked, multi-device sessions, inactivity.
* **Platform coverage**: Full coverage for **Web** + **Mobile** login scenarios.
