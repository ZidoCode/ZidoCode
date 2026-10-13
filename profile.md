# ZidoCode 🛡

**Agent security & reliability tooling.**

Building the missing layer for AI agents: not another framework — the
**audit layer** that proves what your agent actually did.

## ✅ 2 plugins officially in the [Hermes Agent plugin catalog](https://github.com/NousResearch/hermes-agent/tree/main/plugin-catalog)

Both plugins were reviewed and merged into the official catalog at
[NousResearch/hermes-agent](https://github.com/NousResearch/hermes-agent).

## Open-source projects

### [agent-ledger](https://github.com/ZidoCode/agent-ledger) · [official catalog entry](https://github.com/NousResearch/hermes-agent/blob/main/plugin-catalog/agent-ledger.yaml)
Write-ahead ledger for Hermes Agent side effects.

- 🕵️ Catches **tool calls issued but silently lost** (compaction teardown)
- 🛡 **Agent Posture scoring** against the [OWASP Top 10 for Agentic Applications 2026](https://genai.owasp.org/resource/owasp-top-10-for-agentic-applications-for-2026/) — ASI02/05/08/10/11, from ledger metadata only
- 📊 Daily posture audit → Telegram (score delta, top findings)
- ✅ 51-test validation suite: ground-truth harness (benign=100, malicious detects all), per-ASI unit tests, adversarial evasion suite, 10k-row benchmark < 0.1s
- 🔍 Passed `hermes plugins validate` security scan — pure observer, no network calls, no env reads

**Officially in the Hermes plugin catalog** (v0.4.4, merged Oct 2026).

### [context-audit](https://github.com/ZidoCode/context-audit) · [official catalog entry](https://github.com/NousResearch/hermes-agent/blob/main/plugin-catalog/context-audit.yaml)
Context-window forensics for Hermes agents.

- 📈 Per-turn token estimates (input/output) — watch your context burn in real numbers
- 🍴 Flags the **largest tool output of every turn** and oversized calls (args > 50 KB) — find your context eaters
- 🗜 Detects compaction events, so you know when history got trimmed under you
- 🔒 Metadata only: tool names, byte lengths, ids, timestamps — **never args or results**
- 💬 `/context-audit` slash command: top 5 context eaters over a window, one mitigation each

**Officially in the Hermes plugin catalog** (v0.1.1, merged Oct 2026).
