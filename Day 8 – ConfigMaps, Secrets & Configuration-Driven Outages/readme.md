# 🚀 Day 8 – ConfigMaps, Secrets & Configuration-Driven Outages

## 📌 Objective

Understand how **application configuration and secrets** can break systems even when Kubernetes infrastructure is completely healthy, and how to **debug configuration-driven failures**.

These outages are often **harder than infra failures** because nothing looks “down”.

---

## 🧪 Scenario

An application depends on environment-based configuration provided via a ConfigMap.
A configuration change causes the application to behave incorrectly or fail at startup.

This simulates:

* Bad configuration changes
* Missing or empty environment variables
* Secret/config drift between environments

---

## 🚨 Symptoms Observed

* Pods are `Running`
* No node or resource issues
* Application behaves incorrectly or fails
* Logs indicate missing or invalid configuration
* Kubernetes reports no infrastructure errors

---

## 🧠 Key Concepts

* **ConfigMap**: Stores non-sensitive configuration
* **Secret**: Stores sensitive data (passwords, tokens)
* **Environment Variables**: Common way apps consume config
* **Config-driven outages**: Infra healthy, app broken

👉 These outages often bypass monitoring and alerts.

---

## 🔍 Investigation Steps

### ConfigMap Creation & Usage

* Created a ConfigMap with application configuration
* Injected configuration into a pod via environment variables
* Verified application behavior using logs

### Configuration Change

* Modified ConfigMap values
* Restarted pod to pick up new configuration
* Observed application behavior change without infra errors

### Validation

* Confirmed pods were healthy
* Identified misconfiguration as root cause

---

## 🧩 Root Cause

An **invalid or missing configuration value** in the ConfigMap caused the application to misbehave, even though Kubernetes infrastructure was healthy.

---

## 🛠️ Resolution

* Corrected the configuration value
* Restarted the affected pod
* Verified application behavior returned to normal

---

## 🛡️ Prevention & Improvements

* Validate configuration before deployment
* Use defaults and input validation in applications
* Version and review configuration changes
* Add startup checks for required config
* Monitor application logs, not just infra metrics

---

## 🎯 Key Learnings

* Configuration errors can cause silent outages
* Kubernetes may show everything as healthy while apps fail
* ConfigMaps require pod restarts to take effect
* Config changes should be treated like code changes

---

## 🗣️ Interview Explanation (STAR-ready)

> “I handled an outage where infrastructure was healthy but the application failed due to a bad ConfigMap value. I identified the issue through application logs, corrected the configuration, and added validation to prevent recurrence.”

---

## 🧠 Skills Demonstrated

* Kubernetes ConfigMaps & Secrets
* Application-level debugging
* Configuration management
* Incident root cause analysis

---

## 📂 Related Topics

* Secret management
* Configuration drift
* Twelve-Factor App principles
* Safe configuration rollout strategies

---

