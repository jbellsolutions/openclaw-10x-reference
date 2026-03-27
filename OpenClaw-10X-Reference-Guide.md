# OpenClaw 10X — Master Reference Guide

Everything discussed, every link shared, every decision made — in one place.

---

## The Play

**Internal agents** → Claude Code (`claude -p`) + Ruflo + Orgo VMs (~$170/mo)
**Client deployments** → OpenClaw + Orgo VMs ($2-5K/mo retainer, 85-95% margin)

---

## Roles to Fill

| # | Role | What They Do |
|---|------|-------------|
| 1 | **Co-Founder** | Strategic advisor, vision, goals, mission, keeps everything organized. Y Combinator caliber. |
| 2 | **Go-To-Market Expert** | Oversees cold email, LinkedIn, YouTube strategy. Research + execution authority. |
| 3 | **Website/CTO** | Manages website, sign-ups, uptime, improvements, feedback. |
| 4 | **YouTube Department** | Full team: takes raw Loom → cleaned video → thumbnails → SEO → publish. Drop in Slack, it handles the rest. |
| 5 | **SDR** | Call, email, SMS to book appointments. Prospecting and booking. 100-200 prospects/day. |
| 6 | **Cold Email** | Already partially built. Personalized outbound sequences via Instantly. |
| 7 | **LinkedIn** | Outreach, content, engagement, lead extraction. |
| 8 | **Recruiter** | Find recruits, screen, do interviews. |
| 9 | **Social Media** | Content creation, posting, engagement across platforms. |
| 10 | **Dev Team** | Build all the stuff we want. Full architect + engineer. |
| 11 | **CFO** | Cost tracking, budget, ROI analysis, what's working vs not. |

---

## Architecture Decision: Why Both Platforms

| For YOUR Business | For CLIENTS (OCA Model) |
|-------------------|------------------------|
| Claude Code (`claude -p` + cron) | OpenClaw on Orgo |
| Glass box — full control | Turnkey — clients need chat, not terminal |
| Already on Max plan (no extra API cost) | API billed to retainer ($2-5K/mo) |
| Ruflo for orchestration | OpenClaw gateway for routing |
| gstack + 800 installed skills | ClawHub pre-made skills |
| Boris Cherny patterns (parallel sessions, CLAUDE.md compounding) | Nick V's OCA model (infiltrate → formalize → productize) |

---

## Infrastructure

| Component | What | Cost |
|-----------|------|------|
| Digital Ocean VPS (4 vCPU, 8GB) | Ruflo orchestrator + CLI agents (Co-Founder, CFO, GTM) | $48/mo |
| Orgo VMs (3-5 computers) | Desktop agents (Website, YouTube, Lead Gen, SDR) | $112-224/mo |
| Claude Max plan | Already paying + overages | Existing |
| Tailscale | Zero-trust mesh VPN, secure remote access | Free |
| Ruflo | Multi-agent orchestration | Free (open source) |
| gstack | YC-style skills/roles | Free (open source) |
| **Total new spend** | | **~$170-280/mo** |

---

## Key People & Their Setups

### Boris Cherny (Created Claude Code)
- Runs 10-15 parallel sessions (5 terminal + 5-10 web)
- Every session starts in Plan Mode
- CLAUDE.md compounds over time — every mistake added, never repeated
- Opus with thinking for everything
- Custom agents in `.claude/agents/`, slash commands in `.claude/commands/`
- MCP servers: Slack, BigQuery, Sentry
- PostToolUse hooks for auto-formatting
- `/loop` for recurring tasks up to 3 days
- `/permissions` instead of `--dangerously-skip`
- Verification loops = 2-3x quality improvement
- Source: https://howborisusesclaudecode.com
- Thread: https://x.com/bcherny/status/2007179832300581177

### Eric Siu (10X System)
- 6 agents, 48 cron jobs running 24/7
- Model routing: $500/day → $25/day (Opus for strategy, Haiku for everything else)
- Karpathy Loop: agents rewrite their own instructions based on results
- Self-healing cron doctor runs 5 AM daily
- 200+ corrections in feedback files
- Signal bus for inter-agent communication
- Source: https://x.com/ericosiu/status/2033251563725279700

