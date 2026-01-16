# 🛡️ Day 14 – GitOps Security & Policy as Code (Hands-On)

## 📌 Objective

Learn how to **prevent unsafe Kubernetes workloads from ever being deployed** by enforcing **policy as code** using an admission controller.

This day focuses on **proactive platform protection**, not reactive fixes.

---

## 🧪 Scenario

Developers can accidentally (or unknowingly) deploy workloads that:

* Run as root
* Have no resource limits
* Violate security or reliability standards

By default, Kubernetes **allows these deployments**.

The goal is to **block them automatically** before they reach the cluster.

---

## 🚨 Problem Statement

* Manual code reviews are not enough
* Humans make mistakes
* Unsafe manifests can reach production
* Security and reliability rules are inconsistently applied

---

## 🧠 Key Concepts

| Concept                    | Explanation                                  |
| -------------------------- | -------------------------------------------- |
| **GitOps**                 | Git is the single source of truth            |
| **Policy as Code**         | Rules enforced automatically, not manually   |
| **Admission Controller**   | Intercepts and validates Kubernetes requests |
| **Preventive Engineering** | Stop bad changes before they happen          |

👉 The safest deployment is the one that **never gets applied**.

---

## 🔧 Hands-On Implementation

### 1️⃣ Installing Kyverno

* Installed Kyverno as a Kubernetes admission controller
* Verified Kyverno controllers were running

Kyverno enables **Kubernetes-native policy enforcement using YAML**.

---

### 2️⃣ Deploying an Unsafe Application (Baseline)

* Created a Deployment with:

  * No resource limits
  * Default (root) user
* Observed Kubernetes allowed it by default

This demonstrated the **risk of relying only on conventions or reviews**.

---

### 3️⃣ Enforcing Resource Limits via Policy

* Created a Kyverno `ClusterPolicy` requiring CPU and memory limits
* Set policy enforcement mode to `Enforce`
* Attempted to redeploy the unsafe application

✅ Deployment was **blocked automatically**
❌ No manual intervention required

---

### 4️⃣ Deploying a Compliant Application

* Added required resource limits to the Deployment
* Re-applied the manifest

✅ Deployment succeeded
🎯 Policy correctly allowed compliant workloads

---

### 5️⃣ Blocking Root Containers (Bonus)

* Added a policy requiring non-root execution
* Prevented containers from running as root

This reduced **blast radius and privilege escalation risk**.

---

## 🧩 Root Cause

Kubernetes does not enforce security or reliability standards by default.
Without policies, unsafe workloads can reach production unintentionally.

---

## 🛠️ Resolution

* Introduced **policy-as-code**
* Enforced rules at the **admission layer**
* Removed reliance on human discipline
* Ensured consistent enforcement across the cluster

---

## 🛡️ Prevention & Improvements

* Enforce policies at multiple layers (CI + admission)
* Version-control policies alongside application code
* Use enforcement, not just warnings, for critical rules
* Treat policies as part of the platform contract

---

## 🎯 Key Learnings

* GitOps improves auditability and control
* Policies prevent misconfigurations automatically
* Admission controllers are powerful safety gates
* Preventive engineering scales better than reviews
* Platform teams should define and enforce guardrails

---

## 🗣️ Interview Explanation (STAR-ready)

> “I implemented policy-as-code using an admission controller to block unsafe Kubernetes deployments automatically, ensuring all workloads met security and reliability standards before reaching production.”

---

## 🧠 Skills Demonstrated

* GitOps principles
* Policy as code
* Kubernetes admission control
* Platform security design
* Preventive reliability engineering

---

## 📂 Related Topics

* Argo CD / Flux
* OPA & Gatekeeper
* Kyverno
* Kubernetes Pod Security Standards
* Secure platform design


