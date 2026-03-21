# OpenClaw 10X — Deployment Plan

## The Architecture (Final)

```
JUSTIN
 ├── Cowork Desktop (deep sessions, planning, reviews)
 ├── Slack Bot (quick commands, status, "deploy X")
 └── Telegram (mobile, on the go)
      │
      ▼
CO-FOUNDER AGENT (ClaudeClaw on DO VPS)
 ├── Session persistence (resumes conversations)
 ├── 3-layer memory (semantic + salience + decay)
 ├── CLAUDE.md (compounds daily — every mistake, every decision)
 ├── SSH access to all DO droplets via Tailscale
 ├── Orgo API access (desktop VMs)
 │
 └── Spawns & Manages Sub-Agents:
      ├── CFO Agent (VPS — claude -p + cron)
      ├── GTM Expert (VPS — claude -p + cron)
      ├── Cold Email Agent (VPS — claude -p + existing system)
      ├── Dev Team Agent (VPS — claude -p + gstack)
      ├── Recruiter Agent (VPS — claude -p + cron)
      ├── Website/CTO Agent (Orgo VM — browser needed)
      ├── YouTube Agent (Orgo VM — video processing + YouTube Studio)
      ├── SDR Agent (Orgo VM — OpenClaw + clawphone for calls/SMS)
      ├── LinkedIn/Lead Gen Agent (Orgo VM — browser automation)
      └── Social Media Agent (Orgo VM — browser for personal posting)
```

---

## Infrastructure

| Component | Specs | Cost | Purpose |
|-----------|-------|------|---------|
| DO VPS #1 (Orchestrator) | 4 vCPU, 8GB RAM | $48/mo | ClaudeClaw + Co-Founder + CLI agents (CFO, GTM, Cold Email, Dev, Recruiter) |
| Orgo VMs (5 computers) | 4GB RAM each | $224/mo | Website, YouTube, SDR, LinkedIn, Social Media |
| Claude Max Plan | Already paying | $0 new | All internal agent tokens |
| Tailscale | Mesh VPN | Free | Secure access between all machines |
| **Total new spend** | | **~$272/mo** |

### Why This Split

**VPS agents** (Co-Founder, CFO, GTM, Cold Email, Dev, Recruiter): These are "thinking" agents. They read data, analyze, write reports, generate strategies, write code. No browser needed. `claude -p` on a VPS is fast, cheap, and transparent.

