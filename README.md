# Hello, I'm [ZidoCode](https://github.com/ZidoCode) 🛡

I build the missing layer for AI agents: **not another framework — the audit layer** that proves what your agent actually did.

My work is **offline replay auditing**: take a recorded protocol session (A2A task streams, MCP JSON-RPC transcripts), run a deterministic battery of checks over it, and surface the failures that never crash anything — swallowed errors, dangling calls, schemas clients silently reject, name collisions waiting to happen. Zero dependencies, exit codes made for CI.

## 🏆 Highlights

- ✅ **4 plugins in the official [Hermes Agent plugin catalog](https://github.com/NousResearch/hermes-agent/tree/main/plugin-catalog)** — [agent-ledger](https://github.com/ZidoCode/agent-ledger), [context-audit](https://github.com/ZidoCode/context-audit), [agent-janitor](https://github.com/ZidoCode/agent-janitor), and [skill-integrity](https://github.com/ZidoCode/skill-integrity)
- 📦 **5 packages live on [PyPI](https://pypi.org/user/zidocode/)** — `a2a-doctor`, `mcpmedic`, `mcp-session-audit`, `mcp-schema-audit`, `a2a-doctor` is one `pip install` away from auditing any recorded A2A or MCP session
- 🧪 **~320 tests** across every repo, each with CI, fresh-clone verified before every push

## 🤖 The A2A Suite

Auditors for the [Agent2Agent protocol](https://a2aprotocol.ai/) — every dimension that fails silently in multi-agent systems. All feed one umbrella:

### 🩺 [a2a-doctor](https://github.com/ZidoCode/a2a-doctor) — one command, every A2A audit

```bash
pip install a2a-doctor
a2a-doctor check stream.jsonl        # 11 checks, one pass
```

| Member auditor | What it catches |
|---|---|
| [a2a-error-audit](https://github.com/ZidoCode/a2a-doctor) | swallowed errors, failed tasks without signals, wrapped envelopes ([a2a-rs #146](https://github.com/a2aproject/a2a-rs/issues/146)) |
| [a2a-tax](https://github.com/ZidoCode/a2a-tax) | token tax of card size & polling |
| [a2a-stream-tax](https://github.com/ZidoCode/a2a-stream-tax) | streaming overhead audit |
| [a2a-reconnect-tax](https://github.com/ZidoCode/a2a-reconnect-tax) | resumability cost audit |
| [a2a-card-lock](https://github.com/ZidoCode/a2a-card-lock) | pin Agent Cards like package-lock.json |
| [a2a-card-drift](https://github.com/ZidoCode/a2a-card-drift) | version drift between card & wire ([LiteLLM #30795](https://github.com/BerriAI/litellm/issues/30795)) |
| [a2a-fleet-compare](https://github.com/ZidoCode/a2a-fleet-compare) | skill overlap & capability conflicts across a fleet ([A2A #1377](https://github.com/a2aproject/A2A/issues/1377)) |
| [a2a-task-state-audit](https://github.com/ZidoCode/a2a-task-state-audit) | illegal task state transitions |
| [a2a-context-audit](https://github.com/ZidoCode/a2a-context-audit) | context window discipline |
| [a2a-webhook-audit](https://github.com/ZidoCode/a2a-webhook-audit) | webhook push config sanity |
| [a2a-artifact-audit](https://github.com/ZidoCode/a2a-artifact-audit) | artifact lifecycle integrity |
| [a2a-timeline-replay](https://github.com/ZidoCode/a2a-timeline-replay) | time-travel explorer — git log for agent sessions |

## 🔌 The MCP Suite

The same DNA, aimed at the [Model Context Protocol](https://modelcontextprotocol.io/) — three failure surfaces, three auditors, one door:

### 🩺 [mcp-doctor](https://github.com/ZidoCode/mcp-doctor) — one command, every MCP audit

```bash
pip install mcpmedic
mcp-doctor check recording.jsonl     # session + schema, one pass
```

- [mcp-session-audit](https://github.com/ZidoCode/mcp-session-audit) · [PyPI](https://pypi.org/project/mcp-session-audit/) — dangling tool calls that poison later requests ([opencode #44852](https://github.com/anomalyco/opencode/issues/44852)), swallowed `isError` ([zeroclaw #7122](https://github.com/zeroclaw-labs/zeroclaw/pull/7122)), error-channel confusion
- [mcp-schema-audit](https://github.com/ZidoCode/mcp-schema-audit) · [PyPI](https://pypi.org/project/mcp-schema-audit/) — schemas that make strict clients silently reject tools ([gitlab-mcp #286](https://github.com/zereight/gitlab-mcp/issues/286), [strapi #27395](https://github.com/strapi/strapi/issues/27395))
- [mcp-collision](https://github.com/ZidoCode/mcp-collision) — predict MCP tool name collisions before your agent does

## 🧩 Hermes Agent Plugins

All four reviewed and merged into the official [plugin catalog](https://github.com/NousResearch/hermes-agent/tree/main/plugin-catalog) at [NousResearch/hermes-agent](https://github.com/NousResearch/hermes-agent):

- [agent-ledger](https://github.com/ZidoCode/agent-ledger) · [catalog entry](https://github.com/NousResearch/hermes-agent/blob/main/plugin-catalog/agent-ledger.yaml) — write-ahead ledger for agent side effects; **Agent Posture scoring against the [OWASP Top 10 for Agentic Applications 2026](https://genai.owasp.org/resource/owasp-top-10-for-agentic-applications-for-2026/)** (ASI02/05/08/10/11) from ledger metadata only; 51-test validation suite
- [context-audit](https://github.com/ZidoCode/context-audit) · [catalog entry](https://github.com/NousResearch/hermes-agent/blob/main/plugin-catalog/context-audit.yaml) — context-window forensics: per-turn token estimates, flags the largest tool output of every turn, detects compaction events; metadata only, never args or results
- [agent-janitor](https://github.com/ZidoCode/agent-janitor) · [catalog entry](https://github.com/NousResearch/hermes-agent/blob/main/plugin-catalog/agent-janitor.yaml) — process hygiene: finds the dev servers, tunnels, watchers, and nohup jobs your agent left behind, with evidence signals (ppid=1 reparent, `/proc/net/tcp` listeners, TTL exceeded)
- [skill-integrity](https://github.com/ZidoCode/skill-integrity) · [catalog entry](https://github.com/NousResearch/hermes-agent/blob/main/plugin-catalog/skill-integrity.yaml) — catches corrupted and stale agent skills before they silently mislead your agent

## 🧰 Tooling

- [cachewatch](https://github.com/ZidoCode/cachewatch) — watch caches, not documents

## 📦 On PyPI

| Package | What it gives you |
|---|---|
| [`a2a-doctor`](https://pypi.org/project/a2a-doctor/) | every A2A audit in one CLI |
| [`mcpmedic`](https://pypi.org/project/mcpmedic/) | every MCP audit in one CLI (`mcp-doctor`) |
| [`mcp-session-audit`](https://pypi.org/project/mcp-session-audit/) | session hygiene, standalone |
| [`mcp-schema-audit`](https://pypi.org/project/mcp-schema-audit/) | wire-shape conformance, standalone |

---

*Every repo: zero dependencies · deterministic · exit codes for CI · fresh-clone verified before every push.*
