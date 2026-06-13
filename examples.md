# Examples

> Note: Examples 1, 6, and 10 show the current full routing packet format, including assignment resource, workload status, capacity action, routing confidence, and confidence reason. The remaining examples are base routing examples focused on route logic.

These examples demonstrate the operator's routing logic across all eight primary routes. Each input uses the intake form format.

---

## Example 1 — STANDARD DESK AUTO UNIT

### Input

```text
CLAIM NUMBER / FILE IDENTIFIER: OH-2026-041182
DATE OF REFERRAL: June 9, 2026
CARRIER / CLAIMS ORGANIZATION: Midwest Mutual Insurance
REFERRING ADJUSTER / HANDLER: Dana Okafor

DATE OF LOSS: June 2, 2026
STATE / JURISDICTION: Ohio
LOSS LOCATION: 4400 Clime Road, Columbus, OH 43228
POLICE REPORT: Yes — Report #26-CPD-100441

CLAIMANT NAME: Patricia Holt
CLAIMANT ROLE: Third party
CLAIMANT CONTACT: (614) 882-3310

INSURED NAME: Victor Slade
POLICY NUMBER: MWM-2024-88741

INJURY CLAIMED: No
VEHICLE DAMAGE CLAIMED: Yes — third-party estimate $4,200
TOTAL CLAIMED EXPOSURE: $4,200

COVERAGE CONFIRMED: Yes
COVERAGE QUESTION: No
LIABILITY STATUS: Accepted — insured has accepted liability

ATTORNEY REPRESENTED: No
COMMERCIAL / RIDESHARE / DELIVERY USE: No
PRIOR CLAIMS HISTORY: None noted

PRIOR HANDLING: No

SPECIAL FLAGS: None

CURRENT HANDLING STATUS: New referral
URGENCY: Routine
WORKLOAD NOTE: Desk adjuster Dana Okafor confirmed within target workload per supervisor.

SOURCE DOCUMENTS REVIEWED:
- Claim setup summary from adjuster notes
```

### Output

```text
PRIMARY ROUTE:
STANDARD DESK AUTO UNIT

SOURCING MODEL:
INTERNAL DESK

ASSIGNMENT RESOURCE:
DESK-AUTO-01 — Internal Desk / Standard Auto Desk Handling

WORKLOAD STATUS:
13/15 — Available

CAPACITY ACTION:
Direct assignment allowed.

GOVERNANCE ACTION:
DIRECT ASSIGNMENT

MODIFIERS / TASK FLAGS:
None.

ROUTING CONFIDENCE:
High

CONFIDENCE REASON:
All required fields present. Coverage confirmed, liability accepted, no injury, no SIU
concerns, no coverage question. Assigned resource (DESK-AUTO-01) is within capacity at
13/15. No blocking gaps.

SOURCE DOCUMENTS REVIEWED:
- Claim setup summary from adjuster notes

MISSING INFORMATION:
None.

REASON:
Coverage is confirmed, liability is accepted, no injury is claimed, no SIU indicators, no attorney representation, no field work needed, no coverage questions. Third-party PD claim at $4,200 with all required fields present. No higher-priority gate applies. Desk adjuster Dana Okafor is confirmed within target workload — direct assignment is appropriate. No queue hold or supervisor step needed.

NEXT ACTION:
Directly assign to desk adjuster Dana Okafor (DESK-AUTO-01). No queue hold or supervisor step needed.

DRAFT ROUTING NOTE:
New PD-only claim. Third-party claimant Patricia Holt, (614) 882-3310. Liability accepted by insured Victor Slade. Damage estimate $4,200. Police report on file #26-CPD-100441. Coverage confirmed. Assigned directly to Dana Okafor — within target workload, routine handling.
```

---

## Example 2 — MATERIAL DAMAGE / APPRAISAL UNIT (Vendor Sourcing)

### Input