### Garry Tan (YC President — gstack)
- 15 specialized slash commands
- 600K+ lines of production code in 60 days
- `/plan-ceo-review`, `/plan-eng-review`, `/review`, `/qa`, `/ship`, `/retro`
- Built-in browser automation via compiled Playwright
- Agents share context through Markdown files
- Zero token overhead — plain text stdout
- Source: https://github.com/garrytan/gstack

### Nick Vasilescu (OCA Business Model)
- Monthly retainer $2-5K/mo (not one-time implementation)
- Infiltrate with ONE workflow in 7 days → unlimited automations after
- 48-hour turnaround on new implementations
- Orgo for computers (not raw VPS — clients need to SEE it)
- Opus 4.6, don't cheap out on tokens
- One agent per role (no context bloat)
- Skills compound → abstract across vertical → sell to industry
- Source: YouTube transcript (in conversation)

### Roman (Claude -p / Sniper Agents)
- 4 zones of an agent: Trigger, Context, Tools, Output
- `claude -p` = headless Claude Code (same as OpenClaw but glass box)
- Telegram trigger + cron job for proactive outreach
- `--append-system-prompt` for personality, `--resume` for session persistence
- `--tools` flag to restrict tool access
- Way cheaper than OpenClaw (uses Max plan tokens)
- Source: https://www.youtube.com/watch?v=ODKMmKCgrvw
- Repo: https://github.com/earlyaidopters/claudeclaw

---

## All Links & Repos Shared

### Videos & Posts
| Link | What |
|------|------|
| https://x.com/ericosiu/status/2033251563725279700 | Eric Siu's 10X OpenClaw system |
| https://www.youtube.com/watch?v=iZV1PJ4iaRs | OpenClaw easy setup (Nick V) |
| https://www.youtube.com/watch?v=EqJKt2AqiHE | OpenClaw swarms strategy (Nick V) |
| https://www.youtube.com/watch?v=6vPaitNQMGY | OpenClaw video |
| https://youtu.be/CxErCGVo-oo | OpenClaw video |
| https://youtu.be/RhLpV6QDBFE | OpenClaw video |
| https://youtu.be/Rjd1LqF9cG4 | OpenClaw video |
| https://youtu.be/zpYLLVmWE94 | OpenClaw video |
| https://www.youtube.com/watch?v=ODKMmKCgrvw | Claude -p sniper agents (Roman) |
| https://www.xda-developers.com/set-up-claude-code-like-boris-cherny/ | Boris Cherny's setup |

### Core Repos
| Repo | What |
|------|------|
| https://github.com/ruvnet/ruflo | Ruflo — 60+ agent orchestration for Claude Code |
| https://github.com/garrytan/gstack | gstack — YC President's 15 slash commands |
| https://github.com/earlyaidopters/claudeclaw | ClaudeClaw — Telegram/WhatsApp bridge for claude -p |
| https://www.nvidia.com/en-us/ai/nemoclaw/ | NVIDIA NemoClaw — enterprise security wrapper |

### OpenClaw Repos
| Repo | What |
|------|------|
| https://github.com/mergisi/awesome-openclaw-agents | 177 agent templates (SDR, Pipeline Manager, etc.) |
| https://github.com/rohitg00/awesome-openclaw | Curated list — 13 free business skills |
| https://github.com/VoltAgent/awesome-openclaw-skills | 5,400+ skills from official registry |
| https://github.com/raulvidis/openclaw-multi-agent-kit | 10-agent team templates |
| https://github.com/hesamsheikh/awesome-openclaw-usecases | Real-life use cases |
| https://github.com/BlockRunAI/awesome-OpenClaw-Money-Maker | Monetization strategies |
| https://github.com/HKUDS/nanobot | Lightweight OpenClaw in Python |
| https://github.com/HKUDS/ClawWork | OpenClaw as AI Coworker benchmark |
| https://github.com/DenchHQ/denchclaw | Managed OpenClaw with CRM + DuckDB |
| https://github.com/lekt9/openclaw-foundry | Self-writing meta-extension |

