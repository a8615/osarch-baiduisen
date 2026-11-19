| # | Figure| This computer |Command it came from||
|---|-----------------|-----------------|--------------|------------------|
| 1 | CPU model | Intel(R) N95| Get-CimInstance Win32_Processor |
| 2 | Cores / logical processors | 4 Cores 4 threads|Get-PhysicalDisk Format-List * |
| 3 | Hardware virtualization: supported? enabled in firmware?| YES|systeminfo| 
| 4 | Memory: total / available now  | 16 GB| Get-CimInstance Win32_PhysicalMemory|
| 5 |  System disk: size, free space, SSD or HDD  | size: 512GB free space:101GB  SSD|Get-Volume,Get-PhysicalDisk|
| 6 | Partition style of the system disk|  ShiJi 512GB |  Get-PhysicalDisk Format-List *|
| 7 |  OS and version | WINDOWS 11| system info|

