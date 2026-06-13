# Routing Decision Rubric

Quick-reference matrix of routing criteria, priority order, and prior handling assessment. Apply decisions in priority order — stop at the first match.

Full logic and edge cases are in `rules.md`.

---

## Decision Hierarchy

| Priority | Primary Route | Route When |
|---|---|---|
| 1 | OUT OF SCOPE / MISROUTED | Referral is not an auto accident insurance claim |
| 2 | RETURN FOR ADDITIONAL INFORMATION | A required field is missing, unreadable, or contradictory | 
| 3 | COVERAGE / SUPERVISOR REVIEW | Coverage question, policy issue, or supervisory flag is present |
| 4 | SIU REFERRAL | SIU indicators are present |
| 5 | COMPLEX / MAJOR CASE AUTO UNIT | Injury, BI, fatality, attorney, or major-exposure indicators are present |
| 6 | MATERIAL DAMAGE / APPRAISAL UNIT | Material damage appraisal is the primary remaining work; no higher-priority gate applies |
| 7 | FIELD ADJUSTER / FIELD INVESTIGATION | Field work is the primary remaining work; no higher-priority gate applies |
| 8 | STANDARD DESK AUTO UNIT | Default — complete in-scope referral, no higher-priority conditions met |

---



## Required Fields for Routing to Proceed

All of these must be present before any routing decision beyond RETURN FOR ADDITIONAL INFORMATION is made:

| Field | Minimum Acceptable |
|---|---|
| Claim number / file identifier | Any unique identifier |
| Date of loss | Exact date or confirmed date range |
| State / jurisdiction | State name or abbreviation |
| Loss location | Address, intersection, or specific named location |
| Claimant name | Full name or sufficient identifying information |
| Claimant role | First party or third party |
| Insured name | Required |
| Policy number | Required — see policy reference rule below |
| Basic nature of claim | Type of loss and what is being claimed |
| Coverage confirmed status | When absence prevents routing (especially for appraisal) |

### Policy Reference / Coverage Status Rule

A missing policy number or policy reference is not automatically blocking if the intake confirms that policy status is active on the date of loss and no coverage question is present.

If policy status is unknown, disputed, not addressed, or contradicted by the source documents, route to `RETURN FOR ADDITIONAL INFORMATION` or `COVERAGE / SUPERVISOR REVIEW` depending on the available facts.

Use `RETURN FOR ADDITIONAL INFORMATION` when the file lacks enough policy information to identify the claim or continue routing.

Use `COVERAGE / SUPERVISOR REVIEW` when the intake contains a specific coverage concern, such as possible lapse, excluded driver, permission issue, commercial/rideshare use, garaging discrepancy, UM/UIM issue, or conflicting coverage information.

---

## Complex / Major Case Threshold

Route to COMPLEX / MAJOR CASE AUTO UNIT when any of the following are present (one is sufficient):

| Indicator | Threshold |
|---|---|
| Injury claimed / BI | Any injury claim present |
| Fatality or catastrophic injury | Any report of death or catastrophic harm |
| Attorney represented | Claimant or insured has retained counsel |
| High exposure | Total claimed exposure exceeds $50,000 (or carrier threshold) |
| Commercial / rideshare / delivery use | Commercial vehicle involved with injury or major exposure |
| Multi-party with injury | Three or more parties with conflicting accounts and injury |
| UM / UIM with injury | UM/UIM claim with confirmed injury after coverage confirmed |
| Reopened BI | Prior BI claim requiring re-evaluation |

Unlike the old senior threshold, a single indicator is sufficient for COMPLEX / MAJOR CASE routing when that indicator involves BI, fatality, or attorney representation.

---

## Material Damage Routing Gate

Route to MATERIAL DAMAGE / APPRAISAL UNIT only when all of the following are true:

| Requirement | Status Required |
|---|---|
| Coverage | Confirmed |
| Coverage question | No open coverage questions |
| SIU indicators | None present |
| Injury claim | No active BI on the same file unit |
| Primary work | Vehicle appraisal, estimate review, or total loss evaluation |

If any item above is not met, a higher-priority gate applies.

---

## Prior Handling Assessment

When prior handling is indicated, assess before finalizing the primary route.

| Prior Result | Action |
|---|---|
| Completed — objective met | Continue routing; note in coordinator notes |
| Completed — partially met | Continue routing; add PRIOR HANDLING CONCERNS flag |
| Incomplete — stopped before completion | Continue routing; add PRIOR HANDLING CONCERNS flag |
| Failed — objective not met | Evaluate for COVERAGE / SUPERVISOR REVIEW if exposure is affected; add PRIOR HANDLING CONCERNS flag |
| Disputed — client disagrees with findings | Add PRIOR FINDINGS DISPUTED flag; evaluate for supervisor review |
| Contradictory — findings conflict with current intake | Add PRIOR FINDINGS DISPUTED flag; evaluate for supervisor or SIU review |
| Incorrect determination — e.g., wrong coverage confirmation | Route to COVERAGE / SUPERVISOR REVIEW; add PRIOR HANDLING CONCERNS and SUPERVISOR REVIEW REQUIRED |
| Prior report missing | Add PRIOR REPORT MISSING flag; if routing-critical, route to RETURN FOR ADDITIONAL INFORMATION |

---

## Sourcing Model Quick Reference

