# 🔗 API Bug Reports  

This file contains **documented bugs** found during testing the E-commerce APIs.  
Each bug is reported in a **consistent format** for clarity and easy tracking.  

---

## 🐞 Bug #1 – Invalid Product ID Returns 500 Instead of 404  
- **Type:** Backend / Orders API  
- **Title:** Wrong status code when invalid product ID is sent.  
- **Steps:**  
  1. Send `POST /api/order` with a non-existing product ID.  
     ```json
     {
       "product_id": "NOT_EXIST",
       "qty": 1
     }
     ```  
  2. Observe API response.  
- **Expected:** API should return `404 Not Found` with clear error message.  
- **Actual:** API returns `500 Internal Server Error`.  
- **Attachments:** Postman response screenshot.  

---

## 🐞 Bug #2 – Expired Coupon Returns Wrong Error Message  
- **Type:** Backend / Promotions API  
- **Title:** Misleading response for expired coupon.  
- **Steps:**  
  1. Apply coupon code `EXPIRED2024` via `POST /api/cart/apply-coupon`.  
  2. Observe API response.  
- **Expected:** Error message should state `Coupon expired`.  
- **Actual:** Response shows generic error `"Invalid coupon"`.  
- **Attachments:** API JSON response.  

---

## 🐞 Bug #3 – Missing Validation on Password Field  
- **Type:** Backend / Auth API  
- **Title:** Password field accepts weak passwords.  
- **Steps:**  
  1. Call `POST /api/register` with password `"12345"`.  
  2. Observe API response.  
- **Expected:** API should return validation error `"Password too weak"`.  
- **Actual:** User is created successfully.  
- **Attachments:** Request/response logs.  

---

## 🐞 Bug #4 – Rate Limiting Not Applied on Login  
- **Type:** Backend / Auth API  
- **Title:** Unlimited login attempts possible without rate limiting.  
- **Steps:**  
  1. Call `POST /api/login` repeatedly with wrong credentials (50+ attempts).  
  2. Observe API behavior.  
- **Expected:** API should throttle requests or return `429 Too Many Requests`.  
- **Actual:** No rate limiting applied, all requests processed normally.  
- **Attachments:** JMeter run results.  

---

## 🐞 Bug #5 – Missing Schema Validation for Order Quantity  
- **Type:** Backend / Orders API  
- **Title:** Order accepts invalid quantity type.  
- **Steps:**  
  1. Call `POST /api/order` with invalid `qty: "ten"`.  
     ```json
     {
       "product_id": "12345",
       "qty": "ten"
     }
     ```  
  2. Observe response.  
- **Expected:** API should return validation error `"Quantity must be integer"`.  
- **Actual:** API accepts request and creates order.  
- **Attachments:** Postman request/response.  

---

## 🎯 Summary  
- Status code issues: **1**  
- Error messages / validation gaps: **3**  
- Security (rate limiting): **1**  

Total: **5 API bugs documented**  
