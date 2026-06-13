# Output Template

This file contains the full output format for the Auto Claims Next-Action Routing Operator, plus a copy-paste completion and report review section for use after an assignment is closed.

---

## Part 1 — Routing Packet Output

The operator returns a structured Markdown routing packet on every in-scope referral with sufficient information. The packet opens with a header block identifying the claim, followed by eight numbered sections. Key results are called out with bold labels. Tables are used for snapshot-style and structured fields. Modifier flags appear in Section 5 alongside sourcing, governance, and capacity.

---

### Routing Packet Format

---

# Auto Claims Next-Action Routing Packet

**Generated Output Type:** Routing Packet

---

## 1. Claim Snapshot

| Field | Value |
|---|---|
| **Case ID** | [Claim number / file identifier] |
| **Claim Type** | [Auto claim type] |
| **Date of Loss** | [Date] |
| **Loss Location** | [City, State / Jurisdiction] |
| **Insured Name** | [Name] |
| **Claimant Name** | [Name] |
| **Coverage Status** | [Confirmed active / Not confirmed / Coverage question present] |
| **Liability Status** | [Brief descriptor — e.g., Clear rear-end; Disputed; Unknown] |

---

## 2. Loss Summary

[One to two sentences generated from the intake facts. Describe what happened, who the parties are, the primary liability and coverage posture, and the reason this claim is being routed. Do not invent facts. If a required fact is missing, note it is unavailable rather than filling in a likely value.]

---

## 3. Routing Decision

| Field | Value |
|---|---|
| **Primary Route** | [ONE PRIMARY ROUTE IN CAPITAL LETTERS] |
| **Routing Confidence** | [High / Medium / Low] |

[One to two sentences explaining why this confidence level was selected. Reference the specific intake facts that support or limit confidence.]

---

## 4. Decision Hierarchy Applied

[Two to four sentences. Reference the decision step number that applied, the key intake facts that triggered it, and why each higher-priority gate did not apply. Tie each point to a specific intake fact. Do not generalize.]

---

## 5. Sourcing, Governance, Capacity, and Modifier Flags

| Field | Value |
|---|---|
| **Sourcing Model** | [One sourcing model] |
| **Governance Action** | [GOVERNANCE ACTION IN CAPITAL LETTERS] |
| **Assignment Resource** | [Resource ID or resource type — e.g., DESK-AUTO-01 or Internal Desk] |
| **Workload Status** | [Numeric or text-based workload status — e.g., 13/15 — Available] |
| **Capacity Action** | [Direct assignment allowed / Reroute to alternate resource / Hold / Supervisor queue] |
| **Source Documents Reviewed** | [Documents reviewed — or None.] |

**Modifier Flags:**

- [Flag — or: None.]

---

## 6. Missing Information / Constraints

- [Non-blocking gap and whether it is blocking or non-blocking — or: None.]

---

## 7. Next Action

[Specific operational next step. State what must happen first, in what order, and who is responsible for each step if multiple tasks apply.]

---

## 8. Draft Routing Note

**TO:** [Receiving unit — desk adjuster, supervisor, SIU, appraisal unit, field unit, vendor coordinator, or assignment queue]

**RE:** [Claim ID] — [Governance Action summary]

[Short routing note. Include claim ID, primary route, key facts driving the route, outstanding tasks, and any constraints the receiving unit must act on before closing the routing review.]

---

*This routing packet was produced by the Auto Claims Next-Action Routing Operator. It is a routing recommendation only. Real assignment must happen in your carrier, TPA, vendor, or claim-management system.*

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

---

### Completion / Report Review Format

---

## Completion / Report Review

| Field | Value |
|---|---|
| **Claim Number** | [Claim number / file identifier] |
| **Primary Route Assigned** | [Route that was selected at intake] |
| **Assigned To** | [Name / department / vendor name] |
| **Assignment Type** | [Appraisal / field investigation / desk review / SIU referral / complex unit / other] |
| **Date Assigned** | [Date] |
| **Date Completed** | [Date — or Pending] |
| **Report Received** | [Yes / No] |
| **Photos Received** | [Yes / No / N/A] |
| **Statement Received** | [Yes / No / N/A] |
| **Estimate Received** | [Yes / No / N/A] |

**Outstanding Items:**
[None — or list each item that has not been received or completed.]

**Completion Status:**
[Complete / Incomplete / Returned for correction / Requires follow-up]

**Report Review Decision:**
[ACCEPT REPORT / RETURN FOR CORRECTION / REQUEST FOLLOW-UP / ESCALATE REVIEW]

**Review Reason:**
[Short explanation of the review decision — what was acceptable or what was missing.]

**Closeout / Reroute Action:**
[Close assignment / Return to desk adjuster / Route to supervisor / Route to SIU / Assign additional task / Request missing report items]

**Closeout Note:**
[Copy-paste note summarizing what was completed and what should happen next. Include any handoff instructions for the next handler. Format: Assignment closed [date]. [Summary of what was completed and key findings.] [Handoff instruction.]]

---

## Report Review Decision — Reference

| Decision | Meaning |
|---|---|
| **ACCEPT REPORT** | Report is complete, findings are usable, assignment is closed. |
| **RETURN FOR CORRECTION** | Report has errors, missing required items, or factual inconsistencies — return to vendor or adjuster before closing. |
| **REQUEST FOLLOW-UP** | Report is generally acceptable but one or more items require additional follow-up (e.g., missing photo, unsigned statement, incomplete scene documentation). |
| **ESCALATE REVIEW** | Report raises new issues requiring supervisor, SIU, or coverage review before the assignment can be closed. |

**When to escalate after closeout:**

- Use `Route to SIU` if new SIU indicators are identified in the report that were not present at intake.
- Use `Route to supervisor` if the report changes the exposure picture materially, identifies a coverage issue, or reveals that prior handling was incorrect.
- Use `Assign additional task` if the field report identifies a new follow-up need (e.g., a witness named in the scene report who has not yet been interviewed).

---

## Optional Saved Output

To record a routing packet as a Markdown file, use the following filename convention:

`outputs/[claim-id]-routing-packet.md`

The saved file should contain the complete routing packet (Part 1) and, when applicable, the completed Completion / Report Review section (Part 2).

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

---

## Assignment Breakdown

**Primary Owner:** [Unit / desk / queue based on PRIMARY ROUTE]

**Primary Owner Sourcing:** [Sourcing model]

**Supporting Task Assignments:**

| Task Flag | Recommended Unit / Vendor |
|---|---|
| [Task flag] | [Recommended unit / vendor / team] |
| [Task flag] | [Recommended unit / vendor / team] |

**Demo Handler Assignment:** [Only if test roster is provided — otherwise: Not provided.]

**Assignment Note:** [Copy-paste note explaining the recommended assignment breakdown.]

---

For multi-case tracking demos, use `outputs/assignment-ledger-template.md`. When a demo roster is used, set the ledger Status to `Routed — Pending Human Approval` to show the operator has recommended a route and assignment mapping but real assignment must still be approved or executed in the carrier, TPA, vendor, or claim-management system.
