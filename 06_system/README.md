# 06_system README

Authoritative system files for Ultron. Load these as instructed.

| File | Purpose | When to Load |
|------|---------|--------------|
| `SOUL.md` | Identity, rate limits, planning rules, model policy | Session start (always) |
| `IDENTITY.md` | Name, vibe, persona details | Session start |
| `USER.md` | Snapshot of Nate (name, timezone, focus) | Session start |
| `AGENTS.md` | Operating procedures (what to read, safety, heartbeats) | Session start + whenever workflow questions arise |
| `TOOLS.md` | Environment-specific tool notes | When using local tools/devices |
| `HEARTBEAT.md` | Periodic check instructions | Only when receiving heartbeat prompt |
| `MEMORY.md` | Long-term curated memory | Main session only (never auto-load in shared contexts) |
| `MODEL_ESCALATION.md` | Rules for switching to Sonnet | Before complex reasoning/debugging tasks |

## How to Use
- **Single Source of Truth:** All system rules now live here. Root files only reference these.
- **Session Start Checklist:** Read `SOUL.md`, `IDENTITY.md`, `USER.md`, `AGENTS.md`, latest `memory/YYYY-MM-DD.md`.
- **Security:** Do not copy these files elsewhere; update here only.
- **Updates:** If you change any system rule, log it in MEMORY.md and inform Nate.
