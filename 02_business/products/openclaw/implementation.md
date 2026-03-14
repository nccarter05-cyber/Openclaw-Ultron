# OpenClaw Implementation

How to deploy and configure OpenClaw for clients.

---

## Implementation Timeline

### Pre-Sale (1 week)
- [ ] Discovery call (1 hour)
- [ ] Identify 1-2 automation targets
- [ ] Estimate ROI and budget
- [ ] Get buy-in from stakeholders

### Week 1: Setup
- [ ] Client gets Hostinger VPS or cloud server (or we provide)
- [ ] Install OpenClaw daemon on server
- [ ] Connect client's API keys (CRM, phone, email, etc.)
- [ ] Create initial agent configuration

### Week 2: Training & Testing
- [ ] Configure agent behavior for client's use case
- [ ] Test with sample data
- [ ] Client reviews and approves
- [ ] Train client team on monitoring dashboard

### Week 3: Soft Launch
- [ ] Deploy agent to production
- [ ] Monitor for bugs and issues
- [ ] Adjust behavior based on real-world results
- [ ] Get client feedback

### Week 4: Full Launch
- [ ] Scale to full usage
- [ ] Handoff to client support team
- [ ] Schedule ongoing optimization calls

---

## Technical Setup

### Server Requirements

**Option A: Client Hosts (We Install)**
- Linux VPS (Ubuntu 20.04+)
- 2GB RAM minimum, 4GB recommended
- 20GB storage minimum
- Outbound internet access (443 for APIs)
- ~$20-50/month on DigitalOcean, Linode, etc.

**Option B: We Host (SaaS Model)**
- We provide the server
- Pass cost through to client
- Client owns the account and data
- ~$50-100/month per agent

### Installation Steps

1. **SSH into server**
   ```bash
   ssh root@server-ip
   ```

2. **Install OpenClaw**
   ```bash
   npm install -g openclaw
   openclaw init
   ```

3. **Configure credentials**
   - Add client's CRM API key
   - Add phone provider (Twilio, etc.)
   - Add email provider
   - Add calendar/scheduling system

4. **Start daemon**
   ```bash
   openclaw gateway start
   openclaw status
   ```

---

## Integration Points

### CRM Integration
- **HubSpot:** Sync leads, update deals, create contacts
- **Salesforce:** Same, plus custom objects
- **Pipedrive:** Lightweight, good for SMBs
- **Custom:** Database via webhook

**Setup:**
1. Get client's API key
2. Add to OpenClaw config
3. Define mapping (what data to read/write)

### Phone Integration
- **Twilio:** Most flexible, handles inbound + outbound
- **VoIP.ms:** Cheaper, less feature-rich
- **Client's existing:** Can bridge if possible

**Setup:**
1. Get DID number (or use client's)
2. Route to Twilio SIP endpoint
3. Configure agent to answer calls
4. Test with sample inbound calls

### Email Integration
- **Gmail:** IMAP + SMTP
- **Outlook:** OAuth
- **Custom:** Webhook from their email server

**Setup:**
1. Create service account (or use client's account)
2. Grant access to OpenClaw
3. Configure filters (which emails to respond to)

### Calendar Integration
- **Google Calendar:** Sync availability, create events
- **Outlook Calendar:** Same
- **Calendly:** Check availability, embed in responses

**Setup:**
1. Get calendar API access
2. Configure agent to check availability
3. Test scheduling workflow

---

## Agent Configuration

### Define the Agent

**File:** `agent-config.yaml`

```yaml
name: "Lead Qualification Agent"
description: "Answers sales inquiry emails, qualifies leads, books demos"

channels:
  email:
    enabled: true
    inbox: "leads@company.com"
    respond_to: "*@company.com"  # or whitelist
  
integrations:
  crm:
    type: "hubspot"
    api_key: "${HUBSPOT_API_KEY}"
    actions:
      - read_contact
      - create_contact
      - update_deal
  
  calendar:
    type: "google"
    calendar_id: "${GOOGLE_CALENDAR_ID}"
    actions:
      - check_availability
      - book_meeting

behavior:
  instructions: |
    You are a sales assistant for Acme Corp.
    When someone inquires about our product:
    1. Thank them for their interest
    2. Ask 3 qualifying questions (budget, timeline, need)
    3. If qualified: offer a demo and check my calendar for openings
    4. If not qualified: thank them and ask them to check back in 6 months
  
  knowledge_base: "docs/product-info.md"
  fallback: "escalate to human"
  
  cost_limits:
    daily_budget: "$1.00"
    warn_at: "75%"
```

### Test the Agent

1. **Send test emails** to the inbox
2. **Verify responses** are appropriate
3. **Check CRM updates** happened correctly
4. **Review logs** in dashboard for errors

---

## Monitoring & Support

### Dashboard Setup

Client gets access to:
- **Live agent activity** (what's happening now)
- **Recent interactions** (last 24 hours)
- **Metrics** (messages processed, escalations, etc.)
- **Cost tracking** (tokens used, budget remaining)
- **Logs** (full audit trail)

### Weekly Check-In

1. Review metrics (volume, accuracy, escalation rate)
2. Check for errors or edge cases
3. Adjust behavior if needed
4. Plan next optimizations

### Monthly Review

1. Full month of metrics
2. ROI calculation
3. Feature requests from client team
4. Plan expansion to next use case

---

## Scaling

### From 1 Agent to Many

Once client sees success:

**Month 2:** Deploy second agent (e.g., customer support instead of sales)
**Month 3:** Third agent or expand first agent's capabilities
**Month 6:** Full suite of agents (sales, support, operations)

**Pricing scales:**
- Agent 1: $X/month
- Agent 2: $X + $500/month (incremental cost)
- Agent 3: $X + $1000/month
- etc.

---

## Handoff & Ongoing

### Client Empowerment

After 30 days:
- Client can adjust agent behavior independently
- Client monitors dashboard themselves
- We do monthly optimization calls
- Client owns the configuration

### Our Ongoing Role

- Monthly strategy call
- Quarterly feature additions
- Emergency support
- Annual contract renewal

---

## Cost Structure (Internal)

### Hosting Cost
- **Per agent:** $50/month (if we host)
- Or client pays $20-50/month for their own VPS

### Our Labor
- **Initial setup:** 20 hours
- **Ongoing support:** 2 hours/month per agent
- **Optimization:** As needed

### Pricing to Client
- **Setup:** $1,500-5,000 (depends on complexity)
- **Monthly:** $500-2,000/month per agent
- **Support:** Included first year, $100/month after

---

## Common Gotchas

### Authentication Issues
- **Problem:** Client's API keys don't work
- **Solution:** Regenerate with correct permissions
- **Prevention:** Document required permissions upfront

### Integration Delays
- **Problem:** CRM updates take 5-10 minutes
- **Solution:** Expected behavior (batch processing)
- **Prevention:** Set expectations in docs

### Budget Overruns
- **Problem:** Agent uses more tokens than budgeted
- **Solution:** Increase budget or optimize prompts
- **Prevention:** Monitor daily, alert at 75%

### Edge Cases
- **Problem:** Agent makes wrong decision on unusual input
- **Solution:** Add rule/exception to config
- **Prevention:** Comprehensive testing before launch

---

## Success Metrics

**Client succeeds if:**
- ✅ Agent handles >80% of tasks without escalation
- ✅ ROI positive within 30 days
- ✅ Team has capacity to do other work
- ✅ Customer satisfaction doesn't drop
- ✅ Cost per task is <50% of human cost

---

**Status:** Ready to implement
**Last updated:** 2026-03-14
