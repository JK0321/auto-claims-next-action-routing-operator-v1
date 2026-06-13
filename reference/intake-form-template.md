# Intake Form Template

Copy and complete this form before submitting a referral. Paste the completed form into the chat and ask Claude to run the Auto Claims Next-Action Routing Operator.

All fields marked **[required]** must be present. Routing cannot proceed without them. Leave optional fields blank or enter "N/A" if not applicable.

For source document preparation guidance, see `reference/intake-preprocessing-guide.md`.

---

```text
CLAIM NUMBER / FILE IDENTIFIER: [required]
DATE OF REFERRAL: [required]
CARRIER / CLAIMS ORGANIZATION: [required]
REFERRING ADJUSTER / HANDLER: [required]

DATE OF LOSS: [required]
TIME OF LOSS: (optional)
STATE / JURISDICTION: [required]
LOSS LOCATION: [required — address, intersection, or named location; "somewhere in [state]" is insufficient]
POLICE REPORT: [Yes / No / Unknown — if yes, include report number]

CLAIMANT NAME: [required]
CLAIMANT ROLE: [required — first party (insured) / third party / unknown]
CLAIMANT CONTACT: (optional — phone or last known address)

INSURED NAME: [required]
POLICY NUMBER: [required]

INJURY CLAIMED: [Yes / No / Unknown — if yes, describe type and confirmed treatment]
VEHICLE DAMAGE CLAIMED: [Yes / No / Unknown — if yes, estimate if known]
TOTAL CLAIMED EXPOSURE: (optional — estimated combined BI + PD)

COVERAGE CONFIRMED: [Yes / No / Pending verification]
COVERAGE QUESTION: [Yes / No — if yes, describe the specific coverage issue]
LIABILITY STATUS: [Accepted / Disputed / Undetermined / Unknown]

ATTORNEY REPRESENTED: [Yes / No / Unknown — if yes, identify which party and provide firm name if known]
COMMERCIAL / RIDESHARE / DELIVERY USE: [Yes / No / Unknown]
PRIOR CLAIMS HISTORY: (optional — relevant prior claims involving same parties)

PRIOR HANDLING: [Yes / No]
  (if Yes, complete below:)
  PRIOR ADJUSTER / HANDLER: [name / team]
  PRIOR ACTIONS TAKEN: [describe what was completed]
  PRIOR RESULT: [completed / incomplete / disputed / incorrect / other]
  PRIOR REPORTS AVAILABLE: [Yes / No / Partial — if partial, describe what is missing]

SPECIAL FLAGS:
  [ ] SIU indicators present (describe below)
  [ ] Fatality or catastrophic injury
  [ ] UM / UIM involvement
  [ ] CAT claim
  [ ] Safety / threat concern
  [ ] Language support needed (specify language: _________)
  [ ] Other (describe: _________)

SIU INDICATOR DESCRIPTION: (complete if SIU box is checked above)

CURRENT HANDLING STATUS: [new referral / pending / reopened / transferred / other]
WORKLOAD NOTE: (optional — known workload status of the target handler, unit, or vendor)
URGENCY: [Routine / Time-sensitive / Urgent — if time-sensitive or urgent, explain]

SOURCE DOCUMENTS REVIEWED:
  - [document type / file name or description / brief summary of what it contains]
  - (add a line for each document reviewed before submission)

ADDITIONAL NOTES: (optional — anything relevant not captured above)
```

---

## Field Completion Notes

**DATE OF LOSS** — Use the actual date of the accident. If exact date is unknown, provide the date range.

**LOSS LOCATION** — Be specific. Examples of sufficient: "1200 Maple Street, Phoenix, AZ," "Intersection of Route 9 and Main Street, Freehold, NJ." "Somewhere in Texas" cannot be routed.

**COVERAGE CONFIRMED** — If coverage is not confirmed, the operator may route to COVERAGE / SUPERVISOR REVIEW before any other action. Confirm coverage status before submitting when possible.

**COVERAGE QUESTION** — Describe the specific coverage issue. Examples: "Policy lapsed two days before DOL," "Named driver exclusion may apply," "Rideshare use — coverage gap question."

**INJURY CLAIMED** — Note the type of injury and whether medical treatment has been confirmed, if known. This affects whether the claim routes to COMPLEX / MAJOR CASE AUTO UNIT.

**ATTORNEY REPRESENTED** — If the claimant or insured has retained an attorney, provide the firm name if available. Attorney representation may trigger COMPLEX / MAJOR CASE routing or SUPERVISOR REVIEW.

**PRIOR HANDLING** — If a prior adjuster handled the file or a prior vendor was assigned, complete this section. Prior handling concerns (disputed findings, failed assignments, incorrect determinations) can redirect routing.

**SIU INDICATORS** — If you have flagged this claim for SIU or noticed any indicators (suspicious injury patterns, prior fraud flag, inconsistent damage, same attorney / same provider patterns), check the SIU box and describe. The operator does not decide SIU outcomes — it routes the referral.

**WORKLOAD NOTE** — If you know the workload status of the target adjuster, unit, or vendor, include it. This improves governance action accuracy. If unknown, the operator defaults to WORKLOAD UNKNOWN.

**SOURCE DOCUMENTS REVIEWED** — List every document reviewed before completing this form. One line per document. Examples:
  - Police report summary — Report #26-CPD-100441
  - Claim setup notes from adjuster Karen Lee
  - Prior vendor report — Falcon Investigative Group, February 2026
  - Demand letter — Martinez & Suarez, P.A., dated June 8, 2026
  - Estimate — body shop, $9,800
