# 📱 Wishlist Module - Mobile App Test Cases

---

## 📌 Purpose
To ensure mobile app wishlist (in-app and API-linked) works reliably, syncing with backend, supporting offline mode, and maintaining proper UI/UX consistency.

---

## ✅ Wishlist - Valid Test Cases

| Step | Action | Expected Result | Attachments |
|------|---------|----------------|--------------|
| 1 | Login and open product | Wishlist heart icon visible |  |
| 2 | Tap wishlist icon | Product added instantly |  |
| 3 | Pull to refresh wishlist screen | Updated product list visible |  |
| 4 | Add multiple products | All items appear correctly |  |
| 5 | Remove one item | Instantly removed |  |
| 6 | Navigate to Wishlist tab | Displays all items with images |  |
| 7 | Offline add (local cache) | Synced when back online |  |
| 8 | Tap wishlist item | Opens product detail |  |
| 9 | Switch to dark mode | Wishlist adapts theme |  |
| 10 | Logout and login again | Wishlist restored |  |

---

## ❌ Wishlist - Invalid Test Cases

| Step | Action | Expected Result | Attachments |
|------|---------|----------------|--------------|
| 1 | Add item while not logged in | Prompt to login |  |
| 2 | Backend API timeout | Show “Try again later” |  |
| 3 | Corrupted payload from server | App handles gracefully |  |
| 4 | Remove item not in wishlist | Safe error shown |  |
| 5 | API returns invalid response | Default empty list |  |
| 6 | App update during action | Action retried safely |  |
| 7 | Add/remove rapidly (stress) | No app crash |  |
| 8 | Network switch WiFi → mobile data | Sync continues |  |
| 9 | User disabled internet | Show retry message |  |
| 10 | Cached data mismatch | Reloads from API |  |

---

## ⚙️ Wishlist - Edge Test Cases

| Step | Action | Expected Result | Attachments |
|------|---------|----------------|--------------|
| 1 | Add 300+ products | Smooth scroll performance |  |
| 2 | Add product with long name or emojis | Renders properly |  |
| 3 | Use app on tablet layout | Responsive UI |  |
| 4 | Rotate device (landscape) | Layout adjusts correctly |  |
| 5 | Receive backend sync during use | Updates silently |  |
| 6 | Dark mode & accessibility text size | Supported fully |  |
| 7 | Low battery mode | Sync defers until active |  |
| 8 | Offline for 24h then reconnect | Sync resumes cleanly |  |
| 9 | Concurrent add/remove from different devices | State consistent |  |
| 10 | User clears cache manually | Reloads from API |  |

---

## 📌 Coverage Achieved

- **Valid Scenarios**: Add/remove, offline cache sync, theme, cross-login persistence, navigation flow.  
- **Invalid Scenarios**: Network issues, invalid data, API timeout, cache mismatch, rapid interactions.  
- **Edge Scenarios**: Stress with 300+ items, emojis, multi-device sync, rotation, battery saver, large accessibility fonts.  

---
