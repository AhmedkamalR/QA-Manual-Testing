# 🔌 API – Profile & Address Module Test Cases

This document contains comprehensive **API test cases** for the **Profile, Settings & Address** modules.  
Covers CRUD, validation, security, sync, integrations, performance, accessibility-related API behaviour, data export/deletion, and regulatory flows.

---

## 👤 Profile — ✅ Valid Test Cases

| Step | Action | Expected Result | Attachments |
|------|--------|-----------------|-------------|
| 1 | GET `/user/profile` with valid auth token | 200 OK with canonical JSON (id, name, email, phone, avatarUrl, dob, language, timezone, privacyFlags) | – |
| 2 | PATCH `/user/profile` with valid fields (firstName, lastName, displayName) | 200 OK; response shows updated fields | – |
| 3 | PATCH `/user/profile` to change email → triggers verification email | 202 Accepted; pending_email field set; verification-email job queued | – |
| 4 | POST `/user/profile/verify-email` with valid token | 200 OK; email_verified = true | – |
| 5 | PATCH `/user/profile` to change phone → triggers OTP via `/user/otp/send` | 202 Accepted; OTP delivery logged | – |
| 6 | POST `/user/profile/avatar` multipart/form-data (jpg, <5MB) | 201 Created; returns avatarUrl and thumbnailUrl | – |
| 7 | POST `/user/change-password` with valid old & strong new password | 200 OK; returns success and invalidates other sessions per policy | – |
| 8 | GET `/user/activity` (with auth) | 200 OK; returns recent profile & security events | – |
| 9 | GET `/user/profile/export` (GDPR export) | 202 Accepted; job id returned; GET `/user/profile/export/{id}` returns file | – |
| 10 | POST `/user/link-provider` for OAuth provider (valid token) | 200 OK; provider linked (providerId stored) | – |

---

## 👤 Profile — ❌ Invalid Test Cases

| Step | Action | Expected Result | Attachments |
|------|--------|-----------------|-------------|
| 1 | GET `/user/profile` with missing/expired token | 401 Unauthorized | – |
| 2 | PATCH `/user/profile` with invalid email format | 400 Bad Request + validation message | – |
| 3 | POST `/user/profile/avatar` with unsupported MIME (exe) | 415 Unsupported Media Type | – |
| 4 | POST `/user/profile/avatar` with > max size | 413 Payload Too Large | – |
| 5 | POST `/user/change-password` with wrong current password | 403 Forbidden | – |
| 6 | PATCH `/user/profile` with missing required fields (if required) | 400/422 Validation error | – |
| 7 | POST `/user/link-provider` where token belongs to another user | 409 Conflict or 403 Forbidden per policy | – |

---

## 👤 Profile — ⚠️ Edge & Advanced Test Cases

| Step | Action | Expected Result | Attachments |
|------|--------|-----------------|-------------|
| 1 | PATCH `/user/profile` concurrently from two devices with different name values | API supports versioning/ETag or last-write-wins; no DB corruption | – |
| 2 | PATCH with extremely long strings in name/bio (> DB limit) | 413 or 422; safe truncation or explicit validation | – |
| 3 | Submit profile fields containing emoji, RTL characters, multibyte Unicode | Stored and returned intact (UTF-8) | – |
| 4 | Reuse expired email verification token | 410 Gone with reissue option | – |
| 5 | Upload HEIC image file (iOS) | Either accepted/converted or rejected with clear message | – |
| 6 | Simulate high-latency upstream storage (avatar upload slow) | API uses async processing and returns 202 Accepted with job id | – |

---

## 👤 Profile — 🔒 Security & Integrity Tests

| Step | Action | Expected Result | Attachments |
|------|--------|-----------------|-------------|
| 1 | Attempt PATCH `/user/profile` using another user's JWT | 403 Forbidden | – |
| 2 | Attempt to set `email_verified=true` via PATCH | Server ignores client-controlled verification flags; server-side verification required | – |
| 3 | Inject SQL/XSS in profile fields (bio/website/name) | Inputs sanitized; stored safely; response escaped | – |
| 4 | Brute force OTP / email token endpoints | Rate-limiting returns 429 and logging/alerting triggered | – |
| 5 | Verify audit trail exists for critical changes (email, phone, password) | 200 ok; audit entries created | – |

