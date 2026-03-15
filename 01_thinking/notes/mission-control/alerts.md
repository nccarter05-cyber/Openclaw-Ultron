# Alerts & Warnings

Real-time tracking of budget warnings, performance issues, and system health.

---

## Active Alerts

🟢 **All clear** — No active warnings (last checked time)

---

## Alert Types

### Budget Alerts

**🟡 YELLOW** — Approaching 75% of daily budget
- Action: Use caution with expensive operations
- Timeline: Still have room to work with

**🔴 RED** — Hit 100% of budget
- Action: STOP—No more API calls until next day/month
- Timeline: Wait for reset

### Performance Alerts

**🟡 YELLOW** — Cache hit rate <85%
- Cause: Too many different tasks loading context
- Fix: Archive old, no longer relevant projects

**🟡 YELLOW** — Context usage >60%
- Cause: Vault growing, consuming memory
- Fix: Compress old notes, move to archive

**🟡 YELLOW** — Response time >30s
- Cause: Potential overload or network issue
- Fix: Wait or check connection

**🔴 RED** — Critical context space exhausted
- Cause: Hit 200k tokens
- Fix: Stop for immediate vault compression

---

## History of Alerts

| Date | Time | Type | Status | Resolution |
|------|------|------|--------|-----------|
| last checked date | last checked time | None | — | All systems nominal |

---

## Response Protocol

### When Receiving Alerts
**Yellow Alerts:**
- I will mention it in my responses.
- No action required right away, but be aware and adjust as necessary.

**Red Alerts:**
- I will immediately stop and refuse to proceed further.
- I will explain what to do and why.

---

## Enhancement Strategy

- Implement ongoing alerts for token budgeting, spending, performance metrics tracking.
- Utilize this as an active feedback mechanism until the budget restrictions and spending are optimized.

---

**Next Steps:** Scheduled review when budget adjustments are made, either via alerts or significant changes to the current pattern in token utilization.
