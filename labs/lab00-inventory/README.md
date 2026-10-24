# Lab 0 — Inventory your own machine

Pair: Aimaral
Machine: DESKTOP-L90681B
Date: 2026-10-10

## What I did

Used PowerShell commands like `Get-CimInstance` and `systeminfo` to query the actual hardware inside my machine.

## Result

| What | Value | Where I got it |
| :--- | :--- | :--- |
| CPU model | Intel(R) N95 | Get-CimInstance Win32_Processor |
| Core count | 4 | Get-CimInstance Win32_Processor |
| Thread count | 4 | Get-CimInstance Win32_Processor |
| Total memory | 16 GB | Get-CimInstance Win32_PhysicalMemory |
| Number of modules | 1 | Get-CimInstance Win32_PhysicalMemory |
| Module speed | 2667 | Get-CimInstance Win32_PhysicalMemory |
| Disk model | ShiJi 512GB | Get-PhysicalDisk |
| Disk type | SSD (SATA) | Get-PhysicalDisk |
| Free space on VM volume | 101 GB | Get-Volume |
| Firmware type | UEFI | $env:firmware_type |
| Virtualization present and enabled | Yes | systeminfo |

## What did not work the first time

At first, I forgot to add the `>` symbol, so the command output was printed on the screen instead of being saved. I learned to redirect it into a `.txt` file.

## Evidence

- [evidence/cpu.txt](evidence/cpu.txt) — proves CPU model and core/thread count
- [evidence/memory.txt](evidence/memory.txt) — proves number of RAM modules and their speed
- [evidence/disk.txt](evidence/disk.txt) — proves disk model, connection type, and size
