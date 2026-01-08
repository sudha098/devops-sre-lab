# 🚀 Day 6 – Kubernetes Services, DNS & Connectivity Failures

## 📌 Objective

Understand how **Kubernetes Services route traffic to Pods**, how **DNS-based service discovery works**, and how to **debug connectivity issues** when Pods are running but the application is not reachable.

Service and DNS misconfigurations are among the **most common real-world Kubernetes outages**.

---

## 🧪 Scenario

An application’s Pods are running and healthy, but traffic to the Service suddenly stops working.

This simulates:

* Service selector mismatches
* Missing or empty endpoints
* DNS-based connectivity failures

---

## 🚨 Symptoms Observed

* Pods in `Running` state
* Service object exists
* Application is unreachable via Service name
* `Endpoints` object is empty

---

## 🧠 Key Concepts

* **Service**: Stable virtual IP for accessing Pods
* **Endpoints**: Actual backend Pods selected by the Service
* **Selectors**: Label matching mechanism between Services and Pods
* **DNS**: Resolves Service names to ClusterIP

👉 **If endpoints are empty, traffic will not reach Pods.**

---

## 🔍 Investigation Steps

### Service & Endpoints Inspection

* Verified Service existence using `kubectl get svc`
* Checked backend mapping using `kubectl get endpoints`
* Identified empty endpoints due to selector mismatch

### Connectivity Testing

* Tested Service access from inside the cluster using a test Pod
* Confirmed DNS resolution of Service name

### Root Cause Isolation

* Compared Service selectors with Pod labels
* Identified mismatch between Service selector and Pod labels

---

## 🧩 Root Cause

The Service selector no longer matched the labels on the backend Pods, resulting in **zero endpoints** and complete traffic failure.

---

## 🛠️ Resolution

* Corrected the Service selector to match Pod labels
* Verified endpoints were repopulated
* Confirmed application connectivity was restored

---

## 🛡️ Prevention & Improvements

* Avoid manual changes to Service selectors in production
* Validate selectors during deployments
* Monitor endpoint counts
* Alert on Services with zero endpoints

---

## 🎯 Key Learnings

* Services route traffic via endpoints, not directly to Pods
* DNS resolves Service names to ClusterIP addresses
* Most Service outages are caused by label/selector mismatches
* Endpoints should always be checked first during connectivity issues

---

## 🗣️ Interview Explanation (STAR-ready)

> “When an application was unreachable despite healthy Pods, I checked the Service endpoints and found them empty due to a selector mismatch. Fixing the selector restored traffic immediately.”

---

## 🧠 Skills Demonstrated

* Kubernetes Service & DNS debugging
* Label and selector troubleshooting
* Production outage diagnosis
* Safe recovery strategies

---

## 📂 Related Topics

* Kubernetes networking fundamentals
* Service discovery
* Zero-downtime operations
* Incident response patterns


