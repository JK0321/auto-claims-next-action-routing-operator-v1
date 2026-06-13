# Assignment Type Definitions

What each primary route means and what that unit, team, or path does.

---

## STANDARD DESK AUTO UNIT

A standard desk adjuster or desk handling unit assigned to manage routine auto claims from intake through resolution.

**What they do:** Contact parties, manage demand and payment, coordinate with body shops and claimants, handle standard PD and no-injury auto claims from desk.

**When assigned:** Complete, in-scope referral. Coverage confirmed. No injury. No SIU indicators. No coverage question. No attorney. No field deployment needed. The claim can be handled entirely by desk methods.

**This is the default routing decision** for complete referrals with no complexity or specialty needs.

---

## MATERIAL DAMAGE / APPRAISAL UNIT

An appraisal unit or appraiser responsible for vehicle damage evaluation and repair estimate review.

**What they do:** Conduct independent vehicle appraisals, review body shop estimates, determine actual cash value for total loss claims, document vehicle damage condition.

**When assigned:** Coverage is confirmed, no injury claim, no SIU indicators, no coverage question. Vehicle damage appraisal, estimate review, or total loss evaluation is the primary remaining work.

**Sourcing note:** Handled by internal desk (default) when internal appraisal capacity is available. Use APPROVED APPRAISAL VENDOR when internal capacity is unavailable or over workload limit. Use TPA / OVERFLOW PARTNER for overflow. Use CAT TEAM if a CAT event is declared.

---

## FIELD ADJUSTER / FIELD INVESTIGATION

A field adjuster or field investigation unit deployed to handle work that cannot be completed by desk methods.

**What they do:** Scene documentation and photography, liability investigation requiring in-person contact, recorded statements from unrepresented parties, witness location and interview, difficult-contact follow-up where desk contact has failed.

**When assigned:** Field work is the primary remaining action. No higher-priority gate applies. Scene evidence may be time-sensitive.

**Sourcing note:** May be handled by internal field staff, an approved field investigation vendor, or a TPA / overflow partner depending on capacity and territory.

**Task flags that often accompany this route:** SCENE INSPECTION / DOCUMENTATION NEEDED, RECORDED STATEMENT NEEDED, WITNESS FOLLOW-UP NEEDED, DIFFICULT CONTACT / UNRESPONSIVE PARTY.

---

## COMPLEX / MAJOR CASE AUTO UNIT

A specialized unit or senior adjuster assigned to handle complex, high-exposure, or injury-involved auto claims.

**What they do:** Manage bodily injury claims, work with attorneys, coordinate medical documentation and review, handle high-exposure negotiations, manage multi-party liability disputes with injury.

**When assigned:** Any injury claim or BI, attorney representation, fatality or catastrophic injury, or exposure exceeding the carrier's major case threshold.

**Sourcing note:** May be handled by the carrier's internal complex or BI unit, an independent adjuster (IA), or a TPA / overflow partner for overflow.

---

## COVERAGE / SUPERVISOR REVIEW

A supervising adjuster or coverage unit assigned to resolve a coverage question, policy issue, or supervisory escalation.

**What they do:** Review policy terms, confirm or deny coverage applicability, resolve exclusion and lapse issues, determine reservation of rights posture, authorize claim handling after coverage is confirmed.

**When assigned:** Any open coverage question, policy lapse, exclusion issue, incorrect prior coverage determination, or supervisory requirement that must be resolved before claim handling can proceed.

**Sourcing note:** Typically handled internally. SUPERVISORY / SIU AUTHORIZATION NEEDED is the sourcing model when supervisor authorization is required before proceeding.

**This unit does not receive the claim for ongoing handling.** Once coverage is confirmed or denied, the claim is rerouted to the appropriate handling unit.

---

## SIU REFERRAL

The carrier's Special Investigations Unit (SIU) or designated fraud investigation unit.

**What they do:** Investigate fraud indicators, conduct SIU-level interviews and surveillance, coordinate with law enforcement when applicable, make SIU determination recommendations.

**When assigned:** SIU indicators are present as defined in `reference/escalation-triggers.md`.

**Sourcing model:** SUPERVISORY / SIU AUTHORIZATION NEEDED — supervisor authorization is required before the SIU referral is transmitted per standard carrier protocol.

**Scope of this operator's role:** This operator identifies the referral and generates the routing packet. SIU decides whether fraud occurred. Coverage authority decides coverage. This operator does not make those determinations.

---

## RETURN FOR ADDITIONAL INFORMATION

The intake coordinator or referring adjuster who submitted the referral.

**What happens:** The routing packet identifies each missing or contradictory required field by name. The referral is returned to the submitting party with a specific list of what is needed before routing can proceed.

**No claim assignment is made.** The case is held until the missing information is received and the form is resubmitted.

**Governance action:** Always `RETURN TO REFERRING PARTY`. Workload status is not applicable. Any risk modifier flags visible in the referral (SIU indicators, injury, attorney representation, etc.) are preserved in the routing packet for the next routing cycle.

**Common reasons:** Missing date of loss, insufficient loss location, missing policy number, missing claimant role identification, coverage status unknown when routing requires it.

---

## OUT OF SCOPE / MISROUTED

The referral source — the party who submitted a non-auto or incorrectly routed claim.

**What happens:** The routing packet identifies the claim type and confirms it is outside scope. The referring party is directed to the correct intake path for their claim type.

**No claim assignment is made.** No action is taken on the referral.

**Governance action:** Always `RETURN TO REFERRING PARTY`. Workload status is not applicable. The routing packet explains why the referral is outside scope and identifies the likely correct intake path or department.

**Common misroutes:** Workers' compensation claims, disability claims, general liability claims, criminal matters, and non-insurance submissions.
