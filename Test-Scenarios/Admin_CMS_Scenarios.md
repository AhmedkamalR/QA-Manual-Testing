# 🛠️ Admin & CMS – Test Scenarios

This document outlines **comprehensive test scenarios** for the **Admin Panel & CMS module** across API, Website (Admin Dashboard), and Mobile (if supported).  
It ensures coverage of valid, invalid, and edge cases for managing products, categories, users, orders, content, and system configurations.

---

## 1. API Scenarios

### ✅ Valid Scenarios
- Admin login with valid credentials.
- Fetch admin dashboard stats (sales, users, orders).
- Create new product with valid parameters.
- Update product details (name, price, stock, description).
- Delete product successfully.
- Create/edit/delete categories.
- Manage users (activate, deactivate, reset password).
- Fetch order details by valid order ID.
- Update order status (Pending → Shipped → Delivered).
- Retrieve logs/audit trail for admin actions.
- Manage CMS pages (create, update, delete).
- Upload media (image, banner) with valid format/size.
- Assign roles & permissions to users.
- Export reports (CSV, PDF).
- API pagination & filters for large datasets.

### ❌ Invalid Scenarios
- Admin login with wrong credentials.
- Login with deactivated admin account.
- Create product with missing required fields.
- Update product with invalid price (negative).
- Upload invalid file type for product image.
- Upload image exceeding size limit.
- Delete product linked to active order (restricted).
- Update order with invalid status.
- Unauthorized API call without admin token.
- Role assignment with invalid role ID.
- API request with malformed JSON body.
- CMS page creation with missing title/content.
- Access resource with insufficient permissions.
- Exceeding API rate limits.

### ⚠️ Edge Scenarios
- Bulk create/update (1000+ products at once).
- Concurrent admin updates on same product.
- Very long product name/description.
- Multi-language content (EN/AR).
- Orders with 100+ items.
- Admin session timeout during update.
- Undo/rollback actions (if supported).
- Schedule product publish/unpublish.
- Exporting reports for 1M+ records.
- High load API stress test.

---

## 2. Website (Admin Dashboard) Scenarios

### ✅ Valid Scenarios
- Admin login with correct credentials.
- Dashboard loads stats correctly.
- Add new product from UI.
- Update product info & save successfully.
- Delete inactive product.
- Manage categories (add/edit/delete).
- Manage banners & CMS pages.
- Search & filter in product list.
- Approve/reject customer reviews.
- Manage discounts/coupons.
- Update stock & pricing.
- Manage orders from UI (view, update status).
- Manage users (block/unblock).
- Logout redirects to login page.
- Multi-admin session works as expected.

### ❌ Invalid Scenarios
- Login with invalid credentials.
- Login with empty username/password.
- Access dashboard without login (redirect to login).
- Broken images in CMS banners.
- Form submission with invalid/empty fields.
- Incorrect error messages on failed actions.
- Uploading corrupted media files.
- Product deletion error not handled.
- Unauthorized access to restricted modules.
- Permission-restricted user accessing super-admin features.
- Broken pagination in product list.

### ⚠️ Edge Scenarios
- Dashboard with 10,000+ products (performance).
- Search with special characters in admin filters.
- Upload banner with very large dimensions.
- Multi-language toggle (EN/AR).
- Editing product while another admin edits same.
- Multiple tabs open with same admin session.
- Notifications flooding dashboard.
- Orders with special payment methods.
- Accessibility: Admin panel usable with screen readers.

---

## 3. Mobile App (If Admin Mobile App Exists)

### ✅ Valid Scenarios
- Admin login from mobile app.
- View dashboard stats.
- Approve/reject orders.
- Update stock for product.
- Add/edit/delete categories.
- Push notification for new order.
- Manage CMS content (if supported).
- Role-based access works correctly.

### ❌ Invalid Scenarios
- Invalid login on mobile app.
- Upload media with unsupported format.
- No internet connection while updating product.
- Unauthorized role trying to access restricted section.
- Corrupted data sync with backend.

### ⚠️ Edge Scenarios
- Very large data sync (products/orders).
- Offline mode (changes queued for sync).
- Mobile app force-closed during update.
- Admin updates product while web admin does too.
- High-frequency push notifications.
- Large banner upload on mobile.

---

## ✅ Key Values / Keywords
- **Entities:** Admin, Product, Category, Order, User, CMS Page, Banner, Role, Permission.  
- **Parameters:** admin_id, product_id, category_id, order_id, role_id, media_id.  
- **States:** Active, Inactive, Draft, Published, Scheduled, Deleted, Blocked.  
- **Edge:** Bulk operations, Multi-language, Concurrency, Large data, High load.  

---