```text
CLAIM NUMBER / FILE IDENTIFIER: TX-2026-088331
DATE OF REFERRAL: June 9, 2026
CARRIER / CLAIMS ORGANIZATION: Lone Star Casualty
REFERRING ADJUSTER / HANDLER: Marcus Webb

DATE OF LOSS: June 5, 2026
STATE / JURISDICTION: Texas
LOSS LOCATION: 8900 Westheimer Road, Houston, TX 77063
POLICE REPORT: Yes — Report #26-HPD-441029

CLAIMANT NAME: Theresa Nguyen
CLAIMANT ROLE: First party (insured)
CLAIMANT CONTACT: (713) 554-8821

INSURED NAME: Theresa Nguyen
POLICY NUMBER: LSC-2025-331002

INJURY CLAIMED: No
VEHICLE DAMAGE CLAIMED: Yes — insured's vehicle, damage estimate $9,800
TOTAL CLAIMED EXPOSURE: $9,800

COVERAGE CONFIRMED: Yes
COVERAGE QUESTION: No
LIABILITY STATUS: Undetermined — third party is unknown (hit-and-run)

ATTORNEY REPRESENTED: No
COMMERCIAL / RIDESHARE / DELIVERY USE: No
PRIOR CLAIMS HISTORY: None

PRIOR HANDLING: No

SPECIAL FLAGS: None

CURRENT HANDLING STATUS: New referral
URGENCY: Routine

ADDITIONAL NOTES: Internal appraisal staff in Houston at capacity this week. Adjuster requesting vendor appraisal authorization.

SOURCE DOCUMENTS REVIEWED:
- Claim setup notes
- Police report summary (hit-and-run, unknown third party)
```

### Output

```text
PRIMARY ROUTE:
MATERIAL DAMAGE / APPRAISAL UNIT

SOURCING MODEL:
APPROVED APPRAISAL VENDOR

WORKLOAD STATUS:
OVER WORKLOAD LIMIT

GOVERNANCE ACTION:
ROUTE TO ALTERNATE QUEUE

MODIFIERS / TASK FLAGS:
POLICE REPORT MISSING / UNAVAILABLE — note: police report exists but third-party vehicle is unknown; liability determination is pending

SOURCE DOCUMENTS REVIEWED:
- Claim setup notes
- Police report summary (hit-and-run, unknown third party)

MISSING INFORMATION:
None blocking routing.

REASON:
Coverage is confirmed, no injury is claimed, no SIU indicators, no attorney, no coverage dispute. PD-only claim with damage estimate of $9,800. Vehicle appraisal is the primary remaining work. Internal appraisal staff are confirmed at capacity; vendor appraisal is appropriate. Governance action is ROUTE TO ALTERNATE QUEUE since internal capacity is over limit — route to approved appraisal vendor queue rather than direct-assigning to over-capacity internal staff.

NEXT ACTION:
Route to approved appraisal vendor queue. Authorize vendor appraisal. Provide vehicle location, contact for insured Theresa Nguyen (713) 554-8821, and damage estimate for reference.

DRAFT ROUTING NOTE:
PD-only claim, first-party insured. Insured's vehicle, hit-and-run, third party unknown. Damage estimate $9,800. Coverage confirmed. Internal appraisal over capacity this week — authorize approved vendor appraisal. Insured contact: Theresa Nguyen, (713) 554-8821. Police report on file #26-HPD-441029.
```

---

## Example 3 — FIELD ADJUSTER / FIELD INVESTIGATION

### Input

```text
CLAIM NUMBER / FILE IDENTIFIER: GA-2026-019930
DATE OF REFERRAL: June 9, 2026
CARRIER / CLAIMS ORGANIZATION: Peach State Insurance
REFERRING ADJUSTER / HANDLER: Sarah Kimball

DATE OF LOSS: June 4, 2026
STATE / JURISDICTION: Georgia
LOSS LOCATION: Intersection of Peachtree Road NE and Lenox Road NE, Atlanta, GA 30326
POLICE REPORT: No — accident self-reported, officer not called

CLAIMANT NAME: Daniel Frost
CLAIMANT ROLE: Third party
CLAIMANT CONTACT: (404) 721-6645

INSURED NAME: Alicia Marchetti
POLICY NUMBER: PSI-2025-091203

INJURY CLAIMED: No
VEHICLE DAMAGE CLAIMED: Yes — claimant estimate $6,100, insured disputes $3,500
TOTAL CLAIMED EXPOSURE: $6,100 (disputed)

COVERAGE CONFIRMED: Yes
COVERAGE QUESTION: No
LIABILITY STATUS: Disputed — insured states claimant ran red light; claimant states insured ran red light. No police report, no witnesses identified at scene.

ATTORNEY REPRESENTED: No
COMMERCIAL / RIDESHARE / DELIVERY USE: No
PRIOR CLAIMS HISTORY: None

PRIOR HANDLING: No

SPECIAL FLAGS: None

CURRENT HANDLING STATUS: New referral
URGENCY: Time-sensitive — accident was 5 days ago; traffic signal evidence at the intersection may still be retrievable
WORKLOAD NOTE: Internal field adjuster Robert Park in Atlanta metro confirmed within target workload per team coordinator.

SOURCE DOCUMENTS REVIEWED:
- Claim setup notes
- Insured's recorded account (provided by adjuster)
```

### Output

