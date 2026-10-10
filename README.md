# ZidoCode 🛡

**Agent security & reliability tooling.**

Building the missing layer for AI agents: not another framework — the
**audit layer** that proves what your agent actually did.

## Open-source projects

### [agent-ledger](https://github.com/ZidoCode/agent-ledger)
Write-ahead ledger for Hermes Agent side effects.

- 🕵️ Catches **tool calls issued but silently lost** (compaction teardown)
- 🛡 **Agent Posture scoring** against the [OWASP Top 10 for Agentic Applications 2026](https://genai.owasp.org/resource/owasp-top-10-for-agentic-applications-for-2026/) — ASI02/05/08/10/11, from ledger metadata only
- 📊 Daily posture audit → Telegram (score delta, top findings)
- ✅ 51-test validation suite: ground-truth harness (benign=100, malicious detects all), per-ASI unit tests, adversarial evasion suite, 10k-row benchmark < 0.1s
- 🔍 Passed `hermes plugins validate` security scan — pure observer, no network calls, no env reads

Submitted to the official Hermes plugin catalog (PR pending review).

### [cachewatch](https://github.com/ZidoCode/cachewatch)
Local-first LLM cache-hit observability proxy — see your real prompt-cache
hit rate per model, per day.

## Principles

1. **Observe, don't interfere** — tools that watch agents must never change agent behavior
2. **Honest coverage** — every report states exactly what is and isn't detectable; no security theater
3. **Local-first** — your ledger, your secrets, your machine

---
*Building in public. Security researcher × indie developer.*
