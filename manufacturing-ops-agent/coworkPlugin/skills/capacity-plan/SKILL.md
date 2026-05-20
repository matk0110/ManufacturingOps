---
name: capacity-plan
description: Build a manufacturing capacity plan with bottleneck and constraint analysis. Use when the user asks about capacity planning, line/load balance, demonstrated capacity, labor or machine bottlenecks, takt vs. cycle time, or whether they can meet customer demand.
argument-hint: "[line or cell] [horizon — week | month | quarter]"
---

# /capacity-plan — Capacity Planning & Constraint Analysis

Apply Theory of Constraints (TOC) thinking. Identify the constraint, quantify it, recommend rebalancing.

## Required clarifications

- Lines / cells in scope and product mix
- Horizon (week, month, quarter)
- Customer demand and takt time
- Available shifts × hours × days, planned maintenance, changeover plan
- Headcount and skill matrix

## Method

1. **Available Time** per resource = (Shifts × Hours × Days) − Planned Downtime
2. **Demand** = Customer takt × Units required
3. **Constraint** = resource with lowest (Available Time ÷ Demand) ratio
4. **Constraint utilization** = Demonstrated output ÷ Theoretical max

## Output structure

```markdown
# Capacity Plan — [Line] [Horizon]

## Demand vs. Capacity
| Line / Cell | Demand (units) | Demonstrated Cap | Gap | Utilization % |

## Bottleneck Identification (TOC)
- Constraint resource: [name]
- Constraint utilization: [%]
- Buffer policy: [DBR / time buffer]

## Labor Analysis
- Headcount vs. standard: [n / n]
- Skill matrix gaps: [list]
- OT requirement: [hrs/week]

## Machine Utilization
- Scheduled hrs vs. available: [n / n]
- Planned maintenance windows: [schedule]
- Changeover impact: [SMED target vs. actual]

## Recommendations (ranked)
1. Rebalance / overtime / subcontract / capex — with $ impact and lead time
```

## Reference

Use TOC vocabulary (constraint, exploit, subordinate, elevate). Standard capacity formula above. SMED for changeover reduction. Frame all recommendations against waste elimination (TIMWOODS).