---

## 👤 Profile — ⚡ Performance / Load Tests

| Step | Action | Expected Result | Attachments |
|------|--------|-----------------|-------------|
| 1 | 500 concurrent GET `/user/profile` requests | Responses within SLA (e.g., 200ms median) | – |
| 2 | 1000 avatar upload attempts/minute in QA | System queues, storage scales; no data loss | – |
| 3 | Profile export job heavy load (many fields) | Job runs async; progress endpoints provided | – |

---

## ⚙️ Settings — ✅ Valid Test Cases

| Step | Action | Expected Result | Attachments |
|------|--------|-----------------|-------------|
| 1 | GET `/user/settings` | 200 OK with notification, language, currency, timezone, privacy settings | – |
| 2 | PUT `/user/settings` to change language | 200 OK; subsequent localized endpoints reflect language | – |
| 3 | PUT `/user/settings` to toggle push/email/SMS notifications | 200 OK; preferences persist and affect notification dispatch | – |
| 4 | PUT `/user/settings` to update timezone | 200 OK; timestamps in subsequent order responses adjusted | – |
| 5 | POST `/user/2fa/setup` (authenticator) | 200 OK; returns secret/QR; POST `/user/2fa/confirm` verifies | – |

---

## ⚙️ Settings — ❌ Invalid Test Cases

| Step | Action | Expected Result | Attachments |
|------|--------|-----------------|-------------|
| 1 | PUT `/user/settings` with unsupported language code | 400 Bad Request | – |
| 2 | PUT `/user/settings` without auth | 401 Unauthorized | – |
| 3 | POST `/user/2fa/setup` and then confirm with wrong code | 422 Invalid 2FA Code | – |
| 4 | PUT `/user/settings` with invalid timezone format | 400 Validation Error | – |

---

## ⚙️ Settings — ⚠️ Edge Tests

| Step | Action | Expected Result | Attachments |
|------|--------|-----------------|-------------|
| 1 | Toggle many settings rapidly (50 changes) | System persists latest state; rate-limit safeguards if needed | – |
| 2 | Enable 2FA then attempt recovery codes multiple times | Recovery codes work once then invalidated | – |
| 3 | Change preferred currency while orders in cart | Prices re-calculated consistently; no rounding mismatch | – |

---

## ⚙️ Settings — 🔒 Security Tests

| Step | Action | Expected Result | Attachments |
|------|--------|-----------------|-------------|
| 1 | Attempt to POST `/user/2fa/disable` without reauthentication | 403 Forbidden or require password | – |
| 2 | Attempt to change notification webhook URL to external malicious domain | Validation blocks or warns admin | – |

---

## 🏠 Address — ✅ Valid Test Cases

| Step | Action | Expected Result | Attachments |
|------|--------|-----------------|-------------|
| 1 | GET `/user/addresses` with auth | 200 OK list with ids, nicknames, type (shipping/billing), coordinates | – |
| 2 | POST `/user/addresses` with valid international address payload | 201 Created with addressId | – |
| 3 | PUT `/user/addresses/{id}` to edit street/zip | 200 OK; updated returned | – |
| 4 | DELETE `/user/addresses/{id}` (owned address) | 204 No Content; subsequent GET does not include it | – |
| 5 | PUT `/user/addresses/{id}/default` to set default shipping | 200 OK; subsequent order APIs show this as default | – |
| 6 | GET `/user/addresses?type=billing` | 200 OK filtered list | – |
| 7 | POST `/user/addresses/validate` calls geocoding service | 200 OK with {valid:true/false, suggestions:[]} | – |
| 8 | POST `/user/addresses/import` CSV with valid rows | 202 Accepted, job id returned; errors per-row reported | – |
| 9 | GET `/orders/{id}` returns snapshot of address used at order time | 200 OK; historical address preserved | – |

