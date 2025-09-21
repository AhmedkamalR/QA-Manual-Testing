# 📝 Exploratory Testing - Session Notes

These are notes from **exploratory testing sessions** I ran on the E-commerce project.  
I use a **time-boxed approach (60–90 mins)** per session, focusing on **critical business flows** like checkout, payments, login, and order APIs.  
Notes are meant to capture **what I did, what I saw, and what needs follow-up**.  

---

## Session 1: Cart & Checkout (Web)

- **Charter:** Explore cart and checkout flows, focus on usability & errors.  
- **Duration:** 90 mins  
- **Setup:** Chrome (Win11), staging env, test accounts, expired/valid cards  

**What I saw:**
- Checkout fine with single product.  
- Cart doesn’t refresh if same account removes product from another tab.  
- Expired card gives very generic error (“Transaction failed”).  
- Guest checkout skips address validation if ZIP left empty.  

**Issues logged:**
- BUG-101 → Cart not syncing across tabs  
- BUG-102 → Expired card error not user-friendly  
- BUG-103 → Guest checkout ignores ZIP validation  

**To do next time:**
- Multi-currency checkout  
- Payment retry flow on mobile  

---

## Session 2: Mobile App Login & Registration

- **Charter:** Explore login/registration on iOS + Android  
- **Duration:** 60 mins  
- **Setup:** iOS17 (iPhone 13), Android14 (Samsung), staging backend  

**What I saw:**
- Normal login works.  
- Registration accepts weak password (“12345”).  
- FB login → redirects to blank page on iOS Safari.  
- App crashes if OTP is requested multiple times quickly.  

**Issues logged:**
- BUG-201 → Weak password allowed  
- BUG-202 → FB login broken on iOS Safari  
- BUG-203 → OTP request crash  

**To do next time:**
- Try biometric login (FaceID/Fingerprint).  
- Test login on poor network (3G, airplane toggle).  

---

## Session 3: API Order Placement

- **Charter:** Explore `/api/order` endpoint (valid + invalid inputs)  
- **Duration:** 75 mins  
- **Setup:** Postman, staging API, user tokens  

**What I saw:**
- Valid request → 200 + order JSON OK.  
- Invalid product ID → returns 500 (should be 404).  
- Expired coupon → wrong error msg, looks like fallback.  
- Sending negative quantity accepted (e.g., `-2`).  

**Issues logged:**
- BUG-301 → 500 instead of 404 on invalid product  
- BUG-302 → Expired coupon wrong error  
- BUG-303 → Negative quantity accepted  

**To do next time:**
- Schema validation.  
- Stress test with 100+ concurrent order requests.  

---

## Session 4: Search & Filtering (Web)

- **Charter:** Explore product search and filters.  
- **Duration:** 60 mins  
- **Setup:** Chrome, staging env  

**What I saw:**
- Search returns results fast for normal keywords.  
- Arabic keywords return 0 results even if product exists.  
- Price filter sometimes includes products outside range.  
- Long queries (>100 chars) cause page freeze.  

**Issues logged:**
- BUG-401 → Arabic search not supported  
- BUG-402 → Price filter inaccurate  
- BUG-403 → Long query freezes page  

**To do next time:**
- Test autocomplete suggestions.  
- Check behavior on mobile Safari.  

---

## Session 5: Notifications & Emails

- **Charter:** Verify push notifications + order confirmation emails.  
- **Duration:** 45 mins  
- **Setup:** Android + Gmail test accounts  

**What I saw:**
- Push notification works for order confirmation.  
- No notification when order status changes to “Shipped”.  
- Confirmation email sometimes delayed >10 mins.  
- Email layout broken on Outlook desktop client.  

**Issues logged:**
- BUG-501 → Missing notification on shipped order  
- BUG-502 → Email delay  
- BUG-503 → Outlook email formatting broken  

**To do next time:**
- Test unsubscribe link.  
- Verify SMS fallback for critical messages.  

---

## Quick Notes

- Sessions are always **time-boxed** → avoids rabbit holes.  
- I log issues immediately with screenshots/responses.  
- Started with **critical business flows** (checkout, login, orders).  
- Adding coverage on **search, notifications, and emails** improved findings.  
- Notes stay short & actionable → easy for devs to pick up.  
