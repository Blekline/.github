# Welcome to Blekline

<p align="center">
  <a href="https://blekline.com">
    <img
      alt="Blekline"
      src="https://github.com/Blekline/blekline-oss/raw/main/assets/images/blekline-logo-dark.svg"
      width="320"
    />
  </a>
</p>

**Blekline is workflow execution infrastructure for AI actions.** Platform teams publish runtime policy, start **act runs**, and run steps in short-lived **cells** in **your cloud**. Ingress clients mask prompts, enforce tool calls, and record **metadata-first audit** before traffic reaches models and downstream MCP tools.

This org ships **[blekline-oss](https://github.com/Blekline/blekline-oss)** (clients, contracts, and agent ingress). **Cells run on [app.blekline.com](https://app.blekline.com)** (hosted or connected compute).

Connect Cursor, Claude Desktop, Codex, or your own agents with `@blekline/mcp-server` and `@blekline/mcp-proxy`, or embed the Apache SDK. Use [Blekline Cloud](https://app.blekline.com) for workspaces, fleet policy, investigations, and billing.

| Open source ([blekline-oss](https://github.com/Blekline/blekline-oss)) | Platform |
| --- | --- |
| MCP server, proxy, contracts, SDK | Workflows, act runs, cells |
| Cursor / Codex hooks | Policy compile at run start |
| `cluster-posture` CLI | Metadata audit and investigations |

---

### Start here

| | Link |
|---|------|
| **Website** | [blekline.com](https://blekline.com) |
| **Open source** | [github.com/Blekline/blekline-oss](https://github.com/Blekline/blekline-oss) |
| **First workflow run** | [app.blekline.com/docs/workflows-and-runs](https://app.blekline.com/docs/workflows-and-runs) |
| **Documentation** | [app.blekline.com/docs](https://app.blekline.com/docs) |
| **Cloud workspace** | [app.blekline.com](https://app.blekline.com) |
| **Community** | [Discussions](https://github.com/Blekline/blekline-oss/discussions) · [Design partner intake](https://github.com/Blekline/blekline-oss/issues/new?template=design_partner.yml) |
| **npm** | [`@blekline/init`](https://www.npmjs.com/package/@blekline/init) · [`@blekline/client`](https://www.npmjs.com/package/@blekline/client) · [`@blekline/mcp-server`](https://www.npmjs.com/package/@blekline/mcp-server) |

### Guides worth reading

- [Workflows and runs](https://app.blekline.com/docs/workflows-and-runs) — act runs, cells, and your cloud
- [Runtime policy](https://app.blekline.com/docs/runtime-policy) — publish policy before execution
- [AI Enablement Stack](https://app.blekline.com/docs/introduction/architecture) — where Blekline sits vs sandboxes and agents
- [MCP proxy](https://app.blekline.com/docs/mcp/proxy) — allow, mask, and block tool args before downstream MCP
- [Interaction governance](https://app.blekline.com/docs/introduction/interaction-governance) — mask and enforce at the agent boundary
- [Trust boundaries](https://app.blekline.com/docs/security/trust-boundaries) — what leaves your perimeter

Read the full doc index at **[app.blekline.com/docs](https://app.blekline.com/docs)**.

---

### First act run (~60 seconds)

[Create a workspace](https://app.blekline.com/auth/signup), add an API key with **runs:write**, publish [runtime policy](https://app.blekline.com/docs/runtime-policy), then:

```bash
npx -y @blekline/init
export BLEKLINE_WORKSPACE_TOKEN="blw_..."
export BLEKLINE_API_URL="https://app.blekline.com"
export BLEKLINE_WORKFLOW_ID="wf_your_workflow_id"
```

Guide: [Run first workflow](https://app.blekline.com/docs/workflows-and-runs) · Example: [first-act-run](https://github.com/Blekline/blekline-oss/tree/main/examples/cells/first-act-run)

**Cursor ingress** — add to `.cursor/mcp.json`:

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
  <a href="https://app.blekline.com/docs">Docs</a> ·
  <a href="https://github.com/Blekline/blekline-oss/discussions">Discussions</a> ·
  <a href="https://github.com/Blekline/blekline-oss/issues/new?template=design_partner.yml">Design partners</a>
</p>