
# 🚀 Day 2 – Memory Management, OOMKills & Pod Restarts

## 📌 Objective

Understand how **memory exhaustion** occurs in Linux and Kubernetes, how **OOMKills happen**, and why pods **restart even when CPU usage is normal**.

This exercise focuses on **hard failures** that frequently cause production incidents.

---

## 🧪 Scenario

A Kubernetes workload consumes excessive memory and exceeds available limits, causing the Linux kernel to terminate the process.

This simulates:

* Memory leaks
* Unbounded workloads
* Missing or incorrect memory limits

---

## 🚨 Symptoms Observed

* Pod repeatedly restarting
* Pod status showing `OOMKilled`
* Exit code `137`
* Temporary service disruption

---

## 🔍 Investigation Steps

### Linux-Level Analysis

* Inspected system memory using `free -m`
* Understood used vs available memory behavior

### Kubernetes-Level Analysis

* Described the pod to inspect termination reason
* Verified container exit codes
* Observed restart behavior over time

---

## 🧩 Root Cause

The container exceeded available memory due to **missing memory limits**, triggering the Linux OOM killer.

---

## 🛠️ Resolution

* Deleted the offending pod to restore stability
* Confirmed no further memory pressure in the cluster

---

## 🛡️ Prevention & Improvements

* Define **memory requests and limits** for all workloads
* Monitor pod restart counts
* Alert on OOMKilled events
* Test workloads under realistic memory conditions

---

## 🎯 Key Learnings

* Exit code **137** indicates an OOMKill
* Memory exhaustion causes **hard failures**, unlike CPU throttling
* Kubernetes restarts pods automatically when memory is exhausted

---

## 🗣️ Interview Explanation (STAR-ready)

> “I diagnosed a memory-related outage by identifying repeated pod restarts and exit code 137. I confirmed the root cause as memory exhaustion due to missing limits and resolved it by removing the workload and enforcing memory constraints.”

---

## 🧠 Skills Demonstrated

* Linux memory troubleshooting
* Kubernetes pod lifecycle analysis
* Root cause analysis for restarts
* Preventive reliability practices

---

## 📂 Related Topics

* Kubernetes resource requests & limits
* OOM killer behavior
* Pod restart policies
* Observability for memory usage

---

### ✅ Status

✔ Completed
✔ Documented
✔ Interview-ready

---

