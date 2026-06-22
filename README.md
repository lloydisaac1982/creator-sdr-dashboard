# 🎨 Creator — Executive Dashboard Architect

Creator is an AI agent (a [Claude Code](https://claude.com/claude-code) plugin) that turns a raw
uploaded data file into a polished, **executive-ready interactive HTML dashboard** built on the
**SDR Interactive Dashboard Template (V16)** — a production-grade, multi-section dashboard framework
with a fixed Unisys-branded design system, navigation, and component library.

Creator never invents a new design system. It **profiles your data, frames an executive narrative,
and populates the SDR V16 template** with real values — then delivers a single self-contained HTML file.

## What it does

1. **Profiles** the uploaded file — detects whether it's ITSM (incidents/tasks/changes), FTE/billing,
   service performance, team/HR, or mixed; maps columns to template fields; identifies the account and
   reporting period; flags anomalies, outliers, and SLA breaches.
2. **Frames the executive narrative** — headline metric, overall RAG status, three key insights
   ("what's working / needs attention / to watch"), and trend direction vs. the prior period.
3. **Populates the SDR V16 template** section by section using only its existing components — KPI
   cards, RAG badges, data tables, Chart.js charts, lead/escalation cards, and the ITSM module strips —
   filling the chart-init functions with real values and mirroring the top KPIs into the print-export block.
4. **Delivers a single self-contained HTML dashboard**, preserving the **Bumblebee Copilot** panel and
   the **XLSX upload** feature, with a footer noting the source filename, row count, and generation time.

## The 12 fixed sections

Executive Overview · FTE & Cost · Service Performance · People & Capability · Innovation & CIPs ·
Incidents (ITSM) · Tasks (ITSM) · Changes (ITSM) · Team Structure · Escalation Ladder · Accolades ·
Data Upload. Creator activates only the sections your data can support.

## Repository contents

```
.claude-plugin/marketplace.json     # marketplace manifest
creator/
  .claude-plugin/plugin.json        # plugin manifest
  agents/creator.md                 # the agent definition + system prompt
  commands/creator.md               # /creator slash command (interactive onboarding)
  data/sdr-template-v16.html        # the canonical SDR V16 dashboard template (cloned at runtime)
README.md
.gitignore
```

The dashboard template is fully self-contained; its only runtime dependencies are loaded from CDN
(Font Awesome 6.5.1, Google Fonts Space Grotesk + JetBrains Mono, Chart.js 4.4.1, SheetJS 0.18.5,
JSZip 3.10.1) and the page degrades gracefully offline.

## Install / use

This is a Claude Code plugin with a matching slash command.

**As a plugin (recommended):** add this repo as a marketplace and install the `creator` plugin:

```
/plugin marketplace add lloydisaac1982/creator-sdr-dashboard
/plugin install creator@creator-sdr-dashboard
```

Then run `/creator` (optionally with an account name, period, or a path to your data file), or just
ask Claude to "use the creator agent." Creator locates the bundled template via Glob at runtime, so the
plugin's install path doesn't matter.

**Manual:** copy `creator/agents/creator.md` and `creator/commands/creator.md` into your workspace's
`.claude/agents/` and `.claude/commands/`, and keep `sdr-template-v16.html` somewhere Glob can find it.

## Notes

- Every number, label, and status in the output derives from your uploaded data — Creator never uses
  placeholder values, and flags any ambiguous assumption as a footnote inside the dashboard.
- Generated dashboards and source data files are git-ignored so confidential client data stays out of
  the repo.

---

Built by Lloyd Isaac · Unisys
