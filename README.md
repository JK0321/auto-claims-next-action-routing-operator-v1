# Auto Claims Next-Action Routing Operator

## Project Overview

The Auto Claims Next-Action Routing Operator is a post-FNOL (after the initial claim is filed and set up) folder-based Claude operator that reviews auto accident claim referrals and produces one primary next-action routing packet.

It routes claims across eight ordered handling paths — Out of Scope / Misrouted, Return for Additional Information, Coverage / Supervisor Review, SIU Referral, Complex / Major Case Auto Unit, Material Damage / Appraisal Unit, Field Adjuster / Field Investigation, and Standard Desk Auto Unit — applied in order and stopping at the first applicable match. The operator also adds sourcing guidance, workload status, governance action, modifier flags, missing information, reasoning, and a draft routing note for claims coordinators and adjusters.

## Workflow Overview

The operator runs in eight stages. During Stage 3, Routing Decision, the operator applies the Decision Hierarchy to select one primary route.

```text
1. Intake Preparation
   |
   v
2. Structured Auto Claim Referral
   |
   v
3. Routing Decision
   |
   +-- Decision Hierarchy
       |
       +-- 1. OUT OF SCOPE / MISROUTED
       +-- 2. RETURN FOR ADDITIONAL INFORMATION
       +-- 3. COVERAGE / SUPERVISOR REVIEW
       +-- 4. SIU REFERRAL
       +-- 5. COMPLEX / MAJOR CASE AUTO UNIT
       +-- 6. MATERIAL DAMAGE / APPRAISAL UNIT
       +-- 7. FIELD ADJUSTER / FIELD INVESTIGATION
       +-- 8. STANDARD DESK AUTO UNIT
   |
   v
4. Routing Confidence
   |
   v
5. Sourcing / Governance
   |
   v
6. Capacity Check
   |
   v
7. Demo Ledger Tracking
   |
   v
8. Completion / Report Review
```

The Decision Hierarchy is applied in priority order and stops at the first applicable match. One primary route is selected per referral — no split decisions, no tied outcomes.

Secondary issues are captured as modifier flags, not competing primary routes. Capacity affects assignment action, not the primary route.


## Purpose

After an auto accident claim is filed and set up, someone has to decide who handles it next, how it should be sourced, and whether it needs review, field work, SIU, appraisal, or missing information. This operator supports that next-action routing decision.

This folder turns Claude into a next-action routing operator for auto accident insurance claims.

The operator reviews one auto claim referral at a time — after FNOL and claim setup have been completed — and recommends one primary next handling path. The output includes sourcing guidance, workload status, governance action, and applicable modifier flags. It makes the routing decision and returns the complete packet. It does not ask the coordinator what to do.

This operator is not a claims adjuster, coverage decision engine, liability calculator, reserve authority, settlement tool, or SIU outcome engine. It supports triage, assignment, and workload-aware routing for claims operations.

Each routing packet includes a routing confidence level — High, Medium, or Low — reflecting how completely the intake facts support the recommended route.

## How To Use

**Quick start:** Add this folder to a Claude Project. Then paste a completed referral and ask Claude to act as the Auto Claims Next-Action Routing Operator.

