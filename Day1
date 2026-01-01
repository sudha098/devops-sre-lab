ubuntu:~$ cat check_disk.py 
#!/usr/bin/env python3

import subprocess

THRESHOLD=80

command="df -h / | tail -1 | awk {'print$5'} | sed 's/%//'"

usage = subprocess.check_output(command, shell=True).decode().strip()

usage = int(usage)

if usage > THRESHOLD:
  print(f"Disk Usage High: {usage}%")
else:
  print(f"Disk usage Normal: {usage}%")

ubuntu:~$ 
ubuntu:~$ chmod +x check_disk.py
ubuntu:~$ 
ubuntu:~$ ./check_disk.py
Disk usage Normal: 29%
