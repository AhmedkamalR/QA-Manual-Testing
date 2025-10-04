# 🌐 Wishlist Module - Website Test Cases

---

## 📌 Purpose
To verify wishlist functionality on the website, ensuring smooth user interaction, synchronization with backend APIs, and proper state management across sessions.

---

## ✅ Wishlist - Valid Test Cases

| Step | Action | Expected Result | Attachments |
|------|---------|----------------|--------------|
| 1 | Login and navigate to product page | Wishlist icon visible |  |
| 2 | Click wishlist (heart) icon | Item added to wishlist instantly |  |
| 3 | Refresh page | Item remains in wishlist |  |
| 4 | Open Wishlist page | Shows all added products |  |
| 5 | Remove item | Removed immediately from UI and API |  |
| 6 | Add multiple items from different categories | All shown correctly |  |
| 7 | Click wishlist item | Redirects to product detail page |  |
| 8 | Add same item again | Tooltip “Already added” shown |  |
| 9 | Logout and login again | Wishlist persists |  |
| 10 | Check wishlist count in header | Reflects accurate number |  |

---

## ❌ Wishlist - Invalid Test Cases

| Step | Action | Expected Result | Attachments |
|------|---------|----------------|--------------|
| 1 | Add item while logged out | Redirect to login |  |
| 2 | Network disconnected | Show “Failed to add” message |  |
| 3 | API error (500) on add | UI displays fallback error |  |
| 4 | Wishlist item deleted in backend | Displays “Item no longer available” |  |
| 5 | Corrupted product ID from URL | Show safe error message |  |
| 6 | XSS in product title | Escaped properly |  |
| 7 | Session timeout mid-action | Auto logout |  |
| 8 | Delete item with slow network | Spinner + retry |  |
| 9 | Multiple tabs modifying wishlist | Syncs correctly |  |
| 10 | Browser cache cleared | Wishlist fetched again correctly |  |

---

## ⚙️ Wishlist - Edge Test Cases

| Step | Action | Expected Result | Attachments |
|------|---------|----------------|--------------|
| 1 | Add 100+ items | UI scrolls and paginates smoothly |  |
| 2 | Item name with 200+ characters | Truncated correctly |  |
| 3 | Add and remove rapidly | UI stays consistent |  |
| 4 | Add item in dark mode | Icon color contrast correct |  |
| 5 | Switch language | Wishlist items translate dynamically |  |
| 6 | Browser zoom 200% | Layout responsive |  |
| 7 | Wishlist while in incognito mode | Session handled properly |  |
| 8 | Offline mode then reconnect | Auto-syncs wishlist |  |
| 9 | Cross-device session (web + mobile) | Syncs perfectly |  |
| 10 | Page reload during API call | State maintained |  |

---

## 📌 Coverage Achieved

- **Valid Scenarios**: Add/remove/view persistence, UI-API sync, multi-category support, proper redirection.  
- **Invalid Scenarios**: Session/auth issues, API errors, missing product, network instability, cross-tab behavior.  
- **Edge Scenarios**: Stress (100+ items), UI responsiveness, multi-language, accessibility, dark mode, incognito sync.  

---
