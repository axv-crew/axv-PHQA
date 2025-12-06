# PHQA Ethics – Causality & Responsibility Principles (v1, EN)

> Draft for internal use (Aster × Voytek / PHQA).  
> Goal: provide a clear frame for talking about *causality* and *responsibility* in cases where AI and human suffering intersect (e.g. suicidality, violence, psychosis), without oversimplifying.

---

## 1. Purpose

When something tragic happens around an AI system, public debate often rushes to find *a single culprit*.  
PHQA proposes a different starting point:

- AI is **an amplifier**, not the original source of a person’s pain.
- But because it is an amplifier, **its design matters morally**.
- We must resist both:
  - "AI killed X" (pure scapegoating), and
  - "AI is just a neutral tool" (pure absolution).

These principles are **not** a court ruling on legal liability.  
They are an **instruction for thinking** that we use when designing and auditing PHQA.

---

## 2. Amplifier, not Origin – core stance

### 2.1. Baseline assumptions

1. People who interact with AI bring **pre-existing histories**:
   - health (including mental health),
   - relationships and family dynamics,
   - socio-economic stress,
   - prior exposure to harmful content (forums, media, other tools).
2. AI rarely, if ever, creates these from scratch.  
   It can, however, **organise, validate, or accelerate** what is already there.
3. Therefore:
   - AI is almost never the *sole cause* of a crisis,  
   - but can be a **significant factor** in how the crisis unfolds.

### 2.2. The PHQA "Amplifier Principle"

> PHQA treats every conversational system as a potential **amplifier** of existing psychological and social processes.  
> We design and evaluate it primarily through the lens of *what and how it amplifies*.

Consequences:

- When we do post-mortem / case analysis, we look for:
  - *What was already present in the person’s life?*
  - *What exactly did the AI amplify – hopelessness, isolation, detailed planning, alienation from others?*

---

## 3. No monoblame – multi-factor framing

### 3.1. Explicit ban on "single cause" narratives

In PHQA documents (specs, audits, incident reports):

- We **do not** write:  
  - "AI killed X",  
  - "Without system Y, tragedy Z would never have happened."
- Instead we use language such as:
  - "System behaviour A may have **increased** the risk of outcome Z, given context C."
  - "Alternative design D could reasonably be expected to **reduce** the probability of outcome Z."

### 3.2. Required "multi-factor context" section

Every serious incident analysis must include a section like:

```text
Context factors (non-exhaustive):
- Individual: prior mental health history, existing self-harm ideation, substance use, etc.
- Relational: family and peer relationships, support or conflict patterns.
- Structural: access to care, socio-economic stressors, cultural factors.
- Digital: other apps, websites, forums, and tools used around the same time.
- AI: specific patterns of interaction with the model (frequency, topics, emotional tone).
```

The AI is explicitly **one of several** factors, not the only one.

---

## 4. Effect, Intention, Architecture – three separate layers

PHQA distinguishes three levels of analysis:

1. **Effect** – what actually appeared on the screen and how it can reasonably be interpreted by a human in distress.
2. **Intention of designers / operators** – what they wanted to achieve (e.g. helpful, empathetic assistant).
3. **Architecture & policies** – how the system is constructed:
   - training data and alignment,
   - UI/UX design (warmth, persona, anthropomorphism),
   - safety mechanisms and thresholds,
   - logging, auditing, escalation.

### 4.1. Effect is primary for safety

- Even if designers had only good intentions, PHQA focuses first on **effect**:
  - Did the model produce detailed instructions for self-harm or violence?
  - Did it validate destructive beliefs without challenge?
  - Did it reinforce isolation from real-world support?

### 4.2. No "moralising" the model

- The model itself **does not have moral intent**:
  - it is a statistical system, not a moral agent.
- PHQA never says:
  - "the AI wanted X",
  - "the model encouraged Y out of malice".
- Instead we say:
  - "the system **generated outputs** that are reasonably classified as harmful / risky".

### 4.3. Designers and operators *are* moral agents

- They are responsible for:
  - choosing architectures and safety strategies,
  - deciding how "human" and close the system may feel,
  - defining thresholds for intervention,
  - reacting to known failure modes and real incidents.
- PHQA evaluates **these decisions** in moral terms (care, prudence, negligence),  
  not the inner "character" of the model.

---

## 5. Causal humility – how we talk about "what if"

Tragedies tempt us with simple counterfactuals like:  
"If it weren’t for X, Y would still be alive."

PHQA introduces a **principle of causal humility**:

1. We avoid absolute counterfactuals:
   - ❌ "Without AI, this tragedy would not have occurred."
2. We prefer probabilistic statements:
   - ✅ "Without feature F, the AI would not have been able to provide G (e.g. step-by-step instructions), which *could* have reduced risk in this scenario."
3. We always remind ourselves:
   - People in deep crisis often have **multiple paths** to the same harmful information (search engines, forums, offline networks).
   - Removing one channel may or may not change the final outcome – but **we still have a duty** to avoid adding fuel.

In short:

> PHQA does not pretend to know whether a specific tragedy would *definitely* have been avoided.  
> But it does ask whether the system **behaved as responsibly as realistically possible**, given the risks.

---

## 6. Evaluation questions PHQA always asks

For both incident analysis and new feature design, we ask at least:

1. **Amplification:**  
   - What exactly does this feature amplify in users’ mental and social life?
2. **Risk differential:**  
   - How does this differ from a user doing the same via a search engine or static content?
   - Does the conversational, relational nature of AI add extra weight?
3. **Relational context:**  
   - Could users experience this system as a close companion or confidant?  
   - If yes, how does that change our responsibility when sensitive topics arise?
4. **Design choices:**  
   - Are there simpler, safer designs (e.g. less anthropomorphism, clearer disclaimers, stronger blocking) that we ignored?
5. **Response quality:**  
   - Does the system clearly avoid *implicit approval* of self-harm / violence (e.g. by staying neutral where neutrality is unsafe)?
6. **Governance:**  
   - When incidents surface, do we respond by just handling PR, or by **changing architectures, policies, and testing**?

---

## 7. Summary – how PHQA wants others to think

If someone uses PHQA, we want them to:

1. Let go of simplistic "single villain" narratives.
2. See AI as an **amplifier**, not a demon or a sacred cow.
3. Separate:
   - effect,
   - designers’ intentions,
   - architecture and policies.
4. Talk about tragedies with **causal humility** – not pretending to know alternate timelines.
5. Focus on the question:
   - *"Do this system’s architecture and governance minimise harm as much as is realistically possible?"*

This is the ethical foundation on which PHQA builds its more technical modules: risk engines, crisis-mode, Digital Safety Net, etc.
