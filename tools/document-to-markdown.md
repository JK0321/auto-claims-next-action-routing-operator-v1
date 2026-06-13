# Document-to-Markdown Intake Utility

## For non-technical users — Browser tool

Open **`intake/intake.html`** in any web browser.
Drag and drop claim files. Click Convert. Copy the output. No installation required.
See `intake/README.md` for step-by-step instructions.

---

## For technical users — Manual process (original)

## Purpose

This utility helps convert or summarize raw claim materials into clean Markdown before using the Auto Claims Next-Action Routing Operator.

Raw claim materials — PDFs, DOCX files, emails, estimates, police reports, prior vendor reports, and claim notes — often arrive in formats that are not structured for routing. This utility provides a consistent process for converting those materials into a structured intake draft compatible with `reference/intake-form-template.md`.

This utility does not route the claim. It prepares the intake. The routing operator makes the next-action decision after the structured intake is ready.

---

## Accepted Source Types

- PDF (text-copyable)
- DOCX / Word document
- TXT file
- Email body
- Claim system notes
- Police report
- Repair estimate
- Photo summary
- Prior vendor report
- Recorded statement summary

---

## What This Utility Does

- Converts readable source content into clean Markdown
- Preserves document names and source order
- Extracts visible claim facts
- Identifies missing fields
- Identifies contradictions or conflicts between documents
- Produces a structured intake draft compatible with `reference/intake-form-template.md`

---

## What This Utility Does Not Do

- Does not perform OCR
- Does not guarantee extraction from scanned images or image-based PDFs
- Does not make coverage decisions
- Does not make liability decisions
- Does not make SIU findings
- Does not route the claim
- Does not invent missing facts

---

## Recommended Process

1. Place or reference raw claim materials.
2. Convert each readable document into Markdown.
3. Name each converted file or source clearly.
4. Extract claim facts into the structured intake form.
5. List source documents reviewed.
6. Flag missing information and contradictions.
7. Send the completed intake form to the routing operator.

---

## Output Format

Use this format after converting and extracting from source materials:

```markdown
# Converted Claim Material Summary

## Source Documents Reviewed

- [document name / type]

## Extracted Claim Facts

### Claim / Referral ID
[provided / not provided]

### Claim Type
[personal auto / commercial auto / unknown]

### Date of Loss
[date / not provided]

### Loss Location
[location / not provided]

### Parties
[insured / claimant / passenger / witness]

### Vehicles
[vehicles / not provided]

### Injury Claimed
[yes / no / unknown]

### Attorney Represented
[yes / no / unknown]

### Liability
[clear / disputed / unknown]

### Coverage Question
[yes / no / unknown]

### Police Report
[available / missing / requested / unknown]

### Damage / Appraisal Information
[summary]

### Field Need
[summary]

### Statement Need
[summary]

### SIU Indicators
[summary]

### Prior Handling
[summary]

### Workload Status
[within target / at workload limit / over workload limit / workload unknown]

### Requested Action
[summary]

## Missing Information

- [missing item — or None.]

## Contradictions / Conflicts

- [conflict found — or None.]

## Structured Intake Draft

[fill the intake form here using reference/intake-form-template.md]
```

---

## Example Instruction To Use

Copy and paste this instruction to start the document preparation process:

```text
Convert the attached or pasted claim materials into Markdown using `tools/document-to-markdown.md`.
Extract visible facts only. Do not invent missing information. Then produce a completed structured
intake draft using `reference/intake-form-template.md`.
```

---

## Full Workflow

```text
Raw claim materials (PDF / DOCX / TXT / email / estimate / police report / notes)
→ convert / summarize to Markdown using this utility
→ extract claim facts into structured intake form
→ run Auto Claims Next-Action Routing Operator
→ produce routing packet
```
