# 🧩 Notifications Module - API Test Cases

---

## 📌 Purpose
To ensure the notifications API endpoints function correctly across all types of notifications — order updates, promotional messages, reminders, and system alerts — with proper authentication, data consistency, and response handling.

---

## ✅ Notifications - Valid Test Cases

| Step | Action | Expected Result | Attachments |
|------|---------|----------------|--------------|
| 1 | Send GET request to `/notifications` with valid user token | Returns 200 OK with full list of notifications |  |
| 2 | Send POST request to `/notifications/mark-read` with valid IDs | Notifications are marked as read successfully |  |
| 3 | Send DELETE request to `/notifications/{id}` | Returns success message and removes notification |  |
| 4 | Trigger new order event | API sends push notification payload correctly |  |
| 5 | Fetch notifications with pagination (`?page=2&limit=10`) | Correct items returned with valid pagination metadata |  |
| 6 | Fetch only unread notifications (`?status=unread`) | Only unread items are returned |  |
| 7 | Fetch notifications filtered by type (`?type=promotion`) | Only promotional notifications returned |  |
| 8 | Validate push notification payload format | Payload follows schema (title, message, type, timestamp) |  |
| 9 | Fetch notification by ID | Returns correct data for that notification |  |
| 10 | Verify response time under 1 second | Meets performance criteria |  |

---

## ❌ Notifications - Invalid Test Cases

| Step | Action | Expected Result | Attachments |
|------|---------|----------------|--------------|
| 1 | Fetch notifications without authentication token | 401 Unauthorized |  |
| 2 | Use expired/invalid token | 403 Forbidden |  |
| 3 | Fetch notification with invalid ID (`/notifications/abc`) | 400 Bad Request |  |
| 4 | Delete notification with non-existing ID | 404 Not Found |  |
| 5 | Mark notification as read with empty payload | 400 Error |  |
| 6 | Invalid query params (`?limit=-1`) | Validation error returned |  |
| 7 | API returns empty array when user has no notifications | 200 OK, empty list |  |
| 8 | Unauthorized attempt to delete another user's notification | 403 Forbidden |  |
| 9 | Trigger event for deactivated user | No notification sent |  |
| 10 | Backend timeout due to high load | Returns proper 504 Gateway Timeout |  |

---

## ⚙️ Notifications - Edge Test Cases

| Step | Action | Expected Result | Attachments |
|------|---------|----------------|--------------|
| 1 | Send 1000 notifications to same user | API handles without crashing |  |
| 2 | Very large notification body (>1MB) | API truncates or rejects with validation error |  |
| 3 | Notification title with emojis or special characters | Handled and displayed correctly |  |
| 4 | Network interruption mid-request | Retry mechanism ensures safe delivery |  |
| 5 | Concurrency test: mark-read from multiple devices | Consistent status in DB |  |
| 6 | Push notification arrives while app offline | Stored and delivered when online |  |
| 7 | Verify timezone consistency in timestamps | UTC or server timezone maintained |  |
| 8 | Test notification expiry (auto-deletion after X days) | Notification removed as expected |  |
| 9 | SQL/XSS injection attempts in message body | Input sanitized, no execution |  |
| 10 | Send payload with missing required fields | Schema validation error |  |

---

## 📌 Coverage Achieved

- **Valid Scenarios**: Fetch all, filter, pagination, mark as read, delete, event-based push, payload schema, performance validation.  
- **Invalid Scenarios**: Missing/invalid tokens, invalid IDs, empty requests, unauthorized access, no data state, invalid parameters, timeout handling.  
- **Edge Scenarios**: High volume, large payloads, concurrency, offline delivery, timestamp validation, injection security, expiry tests, emoji handling.  

---
