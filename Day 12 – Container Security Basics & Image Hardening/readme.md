# 🔐 Day 12 – Container Security Basics & Image Hardening

## 📌 Objective

Understand **where container security risks come from**, how to **reduce attack surface**, and how **DevSecOps shifts security left** into the build phase instead of reacting in production.

This day focuses on **practical security awareness**, not theoretical perfection.

---

## 🧪 Scenario

Containers run successfully but introduce **hidden security risks** due to:

* Running as root
* Large base images
* Vulnerable OS packages
* Lack of build-time scanning

These risks often go unnoticed until a security incident occurs.

---

## 🚨 Risks Observed

* Containers share the host kernel
* Root containers increase blast radius
* Bloated images increase CVE exposure
* Security issues are detected too late

---

## 🧠 Key Concepts

| Concept                 | Explanation                              |
| ----------------------- | ---------------------------------------- |
| **Root Containers**     | Allow high-impact exploitation           |
| **Attack Surface**      | Number of packages and binaries in image |
| **Shift-Left Security** | Catch issues during build                |
| **Image Scanning**      | Detect known vulnerabilities early       |

👉 Security is about **risk reduction**, not zero risk.

---

## 🔍 Investigation Steps

### Container User Verification

* Ran containers and confirmed default execution as `root`
* Identified risk of privilege escalation

### Non-Root Container Execution

* Modified Dockerfile to run as non-root
* Verified reduced privileges at runtime

### Image Size Comparison

* Compared minimal vs full images
* Observed correlation between size and risk

### Vulnerability Scanning

* Used Trivy (or container-based scan)
* Reviewed CVEs by severity
* Identified base image as primary risk source

---

## 🧩 Root Cause

Most container security risks originate from:

* Unsafe base images
* Excessive privileges
* Lack of security scanning in CI/CD

---

## 🛠️ Mitigations

* Run containers as non-root
* Use minimal base images
* Scan images at build time
* Avoid privileged containers
* Limit host access from pods

---

## 🛡️ Prevention & Improvements

* Integrate image scanning in CI/CD
* Use multi-stage builds
* Enforce least privilege
* Apply Kubernetes Pod Security Standards
* Review base image choices regularly

---

## 🎯 Key Learnings

* Containers are not security boundaries
* Root containers increase impact of compromise
* Most vulnerabilities come from base images
* Build-time security is more effective than runtime fixes
* DevSecOps is about **early detection**

---

## 🗣️ Interview Explanation (STAR-ready)

> “I improved container security by reducing privileges, minimizing base images, and introducing image scanning during the build process to catch vulnerabilities before deployment.”

---

## 🧠 Skills Demonstrated

* Container security fundamentals
* DevSecOps mindset
* Risk analysis
* Image hardening
* CI/CD security awareness

---

## 📂 Related Topics

* Supply chain security
* SBOM generation
* Kubernetes Pod Security
* Runtime security tools


