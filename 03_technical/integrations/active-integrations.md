# Active Integrations

## Exa AI - Neural Web Search

**Status:** ✅ Active  
**Version:** 0.0.2  
**Installed:** `/root/.openclaw/workspace/skills/exa`

### API Key Configuration
- **Env variable:** `EXA_API_KEY`
- **Location:** `~/.openclaw/.env`
- **Key source:** https://dashboard.exa.ai/api-keys
- **Setup:** `export EXA_API_KEY="your-key-here"`

### Agents Using This
- **Pulse** — Web intelligence & research
- **Hunter** — Lead generation & company research

### Usage
```bash
bash scripts/search.sh "query" [num_results] [type] [category]
bash scripts/code.sh "query" [num_results]
bash scripts/content.sh "url1" "url2"
```

### API Endpoints
- `/search` — Neural web search
- `/contents` — Extract full text from URLs

### Documentation
- Vetting report: `/root/.openclaw/workspace/exa-skill-vetting-report.md`
- Skill docs: `/root/.openclaw/workspace/skills/exa/SKILL.md`

---

## Agent Browser - Headless Automation

**Status:** ✅ Active  
**Version:** 0.21.4  
**Installed:** `/root/.openclaw/workspace/skills/agent-browser-clawdbot`

### CLI Installation
- **Binary:** `agent-browser`
- **Location:** `/usr/bin/agent-browser` (global)
- **Installation:** `npm install -g agent-browser`
- **No API key required** — local headless browser only

### Agents Using This
- **Pulse** — Multi-step web research & form interaction
- **Hunter** — Lead gen workflows requiring clicks/form submission

### Usage Pattern
```bash
# 1. Navigate and snapshot
agent-browser open https://example.com
agent-browser snapshot -i --json

# 2. Parse refs and interact
agent-browser click @e2
agent-browser fill @e3 "text"

# 3. Extract data
agent-browser get text @e1 --json
agent-browser get attr @e4 "href" --json
```

### Key Commands
- Navigation: `open`, `back`, `forward`, `reload`, `close`
- Snapshot: `snapshot -i --json` (always use with --json)
- Interaction: `click @e2`, `fill @e3 "text"`, `type`, `hover`, `press`
- Data: `get text @e1`, `get attr @e4 "href"`, `get html`, `get value`
- Wait: `wait @e2`, `wait 1000`, `wait --text "text"`, `wait --load networkidle`

### Documentation
- Vetting report: `/root/.openclaw/workspace/agent-browser-vetting-report.md`
- Skill docs: `/root/.openclaw/workspace/skills/agent-browser-clawdbot/SKILL.md`

---

## When to Use Each

### Agent Browser
- Multi-step workflows
- Form submission
- Dynamic content (JavaScript rendering)
- Element interaction (clicks, typing)
- Session isolation needed

### web_fetch (Built-in)
- Simple page reads
- Static content extraction
- Quick HTML/text lookups
- No interaction needed

### Exa AI
- Natural language search
- Code/documentation discovery
- Research papers & company info
- Better results than keyword search

### web_search (Built-in Brave)
- Quick keyword search
- News/real-time results
- When Exa is not needed

---

## Agent Instructions

**In AGENTS.md:**
- Pulse: Use agent-browser for multi-step workflows, Exa for research queries
- Hunter: Use agent-browser for lead gen forms, Exa for company research

