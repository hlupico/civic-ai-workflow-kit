# Civic AI Workflow Kit
A practitioner's open research into where AI reduces cognitive load in government workflows — analyses, experiments, and implementation frameworks.

## What this is
Government staff carry enormous cognitive loads: processing applications, reviewing documents, routing requests, managing workflows that were never designed to scale. This project researches where AI can responsibly absorb some of that burden — and where humans must remain central.

This is not a vendor pitch, a chatbot project, or an AI hype resource. It is a practitioner's working research system: grounded in real government workflows, honest about limitations, and focused on operational usefulness over impressive demos.

## Who this is for
- Government staff and managers trying to understand where AI fits in their operations
- Civic technologists building tools for public sector workflows
- Product practitioners researching responsible AI implementation in government
- Anyone who wants a non-hype, operations-first perspective on civic AI

## What's in this repo
```
/workflows      Analyses of real government workflows: steps, cognitive load, AI opportunities
/experiments    Experiment notes documenting what worked, what failed, and what's worth testing
/docs           Frameworks and principles for civic AI implementation
/prompts        Example prompts used in experiments, annotated for reuse
/evaluations    Evaluation criteria and checklists for assessing AI outputs in government contexts
/resources      Reading lists, references, and external resources
```

## Guiding principles

Human-in-the-loop by default. AI should support human decision-making, not replace human accountability. Every implementation should be designed around the question: what does the human reviewer need to do their job better?

Operational usefulness over impressive demos. A simple workflow improvement with a realistic implementation path is worth more than a sophisticated prototype that no government team can actually adopt.

Government context is a design constraint, not an afterthought. Public trust, procedural fairness, accessibility, auditability, and equity shape what good AI implementation looks like in a government context.

Small experiments compound. Run small, specific experiments. Document what works and what does not. Let understanding accumulate.

Visible thinking matters. Research, synthesis, and experimentation should be documented publicly to contribute to a body of knowledge others can use.

## Current work
This repo is being built in public as part of a structured 30-day research and practice system.

**Week 1 — AI + Government Workflow Foundations**
Primary question: Where does AI meaningfully fit into government operations?

Workflow analysis: Permit application review — steps, cognitive load, and AI opportunities across the full applicant and staff phases

Experiment: AI cross-document consistency checking — tested whether AI could detect discrepancies across a five-document TNC operating authority license application. All planted discrepancies detected, including a VIN manufacturer prefix flag that required external knowledge of VIN structure.

**Week 2 — AI Readiness in Government Systems**
Primary question: What makes a workflow AI-ready?

Research: Retrieval-Augmented Generation (RAG) — how it works, what it enables, government-specific risks and constraints, and the relationship between RAG and expanding LLM context windows

Workflow analysis: TNC permit intake and pre-application — applicant-facing phase of the TNC operating authority license process, focused on document knowledge gaps as the primary failure mode

Experiment: RAG policy compliance checking — tested whether AI can check an application against policy requirements, not just internal document consistency. Used a fictional policy document (AP-TNC-2024-01) with two application packages: one compliant, one with two planted compliance gaps. Both gaps detected with specific policy citations and exact document values. Clean result returned accurately on the compliant package with no false positives.

**Week 3 — Human-in-the-Loop Operations**
Primary question: Where should humans remain central?

Research: AI failure modes in government operations. A taxonomy of seven failure modes (hallucination, silent retrieval failure, confident wrongness, miscalibration, chunking errors, stale retrieval, scope overreach), why failure carries different stakes in government contexts, and principles for failure-aware evaluation design.

Workflow analysis: TNC permit review stress test - stress-tested the established workflow against realistic operating conditions: degraded input conditions, human-AI interaction design (uncertainty communication, override logging), and equity evaluation before sample sizes allow segmentation.

Experiment: Degraded inputs and edge case escalation — five runs across two packages. Key findings: AI flagged degraded fields explicitly with extracted values rather than guessing or skipping silently; output quality varied between clean and loaded session contexts; a structured four-column output format (Requirement | Policy Section | Finding | Status) with a controlled status vocabulary produced more consistent, skimmable, actionable outputs than open-ended format instructions; edge case escalation (ambiguous vehicle configuration) was handled correctly — the AI declined to make a compliance determination and escalated to the reviewer with a clear explanation of why.

Prompt update: System prompt revised after experiment to specify output format, require extracted values in every finding, and define four status labels (Compliant, Non-Compliant, Needs Manual Review, Requires Human Judgment). Retest confirmed improved consistency and actionability.

## Key findings so far
- AI can detect cross-document inconsistencies accurately, including inconsistencies that require external knowledge to identify (VIN manufacturer prefixes, vehicle make/model mismatches)
- AI can check applications against policy requirements when policy is provided as context which grounds responses in specific policy sections rather than general knowledge
- Clean results (all-clear on compliant applications) are as important as gap detection for staff trust and adoption
- Output format and prompt design affect calibration quality. Structured output specifications in the prompt produce more consistent, scannable results
- Trust in AI-generated results takes repeated exposure, even when intellectual trust is earned quickly.
- Session context affects output quality. Clean sessions (no prior conversation history) produce more specific, skimmable findings than sessions with accumulated context — a deployment variable with direct implications for staff-facing tools.
- Failure mode awareness shapes evaluation design. Controlled experiments with clean inputs are not a reliable proxy for real-world performance. Adversarial evaluation like testing with degraded inputs, subtle discrepancies, edge cases is necessary before deployment.
- Edge case escalation requires explicit prompt design. The AI correctly declined to make a compliance determination on an ambiguous vehicle configuration, but this behavior was reinforced by explicit system prompt instructions.

## What I am not

An AI engineer
An AI influencer
A vendor or consultant selling a product

I am a government product practitioner researching and experimenting with operational AI and documenting the work publicly so others can use it.

Living project. Updated as research and experiments progress.
