# 🌐 Admin CMS Module - Website Test Cases

---

## 📌 Purpose
To verify Admin CMS dashboard UI and content management flows: create/edit/publish pages, manage media, user roles, and ensure proper permissions & sync with API.

---

## ✅ Valid Test Cases

| Step | Action | Expected Result | Attachments |
|------|---------|----------------|--------------|
| 1 | Login as Admin | Dashboard loads successfully | Screenshot |
| 2 | Open “Pages” tab | List of pages displayed | – |
| 3 | Click “Add New Page” | Form opens with required fields | – |
| 4 | Fill title, body, slug, and SEO fields | Validations passed | – |
| 5 | Save page as draft | Appears in Draft tab | – |
| 6 | Click “Publish” | Page visible on frontend | – |
| 7 | Upload banner image | Preview visible | – |
| 8 | Edit page and save changes | Updates reflected instantly | – |
| 9 | Assign Editor to a page | Permission restricted correctly | – |
| 10 | Use WYSIWYG editor formatting | Bold/links/images applied correctly | – |
| 11 | Check autosave on edit | Changes retained on refresh | – |
| 12 | Verify mobile preview mode | Renders properly | – |
| 13 | View revision history | Previous versions listed | – |
| 14 | Restore previous version | Restored successfully | – |
| 15 | Logout | Session invalidated | – |

---

## ❌ Invalid Test Cases

| Step | Action | Expected Result | Attachments |
|------|---------|----------------|--------------|
| 1 | Try adding page without title | Error: “Title required” | – |
| 2 | Upload unsupported file type | Warning shown | – |
| 3 | Publish page missing body | Validation error | – |
| 4 | Edit system page without permission | Access denied | – |
| 5 | Session expires mid-edit | Redirect to login | – |
| 6 | Slow internet while saving | Loading + retry | – |
| 7 | XSS in title field | Escaped output | – |
| 8 | Upload large image > 10MB | Rejected | – |
| 9 | Duplicate slug creation | Shown as error | – |
| 10 | Browser cache corruption | Reloads fresh data | – |
| 11 | Unauthorized user opens Admin URL | Redirect to login | – |
| 12 | Open multiple edit tabs | Latest save prevails | – |

---

## ⚙️ Edge / Advanced Test Cases

| Step | Action | Expected Result | Attachments |
|------|---------|----------------|--------------|
| 1 | Create 200+ CMS pages | UI remains performant | – |
| 2 | Dark mode toggle | All CMS panels readable | – |
| 3 | Drag-drop image inside editor | Saved correctly | – |
| 4 | Edit large HTML (10,000 chars) | Editor responsive | – |
| 5 | Schedule post with future date | Publishes automatically | – |
| 6 | Filter by status = Draft | Works accurately | – |
| 7 | Switch language | CMS labels translated | – |
| 8 | Keyboard shortcuts in editor | Functional | – |
| 9 | CMS under multiple admin edits | Locking mechanism works | – |
| 10 | Browser crash mid-edit | Autosave recovers | – |

---

## 📌 Coverage Achieved

- **Valid Scenarios**: CRUD UI, permissions, drafts, revisions, uploads, SEO, autosave.  
- **Invalid Scenarios**: missing data, permissions, session timeout, duplication, file size/type.  
- **Edge Scenarios**: multi-admin concurrency, heavy content, multi-language, autosave recovery, dark mode.  

---
