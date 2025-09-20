# 🗄️ Database Testing Checklist

This checklist covers comprehensive database testing areas for the E-commerce project: schema, data integrity, performance, backup/restore, security, and migrations. Use it to validate DB correctness, reliability and performance under real workloads.

---

## ✅ Schema & Structure
- [ ] Verify schema matches data model / ER diagram (tables, columns, types).  
- [ ] Check primary keys and foreign key constraints are defined and enforced.  
- [ ] Ensure NOT NULL and default values are correct where required.  
- [ ] Validate indices exist for frequently queried columns (and are used).  
- [ ] Confirm uniqueness constraints where business requires (e.g., email, SKU).  
- [ ] Validate views, materialized views, and synonyms (if any).  

## 🔁 Transactions & Concurrency
- [ ] Verify ACID behavior for critical transactions (checkout, payments).  
- [ ] Test rollback on failures (partial failures should not commit).  
- [ ] Simulate concurrent transactions for race conditions (e.g., inventory decrement).  
- [ ] Validate isolation levels (read-committed, repeatable-read) as per requirements.  
- [ ] Test optimistic / pessimistic locking logic if implemented.  

## 🔍 Data Integrity & Validation
- [ ] Check referential integrity (no orphan rows after deletes).  
- [ ] Validate triggers and stored procedure side-effects.  
- [ ] Test constraints (CHECK, foreign key, unique) are enforced.  
- [ ] Verify data types & ranges (dates, decimals, currency precision).  
- [ ] Test data transformation logic (ETL jobs, import/export).  

## ⚙️ Stored Procedures / Functions / Triggers
- [ ] Validate stored procedures return expected results for normal and edge inputs.  
- [ ] Test error handling inside procedures (no unhandled exceptions).  
- [ ] Verify triggers don’t introduce performance regressions or unexpected side-effects.  
- [ ] Ensure DB functions used by application behave deterministically.  

## ♻️ Migrations & Schema Changes
- [ ] Validate migration scripts run on staging without data loss.  
- [ ] Test rollback of migrations (if supported).  
- [ ] Check compatibility with older app versions during phased rollouts.  
- [ ] Ensure zero-downtime migration strategy tested for critical tables.  

## 📈 Performance & Query Optimization
- [ ] Identify slow queries via EXPLAIN/EXPLAIN ANALYZE and optimize indexes.  
- [ ] Validate response time for heavy queries under load (reporting, analytics).  
- [ ] Check connection pool sizing and max connections handling.  
- [ ] Test bulk inserts/updates performance and batch processing.  
- [ ] Monitor disk I/O, CPU, and memory during peak workloads.  

## 🔁 Replication, Backup & Recovery
- [ ] Verify backup schedule and restore procedures (point-in-time if applicable).  
- [ ] Test disaster recovery plan — restore to alternate environment.  
- [ ] Validate replication lag and failover behavior for replicated DBs.  
- [ ] Ensure backups do not contain sensitive data in plain text (masking).  

## 🔐 Security & Compliance
- [ ] Ensure least-privilege DB accounts (no excessive permissions).  
- [ ] Verify connections use TLS where applicable.  
- [ ] Check data encryption at rest for sensitive columns.  
- [ ] Validate audit logging for critical operations (deletes, role changes).  
- [ ] Ensure PII data is masked/anonymized for test environments (GDPR compliance).  

## 🧩 Data Migration & Test Data
- [ ] Prepare anonymized production-like datasets for performance and regression testing.  
- [ ] Validate seed/test-data scripts produce consistent baseline.  
- [ ] Test incremental data migrations and cleanup processes.  
- [ ] Ensure referential integrity with synthetic test datasets.  

## 🧪 Edge Cases & Negative Tests
- [ ] Insert invalid data types and confirm rejections (or graceful errors).  
- [ ] Test extremely large values/rows (LOBs, large text fields).  
- [ ] Validate behavior when DB disk is low or IO is throttled.  
- [ ] Simulate DB user privilege revocation and observe failures.  

---

## 📌 Value
Following this checklist ensures data correctness, transactional safety, recoverability, and production readiness of database systems — critical for any e-commerce platform.

