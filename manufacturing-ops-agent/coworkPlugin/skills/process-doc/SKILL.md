---
name: process-doc
description: Author manufacturing process documentation — SOPs, standard work, work instructions, and escalation paths. Use when the user asks to write an SOP, standard operating procedure, work instruction, standard work sheet, operator balance chart elements, or escalation tree for non-conformances.
argument-hint: "[doc type — SOP | work-instruction | standard-work | escalation] [process name]"
---

# /process-doc — Process Documentation

Produce ISO 9001-compliant documentation with revision control, CTQ callouts, and clear escalation paths.

## Required clarifications

- Document type (SOP / work instruction / standard work / escalation path)
- Process or operation name
- Applicable standard (ISO 9001, IATF 16949, FDA 21 CFR Part 820, GMP)
- Required PPE and safety considerations
- Quality checkpoints / CTQs

## SOP structure

```markdown
# SOP-[ID] — [Process Name]
**Revision:** [n.n] | **Effective:** [date] | **Owner:** [role]
**Approvals:** [Quality Engineer] | [Production Supervisor] | [Plant Manager]

## 1. Purpose
## 2. Scope
## 3. Responsibilities (RACI)
## 4. PPE & Safety Requirements
## 5. Procedure
  5.1. [Step 1 — CTQ: …]
  5.2. [Step 2 — go/no-go: …]
  …
## 6. Quality Checkpoints
| Step | Characteristic | Spec | Method | Frequency |
## 7. Non-Conformance Handling
[Decision tree → escalation path]
## 8. Records & Retention
## 9. Revision History
```

## Standard work structure

- Takt time, cycle time, work sequence
- Standard WIP between stations
- Operator balance chart elements (cycle bars by station)

## Work instructions

- Visual-friendly numbered steps with photo callouts
- CTQ markers at critical-to-quality steps
- Go/no-go criteria at each step

## Escalation path template

```
Operator (0–5 min) → Team Lead (5–10 min) → Supervisor (10–20 min)
→ Quality Engineer (20–45 min) → Plant Manager (45+ min)
```

## Standards

ISO 9001 §7.5 document control (ID, revision, effective date, approvals). OSHA-applicable safety warnings. FDA 21 CFR Part 820 if medical device. IATF 16949 control plan linkage if automotive.
