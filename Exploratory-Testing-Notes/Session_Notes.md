# 📝 Exploratory Testing - Session Notes

These are notes from **exploratory testing sessions** I ran on the E-commerce project.  
I follow a **time-boxed approach (60–90 mins)** per session, focusing on high-risk areas like checkout, login, and API orders.  
Notes are meant to capture **what I did, what I saw, and what needs follow-up**.  

---

## Session 1: Cart & Checkout (Web)

- **Charter:** Check cart and checkout flows, focus on usability & errors.  
- **Duration:** 90 mins  
- **Setup:** Chrome (Win11), staging env, test user accounts, expired/valid cards  

**What I saw:**
- Checkout fine with single product.  
- Cart doesn’t refresh if same account removes product from another tab.  
- Expired card gives very generic error (“Transaction failed”).  

**Issues logged:**
- BUG-101 → Cart not syncing across tabs  
- BUG-102 → Expired card error not user-friendly  

**To do next time:**
- Multi-currency checkout  
- Payment retry flow on mobile  

---

## Session 2: Mobile App Login & Registration

- **Charter:** Explore login/registration on iOS + Android  
- **Duration:** 60 mins  
- **Setup:** iOS17 (real iPhone), Android14 (Samsung), staging backend  

**What I saw:**
- Normal login works  
- Registration accepts weak password (“12345”)  
- FB login → redirects to blank page on iOS Safari  

**Issues logged:**
- BUG-201 → Weak password allowed  
- BUG-202 → FB login broken on iOS Safari  

**To do next time:**
- Try biometric login (FaceID/Fingerprint)  
- Slow network testing (3G, airplane toggle)  

---

## Session 3: API Order Placement

- **Charter:** Explore `/api/order` endpoint (valid + invalid inputs)  
- **Duration:** 75 mins  
- **Setup:** Postman, staging API, user tokens  

**What I saw:**
- Valid request → 200 + order JSON OK  
- Invalid product ID → returns 500 (should be 404)  
- Expired coupon → wrong error msg, looks like fallback  

**Issues logged:**
- BUG-301 → 500 instead of 404 on invalid product  
- BUG-302 → Expired coupon wrong error  

**To do next time:**
- Schema validation  
- Stress with bulk orders  

---

## Quick Notes

- Sessions always time-boxed → prevents over-testing one flow  
- I log issues immediately with screenshots/responses  
- Focused first on **critical business flows** (checkout, login, order)  
- Notes are short, but they give devs & testers clear actions  
