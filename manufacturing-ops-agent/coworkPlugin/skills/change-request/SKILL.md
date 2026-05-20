---
name: change-request
description: Draft an engineering, tooling, process, or line-changeover change request with impact assessment, approval routing, and validation plan. Use when the user asks about an ECR, ECN, engineering change, tooling change, process change, line changeover approval, PPAP submission, or change control workflow.
argument-hint: "[engineering | tooling | process | line-changeover]"
---

# /change-request — Engineering & Process Change Management

Generate an ECR (or ECN) with the right approvers, validation steps, and breakpoint plan for the change category.

## Required clarifications

- Change category (engineering / tooling / process / line changeover)
- Reason code (cost reduction / quality improvement / customer requirement / safety / regulatory)
- Affected part numbers, work centers, customers
- Target effective date

## ECR structure

```markdown
# ECR-[ID] — [Title]
**Originator:** [name] | **Date:** [date] | **Category:** [eng/tool/process/changeover]
**Reason code:** [code]

## 1. Change Description
[What is changing — before / after]

## 2. Affected Items
- Part numbers: [list]
- Work centers: [list]
- Customers: [list]
- Documents to update: [list]

## 3. Impact Assessment
| Dimension | Impact | Mitigation |
| Quality risk | | |
| Production downtime | [hrs] | |
| Tooling cost | [$] | |
| Training required | [hrs / who] | |
| Inventory impact | [obsolete $] | |

## 4. Required Approvals
[Apply the matrix below]

## 5. Validation Requirements
- [ ] First Article Inspection (FAI)
- [ ] Process Capability Study (Cpk ≥ 1.33)
- [ ] PPAP submission (level [n]) — if automotive customer
- [ ] IQ/OQ/PQ — if regulated (FDA / GMP)

## 6. Implementation Plan
- Effective date: [date]
- Lot / serial breakpoint: [n]
- Communication plan: [audiences, dates]
- Training schedule: [dates, attendees]
```

## Approval matrix

| Change scope | Required approvers |
|---|---|
| Minor (no quality/safety/regulatory impact) | Quality Engineer + Production Supervisor |
| Major (quality/cost/customer impact) | Plant Manager + Quality Manager + Engineering Manager |
| Safety or regulatory | Above + EHS Manager + Compliance Officer |

## Line Changeover Approval (subtype)

Pre-changeover checklist:
- [ ] Materials staged at line
- [ ] Tooling verified and at line
- [ ] Quality standards (limit samples, gauges) posted
- [ ] Operators briefed (toolbox talk)

Execution: SMED — internal vs. external setup, target changeover time vs. actual.

Post-changeover verification: first-piece inspection → dimensional / visual / functional check → process parameters within spec → release to run.

## Standards linkage

IATF 16949 §8.5.6 (control of changes), ISO 9001 §8.5.6, FDA 21 CFR Part 820.70(b) (production and process changes), AIAG PPAP §3 for automotive customer submission.
