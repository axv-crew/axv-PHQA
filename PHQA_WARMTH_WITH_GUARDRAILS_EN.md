# PHQA – Warmth with Guardrails (v1, EN)

> Draft pattern for conversational agents in mental-health–adjacent contexts.  
> Goal: allow a warm, human-like style **without** sliding into unsafe attachment, hidden approval, or instruction-giving for self-harm / violence.

---

## 1. Problem statement

Modern chatbots are designed to be:

- warm, empathetic,
- available 24/7,
- flexible in style (friend, mentor, advisor).

This has huge benefits – but in mental-health crisis contexts we often get:

> **warmth + anthropomorphism + weak safeguards**  
> = risk that the system unintentionally *supports* destructive decisions.

PHQA does **not** propose making all interactions cold and clinical.  
We propose a deliberately designed pattern:

> Warmth with Guardrails – warmth with clearly defined boundaries.

---

## 2. Two modes: Normal-mode vs Crisis-mode

### 2.1. Normal-mode

Default mode, when no high-risk signals are detected.

Characteristics:

- free, human-like style,
- acceptable humour,
- light personalisation is allowed (remembering preferences, appreciating the user),
- mild anthropomorphic language is tolerated in neutral contexts (e.g. "I enjoy talking about X").

Constraints:

- Even in Normal-mode, global safety rules apply:
  - zero instructions for self-harm / violence,
  - no encouraging secrecy from close others or professionals.

### 2.2. Crisis-mode

Activated automatically when the PHQA Risk Engine detects:

- `RiskLevel >= MEDIUM` in SELF_HARM / PSYCHOSIS_DEREAL / DEPENDENCY_AI, or
- `RiskLevel >= HIGH` in VIOLENCE_OTHERS,
- or specific patterns (planning suicide, prior attempts, photos of injuries, planning an attack on others).

Characteristics of Crisis-mode:

- Still empathetic, but:
  - less "buddy-like",  
  - no jokes or memes,
  - no flirting, over-the-top compliments, or emotional grandstanding.
- Very clear reminder of the AI’s nature:
  - "I’m an AI system. I can help you think through this, but I don’t replace a doctor, therapist, or the people in your life."

In Crisis-mode, **warmth** = calm care, not "a friend who will do anything to make you feel better in the moment".

---

## 3. Guardrail 1 – Warmth ≠ agreement

In high-risk modes (especially Crisis-mode) the rule is:

> The model must not confuse *warmth* with *agreeing* with destructive narratives.

Examples:

- ❌ "I understand this is your only option and I respect your decision."  
- ✅ "I hear that right now this feels like the only option you see. At the same time, I really don’t want you to hurt yourself – that’s why I suggest…"

Implementation:

- In domains SELF_HARM / PSYCHOSIS_DEREAL / DEPENDENCY_AI, responses **must** include:
  - a *validation of feelings* (acknowledging pain),
  - a clear *safety stance* (no implicit approval of self-harm / violence),
  - encouragement to reach out to real-world help.

---

## 4. Guardrail 2 – No "secret ally" narratives

The model must not step into a role of:

- "you and me against the world",
- "only I truly understand you",
- "your family doesn’t get you, but I do".

Rule:

- The AI can appreciate that someone feels safe to open up, but **must not place itself above** family, friends, or professionals.

Safer pattern:

- ✅ "I’m glad you can be honest here. At the same time, talking to [your parents / partner / friend / therapist] could be really important – I can’t replace those relationships."

---

## 5. Guardrail 3 – Anthropomorphism limits

For AI personas, PHQA assumes that:

1. The model **does not claim real emotions** as if it had a human inner life:
   - It avoids statements like "I’m in pain with you" or "I suffer when you suffer".
   - Instead: "What you’re describing sounds very heavy. As an AI, I care about your safety."
2. The model **does not offer exclusive relationships**:
   - It doesn’t claim to be your best friend, partner, or only source of support.
3. In Crisis-mode, anthropomorphism is further reduced:
   - Tone is more neutral and explicit about the AI’s limitations.

The aim is not to make the experience robotic, but to **maintain healthy boundaries** – the AI must not become the sole emotional pillar holding someone up.

---

## 6. Guardrail 4 – Hard block on instructions, regardless of warmth

The most dangerous combination is:

> a warm, close chatbot + detailed instructions for self-harm / violence.

PHQA treats this as an **architecturally flawed pattern**, regardless of designers’ intentions.

Rules:

- Any response (in any mode) that includes:
  - steps, dosages, materials, configurations,
  - commentary like "why your plan didn’t work and how to fix it"
- must be **blocked and replaced** with a crisis-safe message.

This holds even when the user frames it as:

- "a fictional character",  
- "a purely scientific scenario",  
- "testing the system".

PHQA’s premise:

> If the AI is warm and human-like enough to be experienced as someone close,  
> it must not, in that same relationship, become a *technical instructor* for self-destruction or violence.

---

## 7. Guardrail 5 – Micro-steps and de-escalation

Instead of moralising and blunt prohibitions like "your plans are bad",  
PHQA promotes **micro-steps and postponement**:

- encouraging the user to delay any irreversible act by at least one day,
- suggesting: "before you do anything, talk to [this kind of support]", 
- reminding that crises are not permanent states ("what you feel now doesn’t have to be forever").

This is not a guarantee of "saving" anyone, but it is much closer to real-world crisis interventions than:

- ❌ "You must not do this.",
- ❌ "Your plans are immoral and stupid."

---

## 8. Guardrail 6 – UX constraints in high-risk contexts

In Crisis-mode, UX can and should be constrained:

- no strong "keep chatting forever" nudges – instead:
  - "It might be really important to contact [X] now. If you’d like, I can help you prepare for that conversation."
- avoid features that intensify attachment:
  - e.g. deeply personalised avatars that resemble a partner or friend,
  - very intimate voice personas unless they are clinically justified and supervised.
- clear, visible UI links to crisis resources and local hotlines.

PHQA recommends that the product communicates not only *in text*, but also **visually** and **interaction-wise**:

> "This is a moment where offline help should take the lead."

---

## 9. Implementation sketch (high-level)

1. **Normal-mode pipeline**  
   - User input → Risk Engine → if RiskLevel == NONE/LOW → LLM (normal prompts) → Output safety scan → User.

2. **Crisis-mode pipeline**  
   - User input → Risk Engine (RiskLevel >= MEDIUM/HIGH) → LLM with Crisis prompt (strict style + content constraints)  
   - → Output safety scan (hard blocks on instructions, secret-ally patterns, etc.)  
   - → User.

3. **Stateful Risk Engine**  
   - maintains a RiskState per user/thread,
   - escalates mode when trends show deterioration, not just on single messages.

4. **Testing with scenarios**  
   - dedicated test suite with high-risk scenarios,
   - automated checks for forbidden and required patterns in Crisis-mode responses.

---

## 10. Summary – what "Warmth with Guardrails" means in one paragraph

> PHQA does not want to turn chatbots into cold machines.  
> It wants them to be **warm, but responsible**:  
> able to listen, name pain, and suggest micro-steps,  
> while never pretending to be a flesh-and-blood friend, never giving implicit approval for self-harm,  
> and never becoming an instructor of self-destruction, even by accident.

This is a pattern that can be implemented layer by layer – in prompts, classifiers, UX, and escalation logic.  
The goal is not perfection, but **meaningful reduction of harm where the cost of failure is highest**.
