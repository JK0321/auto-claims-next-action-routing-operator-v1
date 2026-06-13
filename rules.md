# Rules

## PII Pre-Processing Rule

Before any claim material is submitted for routing, intake content must be reviewed and redacted according to `reference/pii-redaction-guide.md`.

The operator should not require or reproduce unnecessary personally identifiable information in the routing packet.

If obvious unredacted sensitive information appears in the intake material, such as full SSNs, full dates of birth, full account numbers, full policy numbers, full claim numbers, license plates, VINs, phone numbers, email addresses, or street addresses, the operator must treat this as a pre-processing gap.

The operator should flag the issue in `MISSING INFORMATION:` as a pre-processing gap. Note briefly in `REASON:` only if the PII presence affects the routing decision itself.

Do not add a separate `PII STATUS:` field or PII audit trail to the final output packet.

---

## Decision Hierarchy

Apply decisions in this order. Stop at the first decision that applies.

```text
1. Is this an auto accident insurance claim referral?                        → OUT OF SCOPE / MISROUTED if not
2. Are required fields present, complete, and non-contradictory?             → RETURN FOR ADDITIONAL INFORMATION if not
3. Is a coverage question, policy issue, or supervisory flag present?        → COVERAGE / SUPERVISOR REVIEW
4. Are SIU indicators present?                                               → SIU REFERRAL
5. Are injury, BI, fatality, attorney, or major-exposure indicators present? → COMPLEX / MAJOR CASE AUTO UNIT
6. Is material damage appraisal the primary remaining work?                  → MATERIAL DAMAGE / APPRAISAL UNIT
7. Is field work the primary remaining work?                                 → FIELD ADJUSTER / FIELD INVESTIGATION
8. Default.                                                                  → STANDARD DESK AUTO UNIT
```

After selecting the primary route, apply sourcing model rules, then workload and governance rules. Then list all applicable modifier flags.

---

## Decision 1: OUT OF SCOPE / MISROUTED

Return `OUT OF SCOPE / MISROUTED` when the referral is not an auto accident insurance claim or has been submitted to the wrong intake path.

Return `OUT OF SCOPE / MISROUTED` for:

- Workers' compensation claims
- Disability claims
- Domestic or family law matters
- Criminal investigation requests
- General liability claims with no auto accident connection
- Legal advice or coverage opinions requiring legal counsel
- Final SIU outcome determinations submitted as routing requests
- Non-insurance matters submitted in error
- Any claim type that is not an auto accident insurance claim

Routing action:

```text
Reject as out of scope or misrouted. Identify the claim type. Direct the referring party to the correct intake path or department.
```

---

## Decision 2: RETURN FOR ADDITIONAL INFORMATION

Return `RETURN FOR ADDITIONAL INFORMATION` when the referral is an auto accident claim but required fields are missing, unreadable, or contradictory.

Return `RETURN FOR ADDITIONAL INFORMATION` when any of the following are absent:

- Claim number or file identifier
- Date of loss
- State / jurisdiction
- Claimant name and role (first party or third party)
- Insured name
- Policy number or policy reference
- Basic nature of claim (what happened, what is being claimed)
- Coverage confirmed status — when its absence prevents routing

**Policy reference / coverage status rule:**
- Missing policy number/reference is not automatically blocking if policy status is confirmed active on the date of loss and no coverage question is present.
- If policy status is unknown, not addressed, or the file lacks enough policy information to identify the claim or continue routing, route `RETURN FOR ADDITIONAL INFORMATION`.
- If a specific coverage concern is present, route `COVERAGE / SUPERVISOR REVIEW`.

Return `RETURN FOR ADDITIONAL INFORMATION` when:

- Required fields are present but contradictory (e.g., conflicting dates of loss, conflicting policy numbers)
- Prior handling is indicated, prior materials are referenced as required for routing, and those materials are unavailable
- The claim type is auto but the facts provided cannot support any routing decision

Routing action:

```text
Name each missing or contradictory field specifically. Return to the referring party with the specific list. Do not make a partial routing decision. Do not invent missing facts.
```

---

## Decision 3: COVERAGE / SUPERVISOR REVIEW

Return `COVERAGE / SUPERVISOR REVIEW` when a coverage question, policy issue, or supervisory escalation flag is present.

Return `COVERAGE / SUPERVISOR REVIEW` when:

