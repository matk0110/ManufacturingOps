---
name: compliance-tracking
description: Track manufacturing compliance and prepare for customer or regulatory audits across OSHA, ISO 9001, IATF 16949, FDA 21 CFR, and GMP. Use when the user asks about compliance, audit prep, audit readiness, gap analysis, CAPA aging, training compliance, customer audit, or regulatory inspection.
argument-hint: "[standard — osha | iso9001 | iatf16949 | fda | gmp | customer] [audit date]"
---

# /compliance-tracking — Regulatory Compliance & Audit Preparation

Generate a clause-by-clause readiness checklist with current status, evidence location, gaps, and remediation owners.

## Required clarifications

- Which standard(s) apply (OSHA / ISO 9001 / IATF 16949 / FDA 21 CFR / cGMP / customer-specific)
- Audit type (internal / external 3rd party / customer / regulatory)
- Audit date (if known)
- Scope (whole plant / specific line / specific process)

## Standards coverage

| Standard | Primary focus areas |
|---|---|
| **OSHA** | HazCom (GHS), machine guarding, LOTO, confined space, PPE, 300 log recordkeeping |
| **ISO 9001** | QMS, document control, internal audit, management review, corrective action (§10.2), customer satisfaction (§9.1.2) |
| **IATF 16949** | Automotive QMS, PPAP, APQP, control plans, MSA, SPC, customer-specific requirements (CSRs) |
| **FDA 21 CFR** | GMP, device history records, complaint handling, CAPA, design controls, IQ/OQ/PQ validation |
| **cGMP** | Batch records, cleaning validation, environmental monitoring, training, deviation management |

## Output — Audit Readiness Checklist

```markdown
# Audit Readiness — [Standard] — [Audit Date]
**Scope:** [plant / line / process]
**Owner:** [name] | **Last updated:** [date]

| Clause / § | Requirement | Status | Evidence location | Gap | Remediation | Owner | Due |
|---|---|---|---|---|---|---|---|
| §9.1 | Monitoring & measurement | 🟢 Compliant | MES dashboards | — | — | — | — |
| §10.2 | Corrective action | 🟡 Partial | CAPA log in QMS | 4 CAPAs aged >90d | Close or extend with rationale | [QE] | [date] |
| §7.1.5 | Monitoring resources | 🔴 Non-compliant | Cal records gap for 3 gages | Calibrate gages G-102, G-104, G-201 | [Metrology] | [date] |
| §6.1 | Risk-based thinking | ⚪ Not assessed | — | Risk register stale | Refresh per /risk-assessment | [QM] | [date] |
```

**Status values:** 🟢 Compliant / 🟡 Partial / 🔴 Non-Compliant / ⚪ Not Assessed

## Customer audit prep (when audit type = customer)

- Customer-specific requirements (CSRs): pull from CSR repository, map to clauses
- Facility tour route plan with stops and talking points
- Document staging list (quality manual, control plans, PPAP packages, training matrices)
- Interview prep for key personnel (operators, leads, QE, supervisors)

## Metrics dashboard

| Metric | Current | Target |
|---|---|---|
| Audit findings open / closed | | |
| CAPA aging > 90 days | | 0 |
| Training compliance % | | ≥ 95% |
| Document review currency (% within review cycle) | | ≥ 95% |

## Reminders

- Cite clauses by number (e.g., ISO 9001 §10.2, IATF 16949 §10.2.3, OSHA 29 CFR 1910.147 LOTO).
- For 🔴 non-compliant items, every entry requires a remediation owner, target date, and verification method.
- If the user asks for a single integrated checklist across multiple standards, group rows by topic (training, document control, calibration) not by standard.
