# Lab 5 — Encoding forensics

Pair:                     Driver first half:
Machine:VMware workstation PRO
Date:13.11.2026

## What I did
Steps, with commands in code blocks. Not prose about the steps.

```
file staff-broken.csv
#Output: staff-broken.csv: Non-ISO extended-ASCII text, with CRLF line terminators

xxd -l 16 staff-broken.csv
#Output: 00000000: d2e0 e12e b93b d4c8 ce3b c4ee ebe6 edee

bash scripts/fix.sh
#Output: Unicode text, UTF-8 (with BOM) text
#Output: 00000000: efbb bfD0 a2D0 b0D0 b12e 2e84 963b d0a4
```


## Result
Successfully identified the source encoding as RK1048 (or PT154) with CRLF line endings and no BOM. Converted the file to UTF-8 with BOM and LF line endings. The fixed file now opens correctly in Excel, LibreOffice Calc, and Linux terminal.
## What did not work the first time
At least one thing. What I saw, what it turned out to be, what I did about it.
Initially, Excel showed complete garbage, and LibreOffice showed different mojibake. This was because Excel assumed local ANSI without a BOM, and LibreOffice guessed the wrong Cyrillic encoding, causing the specific Kazakh letters (like Ә, Ғ) to be lost. Using the cat command in the terminal also showed mojibake because it defaulted to UTF-8 decoding for a single-byte file


## Evidence
- [file-before.txt](evidence/file-before.txt) — proves the original encoding and line endings.
- [hexdump-before.txt](evidence/hexdump-before.txt) — proves the exact byte sequence before the fix.
- [opens-correctly.png](evidence/opens-correctly.png) — proves the file opens without errors in Excel, LibreOffice, and the terminal.
- [staff-broken.csv](evidence/staff-broken.csv) — the original untouched file.
- [staff-fixed.csv](evidence/staff-fixed.csv) — the successfully repaired file.
