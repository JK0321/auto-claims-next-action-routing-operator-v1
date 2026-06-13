# Intake Preprocessing Guide

This guide explains how to prepare source materials before submitting a referral to the Auto Claims Next-Action Routing Operator.

---

## What This Operator Is and Is Not

This operator is a routing decision tool, not a file converter or OCR engine.

It can:
- Review structured intake forms
- Extract facts from pasted text (emails, notes, summaries)
- Route claims based on extracted intake factors

It cannot:
- Convert PDF or DOCX files into text
- Perform OCR on scanned documents or images
- Read file attachments
- Access external systems, claim databases, or document management platforms

Before submitting a referral, source materials must be converted into text and summarized into the intake form. This is the submitter's responsibility.

---

## Acceptable Source Materials

The following materials can be used to prepare a referral. Paste the text content directly or summarize into the intake form.

| Source Type | How to Prepare |
|---|---|
| Claim system notes or adjuster summary | Copy and paste, or extract key facts into the intake form |
| Email body from adjuster or claimant | Paste text or summarize into intake form fields |
| Police report (text copy or summary) | Extract: date, location, parties, officer findings, injuries noted, report number |
| Body shop estimate (text copy) | Extract: vehicle description, damage estimate amount, repair items |
| Prior vendor report (text copy or summary) | Extract: what was done, result, any flags or concerns |
| Recorded statement summary | Extract: party's account of accident, injuries claimed, prior claims noted |
| Demand letter (text copy or summary) | Extract: attorney name, demand amount, claimed injuries, treatment providers |
| Medical records summary | Extract: treatment type, treatment provider, date of first treatment, injury description |
| Word / DOCX document | Open the document, copy the text, paste into the chat or summarize into the intake form |
| PDF document | Open the PDF, copy the text if copyable, or manually summarize key fields into the intake form |

---

## Source Document Review — What to Note

Before completing the intake form, review each source document and note what it contains. Record this in the SOURCE DOCUMENTS REVIEWED field of the intake form.

Format for each entry:
```text
- [Document type] — [File name or identifier] — [Brief note on what it contains or what it affected in the routing decision]
```

Examples:
```text
- Police report summary — Report #26-CPD-100441 — confirmed date/location, identified two parties, no injury noted
- Claim setup notes — adjuster Karen Lee — coverage confirmed, insured accepted liability
- Prior vendor report — Falcon Investigative Group, Feb 2026 — surveillance failed, subject potentially burned
- Demand letter — Martinez & Suarez, P.A., June 8, 2026 — $85,000 demand, cervical injury, attorney representation confirmed
- Estimate — Ochoa's Auto Body — $9,800 repair estimate, vehicle at shop
```

---

## Conversion Rule: Structured Intake First

The preferred submission method is always the completed intake form from `reference/intake-form-template.md`.

If you paste unstructured notes or documents instead:
1. The operator will first extract visible facts into the intake form structure.
2. After extraction, the operator will route based on the extracted facts.
3. If required fields cannot be extracted from the unstructured input, the operator will return RETURN FOR ADDITIONAL INFORMATION and name the missing fields.

This two-step extraction + routing approach may result in a longer output. If routing speed matters, complete the intake form before submitting.

---

## No Invented Facts Rule

The operator must not invent missing facts.

If a field is not present in the source materials, the operator leaves it blank or marks it as unknown — it does not fill in a likely value, make assumptions about coverage, infer dates, or guess at liability status.

If the absence of a required field prevents routing, the operator routes to RETURN FOR ADDITIONAL INFORMATION and names the specific missing field.

The submitter is responsible for obtaining missing information from the client, adjuster, or system before resubmitting.

---

## Common Preprocessing Errors

**Submitting "investigate" as the client objective with no supporting context.**
Result: RETURN FOR ADDITIONAL INFORMATION. "Investigate" alone is not a routing signal. Specify the objective: liability investigation, appraisal, statement, scene documentation, etc.

**Submitting a state name as the loss location.**
Result: RETURN FOR ADDITIONAL INFORMATION. "Somewhere in Texas" cannot direct a field representative or confirm scene viability. Provide an address, intersection, or specific named location.

**Submitting claim notes that reference prior handling without including the prior result.**
Result: Prior handling concerns flag, possible RETURN FOR ADDITIONAL INFORMATION if prior result is routing-critical. Always note whether prior work was completed, incomplete, failed, or disputed.

**Submitting a demand letter or estimate without identifying coverage status.**
Result: Possible COVERAGE / SUPERVISOR REVIEW routing or RETURN FOR ADDITIONAL INFORMATION. Coverage confirmed status is required for appraisal and complex unit routing. Confirm coverage before submitting if possible.

**Pasting an image or referencing an attached file.**
Result: The operator cannot read image files or attachments. Paste the text content or provide a manual summary.

---

## When to Use the Operator

Submit to the operator after:
- FNOL has been completed
- Claim has been set up in the system
- At least a basic coverage review has occurred (coverage confirmed or coverage question identified)
- Available source documents have been reviewed and summarized

Do not submit:
- At FNOL before claim setup
- Before coverage status has been assessed
- Without at least the required intake form fields completed
