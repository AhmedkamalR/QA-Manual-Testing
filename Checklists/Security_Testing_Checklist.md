# 🔐 Security Testing Checklist

This checklist ensures **comprehensive validation of application security** to identify vulnerabilities, protect sensitive data, and comply with security standards (e.g., OWASP, GDPR, PCI-DSS).  
It covers **authentication, authorization, data protection, network security, and vulnerability scanning** across web, mobile, and API layers.  

---

## ✅ General Security Preparation
- [ ] Define **security requirements** aligned with business and compliance needs.  
- [ ] Perform **threat modeling** to identify high-risk areas.  
- [ ] Ensure test environment has **HTTPS/TLS enabled**.  
- [ ] Validate **security logging and monitoring** are active.  
- [ ] Use updated **security tools** (e.g., OWASP ZAP, Burp Suite, Nessus).  
- [ ] Verify system complies with **data protection regulations**.  

---

## 🔑 Authentication Testing
- [ ] Validate secure **login mechanisms** (no hardcoded credentials).  
- [ ] Test password policy (length, complexity, expiry).  
- [ ] Ensure **multi-factor authentication (MFA)** works as expected.  
- [ ] Verify **session management** (session ID rotation after login).  
- [ ] Test for **brute force attack prevention** (account lockout, CAPTCHA).  
- [ ] Validate login APIs prevent **credential stuffing attacks**.  

---

## 🛂 Authorization Testing
- [ ] Verify users can only access data they are authorized for.  
- [ ] Check **role-based access control (RBAC)** implementation.  
- [ ] Attempt **privilege escalation** (normal user → admin).  
- [ ] Test access to restricted APIs without valid tokens.  
- [ ] Validate direct URL manipulation does not expose hidden resources.  
- [ ] Ensure **least privilege principle** is enforced.  

---

## 🔒 Data Protection
- [ ] Ensure **encryption in transit** (TLS 1.2+).  
- [ ] Validate **encryption at rest** for sensitive data (AES-256).  
- [ ] Verify password hashing with **bcrypt/Argon2**.  
- [ ] Check API tokens, session IDs, and keys are not exposed in logs.  
- [ ] Confirm sensitive data is masked in **UI, logs, and error messages**.  
- [ ] Test **SQL Injection, XSS, CSRF, SSRF** vulnerabilities.  

---

## 🌐 Network & API Security
- [ ] Verify **firewall and WAF rules** block malicious traffic.  
- [ ] Ensure APIs require **authentication tokens (JWT, OAuth2)**.  
- [ ] Test **rate limiting** to prevent DoS attacks.  
- [ ] Check **CORS policy** to prevent unauthorized cross-origin access.  
- [ ] Validate SSL/TLS certificates are valid and not expired.  
- [ ] Scan for **open ports and services**.  

---

## 🧪 Vulnerability & Penetration Testing
- [ ] Run automated scans (OWASP ZAP, Nessus).  
- [ ] Perform **manual penetration testing** on critical flows.  
- [ ] Validate app against **OWASP Top 10** vulnerabilities.  
- [ ] Check mobile apps for **root/jailbreak detection bypass**.  
- [ ] Test APIs for **insecure direct object references (IDOR)**.  
- [ ] Report and patch all discovered vulnerabilities.  

---

## 📌 Value
By following this checklist, QA teams ensure:  
- Application is **resistant to common cyber-attacks**.  
- Compliance with **security and privacy regulations**.  
- Protection of **user data and business assets**.  
- Increased trust and **brand reputation**.  

---
