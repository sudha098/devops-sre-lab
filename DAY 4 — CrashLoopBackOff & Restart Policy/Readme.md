## Day 4 – CrashLoopBackOff & Restart Policy

- CrashLoopBackOff means container repeatedly crashes
- Kubernetes retries with exponential backoff
- restartPolicy controls retry behavior
- Exit codes help identify root cause
- Logs are the first thing to check
