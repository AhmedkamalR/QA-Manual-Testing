# 🐞 Defect Discovery — Exploratory Testing

**Purpose:** a single, practical document to capture defects discovered during exploratory sessions.  
This file is written the way I use it day-to-day: concise, actionable, and focused on business impact. Use it as a template for entering tickets into your tracker (Jira/Asana/Trello) or attaching to PRs.

---

## How I record a defect (quick template)
When I log a bug, I include all fields below. Copy/paste this into a new issue body:

**Title:** [AREA] Short summary — one line (e.g. `Cart not syncing across tabs`)

**Environment**
- Env: `staging` / `qa` / `prod`
- Frontend: `web v1.2.3` / Browser: `Chrome 122 (Win11)`  
- Backend/API: `api v2.0.1` / commit: `abc123`
- Device: `iPhone 13 / Android Pixel 6` (if mobile)
- Network: `Wi-Fi`, `3G`, `throttled` (if relevant)

**Severity:** Critical / High / Medium / Low  
**Priority:** P0 / P1 / P2 / P3

**Pre-conditions / Test data**
- user: `test_user_01@example.com`  
- product SKU: `SKU-1234`  
- coupon: `EXPIRED100`

**Steps to reproduce**
1. Step 1 (clear, numbered).  
2. Step 2.  
3. Final step that shows the problem.

**Expected result**
- Short, specific, measurable (what should happen).

**Actual result**
- What actually happens (attach evidence).

**Reproducibility**
- Always / Sometimes (include % or pattern if flaky)

**Logs / evidence**
- Attach: screenshots, screen recording, HAR, Postman response, stack trace, crash log.

**Impact / Business keywords**
- e.g. `Revenue risk`, `Security`, `UX`, `Data integrity`, `Performance`, `Localization`

**Suggested fix (if you have an idea)**
- Short note for devs (optional, but useful).

**Acceptance criteria (QA retest)**
- Exact conditions that must be met for QA to close the ticket.

---

## Examples — Web defects (pattern + tags)
Below are real-like examples written the way I log them — use these as copyable examples.

### Example: Cart not syncing across tabs
- **Env:** staging / Chrome 122 (Win11)  
- **Severity:** High  
- **Steps:**  
  1. Login with same user in Tab A and Tab B.  
  2. Add `SKU-1234` to cart in Tab A.  
  3. Remove `SKU-1234` in Tab B.  
  4. Return to Tab A (no manual refresh).  
- **Expected:** cart auto-updates in Tab A within 2s or on next action.  
- **Actual:** cart still shows item until manual refresh.  
- **Impact / Keywords:** `Data Sync`, `UX`, `Duplicate Orders`, `High Priority`  
- **Evidence:** screenshot + short video (cart behavior)  
- **Suggested fix:** emit backend cart-update event (websocket) or short client poll after cart changes  
- **Acceptance criteria:** after removal in Tab B, Tab A reflects removal within 2s in 100% of trials

### Example: Search returns zero for Arabic keywords
- **Env:** staging / Chrome  
- **Severity:** High  
- **Steps:** type Arabic keyword `ملابس` into search  
- **Expected:** relevant Arabic products returned, relevance/boosting applied  
- **Actual:** zero results (products exist)  
- **Impact / Keywords:** `i18n`, `Search`, `Conversion risk`  
- **Evidence:** screenshot + sample product IDs  
- **Suggested fix:** verify analyzer / tokenizer for Arabic on search engine (Elasticsearch settings)

---

## Examples — Mobile defects

### Example: Facebook login redirect blank page (iOS)
- **Env:** iOS17 / iPhone (staging)  
- **Severity:** High  
- **Steps:** App → Login with Facebook → complete FB auth flow  
- **Expected:** redirect back to app and user is logged in  
- **Actual:** redirect opens blank Safari page (no token returned)  
- **Impact / Keywords:** `3rd-party integration`, `Auth`, `User Acquisition`  
- **Evidence:** video + console logs (if captured)  
- **Suggested fix:** check redirect URI handling / universal links config on iOS

### Example: App crashes on network switch during checkout
- **Env:** Android 14 / Pixel (staging)  
- **Severity:** Critical  
- **Steps:** start checkout, switch network 3G→Wi-Fi mid-payment  
- **Expected:** app shows retry or timeout flow, no crash  
- **Actual:** app crashes immediately (stack trace attached)  
- **Impact / Keywords:** `Stability`, `Payment flow`, `Revenue risk`  
- **Evidence:** crash log, reproduction steps  
- **Suggested fix:** add graceful network-change handling and retry logic