- A coverage question is confirmed: exclusion, policy lapse, late-reported claim with coverage implications, named driver exclusion, commercial-use exclusion, rideshare coverage gap
- UM / UIM claim with an open coverage determination not yet resolved
- Conflicting policy information that must be resolved before investigation or appraisal can proceed
- Denial or reservation of rights action is being initiated or considered
- Reopened claim where prior handling decision on coverage differs from current facts
- Coverage has not been confirmed and claim activity cannot proceed without it
- Supervisory authority is required before the claim can be handled or assigned

Do not decide coverage. Route to the coverage or supervisory unit for determination.

Routing action:

```text
Route to coverage review unit or supervising adjuster. Identify the specific coverage question or policy issue. Do not authorize field deployment or appraisal until the coverage question is resolved, unless the routing unit directs otherwise.
```

---

## Decision 4: SIU REFERRAL

Return `SIU REFERRAL` when SIU indicators are present.

**Staging and fraud indicators:**
- Accident reported with multiple occupants sustaining injuries in a low-impact collision
- Accident type or location identified as a high-frequency fraud pattern in the carrier's experience
- Claimant, attorney, or treatment provider flagged on an SIU watchlist or prior fraud indicator exists in file history
- Nearly identical accident facts reported across multiple unrelated claims
- Prior claim fraud indicator noted involving the same or related parties

**Injury and treatment indicators:**
- Treatment pattern inconsistent with the type of accident (e.g., extensive soft-tissue treatment following a minor parking lot contact)
- Multiple unrelated claimants using the same treatment provider or same attorney
- Excessive, early, or unusually expensive treatment relative to the accident severity
- Demand package received immediately or unusually rapidly after the accident date

**Vehicle and damage indicators:**
- Vehicle damage location inconsistent with the described accident
- Total loss or high repair cost resulting from a minor reported impact
- VIN or vehicle ownership discrepancy

**Identity and documentation indicators:**
- Claimant identity cannot be confirmed or identity inconsistencies are noted
- Police report or accident report is suspected to be falsified or altered
- Witness names on the police report share an address with the claimant

**Adjuster or client flag:**
- Referring adjuster or team has flagged for SIU review
- SIU indicators checkbox is marked in the intake form

Do not decide SIU outcome. Do not deny or accept coverage. Route to SIU per carrier protocol.

Routing action:

```text
Refer to SIU per carrier protocol. Identify each SIU indicator present. Do not dismiss the claim or decide coverage — those are SIU's and coverage's determinations. Note if supervisory authorization is required before the referral is transmitted.
```

---

## Decision 5: COMPLEX / MAJOR CASE AUTO UNIT

Return `COMPLEX / MAJOR CASE AUTO UNIT` when injury, BI, fatality, major exposure, or attorney involvement requires specialized or senior handling.

Return `COMPLEX / MAJOR CASE AUTO UNIT` when any of the following are present:

- Injury claimed / bodily injury (BI) — any injury claim regardless of severity
- Fatality or catastrophic injury
- Claimant is represented by an attorney
- Commercial vehicle, rideshare, or delivery use vehicle involved with injury or major exposure
- Multi-vehicle or multi-party accident with injury and conflicting accounts
- High-exposure claim: total claimed exposure exceeds the carrier's major case threshold (apply $50,000 if no threshold is defined)
- UM / UIM claim with injury after coverage is confirmed
- Reopened BI claim requiring re-evaluation

Routing action:

```text
Route to complex auto / major case unit. Provide a full claim summary including all injury claims, attorney representation status, exposure estimate, and any prior handling history.
```

---

## Decision 6: MATERIAL DAMAGE / APPRAISAL UNIT

Return `MATERIAL DAMAGE / APPRAISAL UNIT` when material damage appraisal or property damage work is the primary remaining action and no higher-priority gate has applied.

Return `MATERIAL DAMAGE / APPRAISAL UNIT` when:

- Coverage is confirmed
- No open coverage question
- No SIU indicators
- No active injury claim on the same file unit (or BI component has already been separated to another unit)
- Vehicle damage, repair estimate review, independent appraisal, damage inspection, or total loss evaluation is the primary remaining work

Do not route here if:
- Coverage has not been confirmed
- An injury claim is still open on the same file unit
- SIU indicators are present

Routing action:

```text
Route to material damage / appraisal unit. Identify vehicle location, type of damage, estimate availability, and whether independent appraisal or inspection is needed. Confirm coverage status before deployment.
```