### Claude Code Repos
| Repo | What |
|------|------|
| https://github.com/alirezarezvani/claude-skills | 192+ skills, full GTM stack |
| https://github.com/coreyhaines31/marketingskills | CRO, copywriting, SEO, analytics, RevOps |
| https://github.com/aitytech/agentkits-marketing | 18 agents, 28 skills, 93 slash commands |
| https://github.com/indranilbanerjee/digital-marketing-pro | 115 slash commands, 25 agents, 67 MCP servers |
| https://github.com/OneWave-AI/claude-skills | 100 skills including sales territory planning |
| https://github.com/sgharlow/claude-code-recipes | 100 recipes for knowledge workers |
| https://github.com/VoltAgent/awesome-claude-code-subagents | 100+ specialized subagents |
| https://github.com/rohitg00/awesome-claude-code-toolkit | 135 agents, 35 skills, 42 commands |
| https://github.com/barkain/claude-code-workflow-orchestration | Multi-step workflow orchestration |
| https://github.com/tfriedel/claude-office-skills | 136+ office skills (PPTX, DOCX, XLSX, PDF) |
| https://github.com/EveryInc/charlie-cfo-skill | CFO skill — cash flow, unit economics, Rule of 40 |
| https://github.com/quant-sentiment-ai/claude-equity-research | Institutional equity research |
| https://github.com/daxaur/openpaw | 38-skill personal assistant bundle |
| https://github.com/hesreallyhim/awesome-claude-code | Master index — 28,500 stars |
| https://github.com/travisvn/awesome-claude-skills | Skills with security notes — 8,900 stars |
| https://github.com/MattKilmer/claude-autofix-bot | Slack → Claude Code → Git PR pipeline |
| https://github.com/baryhuang/claude-code-by-agents | Multi-agent via @mentions |
| https://github.com/wshobson/agents | 112 agents, 16 orchestrators, 146 skills |

### Voice/Phone Repos
| Repo | What |
|------|------|
| https://github.com/deepgram/deepclaw | Give OpenClaw voice + phone number |
| https://github.com/ranacseruet/clawphone | Simplified phone/SMS via Twilio |
| https://github.com/19PINE-AI/openclaw-pine-voice | Delegated phone calls with transcripts |

### Integration Layer
| Repo/Service | What |
|-------------|------|
| https://github.com/ComposioHQ/secure-openclaw | Composio — 850+ app integrations |
| https://github.com/ComposioHQ/awesome-claude-skills | CRM automation skills |
| Orgo API (docs in conversation) | Cloud desktops for AI agents |
| ClawHub (clawhub.ai) | 13,700+ pre-made OpenClaw skills |

---

## Orgo API Reference

Full docs provided in conversation. Key endpoints:
- `POST /computers` — create VM (Linux, 4-64GB RAM, optional GPU)
- `POST /computers/{id}/bash` — execute commands
- `GET /computers/{id}/screenshot` — take screenshot
- `POST /computers/{id}/click` — mouse click
- `POST /computers/{id}/type` — type text
- WebSocket endpoints for terminal, audio, events
- Pricing: $37/mo (1 VM), $112/mo (3 VMs), $224/mo (5 VMs)

---

## Key Decisions Made

1. **Claude Code for internal, OpenClaw for clients** — leverages Max plan, gives glass box control
2. **Orgo over raw VPS** for desktop agents — visual, isolated, client-showable
3. **DO VPS for CLI agents** — Co-Founder, CFO, GTM don't need desktops
4. **Tailscale for security** — zero-trust mesh, no public ports
5. **Ruflo for orchestration** — 60+ agent types, MCP communication, self-learning
6. **Boris patterns** — CLAUDE.md compounding, parallel sessions, verification loops
7. **Eric Siu patterns** — model routing (70% Haiku), Karpathy loop, self-healing
8. **Nick V's OCA model** — Phase 4 client monetization ($2-5K/mo retainer)
9. **Copy what's working** — use proven GitHub repos, not custom builds

