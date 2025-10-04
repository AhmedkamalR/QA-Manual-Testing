# 📱 Mobile App – Profile & Address Module Test Cases

This document contains **Mobile App** test cases for the combined Profile, Settings & Address modules.  
Mobile-specific interactions covered (camera, gallery, GPS, background sync, push notifications, biometrics).

---

## 👤 Profile — ✅ Valid Test Cases

| Step | Action | Expected Result | Attachments |
|------|--------|-----------------|-------------|
| 1 | Open app → Profile tab | Profile data loads cached then refreshes from server | Screenshot |
| 2 | Edit name → Save (mobile flow) | Success toast; header updates with new name | – |
| 3 | Tap avatar → Take photo (camera) → Crop → Save | Avatar updates, thumbnail synced to server | – |
| 4 | Tap avatar → Choose from gallery → Save | Avatar updated and accessible across devices | – |
| 5 | Change phone → SMS OTP sent → Enter OTP | Phone verified and saved | – |
| 6 | Use biometric to confirm critical change (if enabled) | Bio auth passes and change applied | – |
| 7 | Request profile export → background job | App shows notification when export ready | – |
| 8 | Link social account via native SDK → success | Provider linked and tokens stored | – |

---

## 👤 Profile — ❌ Invalid Test Cases

| Step | Action | Expected Result | Attachments |
|------|--------|-----------------|-------------|
| 1 | Upload corrupted image file from gallery | Upload rejected with error | – |
| 2 | Take picture with no camera permission | App prompts for permission; guides to settings | – |
| 3 | Attempt OTP with invalid code many times | Rate-limit and block with cooldown | – |
| 4 | Edit profile offline and lose app state | Changes queued or user warned per design | – |

---

## 👤 Profile — ⚠️ Edge / Advanced

| Step | Action | Expected Result | Attachments |
|------|--------|-----------------|-------------|
| 1 | Update profile with large image (hi-res) on slow network | Progress indicator; upload resumes or fails gracefully | – |
| 2 | Multiple accounts on device → switch accounts | Selected account profile loads & cache isolation maintained | – |
| 3 | SSO login flow interrupted (app backgrounded) | SSO resumes on foreground; no partial linkage | – |

---

## ⚙️ Settings — ✅ Valid Test Cases

| Step | Action | Expected Result | Attachments |
|------|--------|-----------------|-------------|
| 1 | Open Settings → toggle push/email/SMS | Local changes persisted and synced to server | Screenshot |
| 2 | Enable biometric login in app settings → re-login works with biometrics | Biometric login enabled and usable | – |
| 3 | Configure localization (language/currency) | App strings update and currency format changes | – |

---

## ⚙️ Settings — ❌ Invalid Test Cases

| Step | Action | Expected Result | Attachments |
|------|--------|-----------------|-------------|
| 1 | Attempt to enable biometrics on unsupported device | UI informs unsupported | – |
| 2 | Toggle notification preference while offline | Changes queued and synced on reconnect | – |

---

## 🏠 Address — ✅ Valid Test Cases

| Step | Action | Expected Result | Attachments |
|------|--------|-----------------|-------------|
| 1 | Open Address Book (mobile) | Cached addresses shown, refresh fetches latest | Screenshot |
| 2 | Add address using GPS → adjust details → Save | Coordinates stored; address validated | – |
| 3 | Add address manually → Save | Address added and available in checkout | – |
| 4 | Set default shipping address | Default applied across app (checkout, quick-order) | – |
| 5 | Edit address and save | Changes show in list and used for shipping estimates | – |
| 6 | Delete address with confirmation | Address removed and UI updated | – |
| 7 | Use quick-add (from map long-press) to add address | Address created with lat/lng | – |

---

## 🏠 Address — ❌ Invalid Test Cases

| Step | Action | Expected Result | Attachments |
|------|--------|-----------------|-------------|
| 1 | Add address with missing required field on mobile form | Inline validation prevents save | – |
| 2 | Use GPS but permission denied | App prompts for permission; manual entry fallback | – |
| 3 | Attempt to set default to deleted address | Blocked with error | – |

---

## 🏠 Address — ⚠️ Edge / Advanced

| Step | Action | Expected Result | Attachments |
|------|--------|-----------------|-------------|
| 1 | Offline: add address then uninstall app before sync | On reinstall, behavior per design: queued items lost or restored via account | – |
| 2 | Add address in remote area with no carrier coverage | Saved locally and validated later | – |
| 3 | Bulk add addresses via mobile (CSV import) | Job accepted and progress visible | – |

---

## 🔒 Mobile Security & Privacy

| Step | Action | Expected Result | Attachments |
|------|--------|-----------------|-------------|
| 1 | Ensure avatar files stored in device cache are cleared on logout | No PII persist on device after logout | – |
| 2 | Attempt to access another user’s cached profile | App enforces account isolation | – |
| 3 | Biometric fallback to PIN when biometric fails | User can use fallback and still secure | – |

---

## ♿ Mobile Accessibility

| Step | Action | Expected Result | Attachments |
|------|--------|-----------------|-------------|
| 1 | Screen reader (TalkBack/VoiceOver) navigates profile form | All labels/readouts correct | – |
| 2 | High-contrast and large-text mode | Layout remains usable; elements not clipped | – |

---

## 🔗 Mobile Integration

| Step | Action | Expected Result | Attachments |
|------|--------|-----------------|-------------|
| 1 | Deep link opens profile → edit Avatar | App handles deep link and correct screen opens | – |
| 2 | Map selection returns to app with coordinates | Address form populated accurately | – |

---

## 📌 Coverage Achieved (Mobile)

- Full mobile-specific coverage: camera/gallery flows, GPS/map integration, background sync and queued changes, biometric/SSO behaviours, offline handling, accessibility, and security/privacy for local storage.
