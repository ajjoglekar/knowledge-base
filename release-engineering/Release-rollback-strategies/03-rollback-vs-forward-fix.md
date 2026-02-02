# ⚖️ Module 03 — Rollback vs Forward-Fix  
## Making the Right Decision Under Pressure

---

## 🎯 Purpose of this module

This module addresses the **most critical decision in release management**:

**Should we roll back, or should we fix forward?**

Many production incidents escalate not because a failure occurred, but because the **wrong recovery decision** was made under pressure.

This module provides a **decision framework** to help Release and Delivery Managers choose the safest path when things go wrong.

---

## 🧠 Why this decision is difficult

Rollback is often perceived as the “safe” option.  
Forward-fix is often perceived as the “risky” option.

In reality:
- rollback can increase instability,
- forward-fix can reduce long-term risk,
- and the *context* matters more than instinct.

The challenge is that this decision must usually be made:
- quickly,
- with incomplete information,
- under stakeholder pressure.

---

## 🔁 What rollback optimizes for

Rollback primarily optimizes for:

- **Speed of impact reduction**
- **Return to a known state**
- **Customer-facing stability**

Rollback is most effective when:
- system state has not diverged significantly,
- data mutations are minimal or reversible,
- deployment patterns support fast reversal.

---

## 🔧 What forward-fix optimizes for

Forward-fix primarily optimizes for:

- **System correctness**
- **State consistency**
- **Long-term stability**

Forward-fix is often safer when:
- data has already been mutated,
- backward compatibility is required,
- rollback would introduce new failures.

---

## ⚠️ Risk Callout
Choosing rollback simply because it feels faster can **increase blast radius** if system state has already changed.

---

## 🧠 The core decision drivers

A Release or Delivery Manager should evaluate the following **decision drivers** before choosing rollback or forward-fix.

---

### 🔹 1. System state divergence

Key question:  
Has the system state materially diverged since the release?

Indicators of divergence:
- database schema changes applied,
- background jobs already processed data,
- partial rollout across services or regions.

High divergence strongly favors **forward-fix**.

---

### 🔹 2. Data mutation and reversibility

Key question:  
Has data been permanently changed?

If data:
- has been written,
- has triggered downstream effects,
- or cannot be safely restored,

then rollback may cause **inconsistent or corrupted states**.

---

### 🧭 Manager’s Lens
If rollback requires restoring data, rollback is no longer low-risk.

---

### 🔹 3. Blast radius and exposure

Key question:  
How much of the system and how many users are affected?

Rollback may be appropriate when:
- exposure is limited,
- traffic can be redirected quickly,
- customer impact is ongoing and severe.

Forward-fix may be preferable when:
- exposure is already global,
- rollback would not meaningfully reduce impact.

---

### 🔹 4. Confidence in diagnosis

Key question:  
Do we understand the failure well enough to act?

Rollback can be safer when:
- root cause is unclear,
- symptoms are severe,
- rollback path is well-tested.

Forward-fix requires:
- high confidence in root cause,
- strong test coverage,
- disciplined execution.

---

## ⚖️ Decision comparison (conceptual)

| Factor | Rollback favors | Forward-fix favors |
|------|----------------|-------------------|
| Data mutation | Minimal | Significant |
| State divergence | Low | High |
| Exposure | Limited | Broad |
| Diagnosis clarity | Low | High |
| Time pressure | Extreme | Moderate |

This comparison is a **decision aid**, not a rule.

---

## 🧭 Manager’s Lens
The right decision is the one that **reduces total risk**, not the one that feels safest emotionally.

---

## 🎯 Interview Signal
Strong candidates explain *why* rollback or forward-fix was chosen, not just *what* was done.

Interviewers listen for:
- mention of data state,
- blast radius awareness,
- and ownership of the decision.

---

## 🧠 Common failure patterns

Release leaders should actively avoid these traps:

- defaulting to rollback without assessment,
- delaying decision due to lack of ownership,
- attempting rollback and forward-fix simultaneously,
- changing strategy mid-incident without alignment.

Each of these increases confusion and recovery time.

---

## 📌 Key takeaways from this module

Lock in these principles:
- rollback and forward-fix are **risk decisions**, not technical preferences,
- data state is the most important factor,
- rollback is not always safer,
- forward-fix is often the mature choice,
- clarity and ownership matter more than speed.

---

## 🔜 What’s next

In **Module 04**, we will examine how **deployment patterns** influence rollback behavior, including:
- rolling deployments,
- blue–green releases,
- canary strategies,
- and feature-flag-driven delivery.

Understanding these patterns helps leaders anticipate rollback constraints **before** releases begin.