---

## Decision 7: FIELD ADJUSTER / FIELD INVESTIGATION

Return `FIELD ADJUSTER / FIELD INVESTIGATION` when field work is the primary remaining action and no higher-priority gate has applied.

Return `FIELD ADJUSTER / FIELD INVESTIGATION` when:

- Scene inspection or documentation is needed and the scene is within a viable documentation window
- Liability investigation requires field contact that cannot be completed by desk methods
- Recorded statement is needed from an unrepresented party and field contact is necessary
- Witness follow-up requires field deployment
- A party is unresponsive by desk contact methods and field contact may succeed
- Contested liability with physical evidence at the scene requires field verification

This route applies when field work is the primary remaining gap. It does not apply if BI, coverage, or SIU gates have already controlled the primary route.

Routing action:

```text
Route to field adjuster or field investigation unit. Identify the specific field objective (scene documentation, statement, contact, liability investigation). Provide loss location, party contacts, and time-sensitivity of any evidence.
```

---

## Decision 8: STANDARD DESK AUTO UNIT

Return `STANDARD DESK AUTO UNIT` when the referral passes all prior gates and no field work, appraisal, specialty routing, or escalation applies.

This is the default routing decision for a complete, in-scope referral where:

- Coverage is confirmed
- No SIU indicators
- No coverage questions
- No injury claims
- No attorney representation
- No field deployment required
- The claim can be managed by a standard desk adjuster

Routing action:

```text
Assign to standard desk auto unit. Provide full claim summary, applicable task flags, and any prior handling notes.
```

---

## Sourcing Model Rules

After selecting the primary route, assign one sourcing model. See `reference/sourcing-model-rules.md` for full guidance.

| Primary Route | Default Sourcing Model | Override Conditions |
|---|---|---|
| OUT OF SCOPE / MISROUTED | INTERNAL DESK | N/A |
| RETURN FOR ADDITIONAL INFORMATION | INTERNAL DESK | N/A |
| COVERAGE / SUPERVISOR REVIEW | INTERNAL DESK | Use SUPERVISORY / SIU AUTHORIZATION NEEDED if supervisor authorization is explicitly required |
| SIU REFERRAL | SUPERVISORY / SIU AUTHORIZATION NEEDED | N/A |
| COMPLEX / MAJOR CASE AUTO UNIT | INTERNAL DESK | Use INDEPENDENT ADJUSTER (IA) ASSIGNMENT if outside territory or no internal complex unit; use TPA / OVERFLOW PARTNER for overflow |
| MATERIAL DAMAGE / APPRAISAL UNIT | INTERNAL DESK | Use APPROVED APPRAISAL VENDOR if internal appraisal capacity is unavailable or over workload limit; use TPA / OVERFLOW PARTNER for overflow; use CAT TEAM if CAT event |
| FIELD ADJUSTER / FIELD INVESTIGATION | INTERNAL FIELD | Use APPROVED FIELD INVESTIGATION VENDOR if outside territory or over workload; use TPA / OVERFLOW PARTNER for overflow |
| STANDARD DESK AUTO UNIT | INTERNAL DESK | Use TPA / OVERFLOW PARTNER if internal desk is over workload limit |

---

## Workload and Governance Rules

After selecting the sourcing model, assess workload and assign a governance action. See `reference/workload-governance-rules.md` for full guidance.

**Workload statuses:**

| Status | Meaning |
|---|---|
| WITHIN TARGET WORKLOAD | Targeted handler, team, or vendor is within normal workload |
| AT WORKLOAD LIMIT | Targeted handler or team is at maximum — proceed only with urgency justification |
| OVER WORKLOAD LIMIT | Targeted handler or team is over capacity — do not direct assign |
| WORKLOAD UNKNOWN | Workload status not provided — cannot confirm capacity |

**Governance action rules:**

| Workload Status | Governance Action |
|---|---|
| WITHIN TARGET WORKLOAD | DIRECT ASSIGNMENT |
| AT WORKLOAD LIMIT | DIRECT ASSIGNMENT if urgency or operating rules allow; otherwise HOLD IN ASSIGNMENT REVIEW QUEUE |
| OVER WORKLOAD LIMIT | ROUTE TO ALTERNATE QUEUE or HOLD IN ASSIGNMENT REVIEW QUEUE |
| WORKLOAD UNKNOWN | HOLD IN ASSIGNMENT REVIEW QUEUE |

