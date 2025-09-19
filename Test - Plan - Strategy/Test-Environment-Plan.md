# 🖥 Test Environment Plan - E-commerce Project

## 1. Objective
Ensure stable and scalable environments are available for all phases of testing (Web, Mobile, API, Performance, Security).

## 2. Environments Setup
| Env | Purpose | Tools/Notes |
|-----|----------|-------------|
| DEV | Developer unit testing | Debug logs enabled |
| QA/STAGING | System & integration testing | Mirrors production setup |
| UAT | Business validation | Stable build only |
| PERF | Load & stress testing | Scalable infra |
| PROD | Live environment | Strict access control |

## 3. Hardware/Software Requirements
- **Web**: Chrome, Firefox, Edge, Safari (latest + 2 versions back).  
- **Mobile**: iOS 15–18, Android 11–14, devices with different screen sizes.  
- **API**: Postman, Newman, Swagger, JMeter.  
- **Performance**: JMeter, BlazeMeter, Grafana dashboards.  
- **Security**: Burp Suite, OWASP ZAP.  

## 4. Test Data
- Mock data for dev testing.  
- Anonymized production-like data for QA & performance.  
- Synthetic data for edge cases.  

## 5. Access & Permissions
- QA team: full access to QA & PERF.  
- Business: restricted UAT access.  
- Developers: access to DEV only.  