```text
PRIMARY ROUTE:
FIELD ADJUSTER / FIELD INVESTIGATION

SOURCING MODEL:
INTERNAL FIELD

WORKLOAD STATUS:
WITHIN TARGET WORKLOAD

GOVERNANCE ACTION:
DIRECT ASSIGNMENT

MODIFIERS / TASK FLAGS:
LIABILITY DISPUTED
POLICE REPORT MISSING / UNAVAILABLE
SCENE INSPECTION / DOCUMENTATION NEEDED
WITNESS FOLLOW-UP NEEDED

SOURCE DOCUMENTS REVIEWED:
- Claim setup notes
- Insured's recorded account (provided by adjuster)

MISSING INFORMATION:
No police report available. Witness identification not yet completed.

REASON:
Liability is disputed with conflicting accounts and no police report to resolve the conflict. No injury claimed, coverage confirmed, no SIU indicators, no attorney, no coverage question. Field work is the primary remaining gap: scene documentation at the intersection may yield traffic signal data, sight-line evidence, or surveillance footage. Internal field adjuster Robert Park is confirmed within target workload — direct assignment is appropriate. The accident is 5 days old and scene evidence is time-sensitive; do not queue.

NEXT ACTION:
Directly assign to field adjuster Robert Park. Treat as urgent. Objective: document intersection at Peachtree Road NE and Lenox Road NE, Atlanta — document signal timing, sight lines, any surveillance camera locations. Scene is 5 days old; act immediately.

DRAFT ROUTING NOTE:
Disputed liability, no police report, no witnesses. Intersection of Peachtree Road NE and Lenox Road NE, Atlanta — accident June 4. Scene is 5 days old — time-sensitive. Directly assigned to Robert Park (within target workload). Priority: document intersection, identify traffic signal or surveillance data, canvass for witnesses. Contact: claimant Daniel Frost (404) 721-6645, insured Alicia Marchetti on file.
```

---

## Example 4 — COMPLEX / MAJOR CASE AUTO UNIT

### Input

```text
CLAIM NUMBER / FILE IDENTIFIER: FL-2026-072214
DATE OF REFERRAL: June 9, 2026
CARRIER / CLAIMS ORGANIZATION: Sunshine State P&C
REFERRING ADJUSTER / HANDLER: Kevin Morales

DATE OF LOSS: June 1, 2026
STATE / JURISDICTION: Florida
LOSS LOCATION: I-95 northbound near Exit 79, Palm Beach Gardens, FL
POLICE REPORT: Yes — Report #26-PBSO-88201

CLAIMANT NAME: Sandra Torres
CLAIMANT ROLE: Third party
CLAIMANT CONTACT: On file

INSURED NAME: Brian Kowalski
POLICY NUMBER: SSP-2024-441882

INJURY CLAIMED: Yes — claimant reports cervical and lumbar injury, received ER treatment June 1, currently treating with orthopedic physician
VEHICLE DAMAGE CLAIMED: Yes — third-party vehicle $18,500
TOTAL CLAIMED EXPOSURE: $85,000 (estimated by adjuster based on treatment trajectory)

COVERAGE CONFIRMED: Yes
COVERAGE QUESTION: No
LIABILITY STATUS: Disputed — conflicting accounts

ATTORNEY REPRESENTED: Yes — claimant represented by Martinez & Suarez, P.A., Boca Raton, FL

COMMERCIAL / RIDESHARE / DELIVERY USE: No
PRIOR CLAIMS HISTORY: Claimant has one prior BI claim from 2023 with same carrier

PRIOR HANDLING: No

SPECIAL FLAGS: None

CURRENT HANDLING STATUS: New referral
URGENCY: Time-sensitive — attorney sent preservation of evidence letter June 8

SOURCE DOCUMENTS REVIEWED:
- Claim setup summary
- Police report summary
- Attorney preservation of evidence letter dated June 8, 2026
```

### Output

