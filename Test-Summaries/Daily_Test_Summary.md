# 📅 Daily Test Summary

This file provides a **daily snapshot of QA activities, progress, and defects**.  
It helps stakeholders understand **what was tested, what was found, and what’s pending** each day.

---

## 🏷 Daily Summary – Jan 18, 2025
- **Environment:** Staging (Web + Mobile + API)  
- **Tester:** Ahmed Rakha  
- **Build Version:** v2.5.0-beta-3  

### ✅ Executed
- Regression on checkout flow (Web)  
- Smoke tests on login & registration (Mobile)  
- API validation for `/api/order` (happy paths)  

### 🐞 Bugs Logged
- `BUG-701` → Cart not syncing across tabs (Medium)  
- `BUG-702` → Weak password accepted in mobile registration (High)  
- `BUG-703` → API returns 500 for invalid product ID (High)  

### 📌 Pending
- Multi-currency checkout (Web)  
- Biometric login validation (Mobile)  
- Bulk order stress test (API)  

---

## 🏷 Daily Summary – Jan 19, 2025
- **Environment:** Pre-Production (Web + API)  
- **Tester:** Ahmed Rakha  
- **Build Version:** v2.5.0-rc-1  

### ✅ Executed
- Smoke + sanity check for order placement (API)  
- Regression on store pickup (Web)  
- Multi-language search (EN/AR)  

### 🐞 Bugs Logged
- `BUG-711` → Area filter resets after login in store pickup (Medium)  
- `BUG-712` → Search in Arabic not returning results in Categories tab (High)  
- `BUG-713` → Expired coupon returns wrong error message (Medium)  

### 📌 Pending
- Retry payment flow  
- Order history validation on mobile app  

---

## 🏷 Daily Summary – Jan 20, 2025
- **Environment:** Pre-Production (Web + Mobile)  
- **Tester:** Ahmed Rakha  
- **Build Version:** v2.5.0-rc-2  

### ✅ Executed
- Final regression on cart & checkout (Web)  
- Exploratory session on login edge cases (Mobile)  
- API negative tests for `/api/order`  

### 🐞 Bugs Logged
- `BUG-721` → Expired card gives generic “Transaction failed” error (High)  
- `BUG-722` → FB login broken on iOS Safari (High)  
- `BUG-723` → Order history not loading on mobile app (Critical)  

### 📌 Pending
- Load testing for checkout  
- End-to-end smoke on staging with real payment sandbox  

---

## 📊 Value of Daily Summaries
- Keeps **QA progress transparent** for devs & managers.  
- Highlights **daily blockers & risks**.  
- Ensures **continuous defect visibility** during the sprint/release.  
