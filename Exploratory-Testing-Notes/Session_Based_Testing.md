# 🎯 Session-Based Testing (SBT)

Session-Based Testing (SBT) is a **structured exploratory testing approach**.  
It combines **charters, time-boxing, and note-taking** to balance creativity with accountability.  
This file documents **charters, sessions, and outcomes** from the E-commerce project.

---

## 📝 Why Session-Based Testing?
- Encourages **focused exploration** instead of random ad-hoc tests.  
- Ensures **traceability** of what was tested, when, and by whom.  
- Helps QA leads and stakeholders **track coverage & progress**.  
- Produces tangible **session reports** → useful for retrospectives.  

---

## 📌 Core Structure of a Session
Each session typically includes:
1. **Charter** – Mission of the session (e.g., "Explore coupon validation in checkout").  
2. **Time-box** – 60–90 mins per session.  
3. **Environment** – Web / Mobile / API / Staging or Production-like env.  
4. **Tester & Date** – Who ran the session, when.  
5. **Notes & Observations** – Key findings, both positive & negative.  
6. **Defects Logged** – Bug IDs, severity, references.  
7. **Follow-ups** – Areas that need more scripted or regression coverage.  

---

## 🗂 Charter Templates

Before starting sessions, I define broad charters to guide exploration:

- **Authentication** → email, password, OTP, social login, biometric  
- **Cart & Checkout** → add/remove items, quantity, coupons, payment, shipping  
- **Orders** → order placement, invalid inputs, API response, payment status  
- **Localization** → Arabic/English switching, RTL/LTR behavior, currency formats  
- **Mobile Responsiveness** → UI scaling, gestures, navigation in portrait/landscape  

---

## 🗂 Example Sessions

### 🛒 Session 1 – Cart & Checkout Validation (Web)
- **Charter:** Validate cart updates, checkout flow, and error handling.  
- **Tester:** Ahmed Rakha  
- **Duration:** 90 mins  
- **Environment:** Chrome (Win11), staging backend  

**Observations:**
- Cart not refreshing when updated in another tab.  
- Checkout worked with valid card but failed silently with expired one.  

**Defects Logged:**
- `BUG-101` → Cart not syncing across tabs (Severity: Medium)  
- `BUG-102` → Expired card error message too generic (Severity: High)  

**Follow-ups:**
- Test with coupons, multi-currency, and guest checkout.  

---

### 📱 Session 2 – Login & Registration (Mobile App)
- **Charter:** Explore login & registration on Android/iOS.  
- **Tester:** Ahmed Rakha  
- **Duration:** 75 mins  
- **Environment:** Android14 (Samsung), iOS17 (iPhone)  

**Observations:**
- Registration allowed very weak passwords.  
- Social login (FB) failed on iOS Safari redirect.  

**Defects Logged:**
- `BUG-201` → Weak password allowed (Severity: High)  
- `BUG-202` → FB login broken on iOS Safari (Severity: High)  

**Follow-ups:**
- Biometric login (FaceID/Fingerprint).  
- Test slow/unstable network conditions.  

---

### 🔗 Session 3 – Order Placement (API)
- **Charter:** Test `/api/order` with valid & invalid requests.  
- **Tester:** Ahmed Rakha  
- **Duration:** 80 mins  
- **Environment:** Postman + staging API  

**Observations:**
- Valid requests processed correctly.  
- Invalid product ID returned `500` instead of `404`.  
- Expired coupon returned wrong message.  

**Defects Logged:**
- `BUG-301` → Wrong error code (500 instead of 404).  
- `BUG-302` → Expired coupon message misleading.  

**Follow-ups:**
- Stress test with multiple parallel orders.  
- Validate response schema against OpenAPI spec.  

---

## 📊 How We Track Sessions
To avoid chaos, we track SBT using:
- **Session Sheets** → Excel/MD with charter, duration, notes, defects.  
- **Mind Maps** → To visualize explored flows.  
- **Tagging** → Defects tagged with `exploratory`, `session-X`.  
- **Summary Reports** → Shared weekly with team + stakeholders.  

---

## 📌 Value of Session-Based Testing
- Adds **discipline** to exploratory testing.  
- Helps **justify QA work** with data & metrics.  
- Encourages **creativity within a safe boundary**.  
- Provides **management visibility** into what testers explored.  

---

✅ This document shows how I **apply Session-Based Testing in practice** for critical E-commerce flows (login, checkout, order).  
It demonstrates **coverage, accountability, and risk-based testing** in a professional way.  
