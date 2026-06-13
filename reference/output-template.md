# Output Template

This file contains the full output format for the Auto Claims Next-Action Routing Operator, plus a copy-paste completion and report review section for use after an assignment is closed.

---

## Part 1 — Routing Packet Output

The operator returns a complete routing packet on every in-scope referral with sufficient information.

```text
CASE ID:
[Claim ID, case ID, or demo case identifier]

CLAIM TYPE:
[Auto claim type — e.g., Personal Auto Property Damage]

LOSS SUMMARY:
[One-sentence summary of the loss and key routing posture]

PRIMARY ROUTE:
[One of the 8 primary routes in capital letters]

SOURCING MODEL:
[One sourcing model]

ASSIGNMENT RESOURCE:
[Resource ID or resource type recommended for handling — e.g., DESK-AUTO-01 or Internal Desk]

WORKLOAD STATUS:
[Current load / max load — Available or At Capacity — e.g., 13/15 — Available or 15/15 — At Capacity]

CAPACITY ACTION:
[Direct assignment allowed / Reroute to alternate resource / Hold / Supervisor queue]

GOVERNANCE ACTION:
[DIRECT ASSIGNMENT / ROUTE TO ALTERNATE QUEUE / HOLD IN ASSIGNMENT REVIEW QUEUE / SUPERVISOR APPROVAL REQUIRED / RETURN TO REFERRING PARTY]

MODIFIERS / TASK FLAGS:
[List applicable flags, one per line — or "None."]

ROUTING CONFIDENCE:
High / Medium / Low

CONFIDENCE REASON:
Brief explanation of why this confidence level was selected.

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

## Primary Routes (Reference)

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

## Sourcing Models (Reference)

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

## Governance Actions (Reference)

```text
DIRECT ASSIGNMENT
ROUTE TO ALTERNATE QUEUE
HOLD IN ASSIGNMENT REVIEW QUEUE
SUPERVISOR APPROVAL REQUIRED
RETURN TO REFERRING PARTY
```

---

## Part 2 — Completion / Report Review

Use this section after an assignment is completed and a report, estimate, or statement has been received. Copy and paste the section, complete the fields, and attach to the file or routing record.

This operator does not save cases to a database or department. This section is a copy-paste record only.

```text
---
COMPLETION / REPORT REVIEW

Claim Number:
[Claim number / file identifier]

Primary Route Assigned:
[Route that was selected at intake]

Assigned To:
[Name / department / vendor name]

Assignment Type:
[Appraisal / field investigation / desk review / SIU referral / complex unit / other]

Date Assigned:
[Date]

Date Completed:
[Date — or "Pending"]

Report Received:
[Yes / No]

Photos Received:
[Yes / No / N/A]

Statement Received:
[Yes / No / N/A]

Estimate Received:
[Yes / No / N/A]

Outstanding Items:
[None — or list each item that has not been received or completed]

Completion Status:
[Complete / Incomplete / Returned for correction / Requires follow-up]

Report Review Decision:
[ACCEPT REPORT / RETURN FOR CORRECTION / REQUEST FOLLOW-UP / ESCALATE REVIEW]

Review Reason:
[Short explanation of the review decision — what was acceptable or what was missing]

Closeout / Reroute Action:
[Close assignment / Return to desk adjuster / Route to supervisor / Route to SIU / Assign additional task / Request missing report items]

Closeout Note:
[Copy-paste note summarizing what was completed and what should happen next. Include any handoff instructions for the next handler.]
---
```

---

## Routing Confidence and Completion Review

Low-confidence routing packets should generally receive closer human review and may be more likely to require follow-up, rerouting, escalation, or return for correction. High-confidence packets may still require review if new facts emerge after the initial routing decision.

## Part 2 Usage Notes

**Report Review Decision — what each means:**

- `ACCEPT REPORT` — Report is complete, findings are usable, assignment is closed
- `RETURN FOR CORRECTION` — Report has errors, missing required items, or factual inconsistencies; return to the vendor or adjuster for correction before closing
- `REQUEST FOLLOW-UP` — Report is generally acceptable but one or more items require additional follow-up (e.g., missing photo, unsigned statement, incomplete scene documentation)
- `ESCALATE REVIEW` — Report raises new issues that require supervisor, SIU, or coverage review before the assignment can be closed

**Closeout / Reroute Action — when to escalate:**

Use `Route to SIU` if new SIU indicators are identified in the report that were not present at intake.
Use `Route to supervisor` if the report changes the exposure picture materially, identifies a coverage issue, or reveals that prior handling was incorrect.
Use `Assign additional task` if the field report identifies a new follow-up need (e.g., a witness named in the scene report who has not yet been interviewed).

**Closeout Note format:**

```text
Assignment closed [date]. [Brief summary of what was completed and key findings.]
[Handoff instruction: what happens next with this file — return to adjuster, route to supervisor, close, etc.]
```

---

## Optional Saved Output

To record a routing packet as a Markdown file, use the following filename convention:

`outputs/[claim-id]-routing-packet.md`

The saved file should contain the complete routing packet (Part 1) and, when applicable,
the completed Completion / Report Review section (Part 2).

This operator does not write files automatically. Ask Claude to save the output if needed.

---

## Optional Assignment Breakdown

After the routing packet is produced, the user may optionally request an assignment breakdown showing the primary owner and supporting task assignments. This is not automatic assignment. It is a recommendation for human review.

**Rules:**

1. Primary owner must match the PRIMARY ROUTE.
2. Supporting assignments may be listed for task flags such as RECORDED STATEMENT NEEDED, WITNESS FOLLOW-UP NEEDED, SCENE INSPECTION / DOCUMENTATION NEEDED, or MATERIAL DAMAGE / APPRAISAL.
3. If no demo roster or real assignment roster is provided, use unit-level recommendations only.
4. If a demo roster is provided, label all named assignments as demo/test assignments.
5. Do not assign real claims to real people from the operator alone.
6. Real assignment must happen in the carrier, TPA, vendor, or claim-management system.

**Template:**

```text
PRIMARY OWNER:
[Unit / desk / queue based on PRIMARY ROUTE]

PRIMARY OWNER SOURCING:
[Sourcing model]

SUPPORTING TASK ASSIGNMENTS:
- [Task flag] → [recommended unit / vendor / team]
- [Task flag] → [recommended unit / vendor / team]

DEMO HANDLER ASSIGNMENT:
[Only if test roster is provided — otherwise: Not provided.]

ASSIGNMENT NOTE:
[Copy-paste note explaining the recommended assignment breakdown.]
```

For multi-case tracking demos, use `outputs/assignment-ledger-template.md`. When a demo roster is used, set the ledger Status to `Routed — Pending Human Approval` to show the operator has recommended a route and assignment mapping but real assignment must still be approved or executed in the carrier, TPA, vendor, or claim-management system.