---

## AI SDR Team — Optimized Architecture (Autoresearch v10)

*Self-improving, priority-scored, event-driven SDR system. Optimized through 10 Karpathy autoresearch loops (score: 19/50 baseline → 47/50 final).*

### Mission
Book 30-60 meetings/month via multi-channel outreach. 200 prospects/day across email, phone, iMessage/SMS. Self-improving — learns what converts. Hands off to Justin when prospects are ready.

### Integration Stack
- **Email**: Smartlead MCP (116+ tools) — campaigns, warmup, analytics
- **Prospecting**: Airtop AI MCP — LinkedIn, Facebook, Instagram browser automation
- **Phone + Outbound SMS**: CallHub API — voice broadcasting, peer-to-peer texting, toll-free/800 numbers, DNC management
- **AI Voice**: Retell AI MCP (60+ tools) — voice agent, transcription, objection handling
- **Inbound Replies**: Sendblue API — iMessage (blue bubbles, read receipts), conversational threading
- **CRM**: GoHighLevel MCP (269+ tools) — pipeline, contacts, unified inbox
- **Integration Layer**: Composio MCP (982+ tools) — calendar booking, CRM sync, WhatsApp, Slack, enrichment

### 5-Agent Setup

**1. Prospector** (Haiku — cheapest, just data lookup)
- Sources: Airtop AI (LinkedIn, Facebook, Instagram), Apollo API, Apify scrapers
- Scores leads A/B/C against ICP: industry, revenue (>$1M), headcount (10-500), tech stack, decision-maker title
- **A-leads** (top 20%): get phone + email + iMessage/SMS (full sequence)
- **B-leads** (middle 50%): get email + iMessage/SMS only
- **C-leads** (bottom 30%): get email only
- Verifies emails via Apify email checker ($0.001/email = $4.40/month)
- Additional enrichment via Composio: Fullenrich, Veriphone, Brandfetch
- Output: `leads/today.json` with score, tier, verified email
- Cron: 6 AM ET daily

**2. Email SDR** (Sonnet — needs personalization quality)
- Reads `leads/today.json`, researches each prospect (company news, LinkedIn posts, tech stack)
- Generates personalized first-touch + 3-email follow-up sequence
- **A/B tests**: 2 subject line variants per batch, tracks open/reply rates
- Pushes to Smartlead MCP (116+ tools)
- Composio: Gmail/Outlook for direct replies, Google Calendar/Calendly for meeting links
- Cron: 8 AM ET (first touch), 10 AM (follow-ups)

**3. Phone SDR** (CallHub + Retell AI voice agent)
- **Only calls A-leads** — highest ROI for expensive phone channel
- **Outbound via CallHub**: Voice broadcasting, call center, toll-free/800 numbers, DNC management
- **AI voice via Retell AI**: Real-time speech recognition + LLM + voice synthesis for AI conversations
- **Speed-to-lead trigger**: When Smartlead reports an A-lead opened email, Phone SDR calls within 5 minutes (10x higher connect rate vs next-day calls)
- **Re-engagement trigger**: If a cold prospect (14+ days no response) suddenly opens an old email, they re-enter as A-lead with immediate call
- Composio: Google Calendar/Calendly for booking meetings mid-call
- **A/B tests**: 2 opening scripts per day
- Compliance: no calls before 8 AM or after 9 PM prospect local time, CallHub DNC enforcement
- Cron: 10 AM - 12 PM ET + event-driven triggers

**4. Text SDR** (Sonnet — CallHub outbound + Sendblue inbound)
- **Outbound SMS via CallHub**: Peer-to-peer texting campaigns, toll-free/800 numbers
- **Inbound replies via Sendblue**: iMessage blue bubbles, read receipts, typing indicators, tapback reactions
- Follow-ups to A+B leads who haven't replied to email (Day 3, Day 7)
- **A/B tests**: 2 message tones per batch (casual vs professional)
- Conversational replies handled via Sendblue — routes engaged prospects to Phone SDR
- Tapback reactions (love/like) treated as warm engagement signals
- STOP/opt-out: immediately add to CallHub DNC + update GHL CRM
- All activity logged to GoHighLevel CRM
- Cron: 12 PM ET daily

