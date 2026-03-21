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

