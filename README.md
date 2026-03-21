# OpenClaw 10X — Multi-Agent Deployment Reference Guide

> Deploy 11 AI agent teams for ~$280/month using Claude Code + Ruflo + Orgo VMs. Internal system for your business, OCA retainer model for clients.

**The play**: Internal agents on Claude Code (glass box, Max plan tokens). Client deployments on OpenClaw + Orgo ($2-5K/mo retainer, 85-95% margin).

---

## What's Inside

| File | What |
|------|------|
| [Reference Guide](./OpenClaw-10X-Reference-Guide.md) | Master reference: architecture, infrastructure, key people, all repos, decisions |
| [Role-to-Repo Mapping](./Role-to-Repo-Mapping.md) | All 11 roles mapped to proven GitHub repos with deployment recommendations |
| [Deployment Plan](./Deployment-Plan.md) | 4-phase rollout plan with architecture diagrams and cost breakdowns |

---

## 11 Agent Roles

| # | Role | Platform | Runs On | Best Repo |
|---|------|----------|---------|-----------|
| 1 | Co-Founder | Claude Code | VPS | charlie-cfo-skill + openpaw + gstack |
| 2 | GTM Expert | Claude Code | VPS | digital-marketing-pro + agentkits-marketing |
| 3 | Website/CTO | Claude Code | Orgo VM | gstack + claude-autofix-bot |
| 4 | YouTube | Claude Code | Orgo VM | Custom pipeline (Whisper + FFmpeg + YT API) |
| 5 | SDR | **OpenClaw** | Orgo VM | awesome-openclaw-agents + clawphone |
| 6 | Cold Email | Claude Code | VPS | Existing Python system + email-wizard |
| 7 | LinkedIn | Claude Code | Orgo VM | Existing N8N workflows + browser |
| 8 | Recruiter | Claude Code | VPS | ResumeSkills + custom SOUL.md |
| 9 | Social Media | Claude Code | VPS/Orgo | digital-marketing-pro |
| 10 | Dev Team | Claude Code | VPS | gstack + ruflo + wshobson/agents |
| 11 | CFO | Claude Code | VPS | charlie-cfo-skill |

**OpenClaw wins at**: SDR (multi-channel messaging — phone, SMS, WhatsApp, Telegram is native)
**Claude Code wins at**: Everything else (glass box, Max plan tokens, skills ecosystem, dev tooling)

## Architecture

```
┌─────────────────────────────────────────────────────┐
│                    YOU (Owner)                       │
│         Slack / Telegram / Custom Dashboard          │
└────────────────────┬────────────────────────────────┘
                     │
┌────────────────────▼────────────────────────────────┐
│              RUFLO (Orchestration)                   │
│  - 60+ agent types, swarm coordination              │
│  - MCP-based inter-agent communication              │
│  - SvelteKit dashboard                              │
└────────────────────┬────────────────────────────────┘
                     │
     ┌───────────────┼───────────────┐
     │               │               │
┌────▼─────┐  ┌──────▼──────┐  ┌────▼─────┐
│ Orgo VMs │  │  VPS Agents │  │ Orgo VMs │
│ (desktop │  │  (CLI only) │  │ (desktop │
│ agents)  │  │             │  │ agents)  │
└──────────┘  └─────────────┘  └──────────┘
```

## Cost

| Component | Monthly |
|-----------|---------|
| Digital Ocean VPS (4 vCPU, 8GB) | $48 |
| Orgo VMs (5 desktops) | $224 |
| Claude Max plan | Existing |
| Whisper API | ~$15 |
| Tailscale | Free |
| Ruflo + gstack | Free |
| **Total new spend** | **~$280/month** |

## Key People Referenced

- **Boris Cherny** — Created Claude Code. 10-15 parallel sessions, CLAUDE.md compounding, verification loops.
- **Eric Siu** — 6 agents, 48 cron jobs. Model routing: $500/day → $25/day. Karpathy loop for self-improvement.
- **Garry Tan** — YC President. gstack: 15 slash commands, 600K+ lines in 60 days.
- **Nick Vasilescu** — OCA business model. $2-5K/mo retainer, infiltrate with ONE workflow in 7 days.
- **Roman** — `claude -p` sniper agents. Telegram trigger, session persistence, tool restriction.

## Related Projects

- [OpenClaw SDR Agent](https://github.com/jbellsolutions/openclaw-sdr-agent) — Optimized 5-agent SDR team with autoresearch case study

## License

MIT
