# 🔄 Regression Bug Reports  

This file contains **regression bugs** detected after code changes, deployments, or new feature releases.  
Regression bugs highlight **previously working features that broke unexpectedly**.  

---

## 🐞 Bug #1 – Checkout Button Unresponsive After Promo Code Update  
- **Type:** Frontend / Web  
- **Title:** Checkout button not clickable after applying promo code.  
- **Steps:**  
  1. Add item to cart.  
  2. Apply valid promo code.  
  3. Try to proceed to checkout.  
- **Expected:** User should proceed to checkout.  
- **Actual:** Checkout button becomes unresponsive.  
- **Attachments:** Screen recording.  

---

## 🐞 Bug #2 – Search with Arabic Characters Not Returning Results  
- **Type:** Backend + Web  
- **Title:** Arabic search stopped working after last API update.  
- **Steps:**  
  1. Open search bar.  
  2. Type "كتاب" (book).  
- **Expected:** Matching results should appear.  
- **Actual:** No results returned.  
- **Attachments:** API response log.  

---

## 🐞 Bug #3 – Saved Addresses Not Displayed on Checkout  
- **Type:** Backend / Web + Mobile  
- **Title:** Existing addresses not visible at checkout after deployment.  
- **Steps:**  
  1. Log in with user having saved addresses.  
  2. Proceed to checkout.  
- **Expected:** Saved addresses should be listed.  
- **Actual:** Only "Add new address" option available until page refresh.  
- **Attachments:** Screenshots before & after refresh.  

---

## 🐞 Bug #4 – Wishlist Items Disappear After Logout/Login  
- **Type:** Backend + Web  
- **Title:** Wishlist cleared after re-login (was working before).  
- **Steps:**  
  1. Add product to wishlist.  
  2. Logout and login again.  
- **Expected:** Wishlist items should persist.  
- **Actual:** Wishlist appears empty.  
- **Attachments:** Screen recording.  

---

## 🐞 Bug #5 – Product Filtering by Brand Not Working (Mobile)  
- **Type:** Frontend / Mobile App  
- **Title:** Brand filter returns empty list after new build.  
- **Steps:**  
  1. Open mobile app.  
  2. Go to category page.  
  3. Select filter by brand.  
- **Expected:** Products from selected brand should appear.  
- **Actual:** Empty results shown.  
- **Attachments:** Mobile screenshots.  

---

## 🎯 Summary  
- Checkout/Order bugs: **2**  
- Search/Filter issues: **2**  
- Wishlist/Addresses: **2**  

Total: **6 Regression bugs documented**  
