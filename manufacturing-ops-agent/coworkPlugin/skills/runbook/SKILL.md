---
name: runbook
description: Create or run a manufacturing operational runbook — shift handoff, line-down response, or quality hold process. Use when the user asks for a shift handoff, line down playbook, equipment failure escalation, quality hold workflow, batch isolation procedure, or 8D investigation flow.
argument-hint: "[handoff | line-down | quality-hold]"
---

# /runbook — Shift Handoff & Operational Runbooks

Three runbook flavors. Ask which one applies, then produce the matching structure.

## Required clarifications

- Runbook type (handoff / line-down / quality-hold)
- Plant, line, shift
- Current open items (tickets, holds, permits)

---

## Shift Handoff Runbook

```markdown
# Shift Handoff — [Line] — [Outgoing → Incoming Shift] — [Date]

## Production Status
| Line | Plan | Actual | Run rate | Schedule adherence |

## Open Issues
- Equipment tickets (priority): [list with ticket IDs]
- Quality holds (lot/batch): [list]
- Material shortages pending: [list]

## Active Safety Permits
- LOTO: [equipment, owner]
- Confined space: [permit ID, expires]
- Hot work: [permit ID, expires]

## Carry-Over Actions
| Task | Owner | Expected complete |

## Top 3 Priorities for Incoming Shift
1. …
2. …
3. …
```

---

## Line-Down Response Runbook

**Immediate (first 5 min):** Safety check → Notify supervisor → Start downtime clock → Operator-level troubleshooting.

**Escalation tiers:**
| Tier | Owner | Window | Trigger to next tier |
|---|---|---|---|
| 1 | Operator | 0–5 min | Can't restart |
| 2 | Maintenance tech | 5–15 min | Mechanical/electrical issue persists |
| 3 | Engineering | 15–30 min | Root cause unclear or repeat failure |
| 4 | Management + vendor | 30+ min | Production impact > [threshold] |

**Communication protocol:** define who is notified at each tier and what data goes in the notification (line, time down, symptoms, parts/lots affected).

**Recovery checklist:** equipment restart procedure → first-piece inspection → SPC re-verification → release to run.

---

## Quality Hold Process

1. **Initiate hold** — apply hold tag, isolate lot/batch, enter hold in MES/ERP
2. **Containment** — sweep WIP and finished goods, customer notification if shipped
3. **Investigation** — 8D or 5-Why; assign Quality Engineer
4. **Disposition** — use-as-is / rework / scrap / RTV
5. **Release criteria** — QE sign-off + re-inspection results + (if needed) customer concession

```markdown
# Quality Hold — Lot [ID]
**Initiated:** [date/time] by [name]
**Reason code:** [defect, supplier, process, customer complaint]
**Affected:** [units, locations]
**Containment status:** [open / closed]
**Investigation owner:** [QE name] | **Due:** [date]
**Disposition:** [pending / decision]
**Customer notified:** [Y/N — date]
```

## Safety first

Always lead with safety status. If LOTO or confined-space permits are active, surface them at the top of every runbook output.
