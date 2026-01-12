# 🔐 Day 13 – CI/CD Security & Supply Chain Risks (DevSecOps)

## 📌 Objective

Understand why **CI/CD pipelines are one of the highest-value attack targets**, how **supply chain attacks happen**, and how to **secure pipelines without slowing delivery**.

This day focuses on **security as part of the delivery system**, not as a separate team or afterthought.

---

## 🧪 Scenario

A CI/CD pipeline successfully builds and deploys an application, but later the application is found to be compromised.

Infrastructure and deployment appear healthy, yet the **root cause lies inside the pipeline**.

This reflects many **real-world breaches**.

---

## 🚨 Risks Identified

* Secrets exposed via code, logs, or artifacts
* Over-privileged CI/CD runners
* Untrusted dependencies or base images
* Lack of artifact integrity verification
* Pipelines acting as implicit “admin users”

---

## 🧠 Key Concepts

| Concept                   | Explanation                                                 |
| ------------------------- | ----------------------------------------------------------- |
| **CI/CD Attack Surface**  | Pipelines have access to secrets, artifacts, and production |
| **Supply Chain Security** | Trusting what you build and deploy                          |
| **Least Privilege**       | Pipelines should have minimal permissions                   |
| **Shift-Left Security**   | Catch issues early in the pipeline                          |
| **Artifact Trust**        | Only pipelines should produce deployable artifacts          |

👉 A compromised pipeline equals compromised production.

---

## 🔍 Investigation & Analysis

### CI/CD Attack Surfaces

Identified high-risk areas:

* Secrets storage and exposure
* Pipeline configuration changes
* Artifact repositories
* Third-party dependencies
* Runner permissions

### Secret Leakage Simulation

* Demonstrated how secrets can be accidentally committed or logged
* Highlighted why secrets must never live in Git
* Emphasized short-lived, injected secrets

### Supply Chain Awareness

* Recognized that rebuilding artifacts locally breaks trust
* Understood why reproducible builds matter
* Identified the pipeline as the **single source of truth**

---

## 🧩 Root Cause

CI/CD pipelines are often treated as trusted systems without sufficient restrictions, allowing:

* Excessive permissions
* Secret exposure
* Unverified artifacts

This creates a **single, powerful failure point**.

---

## 🛠️ Mitigations

* Never store secrets in source control
* Inject secrets securely at runtime
* Apply least-privilege permissions to pipelines
* Enforce automated security checks
* Restrict who can modify pipeline definitions
* Treat pipeline configuration as critical infrastructure

---

## 🛡️ Prevention & Improvements

* Add secret scanning to repositories
* Scan dependencies and container images in CI
* Use short-lived credentials
* Restrict artifact publishing
* Audit pipeline access regularly
* Fail builds on critical security findings

---

## 🎯 Key Learnings

* CI/CD pipelines are high-trust systems
* Supply chain attacks often bypass runtime security
* Security must be automated, not manual
* Artifact integrity is as important as code quality
* DevSecOps is about **secure delivery**, not blocking delivery

---

## 🗣️ Interview Explanation (STAR-ready)

> “I secured CI/CD pipelines by identifying secret exposure risks, reducing pipeline permissions, and enforcing automated security checks so only trusted artifacts reach production.”

---

## 🧠 Skills Demonstrated

* CI/CD security awareness
* Supply chain risk analysis
* DevSecOps mindset
* Secure pipeline design
* Incident-driven security thinking

---

## 📂 Related Topics

* Secret management
* SBOMs
* Dependency scanning
* Pipeline hardening
* Zero-trust delivery pipelines