1. Drop this entire folder into a Claude Project.
2. Prepare the claim referral using `reference/intake-form-template.md`.


   Use `reference/intake-form-template.md` for the full intake format. To test the operator immediately, paste this prefilled referral:

   ```text
   CLAIM NUMBER / FILE IDENTIFIER: AC-README-TEST-001
   DATE OF LOSS: 2026-06-01
   LOSS LOCATION: Fort Collins, CO
   CLAIM TYPE: Personal auto property damage
   INSURED NAME: Michael Turner
   CLAIMANT NAME: Rachel Adams
   COVERAGE CONFIRMED: Yes — active policy confirmed for date of loss
   LIABILITY STATUS: Clear rear-end loss; insured rear-ended claimant at stoplight
   INJURY CLAIMED: No
   ATTORNEY REPRESENTED: No
   POLICE REPORT: Not available
   DAMAGE / APPRAISAL NOTE: Minor rear bumper damage; photos available; estimate not yet received
   FIELD NEED: No field inspection requested
   SIU INDICATORS: None
   WORKLOAD NOTE: Internal desk team within target workload
   REQUESTED ACTION: Route for next handling
   ```

   Expected routing results:

   **Primary Route:** MATERIAL DAMAGE / APPRAISAL UNIT  
   **Sourcing Model:** INTERNAL DESK  
   **Assignment Resource:** DESK-AUTO-01  
   **Workload Status:** 13/15 — Available  
   **Governance Action:** DIRECT ASSIGNMENT  
   **Routing Confidence:** High  
   **Modifiers:** POLICE REPORT MISSING / UNAVAILABLE

   Decision 6 (Material Damage / Appraisal Unit) applies because coverage is confirmed, liability is uncontested, no injury or SIU indicators are present, and the primary remaining work is obtaining the damage estimate. The claim does not reach Decision 8 (Standard Desk Auto Unit) because appraisal coordination is still outstanding. The full output uses the eight-section format defined in `reference/output-template.md`.

3. Paste the completed form into the chat.
4. Ask Claude to run the Auto Claims Next-Action Routing Operator.
5. Claude returns one primary route, one sourcing model, workload status, governance action, applicable modifier flags, and a draft routing note.
6. Use the routing packet to assign, escalate, or queue the claim.

If you are working from unstructured notes, emails, a police report, or a prior vendor report, see `reference/intake-preprocessing-guide.md` before submitting.

Before submitting real or demo claim material, redact intake content according to `reference/pii-redaction-guide.md`.

## Input Format

Prepare claims using `reference/intake-form-template.md`. Required fields: claim number, date of loss, state/jurisdiction, claimant name and role, insured name, policy number, and basic nature of claim. For unstructured source documents (emails, police reports, prior vendor reports), convert to intake form format using `reference/intake-preprocessing-guide.md` before routing.

## Primary Routes

The operator assigns one of these on every in-scope referral:

```text
OUT OF SCOPE / MISROUTED
RETURN FOR ADDITIONAL INFORMATION
COVERAGE / SUPERVISOR REVIEW
SIU REFERRAL
COMPLEX / MAJOR CASE AUTO UNIT
MATERIAL DAMAGE / APPRAISAL UNIT
FIELD ADJUSTER / FIELD INVESTIGATION
STANDARD DESK AUTO UNIT
```

## Routing Quick Reference

This table summarizes representative auto claim routing scenarios. It is not an exhaustive rule matrix. The detailed routing logic remains in `rules.md`.

| Condition | Primary Route | Sourcing Model | Governance Action |
|---|---|---|---|
| Minor vehicle damage, estimate not yet received, clear liability, no injury claimed | Material Damage / Appraisal Unit | Internal Desk | Direct Assignment |
| Minor vehicle damage, estimate received, clear liability, no injury claimed | Standard Desk Auto Unit | Internal Desk | Direct Assignment |
| Liability disputed, no injury claimed, witness or statement follow-up needed | Field Adjuster / Field Investigation | Internal Desk or Field Support | Direct Assignment or Supervisor Review |
| Injury claimed, liability disputed, police report missing | Complex / Major Case Auto Unit | Internal Desk or Approved Vendor | Supervisor Approval Required |
| Coverage status unclear, policy issue, excluded driver, or questionable coverage facts | Coverage / Supervisor Review | Internal Desk | Supervisor Approval Required |
| SIU indicators present, inconsistent facts, suspicious loss details, or damage mismatch | SIU Referral | Supervisory / SIU Authorization Needed | SIU or Supervisor Authorization Required |
| Field inspection, scene documentation, or vehicle/location verification needed | Field Adjuster / Field Investigation | Internal Field or Approved Field Investigation Vendor | Direct Assignment or Route to Alternate Queue |
| Loss facts are too incomplete to determine a route | Return for Additional Information | Internal Desk | Return to Referring Party |
| Claim type is outside auto claim scope | Out of Scope / Misrouted | Not Applicable | Return or Redirect |

