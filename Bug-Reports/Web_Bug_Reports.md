# 🌐 Web Bug Reports

This file contains **documented bugs** found during testing the Web application.  
Each bug is reported in a **consistent format** for clarity and easy tracking.

---

## 🐞 Bug #1 – Search with Arabic Characters Not Working
- **Type:** Frontend / Search  
- **Title:** Search with Arabic characters does not return results in all tabs.  
- **Steps:**  
  1. Navigate to the web application.  
  2. Go to the search bar.  
  3. Enter an Arabic word (e.g., "أدوية").  
  4. Check search results in all tabs (Products, Categories, Brands).  
- **Expected:** Results should display matching items in all tabs.  
- **Actual:** No results are displayed when searching with Arabic characters.  
- **Attachments:** Screenshot of empty results page.  

---

## 🐞 Bug #2 – Address Not Displaying in Checkout
- **Type:** Frontend / Checkout  
- **Title:** Address not shown in checkout after login until refresh.  
- **Steps:**  
  1. Open the website as a guest user.  
  2. Proceed to checkout and choose delivery.  
  3. Log in with an account that already has a saved address.  
  4. Observe the address section.  
- **Expected:** Saved address should appear immediately after login.  
- **Actual:** Address is not displayed until the page is refreshed.  
- **Attachments:** Recording showing missing address before refresh.  

---

## 🐞 Bug #3 – News Edit Without Writer
- **Type:** Backend / CMS  
- **Title:** Publishing news without a writer throws generic error.  
- **Steps:**  
  1. Log in to the admin panel.  
  2. Edit any news article.  
  3. Remove the writer field and click "Publish".  
- **Expected:** Validation error should state that "Writer is required".  
- **Actual:** Toast message appears with "Something wrong happened please check later".  
- **Attachments:** API payload shows `writerId = 0`.  

---

## 🐞 Bug #4 – Area Filter Not Retained on Store Pickup
- **Type:** Frontend / Store Pickup  
- **Title:** Selected area filter resets after login.  
- **Steps:**  
  1. As a guest, select pickup from store.  
  2. Apply filter with an area (e.g., Abu Dhabi).  
  3. Log in and go back to store selection.  
- **Expected:** Selected area filter should remain applied.  
- **Actual:** Filter resets, showing all branches instead.  
- **Attachments:** Recording showing reset behavior.  

---

## 🐞 Bug #5 – Cancel Order Validation
- **Type:** Backend / Orders  
- **Title:** Wrong validation message when canceling orders.  
- **Steps:**  
  1. Place an order successfully.  
  2. Try to cancel the order before it is shipped.  
- **Expected:** Order can be canceled if status is "Placed".  
- **Actual:** Message appears "You can cancel order only if status is placed" even though status is already "Placed".  
- **Attachments:** Screenshot of error message.  

---

## 🎯 Summary
- Language-related bugs: **1**  
- Checkout-related bugs: **1**  
- CMS-related bugs: **1**  
- Store pickup bugs: **1**  
- Order management bugs: **1**  

Total: **5 Web bugs documented**
