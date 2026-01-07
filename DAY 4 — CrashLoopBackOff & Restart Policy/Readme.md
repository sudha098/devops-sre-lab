# 🚀 Day 4 – CrashLoopBackOff & Kubernetes Restart Policies

## 📌 Objective

Understand **why CrashLoopBackOff occurs**, how Kubernetes **restarts containers**, and how **restart policies and exit codes** help identify the root cause of repeated failures.

CrashLoopBackOff is one of the **most common Kubernetes production issues**.

---

## 🧪 Scenario

A container starts successfully but **exits immediately**, causing Kubernetes to repeatedly restart it until it enters `CrashLoopBackOff`.

This simulates:

* Bad startup commands
* Missing environment variables
* Invalid application configuration
* Incorrect container entrypoints

---

## 🚨 Symptoms Observed

* Pod status shows `CrashLoopBackOff`
* Restart count increases continuously
* Increasing delay between restarts (backoff)
* Application never becomes available

---

## 🧠 Key Concept

**CrashLoopBackOff means:**

> The container keeps crashing, and Kubernetes is retrying with an increasing delay.

This is **not a Kubernetes bug** — it indicates an **application or configuration issue**.

---

## 🔍 Investigation Steps

### Pod Inspection

* Used `kubectl get pod` to observe pod status
* Used `kubectl describe pod` to inspect:

  * Exit codes
  * Restart count
  * Events showing backoff behavior

### Log Analysis

* Checked container logs using `kubectl logs`
* Observed minimal or no output, indicating immediate process exit

### Restart Policy Review

* Inspected pod specification to confirm default `restartPolicy: Always`
* Understood why Kubernetes keeps retrying indefinitely

---

## 🧩 Root Cause

The container process exited with a **non-zero exit code** due to an invalid startup command, triggering continuous restarts.

---

## 🛠️ Resolution

* Deleted the crashing pod
* Recreated the pod with a valid startup command
* Verified the pod reached `Running` state without restarts

---

## 🛡️ Prevention & Improvements

* Validate container entrypoints and startup commands
* Use **Jobs** for batch workloads instead of long-running Pods
* Monitor pod restart counts
* Alert on sustained CrashLoopBackOff conditions

---

## 🎯 Key Learnings

* CrashLoopBackOff indicates repeated container crashes
* Exit codes are critical for diagnosing failures:

  * `1` → application error
  * `137` → OOMKill
  * `126/127` → command or permission issues
* Restart policy determines retry behavior

---

## 🗣️ Interview Explanation (STAR-ready)

> “When I see CrashLoopBackOff, I first check container logs and exit codes. In this case, the container exited immediately due to an invalid startup command. Kubernetes retried with backoff, and I resolved it by fixing the command and redeploying.”

---

## 🧠 Skills Demonstrated

* Kubernetes pod lifecycle debugging
* Root cause analysis using exit codes
* Understanding of restart policies
* Production incident resolution mindset

---

## 📂 Related Topics

* Kubernetes pod lifecycle
* Restart policies (`Always`, `OnFailure`, `Never`)
* Application startup validation
* Reliability monitoring

---

### ✅ Status

✔ Completed
✔ Documented
✔ Interview-ready
