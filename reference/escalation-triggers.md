# Escalation Triggers

This file catalogs conditions that force a routing decision higher in the priority hierarchy. Triggers are grouped by the route they activate.

Full routing logic and hierarchy are in `rules.md`.

---

## Triggers → COVERAGE / SUPERVISOR REVIEW (Priority 3)

Any of these present routes the claim to COVERAGE / SUPERVISOR REVIEW before any other routing decision below priority 3.

**Policy and coverage triggers:**
- Coverage has not been confirmed and claim activity cannot proceed without it
- Policy lapse: accident occurred during a lapse period
- Named driver exclusion may apply to the operator of the vehicle
- Commercial-use exclusion may apply (vehicle used for delivery or rideshare at time of loss)
- Policy has lapsed, expired, or been cancelled before the date of loss
- Late-reported claim where the reporting delay creates coverage implications under the policy
- Conflicting policy information: two different policy numbers, conflicting coverage amounts, or conflicting policy dates

**UM / UIM triggers:**
- UM / UIM claim is open with no coverage determination yet completed
- Underinsured motorist coverage stacking issue is present

**Supervisory triggers:**
- Supervisory authority is required before the claim can be handled or assigned (per carrier rule or claim complexity)
- Reopened claim where the prior coverage determination is now in question
- Prior adjuster confirmed coverage incorrectly — file now requires supervisory review of the prior determination
- Denial or reservation of rights action is being initiated or considered

---

## Triggers → SIU REFERRAL (Priority 4)

Any single indicator from this list routes the claim to SIU REFERRAL before complex, appraisal, field, or standard routing.

**Staging and fraud indicators:**
- Multiple occupants reporting injuries in a low-impact collision (damage inconsistent with claimed injuries)
- Accident type or location is identified as a high-frequency fraud pattern in the carrier's experience
- Claimant, attorney, or treatment provider appears on an SIU watchlist or a prior fraud flag exists in file history
- Identical or nearly identical accident facts are present across multiple unrelated claims
- Prior claim fraud indicator involving the same or related parties

**Injury and treatment indicators:**
- Treatment pattern is inconsistent with the type of accident (extensive soft-tissue treatment from minor contact)
- Multiple unrelated claimants sharing the same treatment provider or same attorney
- Excessive, early, or unusually expensive treatment relative to accident severity
- Demand letter or representation notice received immediately or unusually rapidly after the date of loss

**Vehicle and damage indicators:**
- Vehicle damage location is inconsistent with the accident description
- Total loss or high repair cost claim resulting from a minor reported impact
- VIN or vehicle ownership discrepancy noted in the file

**Identity and documentation indicators:**
- Claimant identity cannot be confirmed or identity inconsistencies are present
- Police report or accident report is suspected to be falsified or altered
- Witness names on the police report share an address with the claimant

**Adjuster or file flag:**
- Referring adjuster or supervisor has flagged the claim for SIU review
- SIU indicators checkbox is marked in the intake form

**Scope note:** SIU REFERRAL routes the claim for investigation. This operator does not decide SIU outcome, does not dismiss the claim, and does not decide coverage. Those are SIU's and coverage's determinations.

---

## Triggers → COMPLEX / MAJOR CASE AUTO UNIT (Priority 5)

Any single indicator from this list routes to COMPLEX / MAJOR CASE AUTO UNIT (unless a higher-priority gate applies first).

- Any injury claim or bodily injury (BI) is present, regardless of severity
- Fatality or catastrophic injury is reported
- Claimant or insured is represented by an attorney
- Commercial vehicle, rideshare, or delivery use vehicle is involved with injury or significant exposure
- Multi-vehicle or multi-party accident with injury and conflicting liability accounts
- Total claimed exposure exceeds $50,000 (or carrier's defined major case threshold)
- UM / UIM claim with confirmed injury after coverage is confirmed
- Reopened BI claim requiring re-evaluation of prior injury determination

---

## Prior Handling Concerns — When They Escalate Routing

Prior handling concerns are assessed separately from primary routing triggers but can redirect the primary route.

| Prior Handling Issue | Routing Effect |
|---|---|
| Prior adjuster confirmed coverage incorrectly | Add COVERAGE QUESTION PRESENT flag; route primary to COVERAGE / SUPERVISOR REVIEW |
| Prior vendor investigation revealed new SIU indicators not flagged at intake | Add SIU INDICATORS PRESENT flag; route primary to SIU REFERRAL |
| Prior report is missing and its absence prevents routing | Route to RETURN FOR ADDITIONAL INFORMATION |
| Prior result was failed or incomplete with no resolution | Add PRIOR HANDLING CONCERNS flag; evaluate whether complex unit or supervisor review is needed |
| Prior findings are disputed by the adjuster or carrier | Add PRIOR FINDINGS DISPUTED flag; evaluate for COVERAGE / SUPERVISOR REVIEW depending on what was disputed |

---

## When Multiple Triggers Are Present

When SIU triggers and coverage triggers are both present:
- SIU REFERRAL (priority 4) takes the primary route
- COVERAGE QUESTION PRESENT is preserved as a modifier flag
- The routing note should instruct the supervisor to address both concurrently

When injury triggers and coverage triggers are both present:
- COVERAGE / SUPERVISOR REVIEW (priority 3) takes the primary route
- INJURY CLAIMED / BI is preserved as a modifier flag
- The routing note should instruct the coverage unit to resolve coverage before BI investigation proceeds

Never attempt to combine two primary routes. The higher-priority gate controls the primary route; lower-priority gates become modifier flags with explicit concurrent-action instructions in the DRAFT ROUTING NOTE.
