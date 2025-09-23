# 🐞 Defect Summary Report

This file provides a **summary of all defects logged** during testing cycles.  
It highlights defect distribution by **severity, module, and platform** to help stakeholders understand quality risks.

---

## 📌 Defect Distribution by Severity
- **Critical:** 3  
- **High:** 6  
- **Medium:** 5  
- **Low:** 2  

_Total defects logged: 16_

---

## 📌 Defect Distribution by Module
- **Checkout & Cart (Web):** 5  
- **Login & Registration (Mobile):** 4  
- **Order API:** 4  
- **Store Pickup (Web):** 2  
- **CMS (Backend):** 1  

---

## 📝 Sample Defects Logged

### 🔴 Critical
1. `BUG-723` → Order history not loading on mobile app (Mobile / Critical)  
2. `BUG-801` → Payment gateway not responding under load (Web / Critical)  
3. `BUG-802` → API order placement failing intermittently (API / Critical)  

### 🟠 High
1. `BUG-702` → Weak password accepted during mobile registration  
2. `BUG-703` → API returns 500 instead of 404 for invalid product ID  
3. `BUG-711` → Area filter resets after login in store pickup  
4. `BUG-712` → Search in Arabic not returning results in Categories tab  
5. `BUG-721` → Expired card gives generic “Transaction failed” error  
6. `BUG-722` → FB login broken on iOS Safari  

### 🟡 Medium
1. `BUG-701` → Cart not syncing across multiple browser tabs  
2. `BUG-713` → Expired coupon shows wrong error message  
3. `BUG-804` → Slow API response for bulk order placement  
4. `BUG-805` → Incorrect product sorting in category page  
5. `BUG-806` → Notifications delayed on mobile app  

### 🟢 Low
1. `BUG-807` → UI alignment issue on product details page  
2. `BUG-808` → Typo in “Password reset” success message  

---

## 📊 Defect Trends
- Most defects are concentrated in **checkout & order flows**.  
- **High-severity bugs** mainly impact payment, login, and API.  
- Several **UI/UX issues** were logged but categorized as low severity.  

---

## 📌 Value of Defect Summary
- Provides **clear snapshot** of product quality.  
- Helps prioritize **fixing critical/high issues first**.  
- Useful for **release go/no-go decisions**.  
