# 🚀 Day 9 – Resource Requests, Limits & Scheduling Failures

## 📌 Objective

Understand how **Kubernetes schedules pods using resource requests**, how **limits are enforced at runtime**, and why misconfigured resources lead to **Pending pods, OOMKills, and CrashLoopBackOff**.

Resource mismanagement is a **major cause of cluster instability** in production.

---

## 🧪 Scenario

A workload is deployed with strict memory limits but attempts to allocate more memory than allowed, resulting in repeated container crashes.

This simulates:

* Noisy-neighbor problems
* Memory leaks
* Incorrect resource sizing
* Runtime enforcement failures

---

## 🚨 Symptoms Observed

* Pod scheduled successfully
* Container repeatedly restarts
* `CrashLoopBackOff` state
* `OOMKilled` termination reason
* Infrastructure appears healthy

---

## 🧠 Key Concepts

| Concept         | Purpose                                            |
| --------------- | -------------------------------------------------- |
| **Requests**    | Used by the scheduler to place pods                |
| **Limits**      | Enforced at runtime by the kernel                  |
| **Pending Pod** | Scheduler protection due to insufficient resources |
| **OOMKilled**   | Kernel terminated process due to memory limit      |

👉 **Requests protect the cluster; limits protect the node.**

---

## 🔍 Investigation Steps

### Scheduling Verification

* Confirmed pod was scheduled to a node
* Verified resource requests and limits via `kubectl describe pod`

### Runtime Failure Analysis

* Observed repeated restarts
* Inspected container `Last State`
* Identified `Reason: OOMKilled`

### Failure Classification

* Confirmed this was a **runtime memory failure**, not a startup or scheduling error

---

## 🧩 Root Cause

The container attempted to allocate **more memory than its configured limit**, causing the Linux kernel to terminate the process (`OOMKilled`). Kubernetes then restarted the container, resulting in `CrashLoopBackOff`.

---

## 🛠️ Resolution

* Identified excessive memory usage
* Adjusted memory limits to match workload needs **or**
* Optimized application memory consumption
* Verified stable pod behavior after correction

---

## 🛡️ Prevention & Improvements

* Always define resource requests and limits
* Pay special attention to memory limits (hard enforcement)
* Monitor OOMKilled events
* Perform load and stress testing before production rollout
* Alert on sustained CrashLoopBackOff states

---

## 🎯 Key Learnings

* Requests affect **scheduling**, not enforcement
* Limits affect **runtime behavior**
* CPU limits throttle; memory limits kill
* `OOMKilled` is a definitive signal of memory exhaustion
* “Pod Running” does not mean “application healthy”

---

## 🗣️ Interview Explanation (STAR-ready)

> “I debugged a pod repeatedly crashing due to memory exhaustion. The scheduler placed it correctly, but the container exceeded its memory limit and was OOMKilled. Kubernetes restarted it, leading to CrashLoopBackOff. I resolved it by correcting resource limits and validating memory usage.”

---

## 🧠 Skills Demonstrated

* Kubernetes scheduling mechanics
* Runtime resource enforcement
* CrashLoopBackOff diagnosis
* Memory failure analysis
* Production-grade troubleshooting

---

## 📂 Related Topics

* Kubernetes QoS classes
* Noisy neighbor mitigation
* Capacity planning
* Observability for resource usage

---

