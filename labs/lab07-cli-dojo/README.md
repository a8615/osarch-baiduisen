# Lab 7 — CLI dojo

Pair:                     Driver first half:
Machine:VM workstation PRO
Date: 27.11.2026

## What I did
This took me a while but I finished all 20 challenges in CMD. I tried not to open any GUI. The commands and time are in this table:

| # | Challenge | Command | Time |
|---|---|---|---|
| 1 | Print full path | cd | 00:05 |
| 2 | Computer name and account | hostname & whoami | 00:08 |
| 3 | Create logs\old and backup | mkdir C:\dojo\logs\old C:\dojo\backup | 00:15 |
| 4 | Create notes.txt | (echo dojo started& echo %time%) > C:\dojo\notes.txt | 00:45 |
| 5 | Show ping path | where ping | 00:10 |
| 6 | Show IPv4, Gateway, DNS | ipconfig /all \| findstr /i /c:"IPv4" /c:"Default Gateway" /c:"DNS Servers" | 01:20 |
| 7 | Save processes and print line count | tasklist > C:\dojo\procs.txt & type C:\dojo\procs.txt \| find /c /v "" | 00:30 |
| 8 | Start notepad, find PID, kill | start notepad & tasklist \| findstr /i notepad & taskkill /PID 1040 | 01:10 |
| 9 | Print only ERROR lines | findstr "ERROR" C:\dojo\logs\app.log | 00:15 |
| 10 | Count non-INFO lines | findstr /v "INFO" C:\dojo\logs\app.log \| find /c /v "" | 00:40 |
| 11 | Copy app.log and show sizes | copy C:\dojo\logs\app.log C:\dojo\backup\ & dir C:\dojo\logs\app.log C:\dojo\backup\app.log | 00:25 |
| 12 | Redirect errors to file | dir C:\nothing-here 2> C:\dojo\errors.txt | 00:12 |
| 13 | Ping gateway with OK or DOWN | ping -n 1 192.168.240.2 >nul && echo gateway OK \|\| echo gateway DOWN | 00:50 |
| 14 | Find user1 with line numbers | findstr /n /i "user1" C:\dojo\logs\app.log | 00:20 |
| 15 | Sort scores high to low | sort /r C:\dojo\scores.txt | 00:15 |
| 16 | List processes using > 50 MB | tasklist /fi "memusage ge 50000" | 00:35 |
| 17 | Find process on TCP 135 | netstat -ano \| findstr ":135" & tasklist \| findstr "440" | 01:05 |
| 18 | Hosts file test | echo 127.0.0.1 dojo.test >> C:\Windows\System32\drivers\etc\hosts & ping dojo.test -n 1 & notepad C:\Windows\System32\drivers\etc\hosts | 02:30 |
| 19 | List all files recursively | dir C:\dojo /s /a-d | 00:10 |
| 20 | Robocopy mirror and exit codes | robocopy C:\dojo\logs C:\dojo\backup\logs /mir /log:C:\dojo\robocopy.log & echo Exit code: %errorlevel% | 02:15 |

## Result

It worked. All 20 challenges are done. No GUI was used.

## What did not work the first time

I had a small issue in challenge 6. The ipconfig command gave me an error at first. I checked and fixed it, then the findstr command worked.

Also, for challenge 14, I expected 1 line but got 3 lines. I read the file and understood that the same user1 has INFO, ERROR, and WARN logs. 

For challenge 18, changing the hosts file was annoying because I had to open a new admin CMD window. But I did it and the ping worked.

## Evidence

- [evidence/output-all-challenges.txt](evidence/output-all-challenges.txt) 
- [evidence/](evidence/)