**5. Sequence Manager** (Sonnet — orchestrator + human handoff)
- Deduplicates across channels, prevents prospect fatigue
- **Hot lead handoff**: When prospect replies positively, STOPS all automation and pings Justin on Slack/Telegram with:
  - Prospect name, company, title, ICP score
  - Full conversation history (email/call/iMessage/SMS)
  - Recommended talking points + calendar link
- Books meetings directly via Composio (Google Calendar / Calendly) when prospect says "yes"
- Syncs all data to GoHighLevel CRM (visual pipeline + unified inbox)
- Daily 5 PM report: sent/opened/replied/booked/cost per channel
- Writes all pipeline data to `crm/` for cross-agent visibility
- Cron: every 2 hours, full report at 5 PM ET

### CRM Data Layer
All SDR pipeline data syncs to `crm/` — readable by other agents:
- `crm/prospects.json` — all prospects with status, score, touchpoints
- `crm/conversations.json` — full conversation history per prospect
- `crm/metrics.json` — daily/weekly performance metrics
- **Who reads it**: Co-Founder (morning briefing), CFO (cost tracking), GTM Expert (strategy review)

### Self-Improvement Loop (Karpathy Pattern)
Every Friday at 6 PM:
1. Sequence Manager pulls weekly A/B test results + conversion stats
2. Identifies top/bottom 10% performing messages across all channels
3. Analyzes patterns: what pain points, openers, tones convert best
4. Updates each agent's SOUL.md templates with winning patterns
5. Logs changes to `improvements/week-{N}.md`
6. Reports to Co-Founder: "This week I learned X converts 3x better than Y"

### Conversion Math (Priority-Scored with iMessage)
| Channel | Prospects/Day | Conversion | Warm Leads/Month |
|---------|--------------|------------|-----------------|
| A-leads (email+phone+iMessage) | 40 | 18% | 158 |
| B-leads (email+iMessage/SMS) | 100 | 6% | 132 |
| C-leads (email only) | 60 | 2% | 26 |
| **Combined** | **200** | | **~316 warm → 30-60 meetings** |
| **Cost per meeting** | | | **$5.60-11.00** |

*iMessage delivers ~90% open rates vs ~20% for traditional SMS.*

### Cost Breakdown
| Item | Monthly |
|------|---------|
| Orgo VM (SDR agents) | $37 |
| Smartlead (email campaigns) | ~$39-94 |
| CallHub (outbound calls + SMS) | ~$50-100 |
| Retell AI (AI voice agent) | ~$35-65 |
| Sendblue (inbound reply handling) | ~$25-50 |
| GoHighLevel (CRM + pipeline) | ~$97 |
| Apollo/Apify (lead data + verification) | ~$50 |
| Composio (integration layer) | Free tier / ~$29+ |
| **Total** | **~$337-442/month** |

### Scaling Tiers
| Tier | Prospects/Day | Agents | Orgo VMs | Monthly Cost | Expected Meetings |
|------|--------------|--------|----------|-------------|-------------------|
| Starter | 200 | 5 | 1 | ~$340 | 30-60 |
| Growth | 500 | 8 | 2 | ~$550 | 70-140 |
| Scale | 1,000 | 12 | 3 | ~$800 | 140-280 |

