---
command: python3 server.py   # exits 0 instantly? check for missing mcp.run() call
when_to_use: MCP server starts then dies immediately with exit code 0 and no error.
tested_on: 2026-10-12, any Linux with python3
expected_output: Without the fix: process exits 0 in <1s, no banner. With mcp.run()
  added: process hangs (waiting on stdio) and prints "Starting MCP server ...".
---
Exit 0 with no output means the tool functions registered and the script
returned normally — the transport loop was never started. Fix: add
`mcp.run()` as the last line of the server script, outside any tool
definitions. The "hang = alive" test is the positive check.