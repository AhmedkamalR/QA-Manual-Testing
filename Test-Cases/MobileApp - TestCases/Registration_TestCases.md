# Mobile App - Registration Feature Test Cases

This document contains **comprehensive test cases** for the Registration functionality on the mobile app (Android & iOS), covering valid (positive), invalid (negative), and edge scenarios.

---

## ✅ Valid Test Cases

| Step | Action | Expected Result | Attachments |
|------|--------|----------------|-------------|
| 1 | Open the app → tap "Register" | Registration form displayed | Screenshot_Mobile_RegisterForm.png |
| 2 | Enter valid details (name, email, password, phone) → tap Register | Account created successfully, redirected to Home | Screenshot_Mobile_Success.png |
| 3 | Enable biometric (FaceID/TouchID) after registration | Biometric linked to account | Screenshot_Biometric.png |
| 4 | Enter valid details + referral code | Referral applied successfully | Screenshot_Mobile_Referral.png |
| 5 | Register with Google/Facebook/Apple login | Account created via social auth | Screenshot_SocialLogin.png |
| 6 | Password meets all policies (≥8 chars, mix chars) | Registration successful | Screenshot_Mobile_StrongPass.png |
| 7 | Register with valid phone number → OTP sent | OTP screen displayed | Screenshot_OTP.png |
| 8 | Enter correct OTP within 60 seconds | Registration completed | Screenshot_OTP_Success.png |
| 9 | Register offline → retry when network back | Data synced successfully | Screenshot_OfflineSync.png |
| 10 | Registration response time <2s | Pass performance criteria | Screenshot_Performance.png |

---

## ❌ Invalid Test Cases

| Step | Action | Expected Result | Attachments |
|------|--------|----------------|-------------|
| 1 | Tap Register with all fields blank | Error: "All fields required" | Screenshot_Mobile_Blank.png |
| 2 | Enter only email + password, leave name empty | Error: "Name is required" | Screenshot_NoName.png |
| 3 | Enter mismatched password + confirm password | Error: "Passwords do not match" | Screenshot_Mobile_Mismatch.png |
| 4 | Enter invalid email format (`abc@`) | Error: "Invalid email" | Screenshot_InvalidEmail.png |
| 5 | Enter weak password (`123456`) | Error: "Password too weak" | Screenshot_Mobile_WeakPass.png |
| 6 | Enter already registered email | Error: "Email already exists" | Screenshot_Mobile_Duplicate.png |
| 7 | Enter already registered phone | Error: "Phone already exists" | Screenshot_Mobile_DuplicatePhone.png |
| 8 | Enter OTP incorrectly 3 times | Error: "OTP invalid, try again later" | Screenshot_WrongOTP.png |
| 9 | Enter expired OTP (>2 min) | Error: "OTP expired" | Screenshot_ExpiredOTP.png |
| 10 | Kill app while OTP pending | Registration cancelled safely | Screenshot_KillApp.png |
| 11 | Tap Register without internet | Error: "No connection" | Screenshot_NoInternet.png |
| 12 | Register with oversized image (>5MB) | Error: "File too large" | Screenshot_Mobile_BigImage.png |
| 13 | Register with disposable email | Error: "Email not valid" | Screenshot_Disposable.png |
| 14 | Disable required permissions (SMS/Push) during OTP | Error message displayed | Screenshot_NoPermission.png |
| 15 | Tap Register repeatedly fast (10 times) | Only 1 request sent | Screenshot_MultiTap.png |
| 16 | Device clock changed backwards | Error: "Invalid OTP timestamp" | Screenshot_TimeChange.png |

---

## ⚠️ Edge Test Cases

| Step | Action | Expected Result | Attachments |
|------|--------|----------------|-------------|
| 1 | Register with max email length (256 chars) | Error shown | Screenshot_LongEmail.png |
| 2 | Register with max password length (128 chars) | Registration successful | Screenshot_LongPass.png |
| 3 | Register with emojis in name (`Ahmed 🚀`) | Accepted or sanitized | Screenshot_Emoji.png |
| 4 | Enter SQL injection in email (`' OR 1=1 --`) | Input sanitized | Screenshot_SQL.png |
| 5 | Enter XSS in name (`<script>alert(1)</script>`) | Escaped safely | Screenshot_XSS.png |
| 6 | Enter phone with spaces/dashes (`010-123-4567`) | Accepted (normalized) | Screenshot_PhoneFormat.png |
| 7 | Register using offline mode → switch to online | Sync works without duplicates | Screenshot_OfflineSync.png |
| 8 | Try registration with slow 2G network | Graceful timeout/retry shown | Screenshot_SlowNetwork.png |
| 9 | Rotate device (landscape ↔ portrait) mid-registration | Form data persists | Screenshot_Rotate.png |
| 10 | Background app during OTP → return later | Session still valid | Screenshot_Background.png |
| 11 | Use different keyboard language (Arabic, Chinese) for name | Accepted properly | Screenshot_Unicode.png |
| 12 | Register just before midnight → confirm after | Registration still valid | Screenshot_TimeBoundary.png |
| 13 | App crash during form submission | No partial account created | Screenshot_AppCrash.png |
| 14 | Tap back button during registration | Form canceled safely | Screenshot_BackButton.png |
| 15 | App update available during registration | Graceful prompt shown | Screenshot_Update.png |

---

## 📌 Coverage Achieved

- **Valid Scenarios**: Basic registration, OTP verification, social login, referral, offline sync, biometric enablement, password policy, network retry.  
- **Invalid Scenarios**: Empty/missing fields, weak passwords, invalid/duplicate email/phone, wrong/expired OTP, no internet, oversized image, disposable email, denied permissions, multiple taps, device time tampering.  
- **Edge Scenarios**: Long inputs, emoji/unicode, XSS/SQL injection, phone formatting, orientation changes, slow network, background handling, app crash, update handling.  

---
