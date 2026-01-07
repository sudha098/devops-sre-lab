
# 🚀 Day 3 – Readiness vs Liveness Probes & Health Check Failures

## 📌 Objective

Understand how **Kubernetes health probes** work, why **misconfigured probes cause outages**, and how to correctly use **readiness vs liveness** in production systems.

This is one of the **most common real-world Kubernetes failure causes**.

---

## 🧪 Scenario

A Kubernetes application experiences unexpected pod restarts or traffic drops even though CPU and memory usage appear normal.

This simulates:

* Misconfigured health checks
* Aggressive liveness probes
* Traffic disruption due to readiness failures

---

## 🚨 Symptoms Observed

* Pods restarting despite healthy resource usage
* Pods marked `NotReady` without restarts
* Service traffic intermittently failing
* `CrashLoopBackOff` caused by probe failures

---

## 🧠 Key Concepts

| Probe Type          | Purpose                      | Failure Impact           |
| ------------------- | ---------------------------- | ------------------------ |
| **Readiness Probe** | Can the pod receive traffic? | Pod removed from Service |
| **Liveness Probe**  | Is the application stuck?    | Pod restarted            |
| **Startup Probe**   | Is the app still starting?   | Delays liveness checks   |

👉 **Incorrect probe configuration can cause production outages.**

---

## 🔍 Investigation Steps

### Baseline (No Probes)

* Created a pod without probes
* Observed Kubernetes assumes the pod is healthy

### Misconfigured Liveness Probe

* Added an invalid liveness probe path
* Observed repeated pod restarts
* Pod entered `CrashLoopBackOff` even though the app was otherwise healthy

### Readiness Probe Failure

* Configured a readiness probe
* Intentionally broke the probe endpoint
* Observed pod remained running but was marked `NotReady`
* No restarts occurred

---

## 🧩 Root Cause

An **aggressive or incorrect liveness probe** caused Kubernetes to restart healthy pods unnecessarily.

---

## 🛠️ Resolution

* Recreated pods with correct probe configuration
* Used readiness probes to control traffic instead of restarting containers
* Avoided liveness probes unless strictly required

---

## 🛡️ Prevention & Improvements

* Prefer **readiness probes** for traffic management
* Use **liveness probes sparingly**
* Validate probe endpoints carefully
* Add sufficient startup delays for slow-starting applications

---

## 🎯 Key Learnings

* Liveness probe failures restart pods
* Readiness probe failures only stop traffic
* Many Kubernetes outages are caused by probe misconfiguration
* CPU and memory can be healthy while probes still fail

---

## 🗣️ Interview Explanation (STAR-ready)

> “I’ve handled scenarios where pods restarted even though resources were fine. The root cause was an aggressive liveness probe. I fixed it by shifting to readiness probes so traffic was removed safely without restarting healthy containers.”

---

## 🧠 Skills Demonstrated

* Kubernetes health probe design
* Pod lifecycle debugging
* Traffic safety vs restart decisions
* Production reliability thinking

---

## 📂 Related Topics

* Kubernetes Pod lifecycle
* CrashLoopBackOff causes
* Zero-downtime deployments
* Service availability protection

---

### ✅ Status

✔ Completed
✔ Documented
✔ Interview-ready