## Sourcing Models

After selecting a primary route, the operator assigns one sourcing model — who fulfills the work:

```text
INTERNAL DESK
INTERNAL FIELD
INDEPENDENT ADJUSTER (IA) ASSIGNMENT
APPROVED APPRAISAL VENDOR
APPROVED FIELD INVESTIGATION VENDOR
TPA / OVERFLOW PARTNER
CAT TEAM
SUPERVISORY / SIU AUTHORIZATION NEEDED
```

See `reference/sourcing-model-rules.md` for selection logic and override conditions.

## Workload / Governance Layer

After selecting the sourcing model, the operator assesses workload and assigns a governance action:

**Workload statuses:** WITHIN TARGET WORKLOAD / AT WORKLOAD LIMIT / OVER WORKLOAD LIMIT / WORKLOAD UNKNOWN

**Governance actions:** DIRECT ASSIGNMENT / ROUTE TO ALTERNATE QUEUE / HOLD IN ASSIGNMENT REVIEW QUEUE / SUPERVISOR APPROVAL REQUIRED / RETURN TO REFERRING PARTY

When the demo capacity roster is used, workload status should use the numeric format, such as `13/15 — Available` or `15/15 — At Capacity`. Text-based workload labels may still appear as fallback governance language when no roster data is loaded.

`SUPERVISOR APPROVAL REQUIRED` overrides workload-based governance when a supervisor trigger applies. `RETURN TO REFERRING PARTY` is used when `PRIMARY ROUTE` is `RETURN FOR ADDITIONAL INFORMATION` or `OUT OF SCOPE / MISROUTED` — no assignment is made in either case. See `reference/workload-governance-rules.md` for full logic.

## Required Output Format

The operator returns a structured Markdown routing packet. See `reference/output-template.md` for the full format specification.

Each packet opens with a header block — claim number, date of loss, loss location, claim type, insured and claimant names — followed by eight numbered sections:

| Section | Content |
|---|---|
| **1. Claim Snapshot** | Claim identifiers, coverage status, and liability status |
| **2. Loss Summary** | One to two sentence narrative of the loss |
| **3. Routing Decision** | Primary route, confidence level, and modifier flags |
| **4. Decision Hierarchy Applied** | Which decision step triggered and why |
| **5. Sourcing, Governance, and Capacity** | Sourcing model, governance action, and workload status |
| **6. Missing Information / Constraints** | Non-blocking gaps noted |
| **7. Next Action** | Specific operational next step |
| **8. Draft Routing Note** | Short note to the receiving unit |

Key results appear as bold labels:

- **Primary Route:** — Section 3
- **Routing Confidence:** — Section 3
- **Sourcing Model:** — Section 5
- **Governance Action:** — Section 5
- **Capacity Status:** — Section 5
- **Next Action:** — Section 7

## Example Quick Test

A runnable prefilled test case is included in the `## How To Use` section above.

To test other routes, see `examples.md`.

## Why The Routing Output Is Reliable

- Every routing packet names the specific rule that drove the decision. The eight-step hierarchy is explicit, ordered, and reproducible — the same referral produces the same route every time.
- Missing information is named, not guessed. If a required field is absent, the operator returns the specific missing field rather than routing around the gap.
- The operator does not invent facts, infer coverage, assume liability, or fill in workload status it was not given. Unknown fields remain unknown in the output.
- The operator is explicitly prohibited from returning "there are several options to consider" or "use your judgment here." It routes, or it states exactly why it cannot. The Forbidden Output rule is written into `rules.md`.

## After Routing: What Happens Next

The operator produces a routing packet in the chat output. It does not save, transmit,
assign, track, or close claims automatically.

**Workflow:**

