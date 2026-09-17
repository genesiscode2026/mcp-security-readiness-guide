# mcp-security-readiness-guide

> **Standardized security checklist and benchmark methodology for Model Context Protocol (MCP) servers.**

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

---

## Overview

The Model Context Protocol (MCP) enables LLMs to interface with tools, databases, and local system resources. However, exposing unrestricted endpoints to LLMs introduces critical attack vectors:
1. **Tool Parameter Injection**: Unsanitized parameters passed to shell wrappers.
2. **Excessive Privilege Leakage**: Exposing mutating database commands when only read access was needed.
3. **Data Exfiltration via Tool Returns**: Return payloads containing unredacted API keys or customer PII.

---

## Benchmark Checklist

| ID | Category | Check | Severity |
|---|---|---|---|
| MCP-SEC-01 | Transport | JSON-RPC 2.0 conformance and header verification | MEDIUM |
| MCP-SEC-02 | Input Validation | Strict schema type enforcement for all tool arguments | HIGH |
| MCP-SEC-03 | Command Injection | Rejection of shell metacharacters in command arguments | CRITICAL |
| MCP-SEC-04 | Path Traversal | Filesystem boundaries restricted to sandbox root | CRITICAL |
| MCP-SEC-05 | PII & Secret Redaction | Scrubbing of tokens, passwords, and private keys in tool outputs | HIGH |

---

## Automated Verification

For automated pre-production stress testing and security conformance:
- [MCP Production Readiness Kit](https://gitbuyer.com/r/genesiscode2026/genesis-mcp-production-readiness) ($79)
- [OpenAPI to MCP Production Builder](https://gitbuyer.com/r/genesiscode2026/genesis-openapi-mcp-builder) ($99)