```text
PRIMARY ROUTE:
COMPLEX / MAJOR CASE AUTO UNIT

SOURCING MODEL:
INTERNAL DESK

WORKLOAD STATUS:
WORKLOAD UNKNOWN

GOVERNANCE ACTION:
SUPERVISOR APPROVAL REQUIRED

MODIFIERS / TASK FLAGS:
INJURY CLAIMED / BI
LIABILITY DISPUTED
ATTORNEY REPRESENTED
MULTI-VEHICLE / MULTI-PARTY
RECORDED STATEMENT NEEDED
SCENE INSPECTION / DOCUMENTATION NEEDED
SUPERVISOR REVIEW REQUIRED

SOURCE DOCUMENTS REVIEWED:
- Claim setup summary
- Police report summary
- Attorney preservation of evidence letter dated June 8, 2026

MISSING INFORMATION:
None blocking routing.

REASON:
Injury is claimed with confirmed ER treatment and ongoing orthopedic care. Claimant is represented by an attorney. Estimated exposure is $85,000, exceeding the $50,000 complex case threshold. Liability is disputed. Attorney has issued a preservation of evidence letter — active legal involvement exists. Two complex case criteria are present simultaneously (injury + attorney + exposure). Routes to complex auto / major case unit. Supervisor approval is required before assignment given the exposure level, attorney involvement, and evidence preservation demand. A recorded statement cannot be obtained without legal authorization per the attorney representation flag.

NEXT ACTION:
Escalate to complex auto / major case unit supervisor for assignment approval. Do not contact claimant or claimant's attorney without supervisor direction. Address preservation of evidence letter immediately — flag for file retention and litigation hold.

DRAFT ROUTING NOTE:
Complex BI claim. Claimant Sandra Torres, I-95 northbound near Palm Beach Gardens, June 1. Injury: cervical and lumbar, ER June 1, currently treating. Attorney: Martinez & Suarez, P.A. Estimated exposure $85,000. Liability disputed. Preservation of evidence letter received June 8 — litigation hold needed. Prior BI claim on file from 2023 with same carrier. Supervisor assignment required before any contact or field action.
```

---

## Example 5 — COVERAGE / SUPERVISOR REVIEW

### Input

```text
CLAIM NUMBER / FILE IDENTIFIER: NV-2026-031104
DATE OF REFERRAL: June 9, 2026
CARRIER / CLAIMS ORGANIZATION: Desert Ridge Insurance
REFERRING ADJUSTER / HANDLER: Pam Sutter

DATE OF LOSS: May 10, 2026
STATE / JURISDICTION: Nevada
LOSS LOCATION: 5600 Spring Mountain Road, Las Vegas, NV 89146
POLICE REPORT: Yes — Report #26-LVMPD-22810

CLAIMANT NAME: James Yee
CLAIMANT ROLE: First party (insured)
CLAIMANT CONTACT: (702) 334-8872

INSURED NAME: James Yee
POLICY NUMBER: DRI-2025-009932

INJURY CLAIMED: No
VEHICLE DAMAGE CLAIMED: Yes — $11,400 estimate
TOTAL CLAIMED EXPOSURE: $11,400

COVERAGE CONFIRMED: Pending — policy shows lapse period
COVERAGE QUESTION: Yes — policy renewal payment was received May 12, two days after the loss date. Coverage may have lapsed at the time of the accident. Adjuster is requesting coverage determination before proceeding.

LIABILITY STATUS: Third party accepted liability

ATTORNEY REPRESENTED: No
COMMERCIAL / RIDESHARE / DELIVERY USE: No
PRIOR CLAIMS HISTORY: None

PRIOR HANDLING: No

SPECIAL FLAGS: None

CURRENT HANDLING STATUS: New referral — on hold pending coverage determination
URGENCY: Time-sensitive — insured's vehicle is at the body shop awaiting authorization

SOURCE DOCUMENTS REVIEWED:
- Claim setup notes
- Payment receipt dated May 12, 2026
- Policy renewal documentation
```

### Output

```text
PRIMARY ROUTE:
COVERAGE / SUPERVISOR REVIEW

SOURCING MODEL:
SUPERVISORY / SIU AUTHORIZATION NEEDED

WORKLOAD STATUS:
WORKLOAD UNKNOWN

GOVERNANCE ACTION:
SUPERVISOR APPROVAL REQUIRED

MODIFIERS / TASK FLAGS:
COVERAGE QUESTION PRESENT
SUPERVISOR REVIEW REQUIRED

SOURCE DOCUMENTS REVIEWED:
- Claim setup notes
- Payment receipt dated May 12, 2026
- Policy renewal documentation

MISSING INFORMATION:
Coverage determination is the blocking issue — cannot route to appraisal or desk handling until resolved.

REASON:
Coverage has not been confirmed. Policy shows a lapse at the date of loss: the accident occurred May 10 and the renewal payment was received May 12. This is a coverage question that must be resolved by supervisory or coverage authority before any appraisal or desk handling proceeds. The vehicle is at the body shop awaiting authorization — this is time-sensitive, but authorization cannot be given until coverage is confirmed. Routes to coverage / supervisor review. Supervisor authorization is required before any claim activity proceeds.

NEXT ACTION:
Escalate to supervising adjuster or coverage unit immediately. Provide policy number DRI-2025-009932, renewal payment receipt dated May 12, and date of loss May 10. Supervisor must determine whether coverage applies before vehicle authorization is issued. Inform insured that authorization is pending coverage review.

DRAFT ROUTING NOTE:
Coverage question — policy lapse. Accident May 10; renewal payment received May 12. Coverage determination required before vehicle authorization. Insured's vehicle at body shop awaiting authorization — time-sensitive. Policy DRI-2025-009932. Payment receipt on file. Supervisor or coverage unit to determine applicability before any action is taken on this file.
```

