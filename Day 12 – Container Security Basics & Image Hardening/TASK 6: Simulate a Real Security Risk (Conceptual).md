### Scenario

* Container runs as **root**
* Container has **shell access**
* Container gets **compromised**
* Attacker **escapes to host**

---

## ❌ What went wrong?

### 1. Container ran as root

* Root inside the container = **high privileges**
* If the container runtime or kernel has a vulnerability, root can:

  * Abuse kernel syscalls
  * Access sensitive namespaces
  * Attempt container escape

---

### 2. Shell access enabled

* Shell gives attacker:

  * Interactive control
  * Ability to explore filesystem
  * Ability to run privilege-escalation tools
* Turns a vulnerability into **full control**

---

### 3. Weak isolation assumptions

* Containers **share the host kernel**
* Misconfigured:

  * Capabilities
  * Seccomp profile
  * AppArmor/SELinux
* Allowed attacker to break containment

---

### 4. Defense-in-depth missing

* No:

  * Non-root user
  * Capability dropping
  * Read-only filesystem
  * Runtime security monitoring

---

## ✅ How could it be prevented?

### 1. Run as non-root

* Limits what attacker can do even after compromise
* Most kernel exploits require root

---

### 2. Remove shell from image

* No `bash`, no `sh`
* Distroless or scratch images
* Attacker has **no interactive access**

---

### 3. Drop Linux capabilities

* Only allow what the app needs
* Prevents dangerous syscalls

---

### 4. Use seccomp + AppArmor / SELinux

* Restrict system calls
* Block kernel-level attack vectors

---

### 5. Harden container runtime

* Updated kernel
* Updated container runtime
* Rootless containers where possible

---

### 6. Assume breach

* Containers **will** be compromised
* Design so compromise **does not become host compromise**

---

## 🧠 Senior-level summary

> “The failure wasn’t the vulnerability — it was allowing a compromised container to have enough privileges to impact the host.”

---

