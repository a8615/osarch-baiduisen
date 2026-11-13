
# Lab 5 - Encoding forensics

## Diagnosis (before the fix)

- file says: Non-ISO extended-ASCII text, with CRLF line terminators

- First 16 bytes: d2e0 e12e b93b d4c8 ce3b c4ee ebe6 edee

### Annotate the bytes

| Offset | Bytes | What they are |

| :--- | :--- | :--- |

| 00 - 02 | d2 e0 e1 | Cyrillic/Kazakh letters (single-byte encoding) |

| 03 | 2e | Period . (ASCII) |

| 04 - 06 | b9 3b d4 | Cyrillic/Kazakh letters |
-Encoding: RK1048 (or PT154) - evidence: iconv testing.
-Line ending: CRLF - evidence: file command shows CRLF.
-BOM: absent - evidence: starts with d2e0.
## what went wrong
-Excel: No BOM, assumed ANSI
-LibreOffice: Guessed wrong encoding
-cat: Decoded as UTF-8, showed mojibake
##Fix
-command:scripts/fix.sh
-changed: Converted to UTF-8, changed to LF, added BOM
## Verification
- file after: UTF-8 (with BOM)
- original SHA256: 919027f1f8c71d85cba3f12aad0f6c927d4e0450cfb2a2d63378a69f14cab270
- Evidence: See evidence/opens-correctly /png
