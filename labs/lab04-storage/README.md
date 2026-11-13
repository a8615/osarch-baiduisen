# Lab 4 - Partition, mirror, fail, recover

Pair: None
Driver first half: None
Machine: VMware Workstation Pro
Date: 07.11.2026

## What I did
I partitioned the disks in Linux, created a RAID 1 array, and formatted it. I also partitioned and formatted a disk in Windows.

`bash
# Key commands used:
sudo parted /dev/sdb --script mklabel gpt mkpart lab4 1MiB 100% set 1 raid on
sudo mdadm --create /dev/md0 --level=1 --raid-devices=2 /dev/sdb1 /dev/sdc1
sudo mdadm /dev/md0 --fail /dev/sdc1
sudo mdadm /dev/md0 --add /dev/sdd1
