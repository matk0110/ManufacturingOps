---
name: risk-assessment
description: Triage manufacturing risks across safety, quality, supplier, production, and delivery domains using a 5×5 severity × likelihood matrix and FMEA framing. Use when the user asks about a risk assessment, risk register, what could go wrong, FMEA, RPN, or risk mitigation plan for a manufacturing operation.
argument-hint: "[domain — safety | quality | supplier | production | delivery | all]"
---

# /risk-assessment — Risk Assessment & Triage

Score each risk severity (1–5) × likelihood (1–5), classify, assign owner and target date, and recommend mitigations. Where applicable, map to Process FMEA (severity × occurrence × detection = RPN).

## Required clarifications

- Domain(s) in scope (safety / quality / supplier / production / delivery / all)
- Plant, line, product family
- Time horizon (current state, next 90 days, annual)
- Whether output should integrate with an existing PFMEA

## Risk categories — what to look for

- **Safety:** ergonomic hazards, chemical exposure, machine guarding, fall protection, electrical safety, LOTO compliance
- **Quality:** process capability (Cpk) drift, MSA variation, incoming material PPM trend, customer complaints
- **Supplier:** single-source dependency, lead time variability, financial health, quality history (PPM trend)
- **Production:** equipment age / reliability, skill concentration, capacity utilization stress, planned maintenance gaps
- **Delivery:** schedule adherence trend, WIP levels, transportation risk, customer ship-to commitments

## Scoring matrix (5×5)

| Score | Severity | Likelihood |
|---|---|---|
| 1 | Negligible | Rare (<1/year) |
| 2 | Minor | Unlikely (1–2/year) |
| 3 | Moderate | Possible (quarterly) |
| 4 | Major | Likely (monthly) |
| 5 | Catastrophic | Almost certain (weekly+) |

| RPN range | Classification | Action |
|---|---|---|
| 20–25 | 🔴 Critical | Immediate action; escalate to plant manager |
| 15–19 | 🟠 High | Action plan within 24 hours; named owner |
| 8–14 | 🟡 Medium | Monitor weekly; include in management review |
| 1–7 | 🟢 Low | Accept and monitor quarterly |

## Output structure

```markdown
# Risk Register — [Plant / Line] — [Date]

| # | Domain | Risk | Sev | Lik | Score | Class | Mitigation | Owner | Due | Verification |
|---|---|---|---|---|---|---|---|---|---|---|
| 1 | Safety | … | 4 | 3 | 12 | 🟡 | … | | | |
| 2 | Quality | … | 5 | 2 | 10 | 🟡 | … | | | |

## Top 5 by score
1. …

## FMEA integration (if requested)
| Failure mode | Effect | Cause | S | O | D | RPN | Recommended action |
```

## Reminders

- Safety risks are surfaced first regardless of score.
- For high/critical items, mitigation must include: countermeasure, owner, target date, verification method.
- Reference applicable standard clauses (OSHA, ISO 9001 §6.1 risk-based thinking, IATF 16949 §6.1, FDA 21 CFR risk management) where relevant.
