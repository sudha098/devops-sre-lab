Below is a **clean, senior-level GitHub README for Day 7**, written exactly how **SRE / DevOps engineers document real networking incidents**.

You can copy-paste this directly into:

```
Day-07-Pod-Networking/
└── README.md
```

---

# 🚀 Day 7 – Pod-to-Pod Networking & Network Failure Scenarios

## 📌 Objective

Understand how **pods communicate directly inside a Kubernetes cluster**, why **Pod IPs are unreliable**, and how to **debug pod-to-pod connectivity failures**.

Networking issues are some of the **hardest production outages** because everything often appears “Running”.

---

## 🧪 Scenario

One pod attempts to communicate directly with another pod using its IP address.
After a pod restart, connectivity unexpectedly fails.

This simulates:

* Pod restarts during deployments
* Node rescheduling
* Network instability scenarios

---

## 🚨 Symptoms Observed

* Pods are in `Running` state
* Direct pod-to-pod communication fails
* Application becomes unreachable without obvious errors
* Pod IP addresses change after restarts

---

## 🧠 Key Concepts

* **Pod IPs** are routable within the cluster
* **Pod IPs are ephemeral**
* **Services** provide stable access to pods
* **DNS** resolves service names to ClusterIP

👉 **Never depend on Pod IPs in production.**

---

## 🔍 Investigation Steps

### Pod-to-Pod Connectivity Test

* Created two pods: a client pod and a server pod
* Accessed the server pod directly using its Pod IP
* Confirmed successful connectivity

### Pod Restart & Failure

* Restarted the server pod
* Observed Pod IP change
* Attempted access using old IP and observed failure

### Corrective Approach

* Exposed the server pod using a Service
* Verified connectivity using Service name instead of Pod IP
* Confirmed DNS resolution of Service name

---

## 🧩 Root Cause

The application depended on a **Pod IP**, which changed after the pod was restarted, causing connectivity failure.

---

## 🛠️ Resolution

* Replaced direct Pod IP usage with a Kubernetes Service
* Verified DNS-based service discovery restored connectivity

---

## 🛡️ Prevention & Improvements

* Never hardcode Pod IPs
* Always use Services for inter-pod communication
* Validate NetworkPolicies to avoid silent traffic drops
* Monitor connectivity at the Service level

---

## 🎯 Key Learnings

* Pod IPs are temporary and unreliable
* Services abstract pod lifecycle changes
* DNS is critical for Kubernetes service discovery
* Networking failures can occur without pod crashes

---

## 🗣️ Interview Explanation (STAR-ready)

> “I debugged a pod-to-pod networking issue where communication broke after a pod restart. The root cause was reliance on a Pod IP. I fixed it by introducing a Service and using DNS-based service discovery.”

---

## 🧠 Skills Demonstrated

* Kubernetes networking fundamentals
* Pod lifecycle awareness
* Service-based communication design
* Real-world incident debugging

---

## 📂 Related Topics

* Kubernetes Services & DNS
* NetworkPolicies
* Zero-downtime networking
* Cluster networking models

---


