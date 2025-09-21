# 🧠 Exploratory Testing – Mind Maps

Mind maps help me **visualize test ideas quickly**, without being trapped in step-by-step scripts.  
They give a **big picture view** of a feature, while still allowing me to dive deep into edge cases.  

---

## Why Mind Maps?
- Encourage **creative exploration** (branching ideas).  
- Easy to **communicate testing scope** with devs & PMs.  
- Great for **spotting gaps** (what we forgot to test).  
- Useful for both **planning** (before session) and **note-taking** (during session).  

---

## Example 1: Checkout Flow Mind Map

**Central Node:** `Checkout`  
- **Cart**
  - Add/remove items  
  - Quantity update  
  - Apply coupon  
- **Address**
  - New address  
  - Saved address  
  - Invalid/empty fields  
- **Payment**
  - Credit card (valid/expired/invalid)  
  - PayPal  
  - COD (cash on delivery)  
- **Order Confirmation**
  - Success page  
  - Failed transaction  
  - Email/SMS confirmation  

👉 In practice: I found that **expired cards show a generic error** (BUG-102) thanks to this mind map.  

---

## Example 2: Login & Registration Mind Map

**Central Node:** `User Access`  
- **Login**
  - Valid credentials  
  - Wrong password  
  - Locked account  
  - Social login (Google, FB)  
- **Registration**
  - Strong vs weak password  
  - Duplicate email  
  - Missing mandatory fields  
- **Security**
  - Session timeout  
  - Multiple failed attempts  
  - Password reset  

👉 This helped catch the bug where **weak password “12345” was allowed** (BUG-201).  

---

## Example 3: Search & Filters Mind Map

**Central Node:** `Search`  
- **Keywords**
  - English keywords  
  - Arabic keywords  
  - Long queries (>100 chars)  
- **Filters**
  - Price range  
  - Categories  
  - In-stock only  
- **Results**
  - Empty results  
  - Wrong sorting (e.g., relevance vs price)  
  - Pagination  

👉 From this, I explored and found **Arabic search returns 0 results even if product exists** (BUG-401).  

---

## Example 4: Notifications Mind Map

**Central Node:** `Notifications`  
- **Push Notifications**
  - Order placed  
  - Order shipped  
  - Order delivered  
- **Emails**
  - Order confirmation  
  - Delayed emails  
  - Layout on Gmail vs Outlook  
- **SMS**
  - Trigger on critical updates  
  - Delivery delays  

👉 This guided me to test different channels and find **Outlook formatting issues** (BUG-503).  

---

## Key Takeaways
- Mind maps are **living artifacts** → updated as system evolves.  
- They complement **session notes**: notes capture *what happened*, mind maps capture *what could happen*.  
- I often **share snapshots of these maps** with devs/PMs to align on testing coverage.  

