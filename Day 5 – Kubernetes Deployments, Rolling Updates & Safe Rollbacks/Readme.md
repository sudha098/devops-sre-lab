# 🚀 Day 5 – Kubernetes Deployments, Rolling Updates & Safe Rollbacks

## 📌 Objective

Understand how **Kubernetes Deployments manage application releases**, how **rolling updates can fail**, and how to **safely roll back** to restore service during production incidents.

Deployment-related failures are among the **most common causes of outages**.

---

## 🧪 Scenario

A deployment update introduces an invalid container image, causing new pods to fail while the rollout is in progress.

This simulates:

* Failed application releases
* Invalid image tags
* Partial rollouts causing service instability

---

## 🚨 Symptoms Observed

* Pods stuck in `ImagePullBackOff`
* Deployment rollout does not complete
* New ReplicaSet fails to become healthy
* Risk of downtime if old pods are terminated

---

## 🧠 Key Concepts

* **Deployment**: Manages ReplicaSets and Pods
* **ReplicaSet**: Ensures desired number of Pods
* **Rolling Update**: Gradual replacement of Pods
* **Rollback**: Restore a previous stable state

Deployments allow **safe, controlled changes** compared to raw Pods.

---

## 🔍 Investigation Steps

### Deployment Inspection

* Checked rollout status using `kubectl rollout status`
* Inspected Deployment events and conditions
* Reviewed ReplicaSets created during the rollout

### Pod Analysis

* Described failing pods to identify `ImagePullBackOff`
* Verified image name and tag

### Rollout History

* Reviewed deployment revision history to identify last known good state

---

## 🧩 Root Cause

An **invalid container image tag** caused new pods to fail during the rollout, preventing the deployment from completing successfully.

---

## 🛠️ Resolution

* Rolled back the deployment to the previous stable revision using `kubectl rollout undo`
* Verified that healthy pods were restored
* Confirmed service stability after rollback

---

## 🛡️ Prevention & Improvements

* Validate images before rollout
* Use CI/CD pipelines with image verification
* Monitor rollouts actively
* Implement progressive delivery strategies where applicable

---

## 🎯 Key Learnings

* Deployments provide safe release management
* Rolling updates reduce downtime risk
* Rollbacks are critical for fast recovery
* ReplicaSets track deployment history

---

## 🗣️ Interview Explanation (STAR-ready)

> “During a failed rollout caused by an invalid image, I identified the issue using deployment status and pod events, rolled back to the last stable revision, restored service, and then fixed the image before redeploying.”

---

## 🧠 Skills Demonstrated

* Kubernetes release management
* Failure detection during rollouts
* Safe rollback strategies
* Production incident recovery

---

## 📂 Related Topics

* Deployment strategies
* Zero-downtime releases
* CI/CD integration with Kubernetes
* Release observability

---

### ✅ Status

✔ Completed
✔ Documented
✔ Interview-ready
