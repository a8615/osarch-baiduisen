# Lab 7 — CLI dojo

Pair:                     Driver first half:
Machine:VM workstation PRO
Date: 27.11.2026

## What I did
I completed all 20 challenges using only the command line. I didn't use any GUI tools like Task Manager. Here is the table with the commands I used and the time:

| # | Challenge | Command | Time |
|---|---|---|---|
| 1 | Print full path | cd | 00:01 |
| 2 | Computer name and account | hostname & whoami | 00:01 |
| 3 | Create logs\old and backup | mkdir C:\dojo\logs\old C:\dojo\backup | 00:02 |
| 4 | Create notes.txt | (echo dojo started& echo %time%) > C:\dojo\notes.txt | 00:02 |
| 5 | Show ping path | where ping | 00:01 |
| 6 | Show IPv4, Gateway, DNS | ipconfig /all \| findstr /i /c:"IPv4" /c:"Default Gateway" /c:"DNS Servers" | 00:03 |
| 7 | Save processes and print line count | tasklist > C:\dojo\procs.txt & type C:\dojo\procs.txt \| find /c /v "" | 00:02 |
| 8 | Start notepad, find PID, kill | start notepad & tasklist \| findstr /i notepad & taskkill /PID 1040 | 00:03 |
| 9 | Print only ERROR lines | findstr "ERROR" C:\dojo\logs\app.log | 00:02 |
| 10 | Count non-INFO lines | findstr /v "INFO" C:\dojo\logs\app.log \| find /c /v "" | 00:02 |
| 11 | Copy app.log and show sizes | copy C:\dojo\logs\app.log C:\dojo\backup\ & dir C:\dojo\logs\app.log C:\dojo\backup\app.log | 00:02 |
| 12 | Redirect errors to file | dir C:\nothing-here 2> C:\dojo\errors.txt | 00:02 |
| 13 | Ping gateway with OK or DOWN | ping -n 1 192.168.240.2 >nul && echo gateway OK \|\| echo gateway DOWN | 00:03 |
| 14 | Find user1 with line numbers | findstr /n /i "user1" C:\dojo\logs\app.log | 00:02 |
| 15 | Sort scores high to low | sort /r C:\dojo\scores.txt | 00:02 |
| 16 | List processes using > 50 MB | tasklist /fi "memusage ge 50000" | 00:02 |
| 17 | Find process on TCP 135 | netstat -ano \| findstr ":135" & tasklist \| findstr "440" | 00:03 |
| 18 | Hosts file test | echo 127.0.0.1 dojo.test >> C:\Windows\System32\drivers\etc\hosts & ping dojo.test -n 1 & notepad C:\Windows\System32\drivers\etc\hosts | 00:05 |
| 19 | List all files recursively | dir C:\dojo /s /a-d | 00:02 |
| 20 | Robocopy mirror and exit codes | robocopy C:\dojo\logs C:\dojo\backup\logs /mir /log:C:\dojo\robocopy.log & echo Exit code: %errorlevel% | 00:05 |

## Result

The experiment was successful. I managed to solve all 20 challenges within the time limit. The commands prove that no graphical interface was used. The text output and screenshots show the results for each challenge.

## What did not work the first time

At first, I had some trouble with challenge 6. When I ran the ipconfig command, the terminal showed an error saying it was not recognized. I checked my typing and realized I needed to make sure the command was typed correctly in plain English. After I fixed it, the findstr command worked and showed the IP address and DNS servers.

Also, for challenge 14, my findstr command showed 3 lines instead of 1. I looked at the log file and understood it's because the file contains multiple log levels that mention user1. 

For challenge 18, I had to open a new administrator command prompt to edit the hosts file, which was a bit tricky but I managed to ping it and undo the changes.

## Evidence

- [evidence/output-all-challenges.txt](evidence/output-all-challenges.txt) - Contains the text logs for all 20 challenges
- [evidence/](evidence/) - Contains the text logs and screenshots of the commands 

