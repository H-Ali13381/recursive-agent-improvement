# Tool wrapper placeholder

Agent-facing inference wrappers go here later.

Preferred behavior:

- accept JSON input
- return JSON output
- include confidence and threshold metadata
- fail with structured errors
- avoid loading model weights repeatedly if latency matters

Possible targets:

- CLI script
- Python function
- local HTTP service
- MCP server
- Hermes native tool
