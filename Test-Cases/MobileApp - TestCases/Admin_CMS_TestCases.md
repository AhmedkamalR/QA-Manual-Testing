# 📱 Admin CMS Module - Mobile App Test Cases

---

## 📌 Purpose
To ensure mobile app Admin CMS panel (if available or via PWA view) behaves consistently with website CMS, allowing limited moderation and content updates on the go.

---

## ✅ Valid Test Cases

| Step | Action | Expected Result | Attachments |
|------|---------|----------------|--------------|
| 1 | Login as Admin | CMS dashboard loads | – |
| 2 | View list of pages | All pages visible with titles & status | – |
| 3 | Edit page title and save | Updated successfully | – |
| 4 | Change page status to Published | Reflected immediately | – |
| 5 | Upload small image from gallery | Upload successful | – |
| 6 | Check draft pages | List accurate | – |
| 7 | Add SEO tags | Saved successfully | – |
| 8 | Switch between tabs (Pages, Media, Logs) | Navigation smooth | – |
| 9 | Rotate device | Layout adjusts | – |
| 10 | Logout | Session cleared | – |

---

## ❌ Invalid Test Cases

| Step | Action | Expected Result | Attachments |
|------|---------|----------------|--------------|
| 1 | Upload file > max size | Error shown | – |
| 2 | Add empty title | Validation error | – |
| 3 | No internet on save | Retry prompt | – |
| 4 | Unauthorized editor role tries delete | Denied | – |
| 5 | Token expired | Redirect to login | – |
| 6 | Corrupted API response | Safe fallback | – |
| 7 | Try upload unsupported type | Error handled | – |
| 8 | App in offline mode | Data saved locally only | – |
| 9 | Force stop app mid-save | Data integrity preserved | – |
| 10 | Rapid publish/unpublish taps | Debounced safely | – |

---

## ⚙️ Edge / Advanced Test Cases

| Step | Action | Expected Result | Attachments |
|------|---------|----------------|--------------|
| 1 | Manage 300+ pages | App responsive | – |
| 2 | Large HTML content edit | No lag | – |
| 3 | Switch network WiFi→Data | Seamless save | – |
| 4 | Re-login after role change | Permissions updated | – |
| 5 | Offline edits synced on reconnect | Merged properly | – |
| 6 | Rotate device during edit | Layout preserved | – |
| 7 | Run app on tablet | Adaptive layout | – |
| 8 | Receive backend update push | UI refreshes | – |
| 9 | App update mid-session | No data loss | – |
| 10 | Accessibility: TalkBack reads buttons | Fully accessible | – |

---

## 📌 Coverage Achieved

- **Valid Scenarios**: view/edit/publish, image upload, tab navigation, responsive UI, SEO handling.  
- **Invalid Scenarios**: validation, network loss, permissions, token expiry, file type.  
- **Edge Scenarios**: heavy content, device rotation, offline sync, network switch, accessibility, tablet view.  

---
