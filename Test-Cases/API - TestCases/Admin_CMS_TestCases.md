# 🧩 Admin CMS Module - API Test Cases

---

## 📌 Purpose
To ensure Admin CMS API endpoints handle content management securely and efficiently, validating CRUD operations, role permissions, workflow, and audit logging.

---

## ✅ Valid Test Cases

| Step | Action | Expected Result | Attachments |
|------|---------|----------------|--------------|
| 1 | Login as Admin and GET `/cms/pages` | Returns full list of CMS pages with metadata | – |
| 2 | POST `/cms/pages` with valid payload | Page created successfully with 201 response | – |
| 3 | PUT `/cms/pages/{id}` with valid data | Page updated successfully | – |
| 4 | DELETE `/cms/pages/{id}` | Page deleted and audit log entry created | – |
| 5 | PATCH `/cms/pages/{id}/status` = “Published” | Page visible in frontend immediately | – |
| 6 | GET `/cms/pages/{id}` | Returns correct content and status | – |
| 7 | Add SEO meta info fields | Saved and retrievable correctly | – |
| 8 | Add multilingual content | Returns translated content per locale | – |
| 9 | Fetch audit logs `/cms/logs` | Shows accurate user + timestamp info | – |
| 10 | Upload banner image via `/cms/upload` | Returns valid image URL | – |
| 11 | Assign role-based permission to Editor | Permission reflected in GET `/users/roles` | – |
| 12 | Search `/cms/pages?query=policy` | Returns matching results | – |
| 13 | Pagination `/cms/pages?page=2&limit=20` | Works with metadata | – |
| 14 | Sort `/cms/pages?sort=updated_at` | Sorted correctly | – |
| 15 | Validate response JSON schema | All required fields exist | – |

---

## ❌ Invalid Test Cases

| Step | Action | Expected Result | Attachments |
|------|---------|----------------|--------------|
| 1 | POST `/cms/pages` with missing title | 400 Bad Request | – |
| 2 | PUT `/cms/pages/{id}` with invalid ID | 404 Not Found | – |
| 3 | DELETE page without permission | 403 Forbidden | – |
| 4 | Upload non-image file (e.g., .exe) | 415 Unsupported Media Type | – |
| 5 | GET `/cms/pages` with expired token | 401 Unauthorized | – |
| 6 | SQL/XSS in content body | Sanitized and rejected | – |
| 7 | POST invalid JSON structure | 400 Bad Request | – |
| 8 | Publish without mandatory SEO fields | Validation error | – |
| 9 | Unauthorized role (viewer) tries POST | Access denied | – |
| 10 | PATCH invalid status (e.g., “banana”) | 422 Validation Error | – |
| 11 | Delete page with linked content | Returns dependency error | – |
| 12 | Upload image > max size | 413 Payload Too Large | – |
| 13 | Duplicate page slug | 409 Conflict | – |
| 14 | Delete system-reserved page | Forbidden | – |
| 15 | Token tampering attempt | Rejected securely | – |

---

## ⚙️ Edge / Advanced Test Cases

| Step | Action | Expected Result | Attachments |
|------|---------|----------------|--------------|
| 1 | Create 1000+ pages | API performance remains stable | – |
| 2 | Edit content from two sessions simultaneously | Last-write wins with audit log | – |
| 3 | Schedule future publish date | Auto-publish at correct time | – |
| 4 | Large HTML content (10,000 chars) | Stored without truncation | – |
| 5 | Fetch logs with date range filter | Returns correct subset | – |
| 6 | Role permission changed mid-session | New permission reflected immediately | – |
| 7 | API under high load (stress test) | Handles concurrent requests | – |
| 8 | Multi-language slug collision | Handled gracefully | – |
| 9 | Audit log retention policy expiry | Older logs archived | – |
| 10 | Network failure during publish | Retries safely or rollback applied | – |

---

## 🔒 Security & Integrity Tests

| Step | Action | Expected Result | Attachments |
|------|---------|----------------|--------------|
| 1 | Attempt to access another tenant’s CMS data | Denied with 403 | – |
| 2 | API rate-limit exceeded | 429 Too Many Requests | – |
| 3 | JWT token replay attempt | Rejected | – |
| 4 | Inject script in content | Escaped safely | – |
| 5 | Force delete via modified payload | Ignored, logged as suspicious | – |
| 6 | Audit trail tampering attempt | Immutable logs retained | – |
| 7 | CORS misconfiguration test | Allowed only valid origins | – |
| 8 | API key leak simulation | Access revoked instantly | – |
| 9 | Data export request by unauthorized user | Denied | – |
| 10 | Encryption verification for CMS uploads | Files stored encrypted | – |

---

## ⚡ Performance & UX (API-level)

| Step | Action | Expected Result | Attachments |
|------|---------|----------------|--------------|
| 1 | Load 1000 pages via pagination | Average latency < 1.5s | – |
| 2 | Concurrent edits from 50 users | API stable with no crash | – |
| 3 | Publish under high load | Job queued and executed reliably | – |
| 4 | Bulk upload images (50MB total) | System throttles correctly | – |
| 5 | Compare performance on GET cache hit vs miss | Cached responses faster | – |

---

## 📌 Coverage Achieved

- **Valid Scenarios**: CRUD, SEO, translations, audit logging, role management, pagination, scheduling.  
- **Invalid Scenarios**: auth issues, invalid payloads, dependency errors, slugs, XSS, upload violations.  
- **Edge Scenarios**: concurrency, performance stress, future scheduling, retention, rollback.  
- **Security**: JWT validation, tenant isolation, audit integrity, CORS, encryption.  
- **Performance**: pagination, caching, concurrent stability, bulk operations.  
---
