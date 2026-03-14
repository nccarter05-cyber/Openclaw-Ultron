# Alerts & Warnings

Real-time tracking of budget warnings, performance issues, and system health.

---

## Active Alerts

🟢 **All clear** — No active warnings (2026-03-14 04:07 UTC)

---

## Alert Types

### Budget Alerts

**🟡 YELLOW** — Approaching 75% of daily budget
- Action: Use caution with expensive operations
- Timeline: Still have 25% to work with

**🔴 RED** — Hit 100% of budget
- Action: STOP—No more API calls until next day/month
- Timeline: Wait for reset

### Performance Alerts

**🟡 YELLOW** — Cache hit rate <85%
- Cause: Too many different topics, less context reuse
- Fix: Archive completed projects

**🟡 YELLOW** — Context usage >60%
- Cause: Vault is growing, using more memory
- Fix: Compress old notes, move to archive

**🟡 YELLOW** — Response time >30s
- Cause: System overload or network issue
- Fix: Wait or check connection

**🔴 RED** — Out of context space
- Cause: Hit the 200k limit
- Fix: STOP—need to immediately compress vault

---

## Alert History

| Date | Time | Type | Status | Resolution |
|------|------|------|--------|-----------|
| 2026-03-14 | 04:07 | None | — | All systems nominal |

---

## How to Respond

### When I Alert You

**Yellow Alert:**
- I mention it in my response
- No action required, just be aware
- Use more selectively if you want to optimize

**Red Alert:**
- I STOP and refuse to continue
- I explain what needs to happen
- Wait for your fix before continuing

### When to Check

- At session start: `Read alerts in [[mission-control/alerts.md]]`
- During work: I'll mention if threshold crossed
- Before expensive task: Check budget remaining

---

## Thresholds

| Alert Type | Yellow | Red |
|-----------|--------|-----|
| Daily Budget | $0.75 (75%) | $1.00 (100%) |
| Monthly Budget | $3.75 (75%) | $5.00 (100%) |
| Cache Hit | 85% | N/A |
| Context Usage | 60% | 100% |
| Response Time | 30s | 60s |

---

## Escalation Path

1. **Yellow:** Log it here, keep working
2. **Red:** Log it here, STOP, wait for fix
3. **System Down:** Can't work, contact host

---

**Last checked:** 2026-03-14 04:07 UTC
**Next check:** Before high-cost operations
