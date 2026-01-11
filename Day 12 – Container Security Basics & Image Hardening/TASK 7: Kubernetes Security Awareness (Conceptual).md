
# 🔥 TASK 7: Kubernetes Security Awareness (Conceptual)

## ❌ Why `privileged: true` is dangerous

* Gives container **almost full host access**
* Bypasses:

  * cgroups
  * namespaces
  * device restrictions
* Container ≈ host root
* Any compromise = **node compromise**

---

## ❌ Why `hostPath` mounts are risky

* Exposes host filesystem to the pod
* Attacker can:

  * Modify host binaries
  * Read secrets
  * Access `/var/run/docker.sock`
* Enables **container escape via filesystem**

---

## ❌ Why `runAsRoot` is discouraged

* Root inside pod:

  * Easier privilege escalation
  * Larger blast radius
* Violates least privilege
* Makes exploits far more effective

---

## 🛡️ Kubernetes security principle (core idea)

> **Pods should only do what they absolutely need — nothing more.**

This is enforced by:

* Non-root users
* Restricted security contexts
* No host access
* No unnecessary privileges

---

## 🧠 Interview-ready closing statement

> “Kubernetes security is about shrinking the blast radius. A compromised pod should fail safely, not become a node takeover.”