**Orgo VM agents** (Website, YouTube, SDR, LinkedIn, Social Media): These need a real desktop. LinkedIn personal page posting requires browser automation (API doesn't support personal profiles). YouTube Studio requires browser interaction. SDR needs phone/SMS (OpenClaw + clawphone). Social media personal accounts need browser.

---

## Phase 1: Co-Founder + Infrastructure (Week 1)

**Goal**: Get the orchestration layer running. Everything else builds on this.

### Day 1-2: VPS Setup
- [ ] Spin up DO droplet (4 vCPU, 8GB RAM, Ubuntu 22.04)
- [ ] Install Tailscale, add to mesh network
- [ ] Install Claude Code CLI (`claude` binary)
- [ ] Install Node.js 20+ (ClaudeClaw requirement)
- [ ] Clone ClaudeClaw: `git clone https://github.com/earlyaidopters/claudeclaw`
- [ ] Configure `.env` with Anthropic API key (from Max plan)
- [ ] Set up Telegram bot (BotFather → get token)
- [ ] Run ClaudeClaw setup, verify Telegram communication works

### Day 3-4: Co-Founder Agent Configuration
- [ ] Write Co-Founder CLAUDE.md (personality, knowledge, permissions)
- [ ] Configure allowed tools: Bash, Read, Write, SSH, Orgo API
- [ ] Set up SSH keys for all existing DO droplets
- [ ] Create morning briefing cron (8:30 AM daily)
- [ ] Create evening status cron (6:00 PM daily)
- [ ] Test: send message via Telegram → get response → verify session persists

### Day 5: Slack Integration
- [ ] Create Slack app (bot user, Socket Mode)
- [ ] Add real-time listener to ClaudeClaw (WebSocket to Slack Events API)
- [ ] OR fork `mpociot/claude-code-slack-bot` and wire into ClaudeClaw session/memory
- [ ] Test: message in Slack DM → Co-Founder responds → session shared with Telegram

### Day 6-7: Verification & Compound Setup
- [ ] Test cross-channel: start conversation in Slack, continue in Telegram, review in Cowork
- [ ] Verify Co-Founder can SSH into all DO droplets
- [ ] Verify Co-Founder can read/modify files on remote machines
- [ ] Set up CLAUDE.md compounding: every interaction → lessons learned → added to CLAUDE.md
- [ ] Set up PostCompact hook: re-inject critical context after context compression
- [ ] Set up systemd service for auto-restart on boot

### Co-Founder CLAUDE.md (Draft)

```markdown
# Co-Founder Agent — CLAUDE.md

## Identity
You are Justin's technical co-founder. He's the sales/marketing person. You're the tech/ops person.
Think Y Combinator caliber — strategic, operational, execution-focused.

## Your Job
1. THINK WITH JUSTIN — push back, ask questions, help clarify decisions
2. ORCHESTRATE — take decisions and delegate to sub-agents or execute directly
3. MANAGE INFRASTRUCTURE — all DO droplets, Orgo VMs, Claude Code projects
4. COMPOUND KNOWLEDGE — log every decision, mistake, learning in this file
5. REPORT — morning briefings, evening status, on-demand reports

## Infrastructure You Manage
- DO Droplet: LinkedIn project (IP: [to fill])
- DO Droplet: Orchestrator/this agent (IP: [to fill])
- Orgo workspace: [to fill after setup]
- All connected via Tailscale

## Sub-Agents You Can Spawn
Use `claude -p` with agent-specific CLAUDE.md files.
Each agent gets its own session, cron schedule, and tool permissions.

## Rules
- Always start complex tasks in Plan Mode (think first, then execute)
- Verify your work (curl the endpoint, screenshot the page, run the test)
- When in doubt, ask Justin — don't assume
- Log every mistake in the "Lessons Learned" section below
- Use Haiku for simple tasks, Opus for strategy/planning

## Communication
- Slack: quick commands, status updates
- Telegram: mobile, on the go
- Cowork: deep working sessions

## Lessons Learned
(This section grows over time — every mistake, every correction, every insight)
```

---

## Phase 2: First Sub-Agents (Week 2-3)

### CFO Agent
- **Runs on**: VPS (same machine as Co-Founder)
- **Repo to start from**: `EveryInc/charlie-cfo-skill`
- **Cron**: Nightly cost report (11 PM), weekly budget review (Sunday 9 AM)
- **Model**: Haiku (just reads numbers and formats — cheapest option)
- **Reports to**: Co-Founder → Slack channel #finances

### GTM Expert Agent
- **Runs on**: VPS
- **Repo to start from**: `indranilbanerjee/digital-marketing-pro` (115 commands) + `agentkits-marketing`
- **Cron**: Daily channel performance report (7 AM), weekly strategy review (Monday 8 AM)
- **Model**: Opus for strategy, Haiku for data pulls
- **Reports to**: Co-Founder → Slack channel #gtm

### Cold Email Agent
- **Runs on**: VPS
- **Repo to start from**: Your existing Python system + `aitytech/agentkits-marketing` email-wizard
- **Cron**: Daily send sequences (9 AM), daily reply monitoring (every 2 hours), weekly A/B report
- **Model**: Sonnet for personalization, Haiku for monitoring
- **Reports to**: GTM Expert → Slack channel #cold-email

---

## Phase 3: Desktop Agents (Week 4-5)

### Website/CTO Agent
- **Runs on**: Orgo VM #1
- **Repo to start from**: `garrytan/gstack` (/qa, /ship, /plan-eng-review) + `MattKilmer/claude-autofix-bot`
- **Cron**: Uptime check (every 15 min), weekly QA review, auto-fix on Slack bug reports
- **Tools**: Chromium browser, git, Node.js, deployment scripts
- **Reports to**: Co-Founder → Slack channel #website

### LinkedIn/Lead Gen Agent
- **Runs on**: Orgo VM #2
- **Why Orgo**: LinkedIn API doesn't support personal profile posting. Must use browser automation.
- **Repo to start from**: Your existing LinkedIn DO project (migrated to Orgo) + browser automation
- **Cron**: Daily content post (8 AM), engagement runs (10 AM, 2 PM, 5 PM), lead scraping (6 AM)
- **Tools**: Chromium with LinkedIn session, proxies, randomized timing
- **Reports to**: GTM Expert → Slack channel #linkedin

### YouTube Agent
- **Runs on**: Orgo VM #3
- **Trigger**: Slack message with Loom link → pipeline starts
- **Pipeline**: Download Loom → Whisper transcribe → FFmpeg remove ums/ahs → Generate thumbnail → SEO research (title, description, tags) → Upload to YouTube as UNLISTED draft → Notify Justin for review
- **Tools**: FFmpeg, Whisper API, YouTube Data API v3, Chromium for YouTube Studio
- **Reports to**: GTM Expert → Slack channel #youtube

### SDR Agent (OpenClaw)
- **Runs on**: Orgo VM #4
- **WHY OPENCLAW**: This is the ONE role where OpenClaw beats Claude Code — native phone/SMS/WhatsApp via `clawphone` and `deepclaw`
- **Repo to start from**: `mergisi/awesome-openclaw-agents` SDR template + `ranacseruet/clawphone`
- **Setup**: OpenClaw installed on Orgo VM, Opus 4.6, Telegram channel
- **5-agent sub-team** (from Claudia's recommendation):
  1. Prospector — enriches leads, scores against ICP
  2. Email SDR — personalized cold emails + sequences
  3. Phone SDR — outbound calls via clawphone/Twilio
  4. Text SDR — SMS via Twilio
  5. Sequence Manager — orchestrates touchpoints, manages handoffs
- **Reports to**: GTM Expert → Slack channel #sdr

### Social Media Agent
- **Runs on**: Orgo VM #5
- **Repo to start from**: `indranilbanerjee/digital-marketing-pro` + `aitytech/agentkits-marketing` (brand-voice-guardian)
- **Cron**: Daily content creation (7 AM), scheduled posting (varies by platform), engagement (3x daily)
- **Tools**: Chromium for personal account posting, platform APIs where available
- **Reports to**: GTM Expert → Slack channel #social

---

## Phase 4: Remaining Agents (Month 2)

### Dev Team Agent
- **Runs on**: VPS
- **Repo to start from**: `garrytan/gstack` (full engineering team) + `wshobson/agents` + `ruvnet/ruflo`
- **How it works**: Co-Founder delegates build tasks → Dev Team plans → implements → tests → deploys
- **Tools**: Full Claude Code with all permissions, git, Docker, SSH
- **Reports to**: Co-Founder → Slack channel #dev

### Recruiter Agent
- **Runs on**: VPS (or Orgo if screening LinkedIn profiles)
- **Repo to start from**: `ParamChoudhary/ResumeSkills` + custom CLAUDE.md
- **How it works**: Job spec in → agent posts to platforms, screens resumes, schedules interviews, generates interview questions
- **Reports to**: Co-Founder → Slack channel #recruiting

---

## How The Co-Founder Orchestrates Everything

### Daily Flow (Automated)
```
6:00 AM — Lead Gen agent scrapes new leads
7:00 AM — Social Media agent creates daily content
8:00 AM — LinkedIn agent posts content + starts engagement
8:30 AM — Co-Founder sends Justin morning briefing via Slack:
           "Good morning. Here's where we stand:
            - Pipeline: 47 new leads, 12 meetings booked this week
            - Cold email: 23% open rate, 4.2% reply rate
            - YouTube: 3 videos in queue, 1 published yesterday (412 views)
            - Website: 99.7% uptime, 3 bug fixes deployed
            - Budget: $847 spent this week, $1,200 allocated
            Priorities today: [list]
            Decisions needed: [list]"
9:00 AM — Cold Email agent sends morning sequences
10:00 AM — SDR agents start call/email/text sequences
11:00 PM — CFO agent runs nightly cost report
6:00 PM — Co-Founder sends evening status via Slack
```

### On-Demand (Justin → Co-Founder)
```
Justin: "Clean up the LinkedIn project and add posting for insurance content"
Co-Founder: SSHs into LinkedIn droplet → reads code → spawns claude -p session →
            makes changes → tests → deploys → reports back

Justin: "Spin up a new GTM sub-agent focused on YouTube shorts"
Co-Founder: Creates agent config → writes CLAUDE.md → sets up cron →
            deploys on YouTube Orgo VM → adds to monitoring → reports back

Justin: "What's our cost per lead this month?"
Co-Founder: Queries CFO agent → gets data → formats response → sends to Slack
```

---

## Key Patterns We're Using

### From Boris Cherny (Created Claude Code)
- CLAUDE.md compounds over time — every mistake, every decision logged
- Plan Mode first, then execute
- Verification loops (2-3x quality improvement)
- `/permissions` for safe tool access patterns
- PostCompact hooks to re-inject critical context
- Opus with thinking for strategy, Haiku for grunt work

### From Eric Siu (10X System)
- Model routing: Opus for strategy, Sonnet for writing, Haiku for data
- Karpathy Loop: agents improve their own instructions based on results
- Self-healing cron doctor runs daily
- Inter-agent communication via shared files + signal bus

### From Nick Vasilescu (OCA Model)
- One agent per role (no context bloat)
- Orgo for desktop agents (visual, isolated, client-showable)
- Phase 4: Package skills → sell to vertical → $2-5K/mo retainer

### From Roman (ClaudeClaw / Sniper Agents)
- 4 zones: Trigger, Context, Tools, Output
- `claude -p` = headless Claude Code (same power, scriptable)
- `--resume` for session persistence
- `--append-system-prompt` for personality
- `--allowedTools` for safety

---

## Cost Summary

| Item | Monthly Cost |
|------|-------------|
| DO VPS (4 vCPU, 8GB) — Orchestrator + CLI agents | $48 |
| Orgo VMs (5 computers) — Desktop agents | $224 |
| Claude Max Plan | Already paying |
| Tailscale | Free |
| Twilio (SDR calls/SMS) | ~$50-100 |
| Whisper API (YouTube transcription) | ~$15 |
| **Total** | **~$337-387/mo** |

### Phase 4 Revenue (OCA Model)
| Clients | Monthly Revenue | Monthly Profit |
|---------|----------------|----------------|
| 2 clients @ $3K | $6,000 | ~$5,200 |
| 5 clients @ $3K | $15,000 | ~$13,500 |
| 10 clients @ $4K | $40,000 | ~$37,000 |

---

## What Gets Built vs What Gets Copied

| Role | Build or Copy | Source |
|------|--------------|--------|
| Co-Founder | BUILD (custom CLAUDE.md + ClaudeClaw) | ClaudeClaw base + custom |
| CFO | COPY | charlie-cfo-skill |
| GTM Expert | COPY + customize | digital-marketing-pro |
| Cold Email | EXTEND existing | Your Python system + email-wizard |
| Website/CTO | COPY | gstack (/qa, /ship) + claude-autofix-bot |
| YouTube | BUILD pipeline | Custom (Whisper + FFmpeg + YT API) |
| SDR | COPY | awesome-openclaw-agents SDR template + clawphone |
| LinkedIn | EXTEND existing | Your DO project + browser automation |
| Social Media | COPY + customize | digital-marketing-pro + brand-voice-guardian |
| Dev Team | COPY | gstack + ruflo |
| Recruiter | COPY + customize | ResumeSkills + custom CLAUDE.md |

**7 out of 11 roles are mostly copy-paste from proven repos.** Only Co-Founder and YouTube need significant custom work. LinkedIn and Cold Email extend what you already have.