---

## Example 6 — SIU REFERRAL

### Input

```text
CLAIM NUMBER / FILE IDENTIFIER: CA-2026-104882
DATE OF REFERRAL: June 9, 2026
CARRIER / CLAIMS ORGANIZATION: Pacific Coast Casualty
REFERRING ADJUSTER / HANDLER: Rita Mendoza

DATE OF LOSS: June 3, 2026
STATE / JURISDICTION: California
LOSS LOCATION: Intersection of Van Nuys Blvd and Vanowen Street, Van Nuys, CA 91405
POLICE REPORT: Yes — Report #26-LAPD-VN-33102

CLAIMANT NAME: Ricardo Fuentes (passenger), Luz Dominguez (driver, first party)
CLAIMANT ROLE: Multi-claimant — insured driver and three passengers
CLAIMANT CONTACT: Multiple — on file

INSURED NAME: Luz Dominguez
POLICY NUMBER: PCC-2025-772014

INJURY CLAIMED: Yes — all four occupants (driver + 3 passengers) report soft-tissue injury. All four are treating at the same clinic: Pacific Wellness Center, Van Nuys.
VEHICLE DAMAGE CLAIMED: Yes — $2,100 damage to insured's vehicle
TOTAL CLAIMED EXPOSURE: $220,000 (four BI claims combined, per demand letters from same attorney)

COVERAGE CONFIRMED: Yes
COVERAGE QUESTION: No
LIABILITY STATUS: Third-party vehicle accepted liability

ATTORNEY REPRESENTED: Yes — all four claimants represented by the same attorney: Victor Garza, ESQ., Los Angeles

COMMERCIAL / RIDESHARE / DELIVERY USE: No
PRIOR CLAIMS HISTORY: Claimant/insured Luz Dominguez has one prior claim from 2024 at the same intersection.

PRIOR HANDLING: No

SPECIAL FLAGS:
[X] SIU indicators present — adjuster notes: four soft-tissue claims from a minor impact ($2,100 damage), all treating at same clinic, all represented by same attorney, same intersection as a 2024 prior claim

CURRENT HANDLING STATUS: New referral — adjuster requesting SIU authorization
URGENCY: Routine for SIU intake

SOURCE DOCUMENTS REVIEWED:
- Claim setup notes
- Demand letters (4, same attorney)
- Prior claim note from 2024
```

### Output

```text
PRIMARY ROUTE:
SIU REFERRAL

SOURCING MODEL:
SUPERVISORY / SIU AUTHORIZATION NEEDED

ASSIGNMENT RESOURCE:
SIU-REVIEW-01 — SIU Review Queue

WORKLOAD STATUS:
12/15 — Available

CAPACITY ACTION:
Submit for SIU review consideration. Supervisor authorization required before referral.

GOVERNANCE ACTION:
SUPERVISOR APPROVAL REQUIRED

MODIFIERS / TASK FLAGS:
INJURY CLAIMED / BI
ATTORNEY REPRESENTED
MULTI-VEHICLE / MULTI-PARTY
SIU INDICATORS PRESENT
SUPERVISOR REVIEW REQUIRED

ROUTING CONFIDENCE:
High

CONFIDENCE REASON:
All required fields present. Five distinct SIU indicators are documented and supported
by specific facts. Coverage confirmed, sources provided. SIU-REVIEW-01 is within
capacity at 12/15. No blocking gaps.

SOURCE DOCUMENTS REVIEWED:
- Claim setup notes
- Demand letters (4, same attorney)
- Prior claim note from 2024

MISSING INFORMATION:
None blocking routing.

REASON:
Multiple SIU indicators are present simultaneously: (1) four soft-tissue injury claims from a vehicle with only $2,100 in damage — treatment pattern inconsistent with impact severity; (2) all four claimants are treating at the same clinic; (3) all four claimants are represented by the same attorney; (4) the insured has a prior claim from the same intersection in 2024; (5) combined demand of $220,000 on a minor impact. The referring adjuster has flagged this for SIU. Routes to SIU referral. Do not make coverage or liability determinations pending SIU review.

NEXT ACTION:
Submit SIU referral per carrier protocol. Obtain supervisor authorization before transmitting. Provide claim file, police report, demand letters, prior claim reference, and adjuster SIU flag note. Do not contact claimants or their attorney until SIU directs.

DRAFT ROUTING NOTE:
SIU referral requested. Four soft-tissue BI claims from $2,100-damage minor impact. All four claimants treating at Pacific Wellness Center, Van Nuys. All four represented by same attorney Victor Garza, ESQ. Prior claim by same insured at same intersection, 2024. Combined demand $220,000. Adjuster flagged for SIU. SIU-REVIEW-01 available at 12/15. Supervisor authorization required before referral transmission. Do not make coverage or liability decisions pending SIU review.
```

