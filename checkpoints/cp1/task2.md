| # | part | What goes in it |
|---|------|-----------------|
| 1 | Allocation | 2 vCPUs, 4GB RAM, and a 25GB dynamically allocated disk. |
| 2 | Arithmetic | Host: 8 threads, 16GB RAM. VM allocation: 2 vCPUs (2 < 8), 4GB RAM (4GB < 16GB). The VM uses only 25% of the host's CPU threads and 25% of its RAM, leaving 75% for the host OS and other applications. |
| 3 | Justification | I gave the VM 2 vCPUs and 4GB of RAM. My host has 8 threads and 16GB RAM. Allocating 4GB to the VM ensures the guest OS runs smoothly without starving the host system. I also used a 25GB dynamically allocated disk, meaning it only takes up physical space on my host as the VM actually uses it, saving space. |
| 4 | Verification plan |  lscputo verify 2 vCPUs.free -h to verify approximately 4GB of total RAM.  df -h and lsblk to verify the 25GB disk is mounted and recognized.  |
