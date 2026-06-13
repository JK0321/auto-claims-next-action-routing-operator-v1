# Test Run — Auto Claims Next-Action Routing Operator

These test cases demonstrate the operator's routing logic with realistic post-FNOL auto accident claim referrals. Each input uses the intake form format. Outputs are complete routing packets in the canonical format: primary route, sourcing model, assignment resource, workload status, capacity action, governance action, modifier flags, routing confidence, confidence reason, source documents reviewed, missing information, reason, next action, and draft routing note.

---

## Test Case 1 — Standard PD Claim with Workload Confirmation

### Input

```text
CLAIM NUMBER / FILE IDENTIFIER: MN-2026-044201
DATE OF REFERRAL: June 9, 2026
CARRIER / CLAIMS ORGANIZATION: North Star Insurance
REFERRING ADJUSTER / HANDLER: Greg Sorenson

DATE OF LOSS: June 5, 2026
STATE / JURISDICTION: Minnesota
LOSS LOCATION: 4800 White Bear Avenue N, Maplewood, MN 55110
POLICE REPORT: Yes — Report #26-RWCSO-14029

CLAIMANT NAME: Susan Halverson
CLAIMANT ROLE: Third party
CLAIMANT CONTACT: (651) 330-7722

INSURED NAME: Carlos Reyes
POLICY NUMBER: NSI-2025-100833

INJURY CLAIMED: No
VEHICLE DAMAGE CLAIMED: Yes — third-party estimate $5,600
TOTAL CLAIMED EXPOSURE: $5,600

COVERAGE CONFIRMED: Yes
COVERAGE QUESTION: No
LIABILITY STATUS: Accepted — insured accepted liability at scene per police report

ATTORNEY REPRESENTED: No
COMMERCIAL / RIDESHARE / DELIVERY USE: No
PRIOR CLAIMS HISTORY: None

PRIOR HANDLING: No

SPECIAL FLAGS: None

CURRENT HANDLING STATUS: New referral
URGENCY: Routine

ADDITIONAL NOTES: Desk adjuster Maria Chen currently at 82% workload (within target per supervisor).

SOURCE DOCUMENTS REVIEWED:
- Claim setup summary
- Police report summary
```

### Operator Output

```text
PRIMARY ROUTE:
STANDARD DESK AUTO UNIT

SOURCING MODEL:
INTERNAL DESK

ASSIGNMENT RESOURCE:
Internal Desk

WORKLOAD STATUS:
WITHIN TARGET WORKLOAD

CAPACITY ACTION:
Direct assignment allowed.

GOVERNANCE ACTION:
DIRECT ASSIGNMENT

MODIFIERS / TASK FLAGS:
None.

ROUTING CONFIDENCE:
High

CONFIDENCE REASON:
All required fields present. Coverage confirmed, liability accepted, no injury, no SIU
indicators, no coverage question. Workload confirmed within target (82%). No blocking
gaps.

SOURCE DOCUMENTS REVIEWED:
- Claim setup summary
- Police report summary

MISSING INFORMATION:
None.

REASON:
Coverage confirmed, liability accepted, no injury, no SIU indicators, no attorney, no coverage question, no field work needed. PD-only claim at $5,600, complete referral. Desk adjuster Maria Chen is confirmed within target workload at 82%. No higher-priority gate applies. Routes to standard desk auto unit with direct assignment.

NEXT ACTION:
Directly assign to desk adjuster Maria Chen. Provide full claim summary. No supervisor approval needed.

DRAFT ROUTING NOTE:
New PD claim, standard handling. Claimant Susan Halverson, (651) 330-7722. Liability accepted, police report on file #26-RWCSO-14029. Damage estimate $5,600. Coverage confirmed. Assign to Maria Chen — within target workload per supervisor. Routine handling.
```

### Decision
STANDARD DESK AUTO UNIT → INTERNAL DESK → WITHIN TARGET WORKLOAD → DIRECT ASSIGNMENT

### Why This Decision
All required fields present. No gate conditions apply above priority 8. Workload is confirmed within target — direct assignment is appropriate. This demonstrates the complete happy-path routing: a clean PD claim assigned directly without any hold or supervisor step.

### Result
When workload is confirmed within target, the operator produces DIRECT ASSIGNMENT with no queue hold. This is the expected outcome for a routine, complete PD-only claim with no complicating factors.

---

## Test Case 2 — Complex BI Claim, Attorney Represented, Internal Over Capacity

### Input

