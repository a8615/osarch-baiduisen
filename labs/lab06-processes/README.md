# Lab 6 — Live processes and memory pressure

Pair:                     Driver first half:
Machine: VM workstation pro
Date: 21.11.2026

## What I did
I picked python3 in Ubuntu to check
```
htop
Output: Found python3, PID 2572, RES 25788.

Task Manager (Windows)
Output: Found vmware-vmx.exe on host.

Process Explorer (Windows)
Output: Found vmware-vmx.exe Handles 529.
```
Ran memory stress test
```
free -h
Before: Available 3.7 Gi.

python3 -c "import time; a=[]; [a.append(b'x'*100_000_000) or print(len(a)*100, 'MB') or time.sleep(1) for i in iter(int, 1)]"
During: memory went to 5100 MB, swap increased, very laggy.

free -h
After: killed, memory normal.

sudo dmesg -T | grep -i "killed process"
Output: Out of memory: Killed process 2894 
```
## Result
Tools show different numbers because they measure different things. Task Manager shows whole VM memory, htop shows python3 memory. Windows uses Handles, Linux uses File Descriptors. Kernel killed python3 when RAM was full.

## What did not work the first time
When I pasted python code, terminal showed many > symbols and syntax error. I pressed Ctrl+C and pasted again. It worked.
Also I couldn't find vmware-vmx in Windows VM. Then I know it is on real laptop.

## Evidence
- evidence/task-manager.png (Task manager on real laptop)
- evidence/process-explorer.png (Show handles)
- evidence/htop.png (htop show python3)
- evidence/memory-pressure.txt (free -h data)
- evidence/kernel-log-extract.txt (out of memory log)