---

## 🏠 Address — ❌ Invalid Test Cases

| Step | Action | Expected Result | Attachments |
|------|--------|-----------------|-------------|
| 1 | POST `/user/addresses` with missing country or city | 400 Bad Request | – |
| 2 | POST `/user/addresses` with invalid postal pattern for country | 422 Validation Error | – |
| 3 | DELETE `/user/addresses/{id}` not owned | 403 Forbidden | – |
| 4 | PUT `/user/addresses/{id}` with invalid id | 404 Not Found | – |
| 5 | POST `/user/addresses/import` with malformed CSV | 400/422 with row-level errors | – |

---

## 🏠 Address — ⚠️ Edge & Advanced

| Step | Action | Expected Result | Attachments |
|------|--------|-----------------|-------------|
| 1 | Create 1000 addresses via API for single user (bulk) | System accepts or throttles; import job returns progress | – |
| 2 | Set default address while a pending order is being placed | System does not corrupt order; transactional integrity maintained | – |
| 3 | Address validation service down | API returns fallback (store raw input) and queues validation | – |
| 4 | Two devices try to update the same address concurrently | Proper locking/versioning prevents lost updates | – |

---

## 🏠 Address — 🔒 Security & Fraud checks

| Step | Action | Expected Result | Attachments |
|------|--------|-----------------|-------------|
| 1 | Attempt to create address with script tags | Sanitized and rejected as needed | – |
| 2 | Attempt address creation for another user by changing userId field in payload | 403 Forbidden | – |
| 3 | Rate-limit address create/import to prevent abuse | 429 Too Many Requests after threshold | – |
| 4 | Check audit logs for address changes with user & timestamp | Audit entries exist | – |

---

## 🔗 Integration & Contract Tests

| Step | Action | Expected Result | Attachments |
|------|--------|-----------------|-------------|
| 1 | Validate /user/addresses payload contract with frontend schema | Contract tests pass | – |
| 2 | Verify address used by shipping API (POST /shipping/estimate) | Correct rates returned for address | – |
| 3 | Verify export endpoints return data in correct GDPR export format | Export success | – |

---

## 🧪 Data & Regulatory Tests

| Step | Action | Expected Result | Attachments |
|------|--------|-----------------|-------------|
| 1 | Request account data export includes addresses and settings | Export file contains profile, addresses, consent history | – |
| 2 | Request account deletion triggers anonymization/purging per retention policy | Personal data removed; invoices preserved as anonymized records | – |
| 3 | Check consent logs for marketing toggles | Timestamps and origin recorded | – |

---

## ⚡ Performance & SLA Tests

| Step | Action | Expected Result | Attachments |
|------|--------|-----------------|-------------|
| 1 | 1000 GET `/user/profile` /sec | System remains stable; response times within SLA | – |
| 2 | Bulk import of 10k addresses as a job | Job completes or enqueues with progress API; no DB corruption | – |
| 3 | Avatar upload latency under load | Storage and CDN behave; thumbnails generated within expected time | – |

---

## ♿ Accessibility / API Observability

| Step | Action | Expected Result | Attachments |
|------|--------|-----------------|-------------|
| 1 | APIs return clear 4xx messages suitable for UI consumption (consistent codes/messages) | UI can announce errors via screen reader | – |
| 2 | Export job status endpoints accessible and return progress | 200 and informative payload | – |

---

## 📌 Coverage Achieved

- Full API coverage for Profile CRUD, avatar upload, email/phone verification, password change and security flows.  
- Settings: notification, 2FA, language/timezone, currency.  
- Address: full CRUD, validation, mapping/geocoding integration, bulk import/export, default selection, historical snapshot for orders.  
- Security: auth enforcement, injection sanitization, rate-limiting, audit trail.  
- Performance: load & bulk job behaviour, async jobs, SLA expectations.  
- Data & Regulatory: GDPR export/deletion, consent logging, anonymization rules.
