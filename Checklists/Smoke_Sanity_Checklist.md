# 🔥 Smoke & Sanity Testing Checklist

This checklist defines quick high-level validation steps (smoke) and focused checks (sanity) to confirm a new build is stable enough for deeper testing.

---

## 🧪 Smoke Testing (Build Health Check)
Run immediately after deployment to staging/QA:

- [ ] Verify application is reachable (DNS, load balancer).  
- [ ] Confirm basic UI loads (home page, header/footer).  
- [ ] Check authentication: login & logout with test account.  
- [ ] Validate core API health endpoints (`/health`, `/status`).  
- [ ] Ensure DB connection is established and migrations applied.  
- [ ] Perform a simple search and result rendering.  
- [ ] Add item to cart and view cart page.  
- [ ] Initiate checkout up to payment gateway redirect (do not charge).  
- [ ] Confirm background jobs/schedulers started (if applicable).  
- [ ] Verify error pages (404, 500) display correctly.

## ✅ Sanity Testing (Focused verification)
Run after fixes or small feature deployments:

- [ ] Verify the specific bugfix/feature works as expected.  
- [ ] Confirm related flows are not broken (smoke flows must pass).  
- [ ] Validate API contract for changed endpoints.  
- [ ] Check logs for exceptions around the changed module.  
- [ ] Run quick DB checks to ensure data consistency after the change.

## 🛠️ Environment & Pre-checks
- [ ] Ensure test data (accounts, products) exists for validation.  
- [ ] Confirm environment variables & configurations are correctly set.  
- [ ] Ensure mock/sandbox endpoints are enabled for external services.  
- [ ] Notify teams before smoke runs if tests might generate emails/notifications.

## 📈 Quick Exit Rules
- [ ] If smoke fails on critical items (app unreachable / DB down / login fails), **stop** deeper testing and open a blocker ticket.  
- [ ] If sanity fails for the specific fix, do not promote build; send back for fix & redeploy.

---

## 📌 Value
Smoke & sanity tests provide fast validation of build stability—saving time by detecting critical issues early before running full regression cycles.
