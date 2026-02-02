# 🛡️ Rollback Strategy — Sample Example  
## Medium-Risk Enterprise Release

---

## 📦 Release Context

- **Release name / ID:** ORD-SVC-2024.09
- **Application / Service:** Order Processing Service
- **Environment(s):** Production (Primary Region)
- **Deployment pattern:** Canary release (10% → 50% → 100%)
- **Change size:** Medium
- **Data impact:** Additive schema change (new nullable column)

---

## ⚠️ Primary Risk Summary

Primary risks identified for this release:

- increased error rates during order creation
- unexpected impact on downstream billing service
- performance degradation under peak load

---

## 🔍 Detection & Signals

| Signal | Threshold | Time window |
|------|-----------|-------------|
| HTTP 5xx error rate | > 1% | 5 minutes |
| Order creation latency | > p95 800ms | 10 minutes |
| Failed billing events | > 0.5% | 10 minutes |

Monitoring dashboards and alerts validated prior to release.

---

## 🔁 Rollback Options (Classification)

Available rollback strategies:

- [x] Code / Artifact rollback  
- [x] Traffic rollback  
- [ ] Data rollback  
- [ ] Configuration rollback  
- [x] Forward-fix preferred if data already written  

**Primary rollback strategy:**  
Traffic rollback (halt canary and revert traffic to baseline)

**Secondary (fallback) strategy:**  
Forward-fix with hot patch if data mutation confirmed

---

## ⏱️ Rollback Expectations

- **Estimated time to reduce customer impact:** < 5 minutes  
- **Estimated time to stabilize system:** 15–30 minutes  

Rollback does not require data restoration.

---

## 👤 Decision Authority & Ownership

| Responsibility | Owner |
|---------------|-------|
| Rollback decision | Release Manager |
| Rollback execution | Platform / DevOps Team |
| Risk acceptance | Product Owner |
| Stakeholder communication | Delivery Manager |

**Escalation path:**  
Engineering Director → VP Engineering

---

## 📣 Communication Plan

- **Immediate notification:** Engineering, Product, Support
- **Post-stabilization update:** Business stakeholders
- **Customer communication required:** No (internal degradation only)

---

## 🛑 Rollback Triggers

Rollback will be initiated if **any** of the following occur:

- HTTP 5xx error rate exceeds 1% for more than 5 minutes
- order creation latency exceeds p95 800ms for 10 minutes
- failed billing events exceed 0.5%

---

## 🧠 Rollback Safety Check

- [x] Rollback strategy reviewed and agreed
- [x] Deployment pattern supports traffic rollback
- [x] Data changes are backward-compatible
- [x] Monitoring signals active
- [x] Owners available during release window

---

## 📌 Leadership Acknowledgement

This release proceeds with an understood rollback strategy and accepted risk.

- **Release / Delivery Lead:** Ajay Joglekar
- **Product Owner:** Sample Name
- **Date:** YYYY-MM-DD

---
