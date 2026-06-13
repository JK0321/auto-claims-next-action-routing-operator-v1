# Workload and Governance Rules

After selecting the primary route and sourcing model, assess workload and assign a governance action.

Full workload and governance logic is in `rules.md` — Workload and Governance Rules section.

---

## Workload Capacity Statuses

| Status | Meaning |
|---|---|
| WITHIN TARGET WORKLOAD | The targeted handler, unit, or vendor is within normal operating workload. Direct assignment is appropriate. |
| AT WORKLOAD LIMIT | The targeted handler or unit is at maximum capacity. Assignment may proceed with urgency justification, but a hold is the default. |
| OVER WORKLOAD LIMIT | The targeted handler or unit is confirmed over capacity. Direct assignment is not permitted. Route to alternate queue or hold. |
| WORKLOAD UNKNOWN | Workload information was not provided. Cannot confirm capacity. Default to hold in assignment review queue. |

---

## Governance Actions

| Action | Meaning |
|---|---|
| DIRECT ASSIGNMENT | Assign directly to the targeted handler, unit, or vendor. No queue hold or supervisor step needed. |
| ROUTE TO ALTERNATE QUEUE | The primary target is over capacity. Route to the next available handler, unit, or vendor in the same route category. |
| HOLD IN ASSIGNMENT REVIEW QUEUE | Hold the referral in the assignment review queue until a coordinator or supervisor confirms capacity and approves assignment. |
| SUPERVISOR APPROVAL REQUIRED | A supervisor must review and approve the routing before any assignment is executed. This may occur due to exposure level, SIU referral, complex case authorization, or carrier operating rules. |
| RETURN TO REFERRING PARTY | The referral cannot be routed. Return to the submitting party with a specific list of missing or contradictory required fields. No assignment is made. Applicable risk modifier flags are preserved for the next routing cycle. |

---

## Governance Decision Rules

| Workload Status | Governance Action |
|---|---|
| WITHIN TARGET WORKLOAD | DIRECT ASSIGNMENT |
| AT WORKLOAD LIMIT | DIRECT ASSIGNMENT (if urgency or operating rules justify) — otherwise HOLD IN ASSIGNMENT REVIEW QUEUE |
| OVER WORKLOAD LIMIT | ROUTE TO ALTERNATE QUEUE or HOLD IN ASSIGNMENT REVIEW QUEUE |
| WORKLOAD UNKNOWN | HOLD IN ASSIGNMENT REVIEW QUEUE |

---

## Supervisor Approval Required — Additional Triggers

Regardless of workload status, SUPERVISOR APPROVAL REQUIRED applies when:

- Primary route is SIU REFERRAL (always requires supervisor authorization before SIU transmission)
- Primary route is COVERAGE / SUPERVISOR REVIEW and the specific coverage issue requires supervisor sign-off per carrier protocol
- Primary route is COMPLEX / MAJOR CASE AUTO UNIT and the exposure level or complexity requires supervisor authorization before IA or complex unit assignment
- An independent adjuster (IA) assignment is being authorized (IA assignments generally require coordinator or supervisor approval due to cost and scope)
- A vendor assignment requires a purchase order or service authorization approval

**Override rule:** `SUPERVISOR APPROVAL REQUIRED` takes precedence over workload-based governance actions — if any of the above triggers are met, use `SUPERVISOR APPROVAL REQUIRED` regardless of workload status (WITHIN TARGET, AT LIMIT, OVER LIMIT, or UNKNOWN).

---

## Non-Assignment Routes — Governance Rule

When `PRIMARY ROUTE` is `RETURN FOR ADDITIONAL INFORMATION` or `OUT OF SCOPE / MISROUTED`, workload status is irrelevant. The governance action is always `RETURN TO REFERRING PARTY`.

**RETURN FOR ADDITIONAL INFORMATION:**
- The referral may be in scope but required fields are missing or contradictory.
- Do not assign to any handler, unit, or vendor.
- List each missing or contradictory required field by name.
- Preserve any visible risk modifier flags (SIU indicators, injury, attorney, etc.) in the routing packet for the next routing cycle when the referral is resubmitted.
- Do not make a partial routing decision. Do not invent missing facts.

**OUT OF SCOPE / MISROUTED:**
- The referral does not belong in this operator's auto claims next-action routing workflow.
- Do not assign to any handler, unit, or vendor.
- Explain why the referral is outside scope.
- Identify the likely correct intake path or department if available.
- No claim handling action is taken inside this operator.

---

## Field Urgency Override Rule

When all three conditions are met simultaneously:

1. Primary route is FIELD ADJUSTER / FIELD INVESTIGATION
2. Internal field staff are OVER WORKLOAD LIMIT
3. Field evidence is time-sensitive (scene evidence, surveillance footage, physical evidence that may be lost or degraded)

**Action:** Keep FIELD ADJUSTER / FIELD INVESTIGATION as the primary route. Switch the sourcing model to APPROVED FIELD INVESTIGATION VENDOR or TPA / OVERFLOW PARTNER. Use ROUTE TO ALTERNATE QUEUE as the governance action. Add INTERNAL CAPACITY CONSTRAINT and VENDOR ASSIGNMENT REQUIRED as modifier flags.

**Do not hold field work for internal capacity when evidence may be lost.** The HOLD IN ASSIGNMENT REVIEW QUEUE governance action is not appropriate when field evidence urgency is present. Authorize the vendor immediately.

---

## Assignment Review Queue — What It Is and Is Not

The Assignment Review Queue is a governance concept, not a primary route.

- It is a holding state where the referral waits for coordinator or supervisor confirmation of capacity and assignment approval.
- It is not a separate routing decision and does not appear as a primary route.
- A referral in the assignment review queue still has a primary route (e.g., STANDARD DESK AUTO UNIT) and sourcing model (e.g., INTERNAL DESK) — those are already determined. The queue hold means the direct assignment step is pending.

---

## Workload Notes in the Intake Form

If the referring adjuster provides workload information in the intake form (e.g., "Adjuster Maria Chen is at 82% workload per supervisor"), use that as the workload status:
- Under 100% of target → WITHIN TARGET WORKLOAD
- At 100% of target → AT WORKLOAD LIMIT
- Over 100% of target → OVER WORKLOAD LIMIT

If no workload information is provided, use WORKLOAD UNKNOWN and default to HOLD IN ASSIGNMENT REVIEW QUEUE.
