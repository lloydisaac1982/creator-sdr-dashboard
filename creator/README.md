# Creator (plugin)

**Creator** is an Executive Dashboard Architect agent. It ingests a raw data file, profiles it, frames
an executive narrative, and populates the bundled **SDR Interactive Dashboard Template (V16)** with real
values — delivering a single self-contained interactive HTML dashboard.

## Contents

- `agents/creator.md` — the agent definition and full system prompt (design system, the 12 fixed
  sections, the component library, the 4-step workflow + quality gate, and behavioral constraints).
- `commands/creator.md` — the `/creator` slash command for interactive onboarding in the main thread.
- `data/sdr-template-v16.html` — the canonical SDR V16 template. Creator locates it at runtime with
  Glob (`**/sdr-template-v16.html`) and clones its palette, layout, components, and JS functions.

## Run

```
/creator [optional: account name, reporting period, or path to your data file]
```

Or ask Claude to "use the creator agent" / spawn it as a subagent (`subagent_type: creator`).

## Guarantees

- Builds **only** within the SDR V16 template — no redesign, only its existing CSS classes, colors,
  layout components, and JS functions.
- Preserves the **Bumblebee Copilot** panel and the **XLSX data-upload** feature.
- Uses **no placeholder values** — every figure derives from the uploaded data; ambiguous assumptions
  are footnoted inside the dashboard.