```text
CLAIM NUMBER / FILE IDENTIFIER: IL-2026-088774
DATE OF REFERRAL: June 9, 2026
CARRIER / CLAIMS ORGANIZATION: Great Lakes Casualty
REFERRING ADJUSTER / HANDLER: Nancy Fitzgerald

DATE OF LOSS: June 3, 2026
STATE / JURISDICTION: Illinois
LOSS LOCATION: Intersection of Michigan Avenue and East Wacker Drive, Chicago, IL 60611
POLICE REPORT: Yes — Report #26-CPD-551029

CLAIMANT NAME: Antonio Bellini
CLAIMANT ROLE: Third party
CLAIMANT CONTACT: On file via attorney

INSURED NAME: Deborah Kim
POLICY NUMBER: GLC-2025-441009

INJURY CLAIMED: Yes — claimant reports herniated disc at L4-L5, undergoing MRI, first ER visit June 3
VEHICLE DAMAGE CLAIMED: Yes — $22,000 combined
TOTAL CLAIMED EXPOSURE: Estimated $180,000 by adjuster based on injury trajectory

COVERAGE CONFIRMED: Yes
COVERAGE QUESTION: No
LIABILITY STATUS: Disputed — intersection accident, conflicting accounts, police report cites both parties as contributing

ATTORNEY REPRESENTED: Yes — claimant retained Wilson & Kapur, LLC, Chicago, as of June 6

COMMERCIAL / RIDESHARE / DELIVERY USE: No
PRIOR CLAIMS HISTORY: No prior claims

PRIOR HANDLING: No

SPECIAL FLAGS: None

CURRENT HANDLING STATUS: New referral
URGENCY: Time-sensitive — attorney has requested all communications through counsel effective June 6

ADDITIONAL NOTES: Complex auto unit has 4 active adjusters. Three are over workload limit. One (David Park) is at workload limit. No immediate internal capacity confirmed.

SOURCE DOCUMENTS REVIEWED:
- Claim setup summary
- Police report summary
- Attorney representation notice dated June 6
```

### Operator Output

```text
PRIMARY ROUTE:
COMPLEX / MAJOR CASE AUTO UNIT

SOURCING MODEL:
INDEPENDENT ADJUSTER (IA) ASSIGNMENT

ASSIGNMENT RESOURCE:
IA Assignment — pending supervisor authorization

WORKLOAD STATUS:
OVER WORKLOAD LIMIT

CAPACITY ACTION:
Do not direct assign. Complex unit over workload limit. Supervisor to authorize IA
assignment or approve queue hold.

GOVERNANCE ACTION:
SUPERVISOR APPROVAL REQUIRED

MODIFIERS / TASK FLAGS:
INJURY CLAIMED / BI
LIABILITY DISPUTED
ATTORNEY REPRESENTED
MULTI-VEHICLE / MULTI-PARTY
INTERNAL CAPACITY CONSTRAINT
VENDOR ASSIGNMENT REQUIRED
SUPERVISOR REVIEW REQUIRED

ROUTING CONFIDENCE:
High

CONFIDENCE REASON:
Injury confirmed via ER visit with ongoing diagnostic workup. Attorney representation
confirmed as of June 6. Estimated exposure $180,000 — well above $50,000 complex case
threshold. Liability disputed. All required fields present. Three independent complex
case indicators present simultaneously.

SOURCE DOCUMENTS REVIEWED:
- Claim setup summary
- Police report summary
- Attorney representation notice dated June 6

MISSING INFORMATION:
None.

REASON:
Injury is claimed with confirmed ER treatment and ongoing diagnostic workup. Claimant is now represented by an attorney. Estimated exposure is $180,000, well above the $50,000 complex case threshold. Liability is disputed. Three complex unit adjusters are over workload limit; one (David Park) is at workload limit — no confirmed internal capacity. Since internal complex unit is over capacity and the claim is too complex for standard desk handling, route to INDEPENDENT ADJUSTER (IA) ASSIGNMENT. Supervisor approval is required before any IA is assigned given the exposure level, attorney representation, and workload situation. All communications with the claimant must go through counsel as of June 6.

NEXT ACTION:
Request supervisor approval before proceeding. Present three options for supervisor: (1) assign to David Park if urgency justifies the workload exception, (2) authorize an IA assignment for this file, or (3) hold in assignment review queue for next available complex unit slot. Do not contact the claimant directly — all contact must go through Wilson & Kapur, LLC.

DRAFT ROUTING NOTE:
Complex BI claim. Claimant Antonio Bellini, attorney Wilson & Kapur, LLC, Chicago (all contact through counsel as of June 6). Injury: L4-L5 herniated disc, ER June 3, ongoing MRI. Estimated exposure $180,000. Liability disputed, police cites contributing factors. Complex unit over capacity (3 over limit, 1 at limit). Supervisor to approve assignment path — IA authorization or complex unit exception. Do not contact claimant directly.
```

