# 📅 **Day 10 – Week-1 Review: Incident Analysis & SRE Thinking**

### (Hands-on Reflection + Interview Mapping)

---

## 🎯 Day-10 Goal

By the end of Day 10, you should confidently say:

> “I can clearly explain real Kubernetes incidents, their root causes, and how I would prevent them in production.”

This day **separates mid-level from senior**.

---

# 🧠 TASK 1: Incident Review (Very Important)

Create a document (Notion / Markdown) titled:

```
Week-1 Incidents & Learnings
```

List **each day as an incident**:

### Incident 1 – CPU Saturation (Day 1)

* Symptom: High CPU, degraded performance
* Root cause: No CPU limits
* Fix: Remove workload
* Prevention: Requests, limits, HPA

### Incident 2 – OOMKill (Day 2 & Day 9)

* Symptom: Pod restarts, CrashLoopBackOff
* Root cause: Memory limit exceeded
* Fix: Adjust limits
* Prevention: Memory profiling, alerts

### Incident 3 – Probe Misconfiguration (Day 3)

* Symptom: Pod restarts or NotReady
* Root cause: Aggressive liveness probe
* Fix: Use readiness probes
* Prevention: Validate probes

### Incident 4 – CrashLoopBackOff (Day 4)

* Symptom: Repeated restarts
* Root cause: Bad startup command
* Fix: Correct command
* Prevention: Test entrypoints

### Incident 5 – Failed Deployment (Day 5)

* Symptom: Rollout stuck
* Root cause: Invalid image
* Fix: Rollback
* Prevention: CI validation

### Incident 6 – Service Outage (Day 6)

* Symptom: App unreachable
* Root cause: Selector mismatch
* Fix: Restore selector
* Prevention: Endpoint monitoring

### Incident 7 – Networking Failure (Day 7)

* Symptom: Pod unreachable
* Root cause: Pod IP change
* Fix: Use Service
* Prevention: DNS-based access

### Incident 8 – Config Outage (Day 8)

* Symptom: App broken, infra healthy
* Root cause: Bad ConfigMap
* Fix: Fix config + restart
* Prevention: Config validation

### Incident 9 – Resource Enforcement (Day 9)

* Symptom: OOMKilled, CrashLoopBackOff
* Root cause: Memory limits
* Fix: Tune limits
* Prevention: Capacity planning

---

# 🗣️ TASK 2: Practice Interview Answers (CRITICAL)

Answer these **out loud** (yes, out loud):

### Q1: “Pod is running but app is down — what do you check?”

* Probes
* Logs
* Endpoints
* Config

### Q2: “CrashLoopBackOff — what are your first steps?”

* Logs
* Exit code
* Command
* Resources

### Q3: “Service unreachable but pods running?”

* Endpoints
* Selectors
* DNS

### Q4: “Difference between requests and limits?”

* Requests = scheduling
* Limits = runtime enforcement

If you can answer smoothly → **you’re progressing correctly**.

---

# 🧪 TASK 3: One Mini Re-run (Pick ONE)

Re-run **one** of these quickly:

* OOMKill lab
* Service selector break
* Probe failure

Explain **while doing it**:

* What broke
* Why
* How to fix
* How to prevent

This reinforces muscle memory.

---

# 🧠 TASK 4: Write Your First Postmortem (Senior Habit)

Create a **mini postmortem**:

```md
Incident Summary:
- Impact:
- Root Cause:
- Detection:
- Resolution:
- Preventive Actions:
```

Pick **any one Day 1–9 incident**.

This is **very powerful for interviews**.

---

# 📌 TASK 5: Confidence Check (Be Honest)

Answer YES/NO:

* [ ] I can explain OOMKilled clearly
* [ ] I know why probes fail
* [ ] I know why services break
* [ ] I know why pods restart
* [ ] I know what to check first

If most are YES → you’re on track.

---

> “Most Kubernetes outages are caused by misconfiguration rather than infrastructure failure. My approach is to isolate whether the issue is scheduling, runtime, networking, or configuration-related.”

That sentence alone sounds **Senior SRE**.

---

