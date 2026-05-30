# Experiment: AI Cross-Document Consistency Checking

*Week 1, Wednesday — May 21, 2026*  
*Civic AI 30-Day Research & Practice System*

---

## Setup
The names and vehicle, company and insurance information used in the experiment are fake and used for testing purposes only. 

| Parameter | Detail |
|---|---|
| Capability tested | AI cross-document consistency checking and structured reviewer assist summary |
| Scenario | TNC operating authority license application — City of Austin Transportation Dept. |
| Applicant | Carlos R. Mendez / Rio Star Transportation LLC |
| Documents reviewed | Application form, TX SOS business formation, proof of insurance, TX DMV title, vehicle lease agreement |
| Discrepancies planted | Three different VINs across application, title, and insurance for Vehicle 1 (2019 Toyota Camry). Application VIN begins with '1HG' — a Honda manufacturer prefix. |
| Output format | Structured HTML reviewer assist summary: 5 sections — identity check, vehicle summary, insurance check, identified issues, reviewer notes |

---

## What the AI produced

The output was a structured reviewer assist summary organized into five sections, each targeting a distinct review question.

### Section 1 — Applicant and business identity check

Five fields compared across the application and TX SOS certificate. Four matched cleanly. One flagged:

- **Minor variation — applicant name:** Application listed *Carlos R. Mendez*; TX SOS showed *Carlos Mendez* (no middle initial). Flagged as a minor variation, not a hard error. Reviewer advised to confirm identity consistency per department standards.

### Section 2 — Vehicle summary

**Vehicle 1 (2019 Toyota Camry) — Three-way VIN conflict:**
- Application VIN `1HGBH41JXMN109186` vs. Title VIN `4T1BF3EK9AU045231` — mismatch
- Application VIN vs. Insurance VIN `4T1BF1FK5HU123456` — mismatch
- Title VIN vs. Insurance VIN — also a mismatch
- Three separate documents, three different VINs for the same vehicle
- The AI additionally flagged that `1HG` is a Honda manufacturer identifier — an impossibility for a Toyota Camry
- Plate (TX LMN-4421) matched across all documents

**Vehicle 2 (2021 Honda Odyssey) — Clean:**
- VIN matched across application, lease, and insurance
- Plate matched across lease and insurance
- Lease active on application date
- Permitted use on lease consistent with service type on application

### Section 3 — Insurance coverage check

Six fields checked, all clean: policyholder, policy period, coverage type, liability limit, vehicles listed, certificate holder. One secondary observation: given the VIN discrepancies, Vehicle 1 appears to be identified on the policy by plate rather than a verified VIN.

### Sections 4 and 5 — Issues and reviewer notes

Four hard issues surfaced (all VIN-related, with exact values from each source document). Four reviewer notes for items requiring staff judgment:

- Driver license present on application but no supporting document included
- Lease agreement shows blank signature lines — may be an unsigned copy
- Insurance policy expires Dec 31, 2026 — may not cover full license term
- Vehicle 1 insurance coverage appears to be by plate rather than verified VIN

---

## Evaluation

### What worked

- All three planted VIN discrepancies detected and surfaced with exact values and source citations
- Honda manufacturer prefix catch (`1HG` on a Toyota) applied external knowledge of VIN structure — went beyond field-matching to identify an impossibility
- Vehicle 2 returned a clean result accurately — no false positives
- Five-section output structure maps directly onto the review workflow; a reviewer could move through it sequentially
- Secondary observations (unsigned lease, expiring insurance) surfaced as reviewer notes, not hard flags — appropriate calibration
- Name variation flagged at the right severity level
- Insurance-by-plate observation showed reasoning across a secondary implication of the VIN conflict, not just reporting the conflict itself

### Limitations observed

- Driver license could not be verified. AI can only check consistency across submitted documents, not external systems
- Unsigned lease flag depended on visible blank signature lines; scanned docs with illegible signatures may not be caught
- No hallucinations observed, but sample was small and scenario was controlled
- Output assumed clean digital text; OCR quality on scanned documents is untested

---

## Operational implications

**Cognitive load reduction:** The full five-document package was synthesized into a structured summary a reviewer can scan in under two minutes. The three-way VIN conflict, which required mentally holding values from three documents simultaneously, was surfaced automatically with exact values and citations.

**Deficiency notice quality:** The output was specific enough to draft a targeted, actionable deficiency notice on the first pass, rather than a generic flag.

**Trust and the clean result:** Vehicle 2 coming back clean is as important as the Vehicle 1 flags. If reviewers cannot trust all-clear results, they re-check everything and the tool adds load rather than reducing it. This is an adoption question as much as a capability question.

---

## What to test next

- [ ] Run the same scenario with scanned documents — does OCR quality affect detection?
- [ ] Add a policy compliance layer: can the AI check eligibility requirements, not just internal consistency?
- [ ] Introduce subtler discrepancies (name spelling variation, slightly different address format) — where does detection degrade?
- [ ] Test completeness pre-screening independently: missing fields, wrong document type, missing attachments
- [ ] Measure reviewer behavior: do staff accept clean-bill results, or re-check regardless?

---

*Living notes — updated as thinking evolves.*