---

## Example 7 — RETURN FOR ADDITIONAL INFORMATION

### Input

```text
CLAIM NUMBER / FILE IDENTIFIER: (none)
DATE OF REFERRAL: June 9, 2026
CARRIER / CLAIMS ORGANIZATION: Regional Auto Claims
REFERRING ADJUSTER / HANDLER: Tom B.

DATE OF LOSS: (not provided)
STATE / JURISDICTION: Somewhere in Michigan
LOSS LOCATION: Unknown

CLAIMANT NAME: John Smith
CLAIMANT ROLE: Unknown
CLAIMANT CONTACT: Not provided

INSURED NAME: Gary Patterson
POLICY NUMBER: Not provided

INJURY CLAIMED: Unknown
VEHICLE DAMAGE CLAIMED: Yes
COVERAGE CONFIRMED: Unknown
COVERAGE QUESTION: Unknown
LIABILITY STATUS: Unknown
ATTORNEY REPRESENTED: Unknown

SOURCE DOCUMENTS REVIEWED:
- None.
```

### Output

```text
PRIMARY ROUTE:
RETURN FOR ADDITIONAL INFORMATION

SOURCING MODEL:
INTERNAL DESK

WORKLOAD STATUS:
WORKLOAD UNKNOWN

GOVERNANCE ACTION:
RETURN TO REFERRING PARTY

MODIFIERS / TASK FLAGS:
None determinable from available information.

SOURCE DOCUMENTS REVIEWED:
- None.

MISSING INFORMATION:
Six required fields are absent:
(1) Claim number or file identifier
(2) Date of loss — required for all routing decisions
(3) Loss location — "Somewhere in Michigan" is insufficient for routing or field deployment
(4) Claimant role — first party or third party cannot be determined
(5) Policy number — required to confirm coverage
(6) Basic nature of claim — injury, PD, or both cannot be determined

REASON:
The referral cannot be routed. Six required fields are missing or insufficient. "Somewhere in Michigan" does not meet the location specificity requirement. No policy number means coverage cannot be confirmed. Claimant role is unknown. Date of loss is absent. No coverage status can be assessed. The claim type appears to be auto but cannot be confirmed as sufficient information is not present.

NEXT ACTION:
Return referral to Tom B. at Regional Auto Claims with the six specific items listed above. Do not route or assign until all six are provided.

DRAFT ROUTING NOTE:
Referral returned — insufficient information. The following six items are required before routing: (1) claim number, (2) date of loss, (3) specific loss location (address or intersection), (4) claimant role (first party or third party), (5) policy number, (6) basic nature of claim (injury, PD, or both). Resubmit when complete.
```

---

## Example 8 — OUT OF SCOPE / MISROUTED

### Input

```text
CLAIM NUMBER / FILE IDENTIFIER: WC-2026-003310
DATE OF REFERRAL: June 9, 2026
CARRIER / CLAIMS ORGANIZATION: Industrial Risk Partners
REFERRING ADJUSTER / HANDLER: Kelly Novak

DATE OF LOSS: June 2, 2026
STATE / JURISDICTION: Tennessee
LOSS LOCATION: 500 Industrial Park Drive, Memphis, TN 38109

CLAIMANT NAME: Robert Dunmore
CLAIMANT ROLE: Workers' compensation claimant — injured while operating forklift in warehouse

INJURY CLAIMED: Yes — lumbar injury, workers' compensation claim
VEHICLE DAMAGE CLAIMED: No
COVERAGE CONFIRMED: Yes (workers' comp policy)
ATTORNEY REPRESENTED: No

CURRENT HANDLING STATUS: New referral
SOURCE DOCUMENTS REVIEWED:
- Workers' comp intake form
```

### Output

