# Lab 4 — Partition, mirror, fail, recover

Pair:            Driver first half:
Machine: VMware Workstation pro
Date: 07.11.2026

## What I did

I partitioned the disks in Linux, created a RAID 1 array, and formatted it. I also partitioned and formatted a disk in Windows
```bash
# Key commands used:
sudo parted /dev/sdb --script mklabel gpt mkpart lab4 1MiB 100% set 1 raid on
sudo mdadm --create /dev/md0 --level=1 --raid-devices=2 /dev/sdb1 /dev/sdc1
sudo mdadm /dev/md0 --fail /dev/sdc1
sudo mdadm /dev/md0 --add /dev/sdd1
```

# Result
Successfully built the RAID 1 array. Simulated a disk failure, verified data survival via checksums, and rebuilt the array using the spare disk. Windows disk was initialized as GPT, partitioned, and formatted as NTFS.
### windows output
```
PS C:\WINDOWS\system32> $env:firmware_type
UEFI

PS C:\WINDOWS\system32> Get-Disk

Number Friendly Name Serial Number                    HealthStatus         OperationalStatus      Total Size Partition  
                                                                                                             Style      
------ ------------- -------------                    ------------         -----------------      ---------- -----------
0      VMware Vir... B74D_38EB_9DD1_02B8_000C_2960... Healthy              Online                     64 GB GPT        
1      VMware Vir... 3233_0F71_DF22_885A_000C_2969... Healthy              Online                      2 GB GPT        

PS C:\WINDOWS\system32> Get-Partition -DiskNumber 1

   DiskPath: \\?\scsi#disk&ven_nvme&prod_vmware_virtual_n#5&25a13950&0&000001#{53f56307-b6bf-11d0-94f2-00a0c91efb8b}

PartitionNumber  DriveLetter Offset                                        Size Type
---------------  ----------- ------                                        ---- ----
1                            17408                                    15.98 MB Reserved
2                E           16777216                                  1.98 GB Basic

PS C:\WINDOWS\system32> Initialize-Disk -Number 1 -PartitionStyle GPT

PS C:\WINDOWS\system32> New-Partition -DiskNumber 1 -UseMaximumSize -DriveLetter E

PS C:\WINDOWS\system32> Format-Volume -DriveLetter E -FileSystem NTFS -NewFileSystemLabel LAB4

DriveLetter FriendlyName FileSystemType DriveType HealthStatus OperationalStatus SizeRemaining      Size
----------- ------------ -------------- --------- ------------ ----------------- -------------      ----
E           LAB4         NTFS           Fixed     Healthy      OK                          1.97 GB 1.98 GB
```
## What did not work the first time
I made a typo in the parted command, missing a space between gpt and mkpart, which caused an error. I fixed it by adding the space.
At least one thing. What I saw, what it turned out to be, what I did about it.

## Evidence
* `evidence/` — one line per file on what it proves
* `lsblk-before.txt` — Proves the initial layout of the disks.
* `array-healthy.txt` — Proves the RAID 1 was active and healthy ([2/2] [UU]).
* `array-degraded.txt` — Proves a disk was failed ([U_]).
* `checksum-before.txt` — SHA256 before failure.
* `checksum-after-failure.txt` — SHA256 after failure (matches before).
* `array-rebuilt.txt` — Proves the array was restored using sdd1.
