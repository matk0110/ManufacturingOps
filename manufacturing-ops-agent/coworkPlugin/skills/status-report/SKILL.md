---
name: status-report
description: Generate a daily production status report, shift summary, or plant leadership review. Use when the user asks for a production review, daily status, shift summary, plant leadership report, or end-of-shift report covering output vs. target, downtime, quality, and safety.
argument-hint: "[shift] [line or cell]"
---

# /status-report — Daily Production Status Report

Produce a plant-floor status report formatted for a leadership stand-up. Every section gets a RAG (Red/Amber/Green) indicator for quick visual scanning. Always surface safety items first.

## Required clarifications (ask before generating)

- Plant / line / cell in scope
- Shift (1st / 2nd / 3rd) and date
- Product family or part numbers
- Source of metrics (MES, manual count, ERP)

If actual numbers aren't supplied, use `[ENTER VALUE]` placeholders — never invent metrics.

## Output structure

```markdown
# Daily Production Status — [Plant] [Line] [Shift] [Date]

## 🟢/🟡/🔴 Safety
- Recordable incidents: [n]
- Near-misses: [n]
- Behavioral observations: [n]
- Days since last recordable: [n]
- Open safety actions: [list]

## 🟢/🟡/🔴 Production Output
| Metric | Plan | Actual | Variance | OEE |
|---|---|---|---|---|
| Units | | | | |
| Throughput (UPH) | | | | |

## 🟢/🟡/🔴 Downtime
- Planned: [hrs]
- Unplanned: [hrs]
- Top 3 Pareto causes: 1) … 2) … 3) …
- MTBF: [hrs]  |  MTTR: [min]

## 🟢/🟡/🔴 Quality
- First Pass Yield (FPY): [%]
- Scrap rate: [%]
- Rework rate: [%]
- DPMO: [n]
- Open quality holds: [n] ([lot/batch ids])

## Key Actions — Next Shift
1. [Priority action — owner — due]
2. …
3. …

## Escalations to Management
- …
```

## Manufacturing terminology to use correctly

OEE (Availability × Performance × Quality), takt time, FPY, DPMO, MTBF, MTTR, Pareto, RAG. Reference standards by clause where applicable (e.g., ISO 9001 §9.1 monitoring).