---

## Examples — API defects

### Example: Invalid product returns 500 instead of 404
- **Endpoint:** `POST /api/orders` (staging)  
- **Payload:**
```json
{
  "product_id": "NOT_EXIST",
  "qty": 1
}
``` 
- **Expected:** `404 Not Found` with `product not found` message  
- **Actual:** `500 Internal Server Error` (stack trace shows null pointer)  
- **Impact / Keywords:** `API Contract`, `Reliability`, `Integration risk`  
- **Evidence:** Postman response, server log / stack trace  

---

## Examples — API defects (more)

### Example: Expired coupon treated as 0% discount
- **Endpoint:** `POST /api/orders` with coupon `EXPIRED123`  
- **Expected:** `400` or `422` with "Coupon expired" message  
- **Actual:** `200 OK` and order processed with discount 0% (misleading)  
- **Impact / Keywords:** `Business Rules`, `Revenue leakage`, `Validation`  
- **Evidence:** API response + UI order summary screenshot  

### Example: Missing authorization header returns HTML instead of JSON
- **Endpoint:** `GET /api/user/orders` without `Authorization` header  
- **Expected:** `401 Unauthorized` with JSON error body  
- **Actual:** `200 OK` but returns HTML login page (not JSON)  
- **Impact / Keywords:** `Auth`, `API Consistency`, `Integration Break`  
- **Evidence:** Postman response screenshot  

---

## Examples — Performance / Load issues

### Example: Checkout slow under moderate load
- **Setup:** JMeter simulate 500 concurrent users adding to cart + checkout on staging  
- **Expected:** average checkout API latency < 3s, < 5% errors  
- **Actual:** avg latency 8s, 20% errors during peak  
- **Impact / Keywords:** `Scalability`, `SLA`, `Conversion`  
- **Evidence:** JMeter report (CSV), server metrics  

### Example: Mobile memory leak on repeated checkouts
- **Env:** Android device, reproduce 10 consecutive order flows  
- **Expected:** memory stable, no crash  
- **Actual:** memory increases each run → crash at run 10  
- **Impact / Keywords:** `Memory leak`, `Stability`, `App crash`  
- **Evidence:** logcat, memory profile snapshot  

---

## Examples — Security related defects

### Example: Password reset token not expiring
- **Steps:** request reset link, reuse link after 48 hours  
- **Expected:** token invalid after short TTL (e.g. 15–30 min)  
- **Actual:** link still valid after 48h  
- **Impact / Keywords:** `Security`, `Account takeover`, `Critical`  
- **Evidence:** reproduced token reuse  

### Example: Sensitive server error messages exposed to client
- **Steps:** trigger server-side failure (bad DB call)  
- **Expected:** generic error message: `Something went wrong` + internal logging only  
- **Actual:** API returns stack trace / DB details in response body  
- **Impact / Keywords:** `Info disclosure`, `Security risk`  
- **Evidence:** API response screenshot  

---

## Tags / Keywords I add to defects
Use these in labels for easy triage and filtering:
- `security`, `performance`, `ux`, `i18n`, `data-integrity`,  
- `api-contract`, `payment`, `stability`, `regression-required`,  
- `prod-impact`, `reproducible`, `intermittent`

---

## Severity vs Priority — the quick guide I present in triage
- **Severity** = technical/business impact (Critical / High / Medium / Low)  
- **Priority** = when we fix it (P0 / P1 / P2 / P3) — decided by PM/Owner after triage  
- Example: `Critical + P0` → production payment failure, stop release.  
- Example: `Medium + P2` → cosmetic UI issue, schedule in next sprint.  

---

## Retest / Close checklist (what QA does after dev fix)
1. Confirm developer’s PR/commit and environment where fix deployed.  
2. Reproduce original steps with same test data.  
3. Validate **Acceptance Criteria** from the ticket.  
4. Run small regression for related flows (smoke pack).  
5. Attach evidence (screenshots, API response) and move to `Done`.  
6. If flaky, run multiple attempts / automation to verify stability.  

---

## Quick practical notes / tips
- Short, **numbered steps** → devs love reproducible issues.  
- Always attach **evidence** (HAR, screenshot, log, video).  
- For intermittent bugs, include timestamps and frequency.  
- Always mention **business impact**: e.g. *“High revenue risk”*.  

---