| Primary Route | Default Sourcing | Override Condition |
|---|---|---|
| OUT OF SCOPE / MISROUTED | INTERNAL DESK | N/A |
| RETURN FOR ADDITIONAL INFORMATION | INTERNAL DESK | N/A |
| COVERAGE / SUPERVISOR REVIEW | INTERNAL DESK | SUPERVISORY / SIU AUTHORIZATION NEEDED if supervisor auth required |
| SIU REFERRAL | SUPERVISORY / SIU AUTHORIZATION NEEDED | N/A |
| COMPLEX / MAJOR CASE AUTO UNIT | INTERNAL DESK | INDEPENDENT ADJUSTER (IA) if no internal complex capacity; TPA / OVERFLOW PARTNER for overflow |
| MATERIAL DAMAGE / APPRAISAL UNIT | INTERNAL DESK | APPROVED APPRAISAL VENDOR if internal capacity unavailable or over limit; CAT TEAM if CAT; TPA / OVERFLOW for overflow |
| FIELD ADJUSTER / FIELD INVESTIGATION | INTERNAL FIELD | APPROVED FIELD INVESTIGATION VENDOR if over capacity; TPA / OVERFLOW for overflow |
| STANDARD DESK AUTO UNIT | INTERNAL DESK | TPA / OVERFLOW PARTNER if internal desk over capacity |

---

## Governance Action Quick Reference

| Workload Status | Governance Action |
|---|---|
| WITHIN TARGET WORKLOAD | DIRECT ASSIGNMENT |
| AT WORKLOAD LIMIT | DIRECT ASSIGNMENT (with urgency justification) or HOLD IN ASSIGNMENT REVIEW QUEUE |
| OVER WORKLOAD LIMIT | ROUTE TO ALTERNATE QUEUE or HOLD IN ASSIGNMENT REVIEW QUEUE |
| WORKLOAD UNKNOWN | HOLD IN ASSIGNMENT REVIEW QUEUE |

Special: Field urgency override — if urgent evidence may be lost and internal field is over capacity, keep FIELD ADJUSTER / FIELD INVESTIGATION as primary route, switch to vendor sourcing, and use ROUTE TO ALTERNATE QUEUE.

Special: RETURN FOR ADDITIONAL INFORMATION — governance action is always `RETURN TO REFERRING PARTY` regardless of workload status. List all missing or contradictory required fields. Preserve risk modifier flags for the next routing cycle.

Special: OUT OF SCOPE / MISROUTED — governance action is always `RETURN TO REFERRING PARTY` regardless of workload status. Explain why the referral is outside scope and identify the correct intake path if available. No claim handling action is taken.

Special: SUPERVISOR APPROVAL REQUIRED overrides workload-based governance when a supervisor trigger applies.

**Capacity roster format:** When `reference/assignment-capacity-roster.md` is active, workload status displays numerically — e.g., `13/15 — Available` or `15/15 — At Capacity`. The governance actions above apply to both text-based and numeric formats.

---

## Capacity Check Quick Reference

After sourcing model selection, check the recommended resource against `reference/assignment-capacity-roster.md`. A resource at max capacity (`Current Load` equals `Max Load`) should not receive a new assignment. If capped, identify an alternate resource or route to the supervisor queue. Capacity check does not change the primary route — it changes the assignment action.

| Resource Status | Assignment Action |
|---|---|
| Below max capacity (e.g., 13/15) | Direct assignment allowed |
| At max capacity (e.g., 15/15) | Do not assign — reroute to alternate resource or supervisor queue |

---

## Routing Confidence Quick Reference

| Level | When to Use |
|---|---|
| High | All required facts clearly support the route; no material contradictions; missing info, if any, is non-blocking |
| Medium | Route is reasonable but intake contains non-blocking missing information or unresolved facts requiring follow-up |
| Low | Facts are insufficient, materially conflicting, or unclear; routing recommendation should be treated as tentative; human review required |

Routing confidence is not a fraud-risk score, a claimant-credibility score, or a determination of coverage, liability, payment, denial, or SIU outcome. See `rules.md` — `## Routing Confidence` for full definition and examples.

---

## Modifier / Task Flag Quick Reference

| Flag | Trigger |
|---|---|
| ATTORNEY REPRESENTED | Any party has retained counsel |
| INJURY CLAIMED / BI | Injury or BI present |
| FATALITY OR CATASTROPHIC INJURY | Death or catastrophic harm reported |
| LIABILITY DISPUTED | Conflicting party accounts |
| COVERAGE QUESTION PRESENT | Any open coverage issue, regardless of route |
| COMMERCIAL / RIDESHARE / DELIVERY USE | Commercial or gig-economy vehicle involved |
| UM / UIM INVOLVEMENT | Uninsured or underinsured motorist coverage implicated |
| MULTI-VEHICLE / MULTI-PARTY | 3+ vehicles or parties involved |
| POLICE REPORT MISSING / UNAVAILABLE | No police report, circumstances unconfirmed |
| RECORDED STATEMENT NEEDED | Statement from a party is a task objective |
| WITNESS FOLLOW-UP NEEDED | Witness locate or interview is a task objective |
| SCENE INSPECTION / DOCUMENTATION NEEDED | Scene work is a task objective |
| PRIOR HANDLING CONCERNS | Prior handling issues flagged |
| PRIOR REPORT MISSING | Prior report referenced but unavailable |
| PRIOR FINDINGS DISPUTED | Prior result disputed or contradictory |
| DIFFICULT CONTACT / UNRESPONSIVE PARTY | Prior contact attempts failed |
| SAFETY / THREAT CONCERN | Safety risk noted for assigned handler |
| LANGUAGE SUPPORT NEEDED | Primary party needs non-English language support |
| SIU INDICATORS PRESENT | SIU indicators present regardless of primary route |
| MULTIPLE ASSIGNMENTS REQUIRED | Two or more major work types simultaneously needed |
| INTERNAL CAPACITY CONSTRAINT | Target handler/team/vendor over workload |
| VENDOR ASSIGNMENT REQUIRED | Internal resources unavailable |
| SUPERVISOR REVIEW REQUIRED | Supervisor review required before action |
