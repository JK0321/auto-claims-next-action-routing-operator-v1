# Assignment Capacity Roster

This roster is for demo routing only. It does not represent a live claim assignment system.

The capacity roster helps the operator check whether a recommended resource is available before assignment. If a resource is at max capacity, the packet should identify the capacity issue and recommend an alternate sourcing or governance action.

| Resource ID | Resource Type | Handling Role | Current Load | Max Load | Capacity Status | Fallback Action |
|---|---|---|---:|---:|---|---|
| DESK-AUTO-01 | Internal Desk | Standard Auto Desk Handling | 13 | 15 | Available | Assign directly |
| FIELD-AUTO-01 | Field Adjuster | Field Investigation / Scene Review | 15 | 15 | At Capacity | Reroute to IA vendor or supervisor queue |
| IA-AUTO-01 | Independent Adjuster | Field overflow / external inspection | 9 | 15 | Available | Assign if field staff unavailable |
| SIU-REVIEW-01 | SIU Review Queue | SIU referral review consideration | 12 | 15 | Available | Submit for SIU review consideration |
| SUP-AUTO-01 | Supervisor Queue | Approval / complex routing review | 14 | 15 | Available | Route for supervisor approval |

## Capacity Rule

If `Current Load` is equal to `Max Load`, the resource is at capacity and should not receive a new assignment.

The routing packet should then show:

```text
WORKLOAD STATUS:
15/15 — At Capacity

CAPACITY ACTION:
Do not assign. Reroute to alternate resource or supervisor queue.
```

If the resource is below max capacity, the routing packet should show:

```text
WORKLOAD STATUS:
13/15 — Available

CAPACITY ACTION:
Direct assignment allowed.
```
