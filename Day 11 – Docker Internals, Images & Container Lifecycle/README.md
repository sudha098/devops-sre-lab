# 🚀 Day 11 – Docker Internals, Images & Container Lifecycle

## 📌 Objective

Understand how **Docker images are built**, how **containers start and stop**, and why **misconfigured ENTRYPOINT/CMD cause container failures** that later surface as `CrashLoopBackOff` in Kubernetes.

This day builds the **mental model required to debug container and Kubernetes startup issues**.

---

## 🧪 Scenario

Containers fail to start or exit immediately due to incorrect commands or misunderstanding of Docker image behavior.

This simulates:

* Startup failures
* Bad entrypoints or commands
* CrashLoopBackOff root causes in Kubernetes
* CI/CD image issues

---

## 🚨 Symptoms Observed

* Container exits immediately after start
* Errors like `executable file not found in $PATH`
* Exit codes `1`, `127`, or `128`
* Kubernetes would continuously restart such containers

---

## 🧠 Key Concepts

| Concept          | Explanation                                 |
| ---------------- | ------------------------------------------- |
| **Docker Image** | Immutable filesystem built from layers      |
| **Container**    | Runtime instance of an image                |
| **ENTRYPOINT**   | Fixed executable that always runs           |
| **CMD**          | Default arguments, can be overridden        |
| **PID 1**        | Main process; container exits when it exits |

👉 Most container failures are **application startup issues**, not infrastructure problems.

---

## 🔍 Investigation Steps

### Inspecting a Running Container

* Ran an Nginx container
* Inspected ENTRYPOINT and CMD using `docker inspect`
* Observed how containers are configured internally

### ENTRYPOINT vs CMD Behavior

* Overrode CMD while keeping ENTRYPOINT
* Observed failures when invalid commands were passed
* Confirmed ENTRYPOINT always executes unless explicitly overridden

### Startup Failure Simulation

* Ran container with invalid command
* Observed immediate exit with error
* Connected this behavior to Kubernetes `CrashLoopBackOff`

---

## 🧩 Root Cause

Containers exited immediately because **PID 1 failed to start** due to invalid commands passed via CMD. Docker correctly terminated the container, which Kubernetes would later retry indefinitely.

---

## 🛠️ Resolution

* Corrected Dockerfile CMD
* Built a minimal and valid image
* Ensured the container process stays alive
* Verified successful container execution

---

## 🛡️ Prevention & Improvements

* Clearly understand ENTRYPOINT vs CMD
* Test Docker images locally before pushing
* Keep images minimal
* Validate container startup commands in CI/CD
* Avoid overriding CMD blindly in Kubernetes manifests

---

## 🎯 Key Learnings

* Docker images are built from layers
* ENTRYPOINT defines what runs
* CMD defines default arguments
* Containers stop when PID 1 exits
* Startup failures directly translate to Kubernetes pod restarts
* Smaller images are faster and safer

---

## 🗣️ Interview Explanation (STAR-ready)

> “I debugged a container startup issue by inspecting ENTRYPOINT and CMD. The container was exiting immediately due to an invalid command passed as CMD. Fixing the Dockerfile resolved the issue and prevented CrashLoopBackOff in Kubernetes.”

---

## 🧠 Skills Demonstrated

* Docker image inspection
* ENTRYPOINT vs CMD debugging
* Container lifecycle understanding
* Kubernetes failure correlation
* Production-grade troubleshooting mindset

---

## 📂 Related Topics

* Dockerfile best practices
* Image optimization
* Kubernetes container lifecycle
* CI/CD image validation

---