Manual input / copy-paste case file
→ structured intake review by the operator
→ routing packet generated in chat output
→ user or Claude Code saves packet as a Markdown file (optional)
→ human operator or claims system executes the real assignment
→ returned report reviewed using the completion/report review template in
  `reference/output-template.md`

**Reference view:** [`reference/routing-tree.md`](reference/routing-tree.md) shows the full intake-to-review workflow as a visual tree.

**To save a routing packet:**

Ask Claude: "Save this routing output as `outputs/[claim-id]-routing-packet.md`."

**Important:** This operator is not a claim-management system. It produces a routing
recommendation. Real assignment must happen in your carrier, TPA, vendor, or
claim-management system.

Without a roster, the operator recommends units and vendors only, not named handlers. See `reference/output-template.md` — Optional Assignment Breakdown.

If a demo roster is provided, the routing packet can optionally be expanded into a demo assignment breakdown and ledger entry — see `reference/assignment-capacity-roster.md` and `outputs/assignment-ledger-template.md`.

## What This Operator Handles

Post-FNOL auto accident claim routing for:

- Standard auto liability and property damage claims
- Complex, high-exposure, and injury claims
- Claims requiring coverage or supervisory review
- Claims with SIU indicators
- Material damage and appraisal routing
- Field adjuster and field investigation routing
- Workload-aware assignment guidance
- Claims with prior handling concerns

## What This Operator Does Not Handle

- FNOL intake or initial claim setup
- Coverage decisions or determinations
- Liability determinations
- Reserve setting
- Settlement authority
- SIU outcome decisions
- Case management beyond triage and routing
- Non-auto-accident claims (workers' comp, disability, general liability, etc.)

## Limitations

- Does not adjudicate coverage, liability, reserves, settlements, or SIU outcomes — it routes only
- Does not perform OCR or extract facts from attached documents — convert to intake form format first
- Does not handle non-auto-accident claims (workers' comp, disability, general liability, etc.)
- Workload routing depends on workload notes provided in the intake form — if none are provided, defaults to HOLD IN ASSIGNMENT REVIEW QUEUE
- Complex case threshold defaults to $50,000 if no carrier-specific threshold is defined

## Repository Structure

This project is organized as a Markdown-based routing operator. The core workflow can be reviewed and used through the Markdown instruction files without requiring Python.

```text
AutoClaimsNextActionRoutingOperator/
├── README.md                         Project entry point, workflow overview, and usage guide
├── identity.md                       Operator role, scope, limits, workflow behavior, routing outcomes, sourcing models, and modifier flags
├── rules.md                          Canonical routing logic and Decision Hierarchy; source of truth for routing decisions
├── examples.md                       Worked routing examples across the primary route types
├── test-run.md                       Test cases with full routing packet outputs
│
├── reference/
│   ├── intake-form-template.md        Structured input form for claim referrals
│   ├── intake-preprocessing-guide.md  Guidance for preparing unstructured source documents before intake
│   ├── pii-redaction-guide.md         PII review and redaction guidance
│   ├── output-template.md             Canonical output format; source of truth for output fields
│   ├── routing-decision-rubric.md     Quick-reference routing criteria and Decision Hierarchy matrix
│   ├── escalation-triggers.md         Conditions that force SIU, coverage, supervisor, or complex routing
│   ├── assignment-type-definitions.md Definitions for all eight primary routes
│   ├── sourcing-model-rules.md        Sourcing model selection logic and override conditions
│   ├── workload-governance-rules.md   Workload capacity statuses and governance action logic
│   ├── routing-tree.md                Visual tree of the full intake-to-review workflow
│   ├── assignment-capacity-roster.md  Demo roster for workload caps and alternate routing
│   └── demo-assignment-roster.md      Named demo handlers and vendors for assignment breakdown and ledger output
│
├── outputs/
│   ├── assignment-ledger-template.md  Demo ledger tracker for routing packet entries
│   └── AC-DOCX-TEST-2026-021-routing-packet.md
│                                       Saved example routing packet
```
