# Website - Registration Feature Test Cases

This document contains **comprehensive test cases** for the Registration functionality on the website, covering valid (positive), invalid (negative), and edge scenarios.

---

## ✅ Valid Test Cases

| Step | Action | Expected Result | Attachments |
|------|--------|----------------|-------------|
| 1 | Navigate to Registration page | Registration form displayed with all required fields (Name, Email, Password, Confirm Password, Phone, etc.) | Screenshot_RegisterPage.png |
| 2 | Enter valid name, email, password, phone, and submit | Account created successfully, redirected to Welcome/Dashboard | Screenshot_RegisterSuccess.png |
| 3 | Enter valid details + check "Subscribe to Newsletter" | User account created + newsletter subscription confirmed | Screenshot_Newsletter.png |
| 4 | Enter valid details with referral code | Referral code applied successfully | Screenshot_Referral.png |
| 5 | Password meets all policies (≥8 chars, uppercase, lowercase, number, special char) | Registration successful | Screenshot_StrongPassword.png |
| 6 | Register with max allowed password (64 chars) | Registration successful | Screenshot_MaxPassword.png |
| 7 | Register with hyphenated name (`Ahmed-Kamal`) | Accepted successfully | Screenshot_SpecialName.png |
| 8 | Register with international phone number (+201001234567) | Accepted successfully | Screenshot_IntPhone.png |
| 9 | Register with valid email, confirm password matching | Registration successful | Screenshot_ConfirmPassword.png |
| 10 | Validate response time under 2s | Pass performance criteria | Screenshot_Performance.png |

---

## ❌ Invalid Test Cases

| Step | Action | Expected Result | Attachments |
|------|--------|----------------|-------------|
| 1 | Leave all fields blank, click Register | Error: "All fields are required" | Screenshot_BlankFields.png |
| 2 | Enter valid name + email only, leave password blank | Error: "Password is required" | Screenshot_NoPassword.png |
| 3 | Enter password only, leave email blank | Error: "Email is required" | Screenshot_NoEmail.png |
| 4 | Enter mismatched passwords | Error: "Passwords do not match" | Screenshot_MismatchPassword.png |
| 5 | Enter invalid email format (`test@com`) | Error: "Invalid email address" | Screenshot_InvalidEmail.png |
| 6 | Enter password too short (5 chars) | Error: "Password must be at least 8 characters" | Screenshot_ShortPassword.png |
| 7 | Enter weak password (`12345678`) | Error: "Password too weak" | Screenshot_WeakPassword.png |
| 8 | Reuse already registered email | Error: "Email already exists" | Screenshot_DuplicateEmail.png |
| 9 | Reuse already registered phone | Error: "Phone already exists" | Screenshot_DuplicatePhone.png |
| 10 | Upload oversized profile image (>5MB) | Error: "File too large" | Screenshot_BigImage.png |
| 11 | Register with disposable email (mailinator.com) | Error: "Invalid email domain" | Screenshot_DisposableEmail.png |
| 12 | Register with special chars in phone (`123#@!`) | Error: "Invalid phone number" | Screenshot_InvalidPhone.png |
| 13 | Submit without checking required "Terms & Conditions" | Error: "You must accept terms" | Screenshot_Terms.png |
| 14 | Register with expired invitation link | Error: "Link expired" | Screenshot_ExpiredLink.png |
| 15 | Multiple registration attempts in <1 minute | CAPTCHA displayed or throttling applied | Screenshot_TooManyAttempts.png |
| 16 | Register with JS disabled | Graceful error page shown | Screenshot_NoJS.png |
| 17 | Attempt to register without internet connection | Error: "No internet connection" | Screenshot_NoInternet.png |
| 18 | Register with inactive email (bounced mail) | Error: "Email verification failed" | Screenshot_EmailNotVerified.png |

---

## ⚠️ Edge Test Cases

| Step | Action | Expected Result | Attachments |
|------|--------|----------------|-------------|
| 1 | Email with 256 characters | Error: "Email too long" | Screenshot_LongEmail.png |
| 2 | Password with 128 characters | Registration successful (if allowed) | Screenshot_LongPassword.png |
| 3 | Name with only spaces | Error: "Name cannot be empty" | Screenshot_EmptyName.png |
| 4 | Input SQL injection in email (`' OR 1=1 --`) | Registration blocked, input sanitized | Screenshot_SQL.png |
| 5 | Input XSS in name (`<script>alert(1)</script>`) | Registration blocked, script escaped | Screenshot_XSS.png |
| 6 | Input emoji in name (`Ahmed😊`) | Accepted or sanitized | Screenshot_EmojiName.png |
| 7 | Register at midnight (23:59 → 00:00) | Registration successful | Screenshot_BoundaryTime.png |
| 8 | Register with blacklisted domain (`@spam.com`) | Error: "Domain not allowed" | Screenshot_Blacklist.png |
| 9 | Register with mixed case email (`TestUser@Domain.com`) | Email normalized, account created | Screenshot_EmailCase.png |
| 10 | Register with leading/trailing spaces in email (` test@domain.com `) | Spaces trimmed, accepted | Screenshot_TrimmedEmail.png |
| 11 | Open multiple tabs → register same email simultaneously | Only first succeeds, others fail | Screenshot_DuplicateRace.png |
| 12 | Simulate network packet loss (50%) | Graceful retry or error | Screenshot_PacketLoss.png |
| 13 | Submit 1MB JSON payload | Error: "Payload too large" | Screenshot_BigPayload.png |
| 14 | Kill browser tab mid-registration | System stable, no partial account created | Screenshot_TabKill.png |
| 15 | Refresh page during submission | No duplicate accounts created | Screenshot_Refresh.png |

---

## 📌 Coverage Achieved

- **Valid Scenarios**: Normal registration, strong password policy, confirm password, newsletter, referral codes, special names, max password, international phone, terms acceptance, performance check.  
- **Invalid Scenarios**: Empty/missing fields, invalid email, mismatched passwords, short/weak passwords, duplicate accounts, disposable email, invalid phone, oversized uploads, inactive email, expired link, JS disabled, no internet, multiple attempts.  
- **Edge Scenarios**: Very long inputs, special characters, SQL injection, XSS, emojis, case sensitivity, trimmed inputs, concurrency/race conditions, payload size limits, boundary timing, network instability, browser crashes.  

---
