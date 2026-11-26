# Lab 6 — Live processes and memory pressure

Pair:                     Driver first half:
Machine: VM workstation pro
Date: 21.11.2026

## What I did
### 1.Three tools comparison
I looked at the bash process in Linux. On the Windows side, I looked at vmware-vmx.exe because it runs the VM.
$ htop
(bash process: PID 2714, RES 6328)

Task Manager (Windows host)
(vmware-vmx.exe memory: 28.3 MB)

Process Explorer (Windows host)
(vmware-vmx.exe Handles: 529)


### 2. Memory pressure experiment
Here are the exact numbers from my terminal:

$ free -h (Before)
total        used        free      shared  buff/cache   available
Mem:           5.8Gi       1.1Gi       3.8Gi        12Mi       1.1Gi       4.5Gi
Swap:          2.0Gi          0B       2.0Gi

$ python3 -c "..."
(During: It went up to 5100 MB. Swap went from 0B to 1.2Gi. VM froze.)

$ free -h (After)
total        used        free      shared  buff/cache   available
Mem:           5.8Gi       1.0Gi       4.0Gi        12Mi       1.0Gi       4.6Gi
Swap:          2.0Gi       1.1Gi       0.9Gi

$ sudo dmesg -T | grep -i "killed process"
[1365.102285] Out of memory: Killed process 2894 (python3) total-vm:5097012kB...



## Result

The experiment worked. The OOM killer killed python3. 
The tools disagree because they measure different things. Windows uses Handles, Linux uses File Descriptors. Task Manager shows whole VM memory, but htop shows only bash memory.

## What did not work the first time

When I pasted python code, terminal showed syntax errors. I used Ctrl+C and pasted again. Also, I looked for the process in the Windows VM first, but then I realized it is on my real laptop.

## Evidence

- [evidence/task-manager.png](evidence/task-manager.png)
- [evidence/process-explorer.png](evidence/process-explorer.png)
- [evidence/htop.png](evidence/htop.png)
- [evidence/memory-pressure.txt](evidence/memory-pressure.txt)
- [evidence/kernel-log-extract.txt](evidence/kernel-log-extract.txt)
