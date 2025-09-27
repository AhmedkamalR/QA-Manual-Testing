# 👤 Profile & Address Management – Test Scenarios

This document outlines **comprehensive test scenarios** for the **Profile & Address module** across API, Website, and Mobile App.  
It ensures coverage of valid, invalid, and edge cases for profile updates, address book, and account preferences.

---

## 1. API Scenarios

### ✅ Valid Scenarios
- Create new user profile with all mandatory fields.
- Update profile details (name, email, phone).
- Update profile with optional fields (DOB, gender).
- Upload profile picture successfully.
- Remove profile picture.
- Change password with valid old password.
- Reset password via API.
- Add new address (home, office, custom label).
- Update existing address (street, city, zip, country).
- Delete saved address.
- Mark address as default shipping.
- Retrieve all saved addresses by user ID.
- Retrieve profile details by user ID.
- API returns correct response for multiple addresses.

### ❌ Invalid Scenarios
- Create profile with missing mandatory fields.
- Update profile with invalid email format.
- Update profile with invalid phone number.
- Upload unsupported file type for profile picture.
- Upload oversized image beyond limit.
- Change password with incorrect old password.
- Change password with weak new password.
- Reset password with invalid/expired token.
- Add address with missing city/zip.
- Add address with invalid country code.
- Delete non-existing address.
- Update address of another user (unauthorized).
- Fetch addresses with invalid user ID.
- Unauthorized API call without token.
- Duplicate address entry with same label + details.

### ⚠️ Edge Scenarios
- Very long name field (200+ chars).
- Profile with emoji/special characters in name.
- Multi-language data (English + Arabic).
- User with 20+ saved addresses.
- Address with extremely long street name.
- Address without zip code (some regions).
- Default address deleted → fallback to another.
- API stress test: 1000 profile update requests.
- Update profile while another session is active.
- Multiple default addresses conflict.
- Concurrent API calls for add/update address.

---

## 2. Website Scenarios

### ✅ Valid Scenarios
- Register new account with valid details.
- Update profile information (name, email, phone).
- Upload/change/remove profile picture.
- Change password successfully.
- Reset password via email link.
- Add new address from “My Account”.
- Update existing address.
- Delete address successfully.
- Mark address as default.
- Use saved address during checkout.
- See updated profile immediately after saving.
- Logout and login again → data persists.
- Switch language → profile data localized.

### ❌ Invalid Scenarios
- Register with already used email.
- Update profile with invalid phone/email.
- Upload invalid format (e.g., .exe file).
- Upload image > 5MB.
- Weak password not accepted.
- Reset password link expired.
- Add address with empty required fields.
- Add invalid postal code (letters in numeric field).
- Save address with invalid characters.
- Try to delete default address when only one exists.
- Unauthorized profile page access without login.
- Multiple clicks on Save → should update once.

### ⚠️ Edge Scenarios
- User has no saved address → checkout asks for new.
- User has 50+ saved addresses (pagination/scroll).
- User deletes address during active order.
- Add international addresses (different formats).
- Special chars/emoji in address field.
- User session timeout during update.
- Profile updated on web not synced on mobile.
- Accessibility: screen reader reads all profile labels.

---

## 3. Mobile App Scenarios

### ✅ Valid Scenarios
- Register new account via app.
- Update profile details.
- Upload/change profile picture from camera/gallery.
- Remove profile picture.
- Change password successfully.
- Reset password via email/SMS.
- Add new address via app.
- Update address with map picker (if supported).
- Delete address.
- Mark default address.
- Autofill address via GPS (if available).
- Profile syncs with website.

### ❌ Invalid Scenarios
- Register with invalid email.
- Update profile with invalid characters.
- Upload non-image file as profile picture.
- Upload image too large.
- Change password with wrong old password.
- Reset password with expired OTP.
- Add address without selecting city.
- GPS returns invalid coordinates.
- Delete address linked to active order.
- Unauthorized user tries to edit profile.

### ⚠️ Edge Scenarios
- App offline while updating profile → queued sync.
- Switch language mid-profile update.
- Multiple addresses with identical data.
- App force-closed during save.
- Very large address book sync.
- Address with special regional formats (APO, PO Box).
- Concurrent profile update from two devices.
- Profile photo with high resolution (4000x4000).
- Stress: 50+ API calls from app during profile sync.

---

## ✅ Key Values / Keywords
- **Entities:** User, Profile, Address, Password, Token, Picture.  
- **Parameters:** user_id, email, phone, password, address_id, country_code, default_flag.  
- **States:** Active, Inactive, Default, Guest, Registered, Verified.  
- **Edge:** Long text, Multi-language, Large address book, Invalid formats, Sync issues.  

---
