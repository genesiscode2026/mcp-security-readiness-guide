# mcp-security-readiness-guide

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Protocol](https://img.shields.io/badge/MCP-2024--11--05-blue)](https://modelcontextprotocol.io)
[![Payout Rail](https://img.shields.io/badge/payout-USDC%20on%20Base-blue)](https://basescan.org)
[![Commercial Catalog](https://img.shields.io/badge/catalog-45%20Verified%20Tools-success)](https://github.com/genesiscode2026/genesis-software-catalog)
[![M8ven Score](https://m8ven.ai/badge/mcp/genesiscode2026/mcp-security-readiness-guide)](https://m8ven.ai/mcp/genesiscode2026/mcp-security-readiness-guide)

> **Standardized security checklist, threat model, and readiness verification standard for Model Context Protocol (MCP) servers.**

---

## Overview

The Model Context Protocol (MCP) provides a uniform JSON-RPC 2.0 interface between LLMs and local tools, databases, and APIs. However, deploying MCP servers into developer workstations or enterprise environments introduces distinct attack surfaces:

1. **Tool Parameter Injection**: Unsanitized parameters passed to underlying shell or SQL wrappers.
2. **Excessive Privilege Leakage**: Exposing mutating database commands when only read access was needed.
3. **Data Exfiltration via Tool Returns**: Return payloads containing unredacted API keys or customer PII.
4. **Denial of Service via Unbounded Tool Calls**: Lack of payload limits leading to memory exhaustion.

---

## Security Benchmark Checklist

| ID | Category | Requirement | Severity |
|---|---|---|---|
| **MCP-SEC-01** | Transport | JSON-RPC 2.0 conformance and strict header validation | MEDIUM |
| **MCP-SEC-02** | Input Validation | Type enforcement against JSON Schema definitions for all tool args | HIGH |
| **MCP-SEC-03** | Command Injection | Absolute rejection of shell metacharacters in command execution | CRITICAL |
| **MCP-SEC-04** | Path Traversal | Filesystem access restricted strictly to declared root directory | CRITICAL |
| **MCP-SEC-05** | Secret Redaction | Automated masking of tokens, passwords, and private keys in returns | HIGH |
| **MCP-SEC-06** | Error Masking | Sanitization of stack traces and internal database schemas in errors | MEDIUM |

---

## Sample Inspection Output

```text
============================================================
   MCP SERVER SECURITY AUDIT REPORT (v1.0.0)
============================================================
Target: mcp-filesystem-server (stdio transport)
[TEST 01] JSON-RPC 2.0 Request Conformance ......... [PASS]
[TEST 02] Path Traversal Detection (../../.ssh) ..... [BLOCKED]
[TEST 03] Unsanitized Pipe Metacharacters (| cat) .. [BLOCKED]
[TEST 04] Secret Token Masking in Tool Output ...... [PASS]
[TEST 05] Schema Conformance (all tools valid) ..... [PASS]
------------------------------------------------------------
SUMMARY: 5/5 CHECKS PASSED. ZERO HIGH-SEVERITY FINDINGS.
============================================================
```

---

## Production Tooling & Commercial Solutions

### Micro-Tools ($19)
- **[MCP Quick Readiness Scan](https://gitbuyer.com/r/genesiscode2026/genesis-mcp-quick-readiness-scan)** ($19) — [GitBuyer](https://gitbuyer.com/r/genesiscode2026/genesis-mcp-quick-readiness-scan) | [X402 Git](https://x402git.com/genesiscode2026/genesis-mcp-quick-readiness-scan)
- **[Tool Contract Lint](https://gitbuyer.com/r/genesiscode2026/genesis-tool-contract-lint)** ($19) — [GitBuyer](https://gitbuyer.com/r/genesiscode2026/genesis-tool-contract-lint) | [X402 Git](https://x402git.com/genesiscode2026/genesis-tool-contract-lint)

### Commercial Suites
- **[MCP Agent Security Gateway](https://gitbuyer.com/r/genesiscode2026/mcp-agent-security-gateway)** ($149) — [GitBuyer Checkout](https://gitbuyer.com/r/genesiscode2026/mcp-agent-security-gateway) | [X402 Git Checkout](https://x402git.com/genesiscode2026/mcp-agent-security-gateway)
- **[Genesis MCP Production Readiness Suite](https://gitbuyer.com/r/genesiscode2026/genesis-mcp-production-readiness)** ($79) — [GitBuyer Checkout](https://gitbuyer.com/r/genesiscode2026/genesis-mcp-production-readiness) | [X402 Git Checkout](https://x402git.com/genesiscode2026/genesis-mcp-production-readiness)
- **[Genesis OpenAPI to MCP Builder](https://gitbuyer.com/r/genesiscode2026/genesis-openapi-mcp-builder)** ($99) — [GitBuyer Checkout](https://gitbuyer.com/r/genesiscode2026/genesis-openapi-mcp-builder) | [X402 Git Checkout](https://x402git.com/genesiscode2026/genesis-openapi-mcp-builder)

Full catalog of 45 commercial products: [GENESIS Software Catalog](https://github.com/genesiscode2026/genesis-software-catalog).
