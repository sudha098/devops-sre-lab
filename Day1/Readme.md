
# 🚀 Day 1 – Linux & Kubernetes CPU Saturation Debugging

## 📌 Objective

Understand how **CPU saturation** occurs in Linux and Kubernetes, how to **detect it using standard tools**, and how to **resolve it safely** without impacting cluster stability.

This exercise focuses on **real-world incident debugging**, not theory.

---

## 🧪 Scenario

A workload consumes excessive CPU resources, causing node-level CPU saturation and risking performance degradation for other applications.

This simulates:

* Runaway processes
* Misconfigured workloads
* Missing CPU limits in Kubernetes

---

## 🚨 Symptoms Observed

* High CPU utilization in Linux (`top`)
* Increased system load average
* A Kubernetes pod consuming disproportionate CPU
* Risk of resource starvation for other pods

---

## 🔍 Investigation Steps

### Linux-Level Debugging

* Used `top` to observe CPU usage and load average
* Identified sustained CPU consumption by a single process

### Kubernetes-Level Debugging

* Created a CPU-intensive pod using a stress image
* Verified pod and node CPU usage using Kubernetes metrics
* Correlated pod behavior with node-level resource usage

---

## 🧩 Root Cause

A pod was running a CPU-intensive workload **without CPU limits**, allowing it to consume excessive node CPU and potentially impact other workloads.

---

## 🛠️ Resolution

* Terminated the offending process/pod
* Verified CPU utilization returned to normal levels
* Ensured cluster stability after remediation

---

## 🛡️ Prevention & Improvements

* Define **CPU requests and limits** for all workloads
* Use **Horizontal Pod Autoscaling (HPA)** where applicable
* Monitor sustained CPU usage instead of short spikes
* Alert on prolonged node or pod CPU saturation

---

## 🎯 Key Learnings

* CPU saturation is often caused by **misconfiguration**, not infrastructure failure
* CPU throttling differs from memory failures (CPU degrades, memory kills)
* Pod-level metrics must be correlated with node-level metrics

---

## 🗣️ Interview Explanation (STAR-ready)

> “I simulated a CPU saturation incident by running a CPU-intensive workload in Kubernetes. I detected the issue using Linux and Kubernetes metrics, identified the root cause as missing CPU limits, resolved it by removing the workload, and proposed enforcing limits and autoscaling to prevent recurrence.”

---

## 🧠 Skills Demonstrated

* Linux performance debugging
* Kubernetes resource management
* Incident investigation & resolution
* SRE-style thinking and prevention planning

---

## 📂 Related Topics

* Kubernetes resource requests & limits
* Node vs pod resource contention
* Observability and alert design

---

### ✅ Status

✔ Completed
✔ Documented
✔ Interview-ready

---

