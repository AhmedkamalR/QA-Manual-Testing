# 💻 Website – Profile & Address Module Test Cases

This document contains **Website (web UI)** test cases for Profile, Settings & Address modules.  
It covers UI flows, validations, edge behaviours, accessibility, 3rd-party integrations (maps, OAuth), and regulatory interactions.

---

## 👤 Profile — ✅ Check Valid Test Cases

| Step | Action | Expected Result | Attachments |
|------|--------|-----------------|-------------|
| 1 | Login → Click Profile | Profile page loads with name, email, phone, avatar, joined date | Screenshot |
| 2 | Edit name fields and click Save | UI shows success toast; updated shows immediately; backend persists | – |
| 3 | Change email → enters new email → Save | UI shows "verification sent" state; old email remains until verified | – |
| 4 | Click avatar → Upload file (jpg/png, <=5MB) → Crop → Save | Avatar updated on UI and in header; thumbnail created | – |
| 5 | Change phone → click “Send OTP” → enter OTP → Verify | Phone updated and marked verified | – |
| 6 | Use OAuth link ("Connect Google") → OAuth popup → Accept | Provider linked; account shows provider name | – |
| 7 | Click "Export my data" → request triggered | UI shows pending job; email/notification sent when ready | – |
| 8 | View profile on desktop and mobile breakpoints | Responsive layout correct | – |

---

## 👤 Profile — ❌ Check Invalid Test Cases

| Step | Action | Expected Result | Attachments |
|------|--------|-----------------|-------------|
| 1 | Enter invalid email and click Save | Inline validation error; field highlighted | – |
| 2 | Upload a very large avatar (>limit) | Rejection message with allowed size info | – |
| 3 | Enter invalid phone then OTP attempt | No OTP sent; validation error | – |
| 4 | Use browser autofill to put malicious strings in bio | Input sanitized before display | – |
| 5 | Attempt to change another user's profile using devtools | Server rejects; UI shows error on save | – |

---

## 👤 Profile — ⚠️ Edge / Advanced

| Step | Action | Expected Result | Attachments |
|------|--------|-----------------|-------------|
| 1 | Simultaneous edits in two tabs → save in tab A then B | Tab B warns about stale data or overwrites per policy | – |
| 2 | Use very long bio (10k chars) | Client-side truncates or displays warning; server enforces limit | – |
| 3 | Upload HEIC via browser (requires conversion) | Browser support fallback or instruct user | – |
| 4 | Change language on profile page to RTL (Arabic) | Layout flips and fields correctly align | – |

---

## 👤 Profile — 🔒 Security & Privacy

| Step | Action | Expected Result | Attachments |
|------|--------|-----------------|-------------|
| 1 | Inspect network calls on profile save to ensure no PII in query strings | All sensitive data in request body over HTTPS | – |
| 2 | Attempt XSS in displayName → save → view profile | Input sanitized; no script executed | – |
| 3 | Try CSRF attack on profile update form | CSRF token required; attack fails | – |

---

## ⚙️ Settings — ✅ Valid Test Cases

| Step | Action | Expected Result | Attachments |
|------|--------|-----------------|-------------|
| 1 | Open Settings page → view notification toggles | Current values shown and toggles are interactive | Screenshot |
| 2 | Toggle email marketing OFF → Save | UI confirms; subsequent marketing calls reflect off | – |
| 3 | Enable two-factor → follow setup flow with authenticator app | Shows QR & secret; verification success | – |
| 4 | Set preferred currency & language → Save | UI content and currency display updated across site | – |

---

## ⚙️ Settings — ❌ Invalid Test Cases

| Step | Action | Expected Result | Attachments |
|------|--------|-----------------|-------------|
| 1 | Enter unsupported locale in UI (manually) | UI reverts to default or shows error | – |
| 2 | Try to disable 2FA without verification | UI blocks and asks reauthentication | – |
| 3 | Try toggling notifications when server offline | UI shows error & queues change for retry | – |

---

## 🏠 Address — ✅ Check Valid Test Cases

| Step | Action | Expected Result | Attachments |
|------|--------|-----------------|-------------|
| 1 | Visit Address Book page | List of addresses shown with default tag | Screenshot |
| 2 | Click "Add Address" → fill form → Save | Address added to list; toast shows success | – |
| 3 | Use map autocomplete → select suggestion → Save | Address fields populated; lat/long stored | – |
| 4 | Mark address as Default → Save | Default marker updated and persists | – |
| 5 | Edit address to correct details → Save | Changes reflected in list and used by checkout | – |
| 6 | Delete address → confirm dialog → Delete | Address removed and not selectable | – |
| 7 | Import addresses via UI CSV upload → shows result | Job accepted; per-row errors displayed | – |

---

## 🏠 Address — ❌ Invalid Test Cases

| Step | Action | Expected Result | Attachments |
|------|--------|-----------------|-------------|
| 1 | Submit address with missing required fields | Inline validation errors; focus moves to first invalid input | – |
| 2 | Use invalid postal code pattern per country | Validation error | – |
| 3 | Try to delete default address while checkout pending | UI warns and requires selecting another default | – |
| 4 | Map autocomplete returning ambiguous result | UI prompts user to refine selection | – |

---

## 🏠 Address — ⚠️ Edge / Advanced

| Step | Action | Expected Result | Attachments |
|------|--------|-----------------|-------------|
| 1 | Add addresses for many countries and verify format | Each displays with correct local format | – |
| 2 | Bulk import 5k addresses via UI (upload) | Job enqueued; progress & partial errors shown | – |
| 3 | Add address in an unserviceable region | UI flags "unserviceable"; block selection in checkout | – |
| 4 | Offline add address on mobile web → reconnect | Syncs to server and shows in UI after refresh | – |

---

## 🔒 Security (Website)

| Step | Action | Expected Result | Attachments |
|------|--------|-----------------|-------------|
| 1 | Check CSRF protection for forms (profile, address) | CSRF token validated | – |
| 2 | Ensure avatar upload uses signed URLs or POST with server-side validation | Direct S3 uploads use signed URL and validation | – |
| 3 | Validate that exported profile download requires 2FA | Protected endpoint requires reauth | – |

---

## ♿ Accessibility (Website)

| Step | Action | Expected Result | Attachments |
|------|--------|-----------------|-------------|
| 1 | Tab through profile form | Logical focus order and focus visible | – |
| 2 | Screen reader reads success & error messages | Live region updates used correctly | – |
| 3 | High contrast & large font settings | Layout remains usable & controls reachable | – |

---

## 🔗 Integration & Regression

| Step | Action | Expected Result | Attachments |
|------|--------|-----------------|-------------|
| 1 | Address selected in checkout reflects UI default | Checkout preselects UI default | – |
| 2 | After profile email change & verify → newsletters use new email | Mailer subscription updated | – |
| 3 | Revoke OAuth provider in settings → provider disconnected at backend | Provider tokens revoked | – |

---

## 📌 Coverage Achieved (Web)

- UI + API contract validated across Profile, Settings & Address.  
- Full positive/negative/edge coverage, multi-locale, mapping integration, import/export, GDPR flows, accessibility & security checks.
