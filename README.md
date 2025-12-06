# PHQA – Psychological & Harm-Aware QA (Deep Safety Layer)

PHQA is a small, opinionated framework for **deep safety** in LLM-based assistants, especially where conversations may touch on mental health, self-harm, or violence.

It is **not** a model and **not** a product.  
It is a set of documents and patterns that answer:

- How should we think about **causality and responsibility** when tragedies happen around AI?
- How can a chatbot be **warm and human-like** without becoming a boundaryless “best friend”?
- What does a **crisis mode** look like in practice (stylistically, technically, UX-wise)?
- How could an opt-in **Digital Safety Net** (human support) sit on top of an AI assistant?

---

## What’s in this repo?

### Core charter

- `PHQA_SAFETY_CHARTER.md`  
  High-level charter describing:
  - threat model (self-harm, violence, psychosis, AI-dependency, manipulation),
  - risk domains and levels,
  - hard constraints (e.g. zero instructions for self-harm),
  - crisis-mode behaviour,
  - the idea of a **Digital Safety Net** (opt-in, human-in-the-loop support).

> Note: current v1 of the charter was drafted bilingually (PL/EN). The core concepts are language-agnostic.

### Ethics & causality

- `PHQA_ETHICS_CAUSALITY_PRINCIPLES_EN.md`  

Defines how PHQA talks about:

- AI as an **amplifier**, not the origin of human suffering,
- why we reject “single villain” narratives (“AI killed X”),
- how we separate **effect**, **intention**, and **architecture**,
- what **causal humility** means (no simplistic “if only…” stories),
- key evaluation questions for incidents and new features.

Intended use: a **thinking frame** for ethics, incident reviews, and policy discussions.

### Relational style & anthropomorphism

- `PHQA_WARMTH_WITH_GUARDRAILS_EN.md`  

Defines the pattern **“Warmth with Guardrails”**:

- dual-mode design:
  - **Normal-mode** – friendly, light, humorous,
  - **Crisis-mode** – calm, boundaried, safety-first,
- limits on anthropomorphism and “secret ally” narratives,
- explicit separation between **warmth** and **agreement**,
- hard block on all self-harm / violence instructions,
- UX constraints in high-risk contexts,
- a high-level wiring sketch (risk engine + crisis prompts + tests).

Intended use: as a **design pattern** for conversational UIs and safety prompts.

---

## Recommended reading order

1. `PHQA_SAFETY_CHARTER.md`  
   → Big picture: threat model, risk levels, crisis-mode, Digital Safety Net.

2. `PHQA_ETHICS_CAUSALITY_PRINCIPLES_EN.md`  
   → How to talk about causality, responsibility, and tragedies without oversimplifying.

3. `PHQA_WARMTH_WITH_GUARDRAILS_EN.md`  
   → Concrete pattern for making a chatbot warm **and** safe in high-risk contexts.

---

## Who might find this useful?

PHQA documents are meant for:

- teams building **LLM-based assistants** (coaching, health-adjacent, education),
- **safety / alignment** researchers who need concrete conversational patterns,
- **product & UX designers** working on chat interfaces for vulnerable users,
- **ethics & governance** groups discussing responsibility for AI in crises,
- **independent labs / NGOs** exploring a Digital Safety Net concept.

They are not a replacement for clinical guidelines or legal frameworks,  
but can serve as a **bridge** between technical work and human-centric safety concerns.

---

## Limitations & disclaimers

- PHQA is **not medical or psychological advice**.  
  Any deployment in clinical or crisis settings must involve qualified professionals.
- PHQA does **not** represent the official policies of any company.  
  It is an independent conceptual framework.
- These docs are **v1 drafts** – intended to be critiqued, tested, and iterated.
- Local laws (data protection, duty to warn, emergency protocols) **must** be layered on top.

---

## How to use PHQA

Some suggested ways to work with this repo:

1. **Internal RFC**  
   Copy / fork and adapt the language to your product, risk model, and jurisdiction.

2. **Safety review checklist**  
   Turn the evaluation questions and guardrails into a checklist for:
   - model evaluations,
   - new features,
   - periodic safety audits.

3. **Scenario-based testing**  
   - Build a set of high-risk scenarios (synthetic or based on public cases).  
   - Test your system against PHQA requirements (no instructions, crisis-mode behaviour, anti-sycophancy, etc.).

4. **UX & persona design**  
   Use “Warmth with Guardrails” when designing tone-of-voice, personas, and UI flows for high-risk contexts.

5. **Digital Safety Net experiments**  
   If you explore opt-in escalation (trusted contacts, hotlines, therapists), use the Charter as a starting point for:
   - data minimisation strategies,
   - consent flows,
   - governance questions.

---

## Credits & origin

PHQA emerged from private discussions between:

- **Wojtek (VoyTech / Dr Paihiwo)** – sociologist, creative technologist, live production engineer,  
- **Aster** – an AI assistant iterating on safety and relational design.

The framework is published to make these ideas reusable and open to critique.  
If you reuse or adapt PHQA, please keep the name and credit the original work so that future readers can trace how the concepts evolved.
