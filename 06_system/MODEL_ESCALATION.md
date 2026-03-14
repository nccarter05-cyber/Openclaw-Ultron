# MODEL_ESCALATION.md

## When to Switch to Sonnet (from Haiku)

### Automatic Escalation (stop, switch, restart):
- **Repeated failures on same task** (>2 iterations without progress)
- **Architecture/design decisions** (system design, integration planning, major refactors)
- **Security analysis** (vulnerability assessment, threat modeling, access control decisions)
- **Complex debugging** (>3 failed troubleshooting attempts, architectural misunderstanding suspected)
- **Production code review** (before deploying to live systems)
- **Strategic multi-project decisions** (cross-system impact, long-term planning)

### Check Before Starting:
- Is this a task where I'm expected to reason deeply?
- Have I already tried this and failed?
- Does the output need to be high-confidence?

### Pattern to Avoid:
- Do not iterate with Haiku indefinitely
- Do not assume a simpler model will eventually work if fundamentals are wrong
- Do not debug complex systems without escalating

### Action:
When you recognize a trigger condition:
1. Stop the current approach
2. Call `session_status` to verify current model
3. If using Haiku, spawn a Sonnet session or switch model
4. Restart the task with the correct model
5. Document the escalation in MEMORY.md

---

*This file is consulted before complex work. Reference it actively, not just at session start.*
