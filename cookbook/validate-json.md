---
command: python3 -m json.tool "$FILE" > /dev/null && echo OK
when_to_use: Check a JSON file parses, without dumping the whole file.
tested_on: 2026-02-10, any Linux with python3
expected_output: "OK" on valid; a line/column parse error otherwise.
---
For pretty-printing instead: `python3 -m json.tool "$FILE"`.
With jq (if installed): `jq empty "$FILE" && echo OK`.
