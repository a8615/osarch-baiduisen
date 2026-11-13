# Lab 4 - Storage

## Windows
Disk 0: partition style GPT, firmware_type UEFI - because the system booted in UEFI mode.
New disk: partition style GPT - because I chose GPT to support modern standards and avoid the 2TB limit.
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
# Linux layout - before
```
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
loop0    7:0    0   1.5M  1 loop /snap/hwctl/131
loop1    7:1    0  66.8M  1 loop /snap/core24/1643
loop2    7:2    0   1.5M  1 loop /snap/hwctl/123
loop3    7:3    0  50.1M  1 loop /snap/snapd/27710
sda      8:0    0    25G  0 disk 
├─sda1   8:1    0     1M  0 part 
├─sda2   8:2    0     2G  0 part /boot
└─sda3   8:3    0    23G  0 part 
  └─ubuntu--vg-ubuntu--lv 252:0 0 11.5G 0 lvm  /
sdb     8:16    0     2G  0 disk 
sdc     8:32    0     2G  0 disk 
sdd     8:48    0     2G  0 disk 
sr0     11:0    1  1024M  0 rom
```
# Linux layout - after the rebuild
```
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
loop0    7:0    0   1.5M  1 loop /snap/hwctl/131
loop1    7:1    0  66.8M  1 loop /snap/core24/1643
loop2    7:2    0   1.5M  1 loop /snap/hwctl/123
loop3    7:3    0  50.1M  1 loop /snap/snapd/27710
sda      8:0    0    25G  0 disk 
├─sda1   8:1    0     1M  0 part 
├─sda2   8:2    0     2G  0 part /boot
└─sda3   8:3    0    23G  0 part 
  └─ubuntu--vg-ubuntu--lv 252:0 0 11.5G 0 lvm  /
sdb     8:16    0     2G  0 disk 
└─sdb1   8:17    0     2G  0 part 
  └─md0    9:0    0     2G  0 raid1 
sdc     8:32    0     2G  0 disk 
└─sdc1   8:33    0     2G  0 part 
sdd     8:48    0     2G  0 disk 
└─sdd1   8:49    0     2G  0 part 
  └─md0    9:0    0     2G  0 raid1 
sr0     11:0    1  1024M  0 rom 
```

| Role             | Device |
|------------------|--------|
| Mirror half A    | sdb1   |
| Failed half      | sdc1   |
| Replacement      | sdd1   |

# The question

Your colleague deleted the wrong file from the mirror an hour ago. Does RAID 1 help? Why?

No, it doesn't help. Because RAID 1 is a mirror, it writes the deletion to both disks at the same time. To get the file back, you need a real backup, like an external hard drive.

## Evidence
* evidence/ — one line per file on what it proves
* lsblk-before.txt — Proves the initial layout of the disks.
* array-healthy.txt — Proves the RAID 1 was active and healthy ([2/2] [UU]).
* array-degraded.txt — Proves a disk was failed ([U_]).
* checksum-before.txt — SHA256 before failure.
* checksum-after-failure.txt — SHA256 after failure (matches before).
* array-rebuilt.txt — Proves the array was restored using sdd1.
