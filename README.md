
# DevOps & SRE Hands-On Labs 🚀

This repository contains **hands-on DevOps and Site Reliability Engineering (SRE) labs** designed to help engineers practice real-world scenarios such as application failures, Kubernetes issues, monitoring, and reliability troubleshooting.

The labs are structured to simulate **production-like problems** and guide you through understanding, debugging, and fixing them.

---

## 🎯 Objectives

By working through this repository, you will learn how to:

- Understand common DevOps & SRE failure scenarios
- Debug Kubernetes issues (OOMKills, pod restarts, crashes, etc.)
- Improve system reliability and observability
- Apply SRE principles like monitoring, alerting, and incident analysis
- Gain confidence with hands-on troubleshooting

---

## 🧰 Prerequisites

Before starting, you should have basic knowledge of:

- Linux fundamentals
- Docker
- Kubernetes (pods, deployments, resources)
- YAML configuration files

Recommended tools:
- Docker
- Kubernetes cluster (Minikube / Kind / EKS / GKE)
- kubectl
- Git

---

## 📂 Repository Structure

```text
devops-sre-lab/
├── Day1/
│   ├── lab-description.md
│   ├── manifests/
│   └── solution.md
├── Day2/
│   ├── lab-description.md
│   ├── manifests/
│   └── solution.md
└── README.md
````

Each lab typically includes:

* **Problem statement** – what is broken and why it matters
* **Setup instructions** – how to reproduce the issue
* **Expected behavior** – what you should observe
* **Solution / Fix** – explanation and resolution steps

---

## 🧪 Example Lab Scenarios

* Pod OOMKill and memory misconfiguration
* Continuous pod restarts
* Application crashes under load
* Misconfigured resource limits
* Debugging logs and events
* Kubernetes health checks (liveness/readiness)

---
