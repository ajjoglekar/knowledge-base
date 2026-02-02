# 🧩 Templates

This folder contains **practical, reusable templates** designed for Release Managers, Delivery Managers, and senior engineering leadership to plan and govern production releases with confidence.

These templates are written to be:
- **enterprise-friendly** (usable in CAB / Change Review settings),
- **risk-based** (used when change impact justifies it),
- **tool-agnostic** (no vendor lock-in),
- and **copy/paste ready** for real release workflows.

---

## 📌 What’s inside

### 🛡️ Rollback Strategy Playbook
**File:** `rollback-strategy-playbook.md`

A risk-based template to define rollback strategy **before production release**, including:
- release context and risk summary,
- detection signals and thresholds,
- rollback options (code/config/traffic/data/forward-fix),
- decision authority and execution ownership,
- communication plan,
- rollback triggers,
- and audit-ready acknowledgement.

---

## 🧭 When to use these templates (risk-based)

These templates are **not required for every release**.

Use them when a release involves medium-to-high risk factors such as:
- database schema or data model changes,
- shared platform or core service changes,
- authentication, authorization, or payment flows,
- infra / deployment pattern changes,
- multi-team coordination,
- compliance or audit exposure.

For routine low-risk deployments, these templates should not add overhead.

---

## ✅ How to use (recommended workflow)

1. **Identify risk level**
   - If the release is medium/high risk, use the playbook.

2. **Complete the template before go/no-go**
   - Use it as a structured discussion tool in release readiness review.

3. **Confirm ownership**
   - Decision owner and execution owner must be explicit.

4. **Keep it auditable**
   - Capture key decisions and observed rollback triggers.

---

## 🔄 Template philosophy

These templates are designed to support a simple principle:

**Rollback is not a technical action.  
Rollback is a leadership risk decision made under uncertainty.**

---

## ✍️ Author

Ajay Joglekar  
Release Management • CI/CD Delivery • Enterprise Governance • Rollback Readiness
