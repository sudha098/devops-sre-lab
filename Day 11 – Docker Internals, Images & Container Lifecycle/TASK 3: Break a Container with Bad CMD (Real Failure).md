
admin@docker-host ➜  docker run nginx wrongcommand
/docker-entrypoint.sh: 47: exec: wrongcommand: not found

admin@docker-host ✖ ^C

admin@docker-host ✖ docker ps -a
CONTAINER ID   IMAGE     COMMAND                  CREATED          STATUS                       PORTS     NAMES
403bf91913e2   nginx     "/docker-entrypoint.…"   3 minutes ago    Exited (127) 3 minutes ago             romantic_haslett
4ce6601f0393   nginx     "/docker-entrypoint.…"   13 minutes ago   Up 13 minutes                80/tcp    web

admin@docker-host ➜  

-----------------------------------

This tells us **three critical things**:

---

## 🧠 1️⃣ ENTRYPOINT is running (important)

The error shows:

```
/docker-entrypoint.sh
```

This means:

* Nginx image has an **ENTRYPOINT**
* Docker is **NOT replacing** the entrypoint
* Your `wrongcommand` was passed as **CMD**

So Docker executed:

```bash
/docker-entrypoint.sh wrongcommand
```

👉 ENTRYPOINT stayed intact
👉 CMD was overridden

---

## 🧠 2️⃣ Why the container failed

Inside `/docker-entrypoint.sh`, it does:

```sh
exec "$@"
```

Since `wrongcommand` does not exist:

```
exec: wrongcommand: not found
```

Container exits immediately.

This is **exactly** how many real CrashLoopBackOffs happen.

---

## 🧠 3️⃣ Why this matters for Kubernetes

In Kubernetes, this would appear as:

```
State: Terminated
Reason: Error
Exit Code: 127
CrashLoopBackOff
```

Because:

* PID 1 exited
* Kubernetes restarts the container
* Backoff increases

---

## 🎯 Senior-Level Takeaway (memorize)

> “If a container exits immediately, I always inspect ENTRYPOINT and CMD.
> Overriding CMD incorrectly is a common cause of CrashLoopBackOff.”

This line sounds **very senior**.

---

## 🔥 Extra (optional but valuable)

Try this:

```bash
docker run --entrypoint sh nginx
```

You’ll drop into a shell **bypassing ENTRYPOINT**.

Now exit and try:

```bash
docker run --entrypoint sh nginx -c "nginx -v"
```

This shows:

* How ENTRYPOINT overrides work
* Why debugging images requires understanding entrypoints




