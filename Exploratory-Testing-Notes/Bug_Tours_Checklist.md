# 🧳 Bug Tours Checklist

Bug tours are a **structured exploratory testing technique** introduced by James Whittaker.  
They guide testers to explore the system from different angles, uncovering issues that scripted tests may miss.  

This file documents **bug tours applied to the E-commerce project**.

---

## 📝 Why Bug Tours?
- Encourage **creative exploration** instead of repeating the same flows.  
- Help uncover **hidden defects** in usability, performance, and integrations.  
- Provide a **systematic approach** for ad-hoc and exploratory sessions.  
- Useful for onboarding new testers → gives them starting points.  

---

## 🧭 Types of Bug Tours & Examples

### 🎒 Feature Tour
Explore each feature in isolation to understand what it does.
- Add/remove product to cart  
- Apply discount coupon  
- Change language from EN → AR  

---

### 🗺️ Error Tour
Purposely provoke errors to see how the system responds.
- Enter invalid coupon code → wrong format  
- Submit order with expired credit card  
- Login with locked user account  

---

### 🚌 Scenario Tour
Walk through real-life user scenarios end-to-end.
- Guest user adds product → checkout with COD  
- Logged-in user uses saved address → places prepaid order  
- User changes password → tries login from another device  

---

### 🏰 Data Tour
Stress the system with unusual or boundary data.
- Very large product quantity (`9999`) in cart  
- Emoji / special characters in name & address  
- Invalid JSON payload in `/api/order`  

---

### 🚦 Configuration Tour
Test different configurations, devices, and environments.
- Dark mode vs Light mode (mobile)  
- Different currencies (USD, EGP, AED)  
- Switching between Wi-Fi → 3G during checkout  

---

### 📜 History Tour
Explore how the system handles data history.
- Re-ordering from past orders  
- Editing an already placed order  
- Viewing order history with 100+ past purchases  

---

### ⏱️ Stress Tour
Push the system to its limits.
- Place 20 orders simultaneously via API  
- Rapidly add/remove product from cart  
- Login/logout repeatedly with same account  

---

## 📌 Value of Bug Tours
- Expands **test coverage** by exploring system from new angles.  
- Reveals **usability gaps** that scripted tests miss.  
- Encourages **team collaboration** by sharing different tours.  
- Acts as a **playbook for exploratory testers**.  

---

✅ This checklist demonstrates how I use **Bug Tours** in exploratory testing to uncover hidden issues in the E-commerce project.  
It shows **creativity, structure, and risk-awareness** in my testing approach.  
