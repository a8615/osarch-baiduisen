| # | Evidence file (command) | What I expected | What I found | What I concluded |
|---|-------------------------|-----------------|--------------|------------------|
| 1 | 05 (systemctl --failed) | nightly-report failing | two units failed: legacy-sync and nightly-report | two leads; check which one is related to the ticket |
| 2 | 2 journalctl -u nightly-report -b| I expected to see the error log for nightly-report |  Found error: "No space left on device"| The disk is full, causing the service to fail. |
| 3 |  df -h | I expected the /var partition to be full |The /var partition has 50% free space | Ruled out the /var partition. The issue must be in /tmp or /home. | 
| 4 | df -h /tmp | I expected to see the space usage of /tmp | Found /tmp is 100% full|  Found the root cause: /tmp is full, blocking the report generation.3| 





