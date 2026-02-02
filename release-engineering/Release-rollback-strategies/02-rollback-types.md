# 🧩 Module 02 — Rollback Types (Taxonomy)  
## Understanding What Kind of Rollback You Are Dealing With

---

## 🎯 Purpose of this module

This module introduces a **clear, decision-oriented taxonomy of rollback types**.

One of the most common mistakes in release management is treating rollback as a **single action**.  
In reality, rollback can take several forms — each with **different risks, constraints, and decision implications**.

A Release or Delivery Manager must first answer:

**“What type of rollback are we actually considering?”**

Before deciding:
- whether rollback is safe,
- how fast it can be executed,
- and who must be involved.

---

## 🧠 Why rollback classification matters

Not all rollbacks:
- affect the system in the same way,
- carry the same level of risk,
- or can be executed with the same confidence.

Failing to classify rollback correctly leads to:
- incorrect assumptions about safety,
- delayed decisions during incidents,
- rollback actions that worsen the situation.

Correct classification allows leaders to:
- anticipate failure modes,
- choose between rollback and forward-fix,
- and communicate risk clearly to stakeholders.

---

## 🔁 The five rollback categories

From a release leadership perspective, rollback strategies fall into **five broad categories**:

1. Code / Artifact Rollback  
2. Configuration Rollback  
3. Traffic Rollback  
4. Data Rollback  
5. Forward-Fix (Rollback Alternative)

Each category represents a **different risk profile**, not just a different technical action.

---

## 🔹 1. Code / Artifact Rollback

**Code rollback** involves reverting an application to a previously known, stable version.

Typical characteristics:
- binary or artifact version change,
- redeployment of a previous release,
- often automated through CI/CD pipelines.

### When code rollback works well
- stateless services,
- backward-compatible interfaces,
- limited or no data mutation,
- fast redeployment capability.

### When code rollback becomes risky
- schema changes already applied,
- shared libraries updated across services,
- partial rollout has created version mismatch.

---

### 🧭 Manager’s Lens
Code rollback is safest when **system state has not materially diverged** since deployment.

---

## 🔹 2. Configuration Rollback

**Configuration rollback** reverses behavioral changes without changing application code.

This may involve:
- feature flags,
- environment variables,
- runtime configuration toggles.

### Why configuration rollback is powerful
- fast execution,
- minimal redeployment,
- often reversible with low risk.

### Hidden risks
- configuration drift across environments,
- unclear ownership of flags,
- flags left enabled long-term, increasing complexity.

---

### 🧭 Manager’s Lens
Configuration rollback shifts risk from deployment to **configuration governance**.

---

## 🔹 3. Traffic Rollback

**Traffic rollback** reduces exposure by redirecting user traffic away from a problematic version.

Commonly associated with:
- blue–green deployments,
- canary releases,
- phased rollouts.

### Strengths
- near-instant exposure reduction,
- minimal system changes,
- highly effective for customer-facing failures.

### Limitations
- underlying issues still exist,
- background processing may continue,
- data side effects may persist.

---

### 🧭 Manager’s Lens
Traffic rollback reduces **impact**, not **root cause**.

---

## 🔹 4. Data Rollback (Highest Risk)

**Data rollback** attempts to revert persisted data to a previous state.

This may include:
- restoring backups,
- reversing migrations,
- compensating transactions.

### Why data rollback is dangerous
- irreversible data loss risk,
- long recovery times,
- high coordination cost,
- regulatory and audit implications.

In many modern systems:
**true data rollback is impractical or impossible**.

---

### ⚠️ Risk Callout
If your rollback strategy depends on data rollback, the release risk is already high.

---

## 🔹 5. Forward-Fix (Rollback Alternative)

A **forward-fix** resolves issues by applying a corrective change instead of reverting.

This approach is often safer when:
- data has already been mutated,
- compatibility constraints exist,
- rollback would introduce more instability.

### Trade-offs
- requires confidence in diagnosis,
- may take longer to implement,
- demands strong testing and observability.

---

### 🧭 Manager’s Lens
Forward-fix is not a failure to roll back — it is often a **more mature risk decision**.

---

## ⚖️ Comparing rollback types at a glance

| Rollback Type | Speed | Risk Level | Typical Use |
|--------------|-------|------------|-------------|
| Code rollback | Medium | Low–Medium | Stateless services |
| Config rollback | Fast | Low | Feature toggles |
| Traffic rollback | Very fast | Low | Customer impact control |
| Data rollback | Slow | Very high | Last resort |
| Forward-fix | Variable | Medium | State-diverged systems |

This table is a **decision aid**, not a rulebook.

---

## 🧠 Why leaders must identify rollback type early

During incidents or go / no-go discussions, confusion often arises because teams:
- talk about “rollback” generically,
- assume safety without classification,
- mix execution concerns with decision authority.

A strong release leader will always clarify:
- **which rollback type is being considered**, and
- **what risks are associated with that type**.

---

## 📌 Key takeaways from this module

Before deciding to roll back, always establish:
- rollback is not a single action,
- different rollback types carry different risks,
- data rollback is the most dangerous,
- forward-fix is often the safer choice,
- classification enables faster, calmer decisions.

Correct rollback decisions begin with **correct rollback classification**.

---

## 🔜 What’s next

In **Module 03**, we will focus on the most critical leadership decision:

**Rollback vs Forward-Fix**

We will build a clear decision framework to help Release and Delivery Managers choose the safest path under pressure.