```text
PRIMARY ROUTE:
OUT OF SCOPE / MISROUTED

SOURCING MODEL:
INTERNAL DESK

WORKLOAD STATUS:
WORKLOAD UNKNOWN

GOVERNANCE ACTION:
RETURN TO REFERRING PARTY

MODIFIERS / TASK FLAGS:
None.

SOURCE DOCUMENTS REVIEWED:
- Workers' comp intake form

MISSING INFORMATION:
None — referral is complete but is not an auto accident insurance claim.

REASON:
This is a workers' compensation claim. The claimant was injured operating a forklift in a warehouse — there is no auto accident connection. This operator handles auto accident insurance claims only. Workers' compensation claims are outside scope.

NEXT ACTION:
Return referral to Kelly Novak at Industrial Risk Partners. Direct to the workers' compensation intake path.

DRAFT ROUTING NOTE:
Referral misrouted. This is a workers' compensation claim (warehouse forklift injury) and is outside the scope of the Auto Claims Next-Action Routing Operator. Please submit to the workers' compensation intake path. No action has been taken on this file.
```

---

## Example 9 — SIU WINS OVER BI (Priority Hierarchy Edge Case)

### Input

```text
CLAIM NUMBER / FILE IDENTIFIER: TX-2026-091110
DATE OF REFERRAL: June 9, 2026
CARRIER / CLAIMS ORGANIZATION: Texan First Insurance
REFERRING ADJUSTER / HANDLER: James Ortega

DATE OF LOSS: May 28, 2026
STATE / JURISDICTION: Texas
LOSS LOCATION: I-10 westbound near Exit 737, El Paso, TX
POLICE REPORT: Yes — Report #26-EPPD-44019

CLAIMANT NAME: Carlos Vargas (driver), two passengers
CLAIMANT ROLE: Third party — three occupants total
CLAIMANT CONTACT: On file

INSURED NAME: Linda Cruz
POLICY NUMBER: TFI-2024-330882

INJURY CLAIMED: Yes — all three occupants report soft-tissue injuries; demand letters from same attorney, received within 7 days of loss date
VEHICLE DAMAGE CLAIMED: Yes — claimant vehicle $1,800
TOTAL CLAIMED EXPOSURE: $175,000 (combined demand)

COVERAGE CONFIRMED: Yes
COVERAGE QUESTION: No
LIABILITY STATUS: Insured accepted liability

ATTORNEY REPRESENTED: Yes — all three represented by same attorney, immediate demand

PRIOR CLAIMS HISTORY: Carlos Vargas has two prior claims in 24 months with similar facts

SPECIAL FLAGS:
[X] SIU indicators present — adjuster notes: $1,800 damage, three soft-tissue claims, same attorney, demand within 7 days, prior claim pattern

CURRENT HANDLING STATUS: New referral
SOURCE DOCUMENTS REVIEWED:
- Claim setup notes
- Three demand letters (same attorney)
- Prior claim history note
```

### Output

```text
PRIMARY ROUTE:
SIU REFERRAL

SOURCING MODEL:
SUPERVISORY / SIU AUTHORIZATION NEEDED

WORKLOAD STATUS:
WORKLOAD UNKNOWN

GOVERNANCE ACTION:
SUPERVISOR APPROVAL REQUIRED

MODIFIERS / TASK FLAGS:
INJURY CLAIMED / BI
ATTORNEY REPRESENTED
MULTI-VEHICLE / MULTI-PARTY
SIU INDICATORS PRESENT
SUPERVISOR REVIEW REQUIRED

SOURCE DOCUMENTS REVIEWED:
- Claim setup notes
- Three demand letters (same attorney)
- Prior claim history note

MISSING INFORMATION:
None.

REASON:
SIU indicators are present and take priority over the COMPLEX / MAJOR CASE AUTO UNIT route in the decision hierarchy. The BI claim and attorney representation would normally trigger COMPLEX / MAJOR CASE, but SIU must be evaluated first. SIU indicators: three soft-tissue claims from $1,800-damage vehicle, all three represented by the same attorney, demand letters received within 7 days of loss, and Carlos Vargas has two prior claims with similar facts in 24 months. Per the hierarchy, SIU REFERRAL (priority 4) applies before COMPLEX / MAJOR CASE AUTO UNIT (priority 5). Do not refer to the complex unit until SIU evaluation is complete.

NEXT ACTION:
Submit SIU referral per carrier protocol. Supervisor authorization required. Do not assign to complex unit or contact claimants until SIU directs. Provide complete file including demand letters, prior claim history, police report.

DRAFT ROUTING NOTE:
SIU referral — takes priority over BI routing. Three soft-tissue claims from $1,800-damage vehicle, all one attorney, demand within 7 days of loss. Carlos Vargas has two prior similar claims in 24 months. Adjuster flagged SIU. Supervisor authorization required before referral. BI claim noted — route to complex unit only after SIU completes review and directs.
```

---

## Example 10 — FIELD ADJUSTER / FIELD INVESTIGATION (Internal Over Capacity → Vendor)

### Input

