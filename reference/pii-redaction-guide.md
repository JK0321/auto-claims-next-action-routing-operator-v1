# PII Redaction Guide

## Purpose

This guide defines what personally identifiable information should be removed or replaced before claim intake content is reviewed by the Auto Claims Next-Action Routing Operator.

The purpose is to preserve claim-handling facts while reducing unnecessary exposure of personal, policy, vehicle, and contact information.

This guide supports the intake workflow. It does not create a separate security system.

## When To Use This Guide

Use this guide before submitting claim intake content into the operator, especially when the source material comes from:

* Claim PDFs
* DOCX claim notes
* Police report excerpts
* Email referrals
* Adjuster notes
* Vendor notes
* Recorded statement summaries
* Intake forms

## Redaction Principle

The operator needs claim facts, not personal identity.

Keep information that helps determine routing, complexity, escalation triggers, missing information, and next handling steps.

Remove or replace information that identifies a person, policy, vehicle, address, or private contact detail when that information is not required for routing.

## Fields To Redact

| Data Type                              | Replace With             |
| -------------------------------------- | ------------------------ |
| Claimant name                          | [CLAIMANT]               |
| Insured name                           | [INSURED]                |
| Driver name                            | [DRIVER]                 |
| Witness name                           | [WITNESS]                |
| Phone number                           | [PHONE REDACTED]         |
| Email address                          | [EMAIL REDACTED]         |
| Home address                           | [ADDRESS REDACTED]       |
| Claim number                           | [CLAIM NUMBER REDACTED]  |
| Policy number                          | [POLICY NUMBER REDACTED] |
| Driver’s license number                | [LICENSE REDACTED]       |
| License plate number                   | [PLATE REDACTED]         |
| VIN                                    | [VIN REDACTED]           |
| Social Security number                 | [SSN REDACTED]           |
| Date of birth                          | [DOB REDACTED]           |
| Medical provider name, when not needed | [PROVIDER REDACTED]      |

## Information That Should Usually Stay

The following information should usually remain because it helps the operator recommend the correct next action:

* Loss type
* Accident facts
* Date of loss, if relevant to handling
* Injury claimed or not claimed
* Liability disputed or accepted
* Police report available or unavailable
* Vehicle damage severity
* Coverage concern indicators
* Prior vendor involvement
* Missing documents
* Witness existence
* Recorded statement needed
* Scene inspection needed
* SIU referral indicators
* Supervisor or coverage escalation triggers

## Example

### Before Redaction

John Smith reported that he was rear-ended by Mary Jones at 123 Main Street. His claim number is AC-123456, policy number is POL-99881, and his phone number is 555-123-4567. He states that the other driver changed lanes suddenly and that he now has neck pain. No police report has been received.

### After Redaction

[CLAIMANT] reported that he was rear-ended by [DRIVER] at [ADDRESS REDACTED]. His claim number is [CLAIM NUMBER REDACTED], policy number is [POLICY NUMBER REDACTED], and his phone number is [PHONE REDACTED]. He states that the other driver changed lanes suddenly and that he now has neck pain. No police report has been received.

## Operator Use

After redaction, the remaining claim facts may be used by the Auto Claims Next-Action Routing Operator to identify:

* Primary route
* Sourcing model
* Workload status
* Governance action
* Modifiers and task flags
* Missing information
* Recommended next handling step

## Boundary

This guide does not replace company privacy rules, claim system controls, legal requirements, or supervisor judgment.

It is a workflow reference for preparing claim intake content before AI-assisted routing review.
