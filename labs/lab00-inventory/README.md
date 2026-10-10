# Lab 0 — Inventory your own machine

Pair: baiduisen
Machine: DESKTOP-L90681B
Date: 2026-10-10

## What I did

Used PowerShell commands like Get-CimInstance and systeminfo to query the actual hardware inside my machine.

## Result

| What | Value | Where I got it |
| :--- | :--- | :--- |
| CPU model |  Intel(R) N95 | Get-CimInstance Win32_Processor |
| Core count | 4 | Get-CimInstance Win32_Processor |
| Thread count | 4 | Get-CimInstance Win32_Processor |
| Total memory | 16 | Get-CimInstance Win32_PhysicalMemory |
| Number of modules | 1| Get-CimInstance Win32_PhysicalMemory |
| Module speed | 2667 | Get-CimInstance Win32_PhysicalMemory |
| Disk model |  ShiJi 512GB | Get-PhysicalDisk |
| Disk type |   SSD | Get-PhysicalDisk |
| Free space on VM volume | 101 GB| File Explorer (C: drive properties) |
| Firmware type | UEFI| $env:firmware_type |
| Virtualization present and enabled |Yes| systeminfo |

## What did not work the first time

The first time I ran the commands, I did not know how to save the output to a text file, so the output was printed on the screen and lost. After that, I learned to use the > symbol to redirect the output into .txt files inside the evidence folder.

## Evidence

- [evidence/cpu.txt](evidence/cpu.txt) — proves CPU model and core/thread count
- [evidence/memory.txt](evidence/memory.txt) — proves number of RAM modules and their speed
- [evidence/disk.txt](evidence/disk.txt) — proves disk model, connection type, and size