```text
CLAIM NUMBER / FILE IDENTIFIER: CO-2026-028891
DATE OF REFERRAL: June 9, 2026
CARRIER / CLAIMS ORGANIZATION: Rocky Mountain Claims
REFERRING ADJUSTER / HANDLER: Teresa Wills

DATE OF LOSS: June 7, 2026
STATE / JURISDICTION: Colorado
LOSS LOCATION: Intersection of South Havana Street and East Hampden Avenue, Aurora, CO 80012
POLICE REPORT: No — parties exchanged information only

CLAIMANT NAME: Mohammed Al-Rashid
CLAIMANT ROLE: Third party
CLAIMANT CONTACT: (720) 338-5501

INSURED NAME: Frank Diaz
POLICY NUMBER: RMC-2025-771114

INJURY CLAIMED: No
VEHICLE DAMAGE CLAIMED: Yes — disputed; claimant estimates $14,500, insured disputes at $6,000
TOTAL CLAIMED EXPOSURE: $14,500 (disputed)

COVERAGE CONFIRMED: Yes
COVERAGE QUESTION: No
LIABILITY STATUS: Disputed — each driver claims the other ran a red light; no police report, no witnesses identified

ATTORNEY REPRESENTED: No
COMMERCIAL / RIDESHARE / DELIVERY USE: No

PRIOR HANDLING: No

SPECIAL FLAGS: None

CURRENT HANDLING STATUS: New referral
URGENCY: Time-sensitive — accident 2 days ago; intersection has a red light camera system, footage may be retained for only 30 days

ADDITIONAL NOTES: Internal field staff in Aurora/Denver metro are over capacity this week per supervisor.

SOURCE DOCUMENTS REVIEWED:
- Claim setup notes
- Insured's recorded account (provided by adjuster)
```

### Output

```text
PRIMARY ROUTE:
FIELD ADJUSTER / FIELD INVESTIGATION

SOURCING MODEL:
APPROVED FIELD INVESTIGATION VENDOR

ASSIGNMENT RESOURCE:
IA-AUTO-01 — Independent Adjuster / Approved Field Investigation Vendor (Aurora/Denver)

WORKLOAD STATUS:
FIELD-AUTO-01: 15/15 — At Capacity. IA-AUTO-01: 9/15 — Available.

CAPACITY ACTION:
Do not assign to FIELD-AUTO-01. Internal field at capacity. Route to IA-AUTO-01
(approved field investigation vendor). Act within 48 hours — camera footage is
time-sensitive.

GOVERNANCE ACTION:
ROUTE TO ALTERNATE QUEUE

MODIFIERS / TASK FLAGS:
LIABILITY DISPUTED
POLICE REPORT MISSING / UNAVAILABLE
SCENE INSPECTION / DOCUMENTATION NEEDED
INTERNAL CAPACITY CONSTRAINT
VENDOR ASSIGNMENT REQUIRED

ROUTING CONFIDENCE:
High

CONFIDENCE REASON:
All required fields present. Liability is disputed with a specific factual basis.
Time-sensitive physical evidence identified. Internal capacity constraint is confirmed.
Vendor fallback resource (IA-AUTO-01) is available at 9/15. No blocking gaps.

SOURCE DOCUMENTS REVIEWED:
- Claim setup notes
- Insured's recorded account (provided by adjuster)

MISSING INFORMATION:
No police report. Witness identification not yet completed.

REASON:
Liability is disputed with no police report. Physical evidence at the intersection — specifically red light camera footage — is time-sensitive and may be available only for 30 days from the accident date. Field work is the primary remaining gap. Internal field staff (FIELD-AUTO-01) are at capacity (15/15). Per the special field urgency rule: when internal field staff are over capacity and urgent evidence may be lost, keep FIELD ADJUSTER / FIELD INVESTIGATION as the primary route and route to an approved field investigation vendor. IA-AUTO-01 is available at 9/15. Do not delay the scene work.

NEXT ACTION:
Authorize IA-AUTO-01 (approved field investigation vendor) immediately. Objective: document intersection at South Havana Street and East Hampden Avenue, Aurora; identify red light camera system operator; request footage preservation for June 7 date/time; photograph scene. Act within 48 hours.

DRAFT ROUTING NOTE:
Disputed liability, no police report. Intersection of Havana and Hampden, Aurora — accident June 7. Time-sensitive: red light camera footage. FIELD-AUTO-01 at capacity (15/15) — routing to IA-AUTO-01 (9/15, available). Vendor objective: document scene, identify camera system operator, request footage preservation for June 7. Claimant Mohammed Al-Rashid (720) 338-5501. Insured Frank Diaz on file. Act within 48 hours.
```
