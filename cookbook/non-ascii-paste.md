---
command: sed -i 's/\x97/-/g' "$FILE" && grep -nP '[^\x00-\x7F]' "$FILE"
when_to_use: Python (or other source) fails with "Non-UTF-8 code starting with
  \x97" after text was pasted through PuTTY/SSH; \x97 is a mangled em dash.
tested_on: 2026-10-12, any Linux with GNU sed/grep
expected_output: grep prints nothing once the file is clean ASCII; any lines
  printed are remaining non-ASCII characters to fix.
---
Prevention: keep generated/pasted source code pure ASCII (use - not em dash).
Prose files tolerate fancy punctuation; source files do not survive terminal
clipboard round-trips. Other common culprits: \x92 (curly apostrophe),
\x93/\x94 (curly quotes) - same sed pattern with the right byte.