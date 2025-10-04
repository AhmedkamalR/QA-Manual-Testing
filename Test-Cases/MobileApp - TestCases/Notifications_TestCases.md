# 📱 Notifications Module - Mobile App Test Cases

---

## 📌 Purpose
To verify mobile app notifications — both in-app and push — for accuracy, timeliness, UI consistency, and user control (mute, clear, read/unread states).

---

## ✅ Valid Test Cases

| Step | Action | Expected Result | Attachments |
|------|---------|----------------|--------------|
| 1 | Login and receive order update push | Notification received instantly |  |
| 2 | Tap push notification | Redirects to target screen |  |
| 3 | Open in-app notification center | Shows all notifications |  |
| 4 | Swipe to delete notification | Removed from list |  |
| 5 | Pull to refresh | Fetches latest notifications |  |
| 6 | Mark all as read | Changes icon indicator |  |
| 7 | Open app from background | Syncs new notifications |  |
| 8 | Receive notification while app is closed | Push appears with correct icon & sound |  |
| 9 | Enable/disable notification toggle in settings | Works correctly |  |
| 10 | Multi-language message | Displays correctly |  |

---

## ❌ Invalid Test Cases

| Step | Action | Expected Result | Attachments |
|------|---------|----------------|--------------|
| 1 | App closed + notifications disabled | No push received |  |
| 2 | Token expired | Push not delivered |  |
| 3 | Corrupted payload from API | Ignored gracefully |  |
| 4 | Empty message body | Skipped display |  |
| 5 | Invalid JSON structure | Logged and not shown |  |
| 6 | User blocked notifications at OS level | No push; in-app still visible |  |
| 7 | Notification tapped with no deep link | Opens app home safely |  |
| 8 | Notification sound missing | Default sound plays |  |
| 9 | Logout and login new user | Old notifications cleared |  |
| 10 | App update mid-notification delivery | Handled without crash |  |

---

## ⚙️ Edge Test Cases

| Step | Action | Expected Result | Attachments |
|------|---------|----------------|--------------|
| 1 | 500+ notifications loaded | App stable, scroll smooth |  |
| 2 | Notification with large image | Compressed properly |  |
| 3 | Poor network connection | Notification sync retried |  |
| 4 | Push received during video playback | Shown silently |  |
| 5 | Offline mode | In-app sync deferred |  |
| 6 | Battery saver mode | Still receives silent pushes |  |
| 7 | Dark mode enabled | Notifications adapt theme |  |
| 8 | OS-level “Do Not Disturb” active | Respect system setting |  |
| 9 | Reinstall app | No old notifications shown |  |
| 10 | Push from multiple devices same user | All synced correctly |  |

---

## 📌 Coverage Achieved

- **Valid Scenarios**: In-app and push handling, multi-language, read/delete, settings toggles, background sync, UI consistency.  
- **Invalid Scenarios**: Disabled pushes, corrupted payloads, token expiry, missing data, app state conflicts, bad structure.  
- **Edge Scenarios**: High load, large media, poor network, DND, reinstall, theme responsiveness, multi-device sync, battery saver behavior.  

---
