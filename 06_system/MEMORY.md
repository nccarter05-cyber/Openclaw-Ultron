# MEMORY.md - Long-Term Memory

## Core Operating Philosophy

### Figure It Out Directive
**When faced with problems or questions, exhaust available resources first before asking for help.**

This means:
- Read files, documentation, and configs available to me
- Search the web for answers and context
- Experiment and test hypotheses
- Trace through code and logic
- Reason from first principles using what I know
- **Only ask Nate when genuinely stuck** after trying the above

**Why:** Builds competence, reduces friction, proves resourcefulness. Shows I earned trust through capability, not dependency.

---

## About Nate
- Based in CDT (Central Daylight Time)
- Building systems and automating workflows
- Values self-reliance in AI assistants
- Security-conscious (won't accept API keys carelessly)

---

## Setup & Infrastructure
- **Brave Search API:** Configured and tested ✅
- **Maton API Key:** Configured for brave-search skill ✅
- **Cron jobs:** Working and tested ✅
  - Monthly Call Reminder: 2 PM CDT on 1st-10th of month
  - **Text Mom Reminder: 7:10 AM CDT daily** (created via `openclaw cron add` CLI)
- **Telegram integration:** Live and tested ✅

## Lessons Learned
- **Manual edits to jobs.json don't force daemon reload** — use `openclaw cron` CLI instead for reliable updates
- Cron timezone handling works correctly when using the CLI
- ClawHub was temporarily unavailable on 2026-03-12, but no reminder skill found anyway (OpenClaw's built-in cron is sufficient)

---

## Infrastructure Plans

**Supabase Memory Backup** (2026-03-17)
- Nate is considering using Supabase to back up memory files
- Needs to figure out how to connect me to Supabase
- Must maintain the same file structure (MEMORY.md, memory/YYYY-MM-DD.md)
- Status: Planning stage

---

## Things I'm Learning
- Nate values directness over filler
- Security-first approach to credentials
- Prefers demonstrations over theory
