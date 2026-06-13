# Auto Claims Routing Tree

This tree shows how the Auto Claims Next-Action Routing Operator moves from raw claim material to routing, sourcing, tracking, and completion review.

```text
Auto Claim Material
│
├── 1. Intake Preparation
│   ├── Clean raw claim facts
│   ├── Summarize and extract facts from source documents if needed
│   ├── Identify missing information
│   └── Identify contradictions
│
├── 2. Structured Auto Claim Referral
│   ├── Loss facts
│   ├── Parties / vehicles
│   ├── Injury indicators
│   ├── Liability facts
│   ├── Coverage concerns
│   └── Available documents
│
├── 3. Routing Decision
│   ├── Select one primary route
│   ├── Identify one main reason
│   ├── Identify next action
│   └── Apply task / modifier flags
│
├── 4. Routing Confidence
│   ├── High
│   │   └── Facts clearly support the route
│   ├── Medium
│   │   └── Route is reasonable, but non-blocking info is missing
│   └── Low
│       └── Facts are incomplete, conflicting, or require human review
│
├── 5. Sourcing / Governance
│   ├── Internal desk
│   ├── Field staff
│   ├── Independent adjuster / vendor
│   ├── Supervisor approval
│   └── SIU referral / review consideration
│
├── 6. Capacity Check
│   ├── Check current load against max load
│   ├── Show workload status, such as 13/15 or 15/15
│   ├── If available, allow assignment
│   └── If at capacity, reroute to alternate resource or supervisor queue
│
├── 7. Demo Ledger Tracking
│   ├── Case ID
│   ├── Route
│   ├── Sourcing model
│   ├── Governance action
│   ├── Routing confidence
│   └── Status
│
└── 8. Completion / Report Review
    ├── Accept report
    ├── Return for correction
    ├── Request follow-up
    ├── Reroute
    ├── Escalate
    └── Close assignment
```

## Clean Workflow

```text
Intake Preparation
→ Structured Auto Claim Referral
→ Routing Decision
→ Routing Confidence
→ Sourcing / Governance
→ Capacity Check
→ Demo Ledger Tracking
→ Completion / Report Review
```

## What This Adds

Routing confidence adds a decision-quality layer. The packet does not only say where the claim should go. It also shows how strongly the available intake facts support that routing recommendation.

The routing quick reference supports the README by giving a fast scenario-to-route view, while this tree shows the full workflow structure.
