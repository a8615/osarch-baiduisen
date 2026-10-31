markdown
# Lab 3 — Teardown, and the same machine from the command line

Pair: Aimaral Baiduisen
Machine: X133-ADN
Date: 2026-10-31
Driver first half:

## What I did

First, I used PowerShell on my Windows host to find out what hardware I actually have. Because it's an unbranded laptop, `Win32_ComputerSystem` just gave me "Default string", so I had to dig deeper.

powershell
On Windows PowerShell (Host)
Get-CimInstance Win32_Processor | Format-List *
Get-CimInstance Win32_PhysicalMemory | Format-List *
Get-PhysicalDisk | Format-List *
Get-CimInstance Win32_BaseBoard | Format-List *
```

Then I ran similar commands in my Ubuntu VM to compare the hardware.

bash
# On Linux (Guest VM)
lscpu > linux-specs.txt
free -h >> linux-specs.txt
sudo dmidecode -t memory >> linux-specs.txt
lsblk -d -o NAME,MODEL,SIZE,ROTA,TRAN >> linux-specs.txt
```

Result

My real laptop has an Intel N95 CPU, 16GB RAM, and a 512GB SATA SSD. The VM shows completely different, virtualized hardware, like a 440BX motherboard and VMware disk.

What did not work the first time

I tried to save the PowerShell transcript to the Desktop using the default path, but it failed with a "path not found" error because my system uses a localized name for the Desktop folder. I fixed this by changing the directory to the Downloads folder before running the transcript command, which worked perfectly.

Evidence

· evidence/windows-specs.txt — Shows the real Windows host hardware (Intel N95, 16GB RAM).
· evidence/linux-specs.txt — Shows the virtualized hardware in the Ubuntu VM (VMware, 25G disk).

