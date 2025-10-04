# 🌐 Notifications Module - Website Test Cases

---

## 📌 Purpose
To validate the website’s notification system (UI and backend integration) for all notification types including real-time order updates, marketing alerts, and user messages.

---

## ✅ Valid Test Cases

| Step | Action | Expected Result | Attachments |
|------|---------|----------------|--------------|
| 1 | Login and open notifications dropdown | Latest notifications visible |  |
| 2 | Click “Mark all as read” | All items marked read instantly |  |
| 3 | Click a notification | Redirects to relevant page (order, promo, etc.) |  |
| 4 | New notification arrives in real time (WebSocket) | Appears without refresh |  |
| 5 | Scroll in notification panel | Lazy load more data |  |
| 6 | Filter unread only | Shows unread ones |  |
| 7 | Refresh page | Notifications persist with correct read/unread state |  |
| 8 | Clear all notifications | Panel empty, confirmation message shown |  |
| 9 | Hover over unread notification | Highlighted visually |  |
| 10 | Receive system-level banner notification | Displayed correctly and dismissible |  |

---

## ❌ Invalid Test Cases

| Step | Action | Expected Result | Attachments |
|------|---------|----------------|--------------|
| 1 | Open notification dropdown while logged out | Redirect to login |  |
| 2 | Network disconnected while fetching | Show retry option |  |
| 3 | Click on deleted notification link | Error message “Notification not found” |  |
| 4 | Load panel when API returns 500 | Graceful fallback UI |  |
| 5 | Unauthorized access to another user’s notifications | Access denied |  |
| 6 | Inject HTML/JS in notification message | Sanitized, no script execution |  |
| 7 | Invalid timestamp format in notification | Display “Invalid date” handled gracefully |  |
| 8 | Multiple browser tabs receive same notification | Consistent display |  |
| 9 | Clear all then refresh page | Still empty (cache cleared) |  |
| 10 | Session timeout before fetching | Auto-logout message |  |

---

## ⚙️ Edge Test Cases

| Step | Action | Expected Result | Attachments |
|------|---------|----------------|--------------|
| 1 | Receive 200+ notifications | Scroll performance maintained |  |
| 2 | Notification with long message (300+ chars) | Text truncated properly |  |
| 3 | Special characters and emojis | Display correctly in all browsers |  |
| 4 | Browser notifications permission blocked | Graceful fallback |  |
| 5 | Notification while in incognito mode | Not stored permanently |  |
| 6 | Switch theme (light/dark) | Notifications adapt theme |  |
| 7 | Resize screen | Responsive design maintained |  |
| 8 | Very slow network | Spinner/loading indicator shown |  |
| 9 | Browser crash recovery | State restored after reload |  |
| 10 | Concurrent logout/login | Notifications updated for correct user |  |

---

## 📌 Coverage Achieved

- **Valid Scenarios**: Real-time alerts, mark-read, lazy loading, filters, redirect validation, persistence, UI feedback.  
- **Invalid Scenarios**: Unauthenticated access, API failures, XSS/HTML injection, missing data, cross-session inconsistencies.  
- **Edge Scenarios**: Large volumes, long text, emoji rendering, theme handling, performance under load, responsiveness, network delay.  

---