### Decision
COMPLEX / MAJOR CASE AUTO UNIT → INDEPENDENT ADJUSTER (IA) ASSIGNMENT → OVER WORKLOAD LIMIT → SUPERVISOR APPROVAL REQUIRED

### Why This Decision
Injury + attorney representation + estimated exposure $180,000 = complex case. Internal complex unit is over capacity with no confirmed available slot. IA assignment is the appropriate sourcing model when internal complex capacity is unavailable. Supervisor approval is required before any IA is engaged given the exposure level. The over-workload condition raises the governance from DIRECT ASSIGNMENT to SUPERVISOR APPROVAL REQUIRED.

### Result
A complex BI claim with internal over-capacity produces SUPERVISOR APPROVAL REQUIRED with IA sourcing recommended. The routing packet tells the supervisor exactly what decision is needed: approve IA assignment, force-assign to David Park with workload exception, or queue. The operator does not make that call — the supervisor does.

---

## Test Case 3 — SIU Referral with Coverage Flag and Prior Handling Concerns

### Input

```text
CLAIM NUMBER / FILE IDENTIFIER: AZ-2026-037714
DATE OF REFERRAL: June 9, 2026
CARRIER / CLAIMS ORGANIZATION: Southwest Auto Insurance
REFERRING ADJUSTER / HANDLER: Tanya Ruiz

DATE OF LOSS: May 20, 2026
STATE / JURISDICTION: Arizona
LOSS LOCATION: 7200 West Indian School Road, Phoenix, AZ 85033
POLICE REPORT: Yes — Report #26-PPD-88204

CLAIMANT NAME: Ray Esposito (driver), Carla Esposito (passenger)
CLAIMANT ROLE: Third party — two occupants
CLAIMANT CONTACT: On file

INSURED NAME: Maria Galvez
POLICY NUMBER: SAI-2024-001132

INJURY CLAIMED: Yes — both occupants report neck and shoulder pain, treating at same chiropractic clinic
VEHICLE DAMAGE CLAIMED: Yes — $2,400 damage to claimants' vehicle
TOTAL CLAIMED EXPOSURE: $95,000 (combined demand received May 30)

COVERAGE CONFIRMED: Pending — adjuster notes policy shows a 10-day lapse prior to reinstatement on May 18. Date of loss is May 20. Prior adjuster confirmed coverage May 25 without identifying the lapse. Coverage status now in question.
COVERAGE QUESTION: Yes — prior adjuster may have incorrectly confirmed coverage

ATTORNEY REPRESENTED: Yes — both claimants represented by same attorney

PRIOR HANDLING: Yes
  PRIOR ADJUSTER: Robert Chen (internal, now reassigned)
  PRIOR ACTIONS TAKEN: Coverage confirmed (potentially incorrect), initial liability investigation begun
  PRIOR RESULT: Incomplete — Robert Chen reassigned before completing; no formal investigation report
  PRIOR REPORTS AVAILABLE: Partial — contact log only, no investigation report

SPECIAL FLAGS:
[X] SIU indicators present — adjuster notes: two soft-tissue claims from $2,400-damage vehicle, same attorney, demand within 10 days, prior claim by Ray Esposito in 2025

CURRENT HANDLING STATUS: Reopened / transferred
URGENCY: Time-sensitive — prior coverage confirmation may have created a reliance issue; supervisor aware

SOURCE DOCUMENTS REVIEWED:
- Claim setup notes
- Prior adjuster contact log
- Demand letters (2, same attorney)
- Policy lapse documentation
```

### Operator Output