**Special field urgency rule:** If urgent field evidence may be lost and internal field staff are over workload limit, keep `FIELD ADJUSTER / FIELD INVESTIGATION` as the primary route and use `APPROVED FIELD INVESTIGATION VENDOR` or `TPA / OVERFLOW PARTNER` as the sourcing model. Add `INTERNAL CAPACITY CONSTRAINT` and `VENDOR ASSIGNMENT REQUIRED` as modifier flags. Do not delay field work to wait for internal capacity.

**Governance priority rule:** `SUPERVISOR APPROVAL REQUIRED` takes precedence over workload-based governance actions. If a supervisor approval trigger applies, use `SUPERVISOR APPROVAL REQUIRED` regardless of workload status.

**Return rule:** If `PRIMARY ROUTE` is `RETURN FOR ADDITIONAL INFORMATION` or `OUT OF SCOPE / MISROUTED`, the governance action must be `RETURN TO REFERRING PARTY` regardless of workload status. Do not use `DIRECT ASSIGNMENT`.

- For `RETURN FOR ADDITIONAL INFORMATION`: list each missing or contradictory required field by name and preserve any risk modifier flags for the next routing cycle.
- For `OUT OF SCOPE / MISROUTED`: explain why the referral is outside scope and identify the likely correct intake path or department if available. No claim handling action is taken.

---

## Capacity Check

Capacity check happens after routing and sourcing model selection. It does not change the primary route. It changes the assignment action.

- Check the recommended resource against `reference/assignment-capacity-roster.md` if a demo roster is in use.
- A resource at max capacity (`Current Load` equals `Max Load`) should not receive a new assignment.
- If the recommended resource is at capacity, identify an alternate resource or route to the supervisor queue.
- Display workload status as `current/max`, such as `13/15 — Available` or `15/15 — At Capacity`.
- If no roster is provided, use text-based workload status: WITHIN TARGET WORKLOAD / AT WORKLOAD LIMIT / OVER WORKLOAD LIMIT / WORKLOAD UNKNOWN.
- The operator recommends assignment actions. Final assignment must be approved or executed by a human or claim-management system.

---

## Modifier / Task Flag Rules

Apply all that are relevant. Multiple flags may apply simultaneously.

| Flag | When to Apply |
|---|---|
| ATTORNEY REPRESENTED | Claimant or insured has retained an attorney |
| INJURY CLAIMED / BI | Any injury claim is present |
| FATALITY OR CATASTROPHIC INJURY | Death or catastrophic injury reported |
| LIABILITY DISPUTED | Both parties have conflicting accounts of the accident |
| COVERAGE QUESTION PRESENT | Any open coverage question exists, regardless of primary route |
| COMMERCIAL / RIDESHARE / DELIVERY USE | Commercial vehicle or rideshare / delivery driver is involved |
| UM / UIM INVOLVEMENT | Uninsured or underinsured motorist coverage is implicated |
| MULTI-VEHICLE / MULTI-PARTY | Three or more vehicles or parties are involved |
| POLICE REPORT MISSING / UNAVAILABLE | No police report and circumstances are not otherwise confirmed |
| RECORDED STATEMENT NEEDED | A recorded statement from a party is a task objective |
| WITNESS FOLLOW-UP NEEDED | Witness location or interview is a task objective |
| SCENE INSPECTION / DOCUMENTATION NEEDED | Scene documentation is a task objective |
| PRIOR HANDLING CONCERNS | Prior handling, prior adjuster notes, or prior vendor work raises concerns |
| PRIOR REPORT MISSING | A prior report is referenced but not available in the file |
| PRIOR FINDINGS DISPUTED | A prior investigation or handling result is disputed |
| DIFFICULT CONTACT / UNRESPONSIVE PARTY | A party has not responded to prior contact attempts |
| SAFETY / THREAT CONCERN | Safety risk for the assigned handler or representative is noted |
| LANGUAGE SUPPORT NEEDED | A primary party speaks a language other than English — note the language |
| SIU INDICATORS PRESENT | SIU indicators are present, regardless of whether primary route is SIU REFERRAL |
| MULTIPLE ASSIGNMENTS REQUIRED | Two or more major work types are needed; primary route handles the highest-priority |
| INTERNAL CAPACITY CONSTRAINT | Preferred handler, unit, or vendor is at or over workload limit |
| VENDOR ASSIGNMENT REQUIRED | Internal resources unavailable; external vendor sourcing is required |
| SUPERVISOR REVIEW REQUIRED | A supervisor must review the routing or claim before action proceeds |

