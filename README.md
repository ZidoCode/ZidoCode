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

### [context-audit](https://github.com/ZidoCode/context-audit)
Context-window forensics for Hermes agents.

- 📈 Per-turn token estimates (input/output) — watch your context burn in real numbers
- 🍴 Flags the **largest tool output of every turn** and oversized calls (args > 50 KB) — find your context eaters
- 🗜 Detects compaction events, so you know when history got trimmed under you
- 🔒 Metadata only: tool names, byte lengths, ids, timestamps — **never args or results**
- 💬 `/context-audit` slash command: top 5 context eaters over a window, one mitigation each

Also submitted to the official Hermes plugin catalog (PR pending review).

### [skill-integrity](https://github.com/ZidoCode/skill-integrity)
Rug-pull detection for installed agent skills.

- 🧬 SHA-256 fingerprints of every skill file — any byte change after install is loud
- 📋 Snapshots record which directories they cover, so `check` can't mass-false-positive on a dirs mismatch
- ⚠️ Honest blind spots: files skipped as oversize (> 512 KB) and symlinks are counted and reported, never silently ignored
- ⏰ Cron-friendly: exit 1 on findings by default, `--json` for machines
- 🔏 Reads skills only; state lives in `~/.skill-integrity/`

### [agent-janitor](https://github.com/ZidoCode/agent-janitor)
Housekeeping for agent state — stale sessions, caches, and scratch files
before they eat the disk. Dry-run first, explicit confirmation for deletes.

### [cachewatch](https://github.com/ZidoCode/cachewatch)
Local-first LLM cache-hit observability proxy — see your real prompt-cache
hit rate per model, per day.

### [zidorouter](https://github.com/ZidoCode/zidorouter)
Personal LLM gateway: multi-provider failover, per-client API keys with
quotas, usage tracking, and a purple dashboard. Built for zero-cost
resilience — I route my own agent through it.

## Principles

1. **Observe, don't interfere** — tools that watch agents must never change agent behavior
2. **Honest coverage** — every report states exactly what is and isn't detectable; no security theater
3. **Local-first** — your ledger, your secrets, your machine
4. **Dogfooded** — every tool here runs live in my own agent stack, not just in CI

---
*Building in public. Security researcher × indie developer.*
