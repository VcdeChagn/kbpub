---
command: python3 -m py_compile "$FILE" && echo COMPILES
when_to_use: Cheap syntax check of a Python file without importing or running it.
tested_on: 2026-10-12, any Linux with python3
expected_output: COMPILES on success; SyntaxError with file/line on failure.
---
Catches syntax errors, bad encoding, and typos in structure, but NOT runtime
errors or bad imports (it never executes the module). Pair with the real
launch test afterwards. On a SyntaxError about non-UTF-8 bytes, see
non-ascii-paste.md.