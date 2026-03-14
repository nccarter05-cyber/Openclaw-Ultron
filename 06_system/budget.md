# Budget Management System

System-level budget rules and controls for all OpenClaw operations.

---

## Budget Framework

### Daily Limit
- **Amount:** $1.00 USD
- **Reset:** Midnight UTC (00:00)
- **Warning Threshold:** $0.75 (75%)
- **Hard Stop:** $1.00 (100%)

### Monthly Limit
- **Amount:** $5.00 USD
- **Reset:** 1st of month at 00:00 UTC
- **Warning Threshold:** $3.75 (75%)
- **Hard Stop:** $5.00 (100%)

---

## How Budget Works

### Phases

**🟢 GREEN (0-75%)**
- Normal operations
- All tasks enabled
- No restrictions

**🟡 YELLOW (75-99%)**
- Approaching limit
- Warn on new requests
- Suggest cost optimization
- Batch expensive operations
- Prefer cheaper models if applicable

**🔴 RED (100%)**
- Hard stop
- No new API calls
- Log attempted requests
- Wait for reset

---

## Budget Behavior Rules

When operating under budget:

1. **Track every transaction**
   - Log to [[mission-control/budget.md]]
   - Include timestamp, tokens, cost, operation

2. **Batch similar requests**
   - 5 web searches at once instead of 1 search per request
   - Combine multiple small tasks into one call
   - Reuse cache hits (avoid duplicate context loads)

3. **Prefer efficient models**
   - Default: Haiku (cheapest, fast enough)
   - Switch to Sonnet only when absolutely needed:
     - Architecture decisions
     - Security analysis
     - Complex reasoning
     - Production code review

4. **Monitor cache efficiency**
   - Target: >90% cache hit rate
   - Reused context costs 90% less than new tokens
   - Check [[mission-control/performance.md]] weekly

5. **Keep context lean**
   - Target: <50% of token window used
   - Archive old projects to `05_archive/`
   - Compress old notes into summaries
   - Move rarely-used reference to external links

---

## When to Alert

### Daily Alert (Yellow)
```
Subject: Daily budget at 75% ($0.75 of $1.00)
Message: "Approaching daily limit. Using caution with expensive operations."
Action: Continue working, but batch requests
```

### Daily Alert (Red)
```
Subject: Daily budget exhausted ($1.00 of $1.00)
Message: "Daily budget reached. Stopping until next day (UTC)."
Action: STOP—no more API calls today
```

### Monthly Alert (Yellow)
```
Subject: Monthly budget at 75% ($3.75 of $5.00)
Message: "Approaching monthly limit. Optimize operations."
Action: Continue, but prioritize and optimize
```

### Monthly Alert (Red)
```
Subject: Monthly budget exhausted ($5.00 of $5.00)
Message: "Monthly budget reached. Waiting for reset on 1st."
Action: STOP—no more API calls this month
```

---

## Cost Optimization Tactics

### Immediate
- Batch requests (do 10 things at once, not 1 at a time)
- Use cache hits (reuse vault context instead of reloading)
- Shorter prompts (be direct, avoid redundancy)

### Short-term
- Archive completed projects
- Move reference docs to external links
- Compress old vault notes

### Long-term
- Model selection by task complexity
- Session batching (fewer, longer sessions vs many short ones)
- Vault structure optimization for cache reuse

---

## Budget Categories (Optional)

Track spending by category:

| Category | Monthly Budget | Current Spent | Remaining |
|----------|----------------|---------------|-----------|
| Core operations | $3.00 | $X.XX | $3.00 |
| Research & analysis | $1.00 | $X.XX | $1.00 |
| Experiments & testing | $1.00 | $X.XX | $1.00 |
| **TOTAL** | **$5.00** | **$X.XX** | **$5.00** |

---

## Reporting

### Weekly Report
Every Monday (or on request):
- Total spent this week
- Breakdown by category
- Cache hit rate
- Efficiency trends
- Projections for month

### Monthly Report
1st of each month:
- Total spent previous month
- Budget remaining (if any)
- Category breakdown
- Performance metrics
- Recommendations for next month

---

## Emergency Protocol

If budget is exhausted but critical task needed:

1. Log why it's critical
2. Ask Nate for approval
3. Get explicit override: "Use emergency budget for X"
4. Document what was spent
5. Plan to reduce budget next month

---

## Implementation

- Tracked in: [[mission-control/budget.md]]
- Monitored by: Ultron at session start
- Reported by: `/status` command
- Reviewed by: Weekly reporting

---

**Status:** Active
**Last updated:** 2026-03-14
**Next review:** Weekly