```text
PRIMARY ROUTE:
SIU REFERRAL

SOURCING MODEL:
SUPERVISORY / SIU AUTHORIZATION NEEDED

ASSIGNMENT RESOURCE:
SIU Review Queue — supervisor authorization required before referral

WORKLOAD STATUS:
WORKLOAD UNKNOWN

CAPACITY ACTION:
Supervisor authorization required before SIU referral is submitted. Do not bypass
supervisor review.

GOVERNANCE ACTION:
SUPERVISOR APPROVAL REQUIRED

MODIFIERS / TASK FLAGS:
INJURY CLAIMED / BI
ATTORNEY REPRESENTED
MULTI-VEHICLE / MULTI-PARTY
COVERAGE QUESTION PRESENT
SIU INDICATORS PRESENT
PRIOR HANDLING CONCERNS
PRIOR REPORT MISSING
SUPERVISOR REVIEW REQUIRED

ROUTING CONFIDENCE:
Medium

CONFIDENCE REASON:
Four SIU indicators present and documented. Coverage question and prior handling
concerns are preserved as modifier flags for concurrent supervisor action. Confidence
is Medium because the prior investigation report is missing and coverage determination
is pending — follow-up gaps, not routing blockers.

SOURCE DOCUMENTS REVIEWED:
- Claim setup notes
- Prior adjuster contact log
- Demand letters (2, same attorney)
- Policy lapse documentation

MISSING INFORMATION:
Complete investigation report from prior adjuster Robert Chen is missing — contact log only on file. Coverage determination from prior handling is unresolved.

REASON:
Multiple SIU indicators are present: two soft-tissue claims from a $2,400-damage vehicle, same attorney for both claimants, demand received within 10 days of loss, and Ray Esposito has a prior claim in 2025. SIU REFERRAL is the controlling priority (priority 4). However, a coverage question is also present (priority 3): the prior adjuster may have incorrectly confirmed coverage without identifying a 10-day policy lapse. Both issues must be escalated — COVERAGE / SUPERVISOR REVIEW would normally apply, but SIU takes priority in the hierarchy because SIU indicators require a separate and urgent referral path. The coverage issue is preserved as a modifier flag (COVERAGE QUESTION PRESENT) and must be addressed concurrently by the supervisor. Prior handling concerns are flagged — investigation report is missing, prior coverage confirmation is potentially incorrect.

NEXT ACTION:
Submit SIU referral per carrier protocol with supervisor authorization. Simultaneously, route the coverage question to the coverage unit for a determination on the lapse period and prior coverage confirmation — this must proceed concurrently with SIU intake, not after. Flag MULTIPLE ASSIGNMENTS REQUIRED: (1) SIU referral and (2) coverage determination.

DRAFT ROUTING NOTE:
SIU referral required — takes priority. Two soft-tissue claims from $2,400-damage vehicle, both represented by same attorney, demand within 10 days, Ray Esposito has 2025 prior claim. Supervisor authorization required before SIU transmission.

Concurrent action needed: coverage question. Prior adjuster confirmed coverage May 25 without identifying 10-day lapse prior to May 18 reinstatement. Date of loss is May 20. Coverage determination must be made by coverage unit — do not rely on prior confirmation. File includes policy lapse documentation.

Prior handling concerns: investigation report from Robert Chen is missing (contact log only). Supervisor should obtain complete prior file before SIU and coverage units proceed.
```

### Decision
SIU REFERRAL → SUPERVISORY / SIU AUTHORIZATION NEEDED → WORKLOAD UNKNOWN → SUPERVISOR APPROVAL REQUIRED

### Why This Decision
SIU indicators trigger priority 4, which is above coverage review at priority 3. But the coverage issue does not disappear — it is preserved as COVERAGE QUESTION PRESENT and flagged for concurrent supervisor action. The operator does not defer the coverage issue; it routes the highest-priority gate first and calls out concurrent action explicitly. Prior handling concerns add PRIOR HANDLING CONCERNS and PRIOR REPORT MISSING flags without changing the primary route.

### Result
A claim with both SIU indicators and a coverage question demonstrates correct priority hierarchy: SIU takes the primary route, coverage flags as a concurrent modifier, and the supervisor is told to address both simultaneously. The operator identifies the conflict between prior coverage confirmation and the policy lapse — it does not resolve it, but it names it precisely so the supervisor and coverage unit can act.

---

## Test Summary

| Test | Scenario | Primary Route | Sourcing Model | Governance Action | Routing Confidence | Result |
|---|---|---|---|---|---|---|
| 1 | Clean PD claim, workload confirmed | STANDARD DESK AUTO UNIT | INTERNAL DESK | DIRECT ASSIGNMENT | High | Confirmed |
| 2 | Complex BI, attorney, internal over capacity | COMPLEX / MAJOR CASE AUTO UNIT | INDEPENDENT ADJUSTER (IA) | SUPERVISOR APPROVAL REQUIRED | High | Confirmed |
| 3 | SIU indicators + coverage question + prior handling concerns | SIU REFERRAL | SUPERVISORY / SIU AUTHORIZATION NEEDED | SUPERVISOR APPROVAL REQUIRED | Medium | Confirmed |

Test 1 confirms that a confirmed workload status triggers DIRECT ASSIGNMENT — no hold needed when capacity is known and within target. Test 2 confirms that internal over-capacity on complex claims routes to IA assignment with supervisor approval. Test 3 confirms the priority hierarchy: SIU (priority 4) overrides COVERAGE (priority 3) as the primary route, but coverage is preserved as a concurrent modifier flag with explicit action instructions.
