# Performance Metrics

Token usage, cache efficiency, and operational health tracking.

---

## Current Session Snapshot (2026-03-14 04:07 UTC)

```
Model: anthropic/claude-haiku-4-5-20251001
Tokens In: 85
Tokens Out: 1,500
Cache Hit Rate: 99%
Cached Tokens: 63,000
New Tokens: 474
Context Usage: 32% of 200k window
```

---

## Performance Targets

| Metric | Target | Current | Status |
|--------|--------|---------|--------|
| Cache Hit Rate | >90% | 99% | 🟢 Excellent |
| Context Usage | <50% | 32% | 🟢 Healthy |
| Tokens Per Session | <5k | ~1.5k avg | 🟢 Efficient |
| Response Time | <10s | ~2s avg | 🟢 Fast |

---

## How These Work

### Cache Hit Rate (99%)
- **What:** Percentage of context that comes from cached prompts
- **Why:** Reused context costs 90% less than new tokens
- **Goal:** Keep above 90% for cost savings

### Context Usage (32%)
- **What:** How much of the 200k token window we're using
- **Why:** More context = more expensive, but better memory
- **Goal:** Stay below 50% to leave room for growth

### Tokens Per Session
- **What:** Average tokens used per conversation session
- **Why:** Higher = more expensive, lower = more restricted
- **Goal:** Keep between 1k-5k for efficiency

### Response Time
- **What:** Seconds from your message to my response
- **Why:** Shows system health and load
- **Goal:** Under 10 seconds (usually 1-5 seconds)

---

## Weekly Trend

Track performance week-over-week:

| Week | Avg Cache Hit | Avg Context | Avg Tokens/Session | Cost |
|------|---------------|-------------|-------------------|------|
| 2026-03-01 to 07 | — | — | — | $0.XX |
| 2026-03-08 to 14 | 99% | 32% | 1.5k | $0.XX |
| 2026-03-15 to 21 | — | — | — | — |

---

## Optimization Opportunities

When to optimize:

- Cache hit <85%: Vault has too much old context
- Context >60%: Archive old sessions or compress vault
- Tokens/session >10k: Requests getting inefficient
- Response time >30s: System is overloaded

**Actions:**
- Archive completed projects to `05_archive/`
- Compress old notes into summaries
- Move rarely-used reference to external links
- Batch similar requests to reuse context

---

## Notes

- **Thinking enabled?** No (uses more tokens, better reasoning)
- **Model:** Haiku (cheapest/fastest)
- **Provider:** Anthropic (Claude)
- **Runtime:** OpenClaw agent on Hostinger

---

**Last updated:** 2026-03-14 04:07 UTC
