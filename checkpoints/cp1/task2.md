| # | Part | What goes in it |
|---|---|---|
| 1 | Allocation | Ubuntu Server: 2 vCPUs, 2GB RAM, 20GB disk (dynamically allocated), Network: Bridged.<br>Windows 11: 4 vCPUs, 4GB RAM, 50GB disk (dynamically allocated), Network: NAT. |
| 2 | Arithmetic | Host specs from Task 4  threads, 16GB RAM, 520GB diskTotal used by VMs: 6 vCPUs, 6GB RAM , 70GB diskюLeft for host: 2 vCPUs, 10GB RAM, 186GB disk. The host OS and background apps usually need around 4GB RAM and 2 cores to stay responsive, so this leaves enough breathing room. |
| 3 | Justification | Windows 11 is heavy, so it needs 4 vCPUs and 4GB RAM to not lag. Ubuntu Server can run smoothly with just 2 cores and 2GB. I used dynamic disks so they won't eat up the host's disk space right away.  |
| 4 | Verification plan | 1. Inside Ubuntu, run lscpu and free -h to confirm it sees 2 CPUs and 2GB RAM4. In Windows 11, open Task Manager > Performance to verify the 4 vCPUs and 4GB RAM. |
