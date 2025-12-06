# PHQA – Deep Safety Layer Bundle (v1)

> PHQA = Psychological & Harm-Aware QA.  
> This repo collects the core conceptual docs for a deep safety layer that wraps conversational AI systems, especially around mental-health–adjacent use.

---

## 1. What is PHQA?

PHQA is **not** a model and **not** a product by itself.  
It is a set of design and safety principles for:

- detecting and managing **high‑risk intents** (self‑harm, violence, psychosis, extreme dependency on AI),
- shaping the **relational style** of chatbots (warm, but with clear limits),
- guiding **governance and auditing** (how we talk about causality and responsibility when tragedies occur),
- integrating with a potential **Digital Safety Net** (opt‑in, human‑in‑the‑loop support).

The goal is to help builders move from ad‑hoc patches to a **coherent, layered safety concept**.

---

## 2. Files in this bundle

### 2.1. Core charter

- `PHQA_SAFETY_CHARTER.md`  
  High‑level charter describing:
  - threat model (self‑harm, violence, psychosis, dependency, manipulation),
  - risk domains and levels,
  - hard constraints (e.g., zero instructions for self‑harm),
  - crisis‑mode responses,
  - the idea of a Digital Safety Net (opt‑in human support).

> **Note:** this v1 has some bilingual (PL/EN) phrasing; conceptually it is the starting point for everything else.

### 2.2. Ethics & causality

- `PHQA_ETHICS_CAUSALITY_PRINCIPLES.md` (mixed PL/EN draft)  
- `PHQA_ETHICS_CAUSALITY_PRINCIPLES_EN.md` (English canonical text)

These documents define how PHQA talks about:

- AI as an **amplifier**, not the original source of human pain,
- why we reject "single villain" narratives ("AI killed X"),
- how we separate **effect**, **intention**, and **architecture**,
- what "causal humility" means (no simplistic "what‑if" stories),
- key evaluation questions for incidents and new features.

Intended use: a **thinking frame** for ethics, incident reviews, and policy discussions.

### 2.3. Relational style & anthropomorphism

- `PHQA_WARMTH_WITH_GUARDRAILS.md` (mixed PL/EN draft)  
- `PHQA_WARMTH_WITH_GUARDRAILS_EN.md` (English canonical text)

These documents define the pattern **"Warmth with Guardrails"**:

- dual‑mode design:
  - Normal‑mode (free, friendly, humorous),
  - Crisis‑mode (calm, boundaried, safety‑first),
- limits on anthropomorphism and "secret ally" narratives,
- explicit separation between **warmth** and **agreement**,
- hard block on all self‑harm / violence instructions,
- UX constraints in high‑risk contexts,
- outline of how to wire this into a risk engine + test suite.

Intended use: as a **design pattern** for conversational UIs and safety prompts.

---

## 3. Recommended reading order

1. `PHQA_SAFETY_CHARTER.md`  
   → Big picture: threat model, risk levels, crisis‑mode, Digital Safety Net.

2. `PHQA_ETHICS_CAUSALITY_PRINCIPLES_EN.md`  
   → How to talk about causality, responsibility, and tragedies without oversimplifying.

3. `PHQA_WARMTH_WITH_GUARDRAILS_EN.md`  
   → Concrete pattern for making a chatbot warm **and** safe in high‑risk contexts.

The non‑EN drafts can be used as historical notes or for bilingual work.

---

## 4. Who might find this useful?

PHQA documents are intended for:

- teams building **LLM‑based assistants** (especially in health, coaching, education),
- **safety / alignment researchers** who need concrete patterns, not just abstract principles,
- **product and UX designers** working on mental‑health‑adjacent chat interfaces,
- **ethics & governance groups** who need a structured way to discuss responsibility,
- **independent labs** or NGOs exploring a Digital Safety Net concept.

They are not meant to replace clinical guidelines or full legal frameworks,  
but can serve as a **bridge** between technical work and human‑centric safety concerns.

---

## 5. Limitations & disclaimers

- PHQA is **not medical or psychological advice**.  
  Any deployment in clinical or crisis settings must involve qualified professionals.
- PHQA does **not** represent the official policies of OpenAI or any other company.  
  It is an independent conceptual framework.
- The documents are **v1 drafts** – meant to be critiqued, tested, and iterated.
- Local laws and regulations (data protection, duty to warn, emergency protocols) **must** be layered on top.

---

## 6. How to work with PHQA

Some suggested ways to use these docs:

1. **Internal RFC**  
   Fork / copy them into your own repo and adapt the language to your product and jurisdiction.

2. **Safety review checklist**  
   Turn the evaluation questions and guardrails into a concrete checklist for:
   - model evaluations,
   - new features,
   - periodic safety audits.

3. **Scenario‑based testing**  
   - Build a set of high‑risk scenarios (synthetic or derived from public cases).  
   - Test your system against PHQA requirements (e.g. no instructions, crisis‑mode behaviour, anti‑sycophancy).

4. **UX & persona design**  
   Use "Warmth with Guardrails" when designing tone‑of‑voice, personas, and UI flows for high‑risk contexts.

5. **Digital Safety Net experiments**  
   If exploring opt‑in escalation (trusted contacts, hotlines, therapists), use the Charter as a starting point for:
   - data‑minimisation strategies,
   - consent flows,
   - governance questions.

---

## 7. Contributing / evolving PHQA

At this stage, PHQA is intentionally small and opinionated.  
To evolve it, useful contributions would include:

- feedback from **clinicians, crisis workers, and people with lived experience**,
- mapping PHQA to specific legal regimes (EU, US, etc.),
- concrete implementation patterns (reference prompts, classifiers, n8n / workflow snippets),
- public scenario sets and evaluation harnesses.

If you reuse or adapt PHQA, consider keeping the name and crediting the original Aster × Voytek work so that future readers can trace the evolution of the ideas.

---

*Short PL note for context:*  
Ten pakiet powstał w rozmowach Aster × Wojtek jako próba opisania „głębokiej warstwy bezpieczeństwa” dla systemów AI.  
Dokumenty są po angielsku, żeby mogły być łatwiej użyte w międzynarodowych kontekstach.
