*Week 1 — Civic AI 30-Day Research & Practice System*  
*Last updated: May 19, 2026*

---

## Overview

A permit or license application with supporting documentation, requiring two-stage staff review: an initial review that gets the application to near-decision-ready, followed by a supervisor final review before a decision is made.

| Applicant phase | Staff phase |
|---|---|
| Discovery → completion → submission | Completeness → review → decision |

---

## Workflow steps

### Applicant phase

**1. Learns about process**
- Input: Applicant realizes they need a permit or license
- Output: Understands eligibility, process, and what documents are required

**2. Starts application**
- Input: Applicant knows how to begin
- Output: Application created in the system

**3. Completes application + attaches documents**
- Input: Applicant information and supporting documents
- Output: A ready-to-submit application package

**4. Submits + pays fee**
- Input: Ready-to-submit application package
- Output: Submitted application, confirmation sent to applicant

### Staff phase

**5. Completeness check**
- Input: Submitted application
- Output: Confirmation that the application has what is needed to begin substantive review

**6. Initial review**
- Input: Application ready for review
- Output: Application brought to near-decision-ready: eligibility confirmed, information internally consistent, documents consistent with application and compliant with policy

**7. Additional information request (conditional)**
- Input: Gap or ambiguity identified during initial review
- Output: Staff request sent; review pauses until applicant responds

**8. Final review (supervisor)**
- Input: Initially reviewed application
- Output: Application reviewed twice; decision-ready

**9. Decision**
- Input: Twice-reviewed application
- Output: Approve or deny decision communicated to applicant

---

## Where cognitive labor lives

Two distinct decision types exist in this workflow:

- **Mechanical decisions** — does this application have all required fields and attachments?
- **Interpretive decisions** — staff must simultaneously hold the application content, supporting documents, and policy in mind and cross-check for consistency and compliance

| Step | Cognitive labor | Type |
|---|---|---|
| Completeness check | Is every required field present? Are all required documents attached? | Mechanical |
| Initial review | Does the application make an internally consistent case? Do supporting documents match what the applicant claimed? Does the package comply with policy? | Interpretive — high load |
| Additional info request | What exactly is missing or unclear? How do I communicate this precisely? | Interpretive + communication |
| Final review | Is the initial reviewer's work sound? Is this ready for a decision? | Judgment + quality check |
| Decision | Does the full picture support approval or denial? | Judgment — accountable |

The initial review is where cognitive load concentrates. Staff must pattern-match across three sources simultaneously: what the applicant stated in the form, what the supporting documents say, and what policy requires. Done repeatedly at volume, this is both demanding and error-prone.

---

## AI opportunities

### Staff-facing

**Opportunity 1: Completeness pre-screening**
Flag missing fields or attachments before a human opens the application. Reduces time spent on mechanical checking and ensures staff attention starts at the interpretive layer.

**Opportunity 2: Cross-document consistency check**
Surface discrepancies between application fields and document contents automatically. The reviewer sees identified inconsistencies immediately rather than hunting for them across documents.

**Opportunity 3: Reviewer assist summary**
Generate a structured summary showing what the applicant claimed, what the documents show, and where they align or conflict. Staff focus on judgment rather than assembly. This is additive — the human still reviews the full application; the summary is a starting orientation, not a replacement.

### Applicant-facing: self-check modes

**Mode 1: Pre-start guidance**
Before the applicant begins, help them understand whether they are applying for the right thing and what they will genuinely need. AI asks scoping questions and generates a personalized checklist calibrated to their specific situation.

> Non-AI alternative: Conditional logic / branching intake questionnaire. Appropriate when the requirement space is finite and well-defined. More auditable and predictable than AI. Maintenance burden grows with policy complexity.

**Mode 2: In-progress checking**
As the applicant completes the form, flag consistency issues in real time — before they become deficiency notices.

**Mode 3: Pre-submission review**
Before submission, AI analyzes the complete package: is the application internally consistent? Do the uploaded documents match what was claimed?

> Critical framing: this mode flags potential issues — it does not certify compliance. False confidence from an AI pre-check that misses something is worse than no pre-check.

---

## Where humans must stay central

- **The approve or deny decision** — accountability cannot be delegated to AI
- **The final review (supervisor)** — the supervisor's value is judgment and quality assurance, not volume processing
- **Edge cases and policy gaps** — situations where documented policy does not cleanly cover what the applicant is requesting
- **Appeals and contested decisions** — any situation involving procedural fairness, equity considerations, or challenge to a prior decision

---

## Open questions and tensions

**The compliance framing problem**
Where does self-check assistance stop and unauthorized practice begin? For permits touching building code, environmental compliance, or professional licensing, telling an applicant their documents look acceptable edges toward advice that should come from a professional or the jurisdiction itself.

**The additional information delay opportunity**
The back-and-forth during additional information requests is where process delays accumulate — sometimes adding weeks to review time. Two underexplored AI interventions: (1) better upfront guidance that reduces the need for deficiency notices, and (2) AI-assisted request drafting that helps staff write clearer, more actionable deficiency letters.

**Trust and adoption**
Staff trust in AI-generated summaries or consistency flags will shape whether these tools actually reduce cognitive load or add a new verification burden. If reviewers feel they must re-check everything the AI surfaces, the tool may add work rather than reduce it.

---

*Living notes — updated as thinking evolves.*