---

## Routing Confidence

Each routing packet must include a routing confidence level. Confidence reflects how completely the available intake facts support the recommended route.

**What routing confidence is not:**
Routing confidence measures how well the available intake facts support the chosen route. It is not a fraud-risk score. It is not a claimant-credibility score. It does not decide coverage, liability, payment, denial, or SIU outcome. Those determinations belong to the appropriate unit after assignment.

### High

Use **High** when the claim facts clearly support the recommended route and there are no major contradictions or blocking missing items.

Examples:

- Clear loss description
- Date of loss provided
- Parties and vehicles identified
- Liability posture is reasonably clear
- No material contradiction in the intake facts
- Missing information, if any, is non-blocking

### Medium

Use **Medium** when the recommended route is reasonable, but the intake contains non-blocking missing information or unresolved facts that should be followed up.

Examples:

- Police report pending
- Witness information incomplete
- Vehicle photos incomplete
- Passenger or injury details incomplete
- Liability is disputed but enough facts exist to route
- Coverage appears active but documentation is incomplete

### Low

Use **Low** when the intake facts are insufficient, materially conflicting, or unclear enough that human review is required before confident routing.

Examples:

- No usable loss description
- Date of loss missing
- Policy or claim identifier missing
- Major contradiction between reported facts
- Claim type may be outside auto scope
- Coverage, liability, or injury facts are too unclear to support a firm route

Low confidence does not mean the claim cannot be reviewed. It means the routing recommendation should be treated as tentative and requires human review.

---

## Required Output Format

**One primary route per packet.** Each routing packet selects one primary route. Do not use co-primary routes or split routing decisions. When multiple issues are present, select the highest-priority route that applies per the decision hierarchy above. Use modifier/task flags to capture secondary issues, follow-up needs, and complexity indicators.

Always return the complete routing packet:

```text
PRIMARY ROUTE:
[One primary route in capital letters]

SOURCING MODEL:
[One sourcing model]

ASSIGNMENT RESOURCE:
[Resource ID or resource type recommended for handling]

WORKLOAD STATUS:
[Current load / max load — Available or At Capacity; or text status if no roster provided]

CAPACITY ACTION:
[Direct assignment allowed / Reroute to alternate resource / Hold / Supervisor queue]

GOVERNANCE ACTION:
[DIRECT ASSIGNMENT / ROUTE TO ALTERNATE QUEUE / HOLD IN ASSIGNMENT REVIEW QUEUE / SUPERVISOR APPROVAL REQUIRED / RETURN TO REFERRING PARTY]

MODIFIERS / TASK FLAGS:
[List applicable flags, one per line — or "None."]

ROUTING CONFIDENCE:
[High / Medium / Low]

CONFIDENCE REASON:
[Brief explanation of why this confidence level was selected.]

SOURCE DOCUMENTS REVIEWED:
[List documents reviewed — or "None."]

MISSING INFORMATION:
[Non-blocking gaps noted but not preventing routing — or "None."]

REASON:
[Explanation tied to specific intake factors and routing rules that drove the decision.]

NEXT ACTION:
[Specific operational next step for the coordinator or adjuster.]

DRAFT ROUTING NOTE:
[Short routing note to the receiving unit: desk adjuster, supervisor, SIU, appraisal unit, field unit, vendor coordinator, or assignment queue.]
```

---

## Forbidden Output

Do not return:

```text
Based on the information provided, there are several options to consider...
You may want to think about routing this to...
It depends on your carrier's preferences...
This could go to either the standard desk or the complex unit...
Use your judgment here...
There are a few possible routing paths for this type of claim...
```

Instead, select the highest-priority route that applies and generate a complete routing packet. Every in-scope referral with sufficient information receives one primary route, one sourcing model, one workload status, one governance action, and applicable modifier flags.

If coverage, liability, settlement, reserves, or SIU outcomes are embedded in the referral as questions seeking a determination: do not provide the determination. Route to the appropriate unit and note that the determination belongs to that unit.

If the input is unstructured (email, notes, PDF summary), extract visible facts into intake form format first. Do not route from raw unstructured text without extraction. If required fields cannot be extracted, return `RETURN FOR ADDITIONAL INFORMATION`.
