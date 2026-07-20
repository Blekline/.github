# Welcome to Blekline

<p align="center">
  <img
    alt="Blekline — Zero-trust execution plane for AI agents"
    src="./blekline_readme-main.png"
    width="100%"
  />
</p>

**Zero-trust execution plane for AI agents.**

*Blekline is NHIM + open-core AI runtime enforcement* — it governs every prompt, model API, and tool call at the agent boundary. Mask secrets and PII, enforce tool policy, and audit metadata **before** traffic reaches LLMs, downstream MCP tools, and L1 sandboxes (Daytona, Modal, E2B, Cloudflare, Vercel Sandbox).

Run it in Cursor, Claude Desktop, or Codex in minutes with `@blekline/mcp-server`, sit `@blekline/mcp-proxy` in front of any downstream MCP, or deploy the **ingress sidecar** for edge mask + enforce. Apache SDK for embed; AGPL server/proxy for self-host or [cloud](https://app.blekline.com).

| Open source ([blekline-oss](https://github.com/Blekline/blekline-oss)) | Enterprise (NHIM image) |
| --- | --- |
| MCP server, proxy, contracts, SDK | Trust Vault (stateful tokenization in VPC) |
| Ingress sidecar shell + Helm | Lineage Firewall engine |
| Cursor hooks | Runtime crypto + admission webhook |

**Blekline Cloud** adds authoritative Azure PII masking, workspace fleet policy (SSE), investigations, and billing — for teams moving agents from pilot to production.

---

### Start here

| | Link |
|---|------|
| **Website** | [blekline.com](https://blekline.com) |
| **Open source** | [github.com/Blekline/blekline-oss](https://github.com/Blekline/blekline-oss) |
| **Documentation** | [app.blekline.com/docs](https://app.blekline.com/docs/introduction/quick-start) |
| **Cloud workspace** | [app.blekline.com](https://app.blekline.com) |
| **Community** | [Discussions](https://github.com/Blekline/blekline-oss/discussions) · [Design partner intake](https://github.com/Blekline/blekline-oss/issues/new?template=design_partner.yml) |
| **npm** | [`@blekline/mcp-server`](https://www.npmjs.com/package/@blekline/mcp-server) · [`@blekline/mcp-proxy`](https://www.npmjs.com/package/@blekline/mcp-proxy) |

### Guides worth reading

- [Why ingress governance](https://app.blekline.com/docs/introduction/why-ingress) — the Layer 4 gap between agents and runtimes
- [AI Enablement Stack](https://app.blekline.com/docs/introduction/ai-enablement-stack) — where Blekline sits (L4) vs sandboxes (L1) and agents (L5)
- [MCP proxy](https://app.blekline.com/docs/mcp/proxy) — allow / mask / block tool args before downstream MCP
- [Trust boundaries](https://app.blekline.com/docs/security/trust-boundaries) — what leaves your perimeter
- [EU AI Act & compliance](https://app.blekline.com/docs/introduction/eu-ai-act) — oversight, audit, and tool transparency
- [Sandbox providers](https://app.blekline.com/docs/integrations/sandbox-providers) — Daytona, Modal, E2B, Cloudflare, Vercel Sandbox

Read the full doc index at **[app.blekline.com/docs](https://app.blekline.com/docs)**.

---

### Get started in 2 minutes

Local MCP server (workspace token from [app.blekline.com](https://app.blekline.com) → Admin → API keys):

```bash
export BLEKLINE_WORKSPACE_TOKEN="blw_..."
export BLEKLINE_API_URL="https://app.blekline.com"
npx -y @blekline/mcp-server
```

**Cursor** — add to `.cursor/mcp.json`:

```json
{
  "mcpServers": {
    "blekline": {
      "command": "npx",
      "args": ["-y", "@blekline/mcp-server"],
      "env": {
        "BLEKLINE_WORKSPACE_TOKEN": "blw_...",
        "BLEKLINE_CLIENT_SURFACE": "cursor"
      }
    }
  }
}
```

In the agent: *"Use blekline_mask_prompt on: Contact Jane at jane@acme.com — API key AKIAIOSFODNN7EXAMPLE"*

**Proxy + sandbox** — [Daytona stack](https://app.blekline.com/docs/integrations/daytona-stack) · [All sandbox providers](https://app.blekline.com/docs/integrations/sandbox-providers)

---

<p align="center">
  <a href="https://github.com/Blekline/blekline-oss"><img src="https://img.shields.io/github/stars/Blekline/blekline-oss?style=social" alt="Star blekline-oss" /></a>
  &nbsp;
  <a href="https://github.com/Blekline/blekline-oss/actions/workflows/oss-ci.yml"><img src="https://github.com/Blekline/blekline-oss/actions/workflows/oss-ci.yml/badge.svg" alt="CI" /></a>
  &nbsp;
  <img src="https://img.shields.io/badge/Proxy%20%26%20server-AGPL%20v3-blue.svg" alt="AGPL v3" />
  &nbsp;
  <img src="https://img.shields.io/badge/SDK%20%26%20contracts-Apache%202.0-green.svg" alt="Apache-2.0" />
</p>

<p align="center">
  <a href="https://blekline.com">Website</a> ·
  <a href="https://app.blekline.com">Cloud</a> ·
  <a href="https://app.blekline.com/docs/introduction/quick-start">Docs</a> ·
  <a href="https://github.com/Blekline/blekline-oss/discussions">Discussions</a> ·
  <a href="https://github.com/Blekline/blekline-oss/issues/new?template=design_partner.yml">Design partners</a>
</p>