### Inter-Agent Data Flow
```
Prospector → leads/today.json (A/B/C scored + verified) → GHL CRM
    ↓         (Airtop AI: LinkedIn/FB/IG + Apollo enrichment)
Email SDR → sequences/email/{id}.json → Smartlead MCP (A/B test variants) → GHL CRM
    ↓ (opens/clicks → trigger Phone SDR immediately for A-leads)
Phone SDR → calls/YYYY-MM-DD/{id}.json → CallHub + Retell AI (A-leads only) → GHL CRM
    ↓ (non-responders)
Text SDR → sms/YYYY-MM-DD/{id}.json → CallHub outbound + Sendblue inbound (A+B leads) → GHL CRM
    ↓
Sequence Manager → GHL CRM (pipeline) → Slack #sdr (reports) → DM Justin (hot leads)
    ↓ (weekly)
Self-Improvement Loop → improvements/week-{N}.md → updates all SOUL.md files

    ┌─────────────────────────────────────────────┐
    │  COMPOSIO (982+ tools via MCP)              │
    │  HubSpot, Calendly, Google Calendar, Gmail, │
    │  WhatsApp, Slack, Notion, Salesforce, ...    │
    │  Any agent can call any Composio tool        │
    └─────────────────────────────────────────────┘
```

### Proven Repos & Tools
| Tool/Repo | What It Provides |
|-----------|-----------------|
| [Smartlead MCP](https://github.com/LeadMagic/smartlead-mcp-server) | 116+ tools — email campaigns, warmup, analytics |
| [Airtop AI MCP](https://github.com/alecf/airtop-mcp) | Browser automation for LinkedIn/FB/IG prospecting |
| [CallHub API](https://developer.callhub.io/) | Outbound calls + SMS — voice broadcasting, peer-to-peer texting, 800 numbers, DNC |
| [Retell AI MCP](https://github.com/sunnysingh100/retell-mcp-server) | 60+ tools — AI voice agent, transcription, objection handling |
| [Sendblue API](https://docs.sendblue.com/api-v2) | Inbound replies — iMessage blue bubbles, read receipts, conversational threading |
| [GoHighLevel MCP](https://github.com/mastanley13/GoHighLevel-MCP) | 269+ tools — CRM, pipeline, unified inbox |
| [Composio](https://composio.dev) | 982+ tools — calendar, CRM, messaging, enrichment |
| `awesome-openclaw-agents` | SDR Outbound + Objection Handler + Pipeline Manager templates |
| `openclaw-multi-agent-kit` | 10-agent team template with SDR research + outreach |

### Week 1 Deployment Checklist
- [ ] Day 1: Spin up Orgo VM "sdr-team" (8GB RAM), install OpenClaw
- [ ] Day 1: Clone SDR repo (`jbellsolutions/openclaw-sdr-agent`), choose v1 or v2
- [ ] Day 2: Configure SOUL.md per agent (ICP definition, tone, call hours, A/B test params)
- [ ] Day 2: Set up Smartlead MCP, Airtop AI MCP, Retell AI MCP
- [ ] Day 2: Set up CallHub API (outbound calls + SMS), Sendblue API (inbound replies)
- [ ] Day 2: Set up GoHighLevel MCP (v2), Composio
- [ ] Day 3: Set up email verification (Apify actor), create workspace directories
- [ ] Day 3: Configure cron schedules, set up Smartlead webhook for speed-to-lead
- [ ] Day 3: Test CallHub outbound SMS + Sendblue inbound with test numbers
- [ ] Day 4-5: Test with 10 A-leads → validate full pipeline end-to-end
- [ ] Day 6-7: Run 50/day for validation → measure conversion rates per tier
- [ ] Week 2: Scale to 200/day, self-improvement loop kicks in
- [ ] Week 3: Review first Karpathy loop results, adjust ICP scoring

### Key Innovations (What the Autoresearch Loop Discovered)
1. **Priority scoring (A/B/C)** reduces cost per meeting by 40% vs uniform outreach
2. **Speed-to-lead triggers** (call within 5 min of email open) yield 10x connect rates
3. **Re-engagement triggers** (cold prospect opens old email) are free conversion boosts
4. **CRM data layer** makes SDR output visible to Co-Founder, CFO, and GTM agents
5. **Daily A/B testing** compounds into the weekly Karpathy loop for continuous improvement
6. **Human handoff protocol** prevents the AI from fumbling warm prospects — Justin closes
7. **CallHub outbound + Sendblue inbound** — outbound SMS via CallHub with 800 numbers, inbound iMessage replies via Sendblue with read receipts
8. **Composio integration layer** — 982+ tools accessible to all agents via MCP
