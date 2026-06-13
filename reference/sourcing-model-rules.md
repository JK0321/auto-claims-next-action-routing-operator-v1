# Sourcing Model Rules

After selecting the primary route, assign one sourcing model. The sourcing model answers: who fulfills the work?

Full sourcing selection table is in `rules.md` — Sourcing Model Rules section.

---

## Sourcing Models

### INTERNAL DESK

**When to use:** The work can be handled by an internal desk adjuster or desk handling unit.

**Applies to:** STANDARD DESK AUTO UNIT (primary use), COVERAGE / SUPERVISOR REVIEW (when no supervisor authorization trigger), RETURN FOR ADDITIONAL INFORMATION, OUT OF SCOPE / MISROUTED, COMPLEX / MAJOR CASE AUTO UNIT (when internal complex unit has capacity), MATERIAL DAMAGE / APPRAISAL UNIT (when internal appraisal capacity is available — this is the default for material damage).

**Override:** If the internal desk unit is OVER WORKLOAD LIMIT, switch to TPA / OVERFLOW PARTNER. For material damage, switch to APPROVED APPRAISAL VENDOR when internal appraisal capacity is unavailable or over workload limit.

---

### INTERNAL FIELD

**When to use:** The work requires a field adjuster and an internal field adjuster is available within the territory.

**Applies to:** FIELD ADJUSTER / FIELD INVESTIGATION (primary use when internal capacity exists and territory is covered).

**Override:** If internal field staff are OVER WORKLOAD LIMIT or outside the territory, switch to APPROVED FIELD INVESTIGATION VENDOR or TPA / OVERFLOW PARTNER. Apply the field urgency rule: if evidence may be lost, do not wait for internal capacity — authorize vendor immediately.

---

### INDEPENDENT ADJUSTER (IA) ASSIGNMENT

**When to use:** A broader claim-handling assignment is needed outside the carrier's internal capabilities, outside territory, or as an authorized overflow for complex claims.

**Applies to:** COMPLEX / MAJOR CASE AUTO UNIT when no internal complex unit capacity is available and a full claim-handling assignment (not just a discrete field task) is needed.

**Distinction from field vendor:** An IA takes on broader claim management, not just a single field task. Use APPROVED FIELD INVESTIGATION VENDOR for specific, bounded field tasks. Use IA for ongoing complex claim management.

**Override condition:** Requires coordinator or supervisor authorization before assignment due to expense and scope.

---

### APPROVED APPRAISAL VENDOR

**When to use:** Material damage appraisal is needed and internal desk / appraisal capacity is unavailable, over workload limit, or geography prevents internal handling.

**Applies to:** MATERIAL DAMAGE / APPRAISAL UNIT when internal appraisal capacity is not available. INTERNAL DESK is the default for material damage when internal capacity is confirmed; APPROVED APPRAISAL VENDOR is the override when it is not.

---

### APPROVED FIELD INVESTIGATION VENDOR

**When to use:** Field work (scene inspection, recorded statement, witness locate, contact attempt) is needed but internal field staff are at or over workload limit, outside territory, or unavailable.

**Applies to:** FIELD ADJUSTER / FIELD INVESTIGATION when internal capacity does not permit direct assignment.

**Urgency rule:** If field evidence is time-sensitive and internal field is over capacity, do not wait — authorize vendor immediately and add VENDOR ASSIGNMENT REQUIRED and INTERNAL CAPACITY CONSTRAINT as modifier flags.

---

### TPA / OVERFLOW PARTNER

**When to use:** Internal capacity (desk, field, or complex unit) is over workload limit and a third-party administrator or overflow partner can take the assignment.

**Applies to:** Any route where the primary internal resource is over capacity. Used as a backup sourcing model for STANDARD DESK, MATERIAL DAMAGE / APPRAISAL, FIELD ADJUSTER, and COMPLEX / MAJOR CASE when internal units are full.

**Note:** Vendors support fact development, appraisal, documentation, and field work. Coverage, liability, reserve, settlement, and SIU outcome decisions are not delegated to a TPA / overflow partner unless authority is explicitly delegated outside this operator.

---

### CAT TEAM

**When to use:** The claim is associated with a declared catastrophe (CAT) event.

**Applies to:** MATERIAL DAMAGE / APPRAISAL UNIT or FIELD ADJUSTER / FIELD INVESTIGATION when the CAT special flag is checked in the intake form or the claim is otherwise identified as part of a CAT event.

**Note:** CAT team deployment supersedes standard appraisal and field vendor routing when a CAT event is declared.

---

### SUPERVISORY / SIU AUTHORIZATION NEEDED

**When to use:** Supervisor authorization is required before the assignment is made or transmitted.

**Applies to:** SIU REFERRAL (always), COVERAGE / SUPERVISOR REVIEW (when supervisor authorization is required by carrier protocol or claim complexity), COMPLEX / MAJOR CASE AUTO UNIT (when exposure level or other factors require supervisor sign-off before IA or complex unit assignment).

**What this means:** The routing packet goes to a supervisor before any assignment is executed. The supervisor reviews the routing, approves or modifies it, and authorizes the assignment.

---

## Sourcing Model vs. Primary Route — Relationship

The primary route answers: what work does the claim need?
The sourcing model answers: who should do that work?

These are two separate decisions. Do not conflate them.

- A FIELD ADJUSTER / FIELD INVESTIGATION primary route can be sourced by INTERNAL FIELD, APPROVED FIELD INVESTIGATION VENDOR, or TPA / OVERFLOW PARTNER depending on capacity.
- A MATERIAL DAMAGE / APPRAISAL UNIT primary route can be sourced by INTERNAL DESK (if internal appraisal staff exist), APPROVED APPRAISAL VENDOR, TPA / OVERFLOW PARTNER, or CAT TEAM.
- An OUT OF SCOPE / MISROUTED primary route is sourced by INTERNAL DESK (the coordinator who handles the rejection).

"Outsource to third-party vendor" is never a primary route. It is a sourcing model answer, always attached to a specific primary route.
