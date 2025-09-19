# 🔗 Requirements Traceability Matrix (RTM) - E-commerce Project

## 1. Objective
To ensure **100% coverage** of business requirements by mapping them to corresponding test cases, defects, and execution status.

---

## 2. Structure of RTM

| Requirement ID | Requirement Description | Test Case IDs | Test Type | Defects Linked | Status |
|----------------|--------------------------|---------------|-----------|----------------|--------|
| REQ-LOGIN-001 | User should be able to login with email & password | TC-WEB-LOGIN-01, TC-API-LOGIN-01, TC-MOB-LOGIN-01 | Functional | DEF-101 | Pass |
| REQ-LOGIN-002 | Support login with social accounts (Google, Facebook) | TC-WEB-LOGIN-08, TC-API-LOGIN-05, TC-MOB-LOGIN-07 | Integration | DEF-109 | In Progress |
| REQ-REG-001 | User should be able to register with email & password | TC-WEB-REG-01, TC-API-REG-01, TC-MOB-REG-01 | Functional | - | Pass |
| REQ-REG-002 | Password must meet complexity rules | TC-WEB-REG-07, TC-API-REG-06, TC-MOB-REG-05 | Security | DEF-115 | Fail |
| REQ-CART-001 | Add item to cart | TC-WEB-CART-01, TC-API-CART-01, TC-MOB-CART-01 | Functional | DEF-121 | Pass |
| REQ-CHECKOUT-001 | Place order with multiple payment methods | TC-WEB-CHECKOUT-05, TC-API-CHECKOUT-02, TC-MOB-CHECKOUT-04 | End-to-End | DEF-140 | In Progress |
| REQ-PERF-001 | Checkout should respond < 3s under 1000 concurrent users | TC-PERF-CHECKOUT-01 | Performance | - | Pending |
| REQ-SEC-001 | Application should prevent SQL Injection | TC-SEC-LOGIN-01, TC-SEC-REG-02 | Security | - | Pass |

---

## 3. Benefits
- Ensures **no requirement is untested**.  
- Helps track defects back to requirements.  
- Provides clear **release readiness** indicator.  
- Useful for audits & compliance.  
