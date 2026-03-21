# Role-to-Repo Mapping: Proven Implementations

Every role matched to GitHub repos with working code. Copy what works.

---

## 1. CO-FOUNDER

**What they do**: Strategic advisor, vision, goals, mission, organization, tracks all workstreams

| Repo | Platform | What it provides | Stars |
|------|----------|-----------------|-------|
| [EveryInc/charlie-cfo-skill](https://github.com/EveryInc/charlie-cfo-skill) | Claude Code | Charlie Munger-style advisor: strategic thinking, capital allocation, Rule of 40 | - |
| [alirezarezvani/claude-skills](https://github.com/alirezarezvani/claude-skills) (solo-founder persona) | Claude Code | Pre-configured solo-founder persona covering strategy, ops, finance | ~5,200 |
| [daxaur/openpaw](https://github.com/daxaur/openpaw) | Claude Code | 38-skill personal assistant: email, calendar, task dashboard, smart scheduling | - |
| [mergisi/awesome-openclaw-agents](https://github.com/mergisi/awesome-openclaw-agents) (Personal CRM agent) | OpenClaw | CRM agent with relationship tracking, follow-up scheduling | 18 |
| [garrytan/gstack](https://github.com/garrytan/gstack) (`/plan-ceo-review`) | Claude Code | CEO-level product strategy review | 23,600 |
| [sgharlow/claude-code-recipes](https://github.com/sgharlow/claude-code-recipes) (Tier 8) | Claude Code | Revenue operations, executive reporting recipes | - |

**Best starting point**: Combine `charlie-cfo-skill` (strategic thinking) + `openpaw` (personal assistant) + gstack `/plan-ceo-review` (CEO review). Run as `claude -p` on VPS with morning/evening cron.

---

## 2. GO-TO-MARKET EXPERT

**What they do**: Oversee cold email, LinkedIn, YouTube strategy. Research + execution.

| Repo | Platform | What it provides | Stars |
|------|----------|-----------------|-------|
| [indranilbanerjee/digital-marketing-pro](https://github.com/indranilbanerjee/digital-marketing-pro) | Claude Code | 115 slash commands, 25 agents, 67 MCP servers. Publish content, launch ads, schedule social, sync CRMs. | - |
| [aitytech/agentkits-marketing](https://github.com/aitytech/agentkits-marketing) | Claude Code | 18 agents including attraction-specialist, lead-qualifier, email-wizard, copywriter, seo-specialist | - |
| [coreyhaines31/marketingskills](https://github.com/coreyhaines31/marketingskills) | Claude Code | CRO, copywriting, SEO, analytics, growth engineering, RevOps | - |
| [alirezarezvani/claude-skills](https://github.com/alirezarezvani/claude-skills) (marketing pod) | Claude Code | 7 marketing sub-pods including growth-marketer persona, SaaS metrics | ~5,200 |
| [VoltAgent/awesome-claude-code-subagents](https://github.com/VoltAgent/awesome-claude-code-subagents) | Claude Code | market-researcher, competitive-analyst, trend-analyst, business-analyst subagents | - |
| [rohitg00/awesome-claude-code-toolkit](https://github.com/rohitg00/awesome-claude-code-toolkit) | Claude Code | Marketing-analyst agent with multi-touch attribution, MMM, budget optimization | - |

**Best starting point**: `digital-marketing-pro` is the most comprehensive — 115 commands covering everything GTM. Layer `agentkits-marketing` agents for specialized execution. Run on VPS.

---

## 3. WEBSITE / CTO DEPARTMENT

**What they do**: Manage website, sign-ups, uptime, improvements, feedback

| Repo | Platform | What it provides | Stars |
|------|----------|-----------------|-------|
| [garrytan/gstack](https://github.com/garrytan/gstack) (`/plan-eng-review`, `/qa`, `/ship`) | Claude Code | Architecture review, browser QA testing, release automation | 23,600 |
| [garrytan/gstack](https://github.com/garrytan/gstack) (`/qa`) | Claude Code | Real Chromium browser testing, 100-200ms per command | 23,600 |
| [wshobson/agents](https://github.com/wshobson/agents) | Claude Code | 112 agents including DevOps, infrastructure, monitoring | - |
| [tfriedel/claude-office-skills](https://github.com/tfriedel/claude-office-skills) | Claude Code | 136+ office skills for documentation, reporting | ~232 |
| [MattKilmer/claude-autofix-bot](https://github.com/MattKilmer/claude-autofix-bot) | Claude Code | Slack → Claude Code → Git PR. Bug reported, fix generated automatically. | - |

**Best starting point**: gstack `/qa` + `/ship` for testing and deployment. `claude-autofix-bot` for auto-fixing bugs reported in Slack. Needs Orgo VM for browser-based testing.

---

## 4. YOUTUBE DEPARTMENT

**What they do**: Raw Loom → cleaned video → thumbnails → SEO → publish

| Repo | Platform | What it provides | Stars |
|------|----------|-----------------|-------|
| [indranilbanerjee/digital-marketing-pro](https://github.com/indranilbanerjee/digital-marketing-pro) (social/content) | Claude Code | Content publishing, social scheduling, SEO optimization | - |
| [aitytech/agentkits-marketing](https://github.com/aitytech/agentkits-marketing) (copywriter + seo-specialist) | Claude Code | SEO-optimized content creation, keyword research | - |
| [coreyhaines31/marketingskills](https://github.com/coreyhaines31/marketingskills) (social-content skill) | Claude Code | Social media content strategy and creation | - |
| OpenClaw built-in Whisper integration | OpenClaw | Voice transcription via Whisper API | - |
| FFmpeg (system tool) | CLI | Video editing, cutting, processing | - |

**Best starting point**: Custom pipeline. No single repo handles the full Loom→YouTube flow. Build using:
- Whisper API for transcription
- FFmpeg for video processing (ums/ahs removal based on transcript timing)
- `digital-marketing-pro` SEO skills for title/description/tags
- YouTube Data API v3 for upload (UNLISTED draft)
- Slack trigger → `claude -p` pipeline
- Runs on Orgo VM (needs desktop for YouTube Studio)

---

## 5. SDR (Sales Development Rep)

**What they do**: Call, email, SMS to book appointments. 100-200 prospects/day.

| Repo | Platform | What it provides | Stars |
|------|----------|-----------------|-------|
| [mergisi/awesome-openclaw-agents](https://github.com/mergisi/awesome-openclaw-agents) (SDR Outbound template) | OpenClaw | Lead research + personalized multi-channel outreach (email, LinkedIn, phone), follow-up cadence, A/B testing | 18 |
| [mergisi/awesome-openclaw-agents](https://github.com/mergisi/awesome-openclaw-agents) (Objection Handler) | OpenClaw | Real-time rebuttals during conversations | 18 |
| [mergisi/awesome-openclaw-agents](https://github.com/mergisi/awesome-openclaw-agents) (Pipeline Manager) | OpenClaw | Lead scoring, outreach drafting, pipeline management | 18 |
| [raulvidis/openclaw-multi-agent-kit](https://github.com/raulvidis/openclaw-multi-agent-kit) | OpenClaw | 10-agent team template including SDR research + outreach agents | - |
| [deepgram/deepclaw](https://github.com/deepgram/deepclaw) | OpenClaw | Voice + phone number for outbound calls | - |
| [ranacseruet/clawphone](https://github.com/ranacseruet/clawphone) | OpenClaw | Phone/SMS via Twilio (simplified) | - |
| [19PINE-AI/openclaw-pine-voice](https://github.com/19PINE-AI/openclaw-pine-voice) | OpenClaw | Delegated phone calls with transcripts | - |
| [ComposioHQ/secure-openclaw](https://github.com/ComposioHQ/secure-openclaw) | OpenClaw | 850+ app integrations including CRM, email, Twilio | - |

**Claudia's recommended 5-agent setup:**
1. **Prospector**: Enriches leads, scores against ICP
2. **Email SDR**: Personalized cold emails + follow-up sequences
3. **Phone SDR**: Outbound calls via voice agent
4. **Text SDR**: SMS via Twilio
5. **Sequence Manager**: Orchestrates 3 daily touchpoints, manages handoff to nurture

**Best starting point**: `awesome-openclaw-agents` SDR template + `clawphone` for calls/SMS. This is the ONE area where OpenClaw clearly wins over Claude Code — the multi-channel messaging integration (WhatsApp, Telegram, phone, SMS) is native. Run on Orgo VM.

---

## 6. COLD EMAIL

**What they do**: Personalized outbound sequences via Instantly. Already partially built.

| Repo | Platform | What it provides | Stars |
|------|----------|-----------------|-------|
| [rohitg00/awesome-openclaw](https://github.com/rohitg00/awesome-openclaw) (cold email writer skill) | OpenClaw | Cold email generation with personalization | - |
| [rohitg00/awesome-openclaw](https://github.com/rohitg00/awesome-openclaw) (prospect research skill) | OpenClaw | Lead research and ICP qualification | - |
| [aitytech/agentkits-marketing](https://github.com/aitytech/agentkits-marketing) (email-wizard agent) | Claude Code | Email sequence creation and optimization | - |
| [coreyhaines31/marketingskills](https://github.com/coreyhaines31/marketingskills) (email-sequence skill) | Claude Code | Email sequence strategy and copywriting | - |
| [alirezarezvani/claude-skills](https://github.com/alirezarezvani/claude-skills) (Sales pod) | Claude Code | Sales email templates, objection handling | ~5,200 |
| Justin's existing system | Python | Scrapers (Apify, Apollo), enrichment, Instantly integration, offer templates | Local |

**Best starting point**: Your existing Python cold email system is already built. Layer `email-wizard` from `agentkits-marketing` for AI-powered personalization. Connect to Instantly via existing N8N workflow or direct API.

---

## 7. LINKEDIN

**What they do**: Outreach, content, engagement, lead extraction

| Repo | Platform | What it provides | Stars |
|------|----------|-----------------|-------|
| [rohitg00/awesome-openclaw](https://github.com/rohitg00/awesome-openclaw) (LinkedIn outreach skill) | OpenClaw | LinkedIn DM outreach automation | - |
| [aitytech/agentkits-marketing](https://github.com/aitytech/agentkits-marketing) (attraction-specialist) | Claude Code | Lead gen campaigns including LinkedIn | - |
| [indranilbanerjee/digital-marketing-pro](https://github.com/indranilbanerjee/digital-marketing-pro) | Claude Code | Social scheduling including LinkedIn | - |
| Justin's existing N8N workflows | N8N | 6 LinkedIn workflows: daily scraper, content agent, prospecting, engagement, lead extraction, SDR orchestrator | Local |

**Best starting point**: Your 6 existing N8N workflows already handle LinkedIn. The question is whether to run them standalone or have an agent operate them. If using Orgo VM, the agent can directly interact with LinkedIn in a browser (more natural, harder to detect).

---

## 8. RECRUITER

**What they do**: Find recruits, screen, do interviews

| Repo | Platform | What it provides | Stars |
|------|----------|-----------------|-------|
| [mergisi/awesome-openclaw-agents](https://github.com/mergisi/awesome-openclaw-agents) (HR category) | OpenClaw | Employee onboarding agent template | 18 |
| [sgharlow/claude-code-recipes](https://github.com/sgharlow/claude-code-recipes) (Tier 7 - HR) | Claude Code | HR, learning & development, people management recipes | - |
| [ParamChoudhary/ResumeSkills](https://github.com/ParamChoudhary/ResumeSkills) | Claude Code | 20 skills: resume screening, ATS analysis, interview prep | - |
| [rohitg00/awesome-openclaw](https://github.com/rohitg00/awesome-openclaw) (meeting prep skill) | OpenClaw | Meeting/interview preparation and brief generation | - |
| [VoltAgent/awesome-claude-code-subagents](https://github.com/VoltAgent/awesome-claude-code-subagents) (business-analyst) | Claude Code | Requirements elicitation, stakeholder management (applicable to job specs) | - |

**Best starting point**: `ResumeSkills` for screening + resume analysis. OpenClaw HR template for candidate communication (email/Telegram). Custom SOUL.md for interview question generation and scoring. Run on VPS (no desktop needed for most recruiting tasks, unless screening LinkedIn profiles — then Orgo).

---

## 9. SOCIAL MEDIA

**What they do**: Content creation, posting, engagement across platforms

| Repo | Platform | What it provides | Stars |
|------|----------|-----------------|-------|
| [indranilbanerjee/digital-marketing-pro](https://github.com/indranilbanerjee/digital-marketing-pro) | Claude Code | Social scheduling, content publishing, cross-platform posting | - |
| [aitytech/agentkits-marketing](https://github.com/aitytech/agentkits-marketing) (copywriter + brand-voice-guardian) | Claude Code | On-brand content creation, copy optimization | - |
| [coreyhaines31/marketingskills](https://github.com/coreyhaines31/marketingskills) (social-content skill) | Claude Code | Social media content strategy | - |
| [mergisi/awesome-openclaw-agents](https://github.com/mergisi/awesome-openclaw-agents) (Social Media Manager template) | OpenClaw | Cross-platform social media management | 18 |
| [VoltAgent/awesome-openclaw-skills](https://github.com/VoltAgent/awesome-openclaw-skills) | OpenClaw | 5,400+ skills including social media automation | - |

**Best starting point**: `digital-marketing-pro` has the most complete social stack (publish content, schedule, track). Layer `brand-voice-guardian` to keep content consistent. If posting needs browser interaction → Orgo VM. If API-based → VPS.

---

## 10. DEV TEAM

**What they do**: Build all the stuff we want. Architecture + engineering.

| Repo | Platform | What it provides | Stars |
|------|----------|-----------------|-------|
| [garrytan/gstack](https://github.com/garrytan/gstack) | Claude Code | Full engineering team: `/plan-eng-review`, `/review`, `/qa`, `/ship`, `/retro` | 23,600 |
| [ruvnet/ruflo](https://github.com/ruvnet/ruflo) | Claude Code | 60+ agents: coder, tester, reviewer, architect, security-architect, performance-engineer | - |
| [wshobson/agents](https://github.com/wshobson/agents) | Claude Code | 112 agents, 16 workflow orchestrators, 146 skills, 79 dev tools | - |
| [barkain/claude-code-workflow-orchestration](https://github.com/barkain/claude-code-workflow-orchestration) | Claude Code | Multi-step orchestration, parallel agent execution, specialized delegation | - |
| [MattKilmer/claude-autofix-bot](https://github.com/MattKilmer/claude-autofix-bot) | Claude Code | Slack → Claude Code → Git PR bug fixing | - |
| [baryhuang/claude-code-by-agents](https://github.com/baryhuang/claude-code-by-agents) | Claude Code | Multi-agent coordination via @mentions | - |

**Best starting point**: gstack is the gold standard — built by YC's president, proven at scale. Add Ruflo for complex multi-agent orchestration. `claude-autofix-bot` for Slack-triggered bug fixes. This is purely Claude Code territory — no OpenClaw needed.

---

## 11. CFO

**What they do**: Cost tracking, budget, ROI analysis

| Repo | Platform | What it provides | Stars |
|------|----------|-----------------|-------|
| [EveryInc/charlie-cfo-skill](https://github.com/EveryInc/charlie-cfo-skill) | Claude Code | Cash management, unit economics (LTV:CAC), capital allocation, 13-week cash flow, driver-based planning, Rule of 40 | - |
| [alirezarezvani/claude-skills](https://github.com/alirezarezvani/claude-skills) (finance module) | Claude Code | DCF valuation, budget variance analyzer, rolling forecast, SaaS metrics (MRR, churn), ratio analysis | ~5,200 |
| [quant-sentiment-ai/claude-equity-research](https://github.com/quant-sentiment-ai/claude-equity-research) | Claude Code | Institutional-grade financial analysis, scenario modeling | - |
| [lab1702/claude-financial-analysis](https://github.com/lab1702/claude-financial-analysis) | Claude Code | Structured financial reports | - |

**Best starting point**: `charlie-cfo-skill` is purpose-built for this. Named after Charlie Munger. Handles bootstrapped company finances perfectly. Run on VPS with Haiku model (cheapest — just reads numbers and formats). Nightly cron.

---

## Summary: Where Each Role Runs

| Role | Platform | Runs On | Best Repo(s) |
|------|----------|---------|-------------|
| Co-Founder | Claude Code | VPS | charlie-cfo-skill + openpaw + gstack |
| GTM Expert | Claude Code | VPS | digital-marketing-pro + agentkits-marketing |
| Website/CTO | Claude Code | **Orgo VM** | gstack + claude-autofix-bot |
| YouTube | Claude Code | **Orgo VM** | Custom pipeline (Whisper + FFmpeg + YT API) |
| SDR | **OpenClaw** | **Orgo VM** | awesome-openclaw-agents SDR template + clawphone |
| Cold Email | Claude Code | VPS | Existing Python system + email-wizard |
| LinkedIn | Claude Code | **Orgo VM** | Existing N8N workflows + browser automation |
| Recruiter | Claude Code | VPS | ResumeSkills + custom SOUL.md |
| Social Media | Claude Code | VPS or Orgo | digital-marketing-pro |
| Dev Team | Claude Code | VPS | gstack + ruflo + wshobson/agents |
| CFO | Claude Code | VPS | charlie-cfo-skill |

**OpenClaw wins at**: SDR (multi-channel messaging is native — phone, SMS, WhatsApp, Telegram)
**Claude Code wins at**: Everything else (glass box, Max plan tokens, skills ecosystem, dev tooling)
