# Question Design & Comprehension Evaluation

This is the core of the mastery learning loop. Questions are not quizzes — they are tools for deepening understanding and diagnosing comprehension gaps.

## Question Design Philosophy

**A good question makes the user THINK, not RECALL.**

- Never ask questions that can be answered by copying text from the document.
- Every question should require the user to process, rephrase, or apply what they learned.
- Questions serve two purposes: (1) help the user consolidate understanding, (2) give you signal about their comprehension level.

## Cross-Difficulty Pattern

Every question set follows a "confidence sandwich" to maintain motivation:

### Q1: Accessible (Confidence Builder)

The user should be able to answer this if they understood the document. Requires rephrasing, not copying.

Good examples:
- "Explain [concept] to a friend in your own words."
- "If someone asks you what [topic] is about, what would you say?"
- "What problem does [concept] solve? Why does it matter?"

Bad examples:
- "What is the definition of [X]?" (pure recall)
- "List three features of [X]." (copy-paste)

### Q2: Application (Deeper Understanding)

Requires using the concept in a new context the document didn't directly address.

Good examples:
- "Imagine you encounter [new scenario]. How would [concept] apply here?"
- "[A] and [B] seem similar. What's the key difference, and when would you choose one over the other?"
- "What would happen if [condition] changed? How would the outcome differ?"

### Q3: Challenge (Optional — Synthesis/Evaluation)

Only include when the topic warrants deeper thinking. Skip for simpler topics or early-stage documents.

Good examples:
- "What do you think is the biggest limitation of [approach]?"
- "If you combined [concept A from doc 2] with [concept B from this doc], what possibilities open up?"
- "Someone claims [plausible but wrong statement]. Do you agree? Why or why not?"

## Motivation-Aware Design

- **After a hard topic**: Make Q1 even easier than usual. The user needs a win.
- **After the user struggled**: Start the next set gentler. Don't punish.
- **Occasionally**: Include a fun/real-life connection question. Learning should feel rewarding.
- **Never**: Put two hard questions back-to-back. Never start with the hardest question.
- **Exam Review mode**: Can have more questions (5-8) with wider difficulty range, since the goal is testing.

---

## Concept-Level Comprehension Evaluation

Evaluate evidence by concept ID, never by a document-level overall impression and never by treating every question as equally valid. First consume each question's coverage status and question type from [lesson-design.md](lesson-design.md). A document can contain several concept states at the same time; no whole-document pass may overwrite concept-level evidence.

### Mandatory Reverse-Alignment Gate

Execute the authoritative [lesson-design.md](lesson-design.md) interface before reading a learner answer as evidence. For every procedural or design question, first derive the minimally acceptable answer and enumerate every required decision, step, field, evidence criterion, and comparison as O1...On. Complete this internal trace without aggregating operations:

| Operation | Required performance | Execution-rule citation | Demonstration/guided-practice citation | Coverage result |
|---|---|---|---|---|
| O1...On | One row per required operation | Lesson citation or `missing` | Lesson citation or `missing` | `pass` only when both citations exist |

Apply the result mechanically:

1. A goal, principle, or high-level checklist proves only topic presence. It is not execution support, and the question text is not teaching evidence.
2. Every row passes only when the lesson both tells the learner how to perform or choose that operation **and** demonstrates it inside a complete method or guided practice.
3. If any mastery-bearing row lacks either form, stop learner grading for the entire question: record `instruction gap`, exclude it from learner state and misconception records, and repair teaching before using an aligned new question.
4. If the question is out of scope, ambiguous, mismapped, or unable to distinguish understanding, record `assessment gap`, exclude it, and repair or retire the question.
5. Only a fully passing trace permits learner evaluation or a learner-directed probe.

For example, a four-step list that merely says "record the adjustment" and "compare with real outcomes" is not a demonstration of which fields to record, how to preserve the baseline, or how to perform the comparison. Do not infer that missing method from the learner's answer and then blame or probe the learner for not supplying it.

The authoritative coverage interface remains in [lesson-design.md](lesson-design.md); the authoritative gap definitions and teaching actions remain in [remediation.md](remediation.md).

### Authoritative Concept State Table

This is the only concept-state definition table in the skill.

| State | Exact definition |
|---|---|
| `unseen` | The concept has not yet been taught. |
| `learning` | The concept is in its first teaching cycle and there is not yet enough valid evidence. |
| `provisional` | The learner is directionally correct, but boundary, transfer, expression, or confidence is not stable. |
| `remediating` | A learner gap has been confirmed and the concept is being re-taught from a different angle. |
| `solid` | The learner can currently explain, transfer, and identify a boundary, with no substantive residual confusion. |
| `durable` | Understanding remains stable on a delayed, changed-context, unprompted retest. |
| `deferred` | Understanding remains unstable after multiple interventions and the learner explicitly agrees to postpone it. |

Keep a separate state, evidence summary, confusion record, next action, and retest deadline for every concept ID. One lesson may therefore contain `solid`, `provisional`, and `remediating` concepts simultaneously.

### The `solid` Conjunction

A concept is `solid` only when **all** of the following are simultaneously true for that concept ID:

1. Coverage is complete and the mastery-bearing questions are aligned under [lesson-design.md](lesson-design.md).
2. The learner explains the core mechanism in their own words.
3. The learner transfers it to a genuinely changed context.
4. The learner identifies at least one boundary, counterexample, or inapplicable condition.
5. The evidence is developed enough to rule out guessing, copying, or mere restatement.
6. No substantive residual confusion is reported, and any low confidence has been diagnosed.
7. No unresolved `instruction gap` or `assessment gap` remains for the concept.

For conjunct 3, compare the assessment scenario with the lesson's worked examples. Reusing the same roles, facts, or decision problem is rehearsed application, not a genuinely changed context; without other transfer evidence, the highest supported state is `provisional`.

Failure of any conjunct means the concept is not `solid`; evidence for another concept or a favorable impression of the document cannot substitute. `solid` can become `durable` only after a later, changed-context, unprompted retest succeeds. Same-session correction, a prompted answer, or success immediately after re-teaching is not durable evidence.

### Required Learner Inputs

Collect and preserve these two fields in every evaluation cycle:

```markdown
User confidence: high | medium | low | not recorded
Most confusing point: [free text | none reported]
```

Confidence is evidence about stability, not a self-awarded mastery state. High confidence cannot override weak performance. Low confidence triggers one targeted diagnostic and must be resolved or explained before `solid`; it does not automatically prove a learner gap. `not recorded` must remain explicit rather than being invented.

A learner's report of **substantive confusion vetoes `solid`** for the affected concept even when their written answer is broadly correct. Run one targeted diagnostic and use the gap-source contract in [remediation.md](remediation.md):

Self-report alone sets no gap source. An already-collected, reverse-aligned answer independently demonstrates a failure only when its reasoning or observable execution rules out alternative interpretations under the "Too Brief to Assess" rule; a terse field list, omission, or ambiguous label remains multi-interpretable. Without that independent evidence, retain the evidence-supported learner state (never `solid`; use `provisional` when direction is correct but stability is affected), choose `probe`, and use the single targeted diagnostic. Only when independent evidence meets that threshold and gap triage excludes instruction and assessment gaps may you set `remediating` without another probe.

- If the core mechanism is still unclear, stop new content that depends on it. A confirmed learner gap sets `remediating`; an instruction or assessment gap leaves learner state unchanged while the teaching or question is repaired.
- If the core is correct but boundary, transfer, expression, or confidence is unstable, set `provisional` and schedule a changed-context retest within the next two documents.
- If the issue is only terminology or phrasing, clarify it and record a low-risk residual issue. This removes the confusion veto only when every `solid` conjunct is otherwise satisfied.

Do not infer the gap source from confidence or confusion alone. Reverse alignment and gap triage happen first.

### The "Too Brief to Assess" Rule

After the relevant item has passed reverse alignment, if the learner evidence could still support multiple interpretations, ask at most one targeted probe in chat before selecting a learner state or gap source. A one-sentence answer with no reasoning does not prove understanding or misunderstanding. If the probe remains thin, use coverage and alignment to decide whether the missing evidence is a learner, instruction, or assessment gap; do not default to learner remediation.

Useful probes include:

- Too short to evaluate: "Can you walk me through your reasoning step by step?"
- Correct but possibly memorized: "Can you give a case where this would not hold?"
- Fuzzy boundary: "What would be an opposite or counterexample case?"
- Contradictory answers: "How do you reconcile your first answer with this example?"

### Action and Dependency Gate

- **Clean advance** only when every prerequisite concept for the next content is `solid` or `durable`.
- **Advance + flag/cross-check** only for a non-blocking `provisional` concept; its retest is due within the next two documents.
- **Probe** only after alignment passes and one targeted question can distinguish insufficient learner evidence, substantive confusion, or learner-gap status.
- **Remediate** only for a confirmed `learner gap`; set the affected concept to `remediating` and follow [remediation.md](remediation.md).
- Set `deferred` only after multiple interventions and explicit learner agreement. A critical prerequisite still blocks dependent content; move only to an independent branch.

Instruction and assessment gaps use their own teaching actions and have no negative learner-state effect. Never use a question excluded by reverse alignment to lower status, create a learner misconception, or schedule learner remediation.

---

## Feedback Format

### For Clean Advance (all solid)

```markdown
## Previous Answers Feedback

**Overall**: [One sentence affirming understanding.]

→ This document advances to [next topic].
```

### For Advance + Clarification (minor fuzziness)

```markdown
## Previous Answers Feedback

**Overall**: [One sentence — what they got right.]

**What clicked**: [1 sentence affirming their strongest answer.]

**One thing to sharpen**: [The specific fuzzy edge, corrected concisely. Max 3 sentences. Give the correct understanding, not just "this is wrong."]

→ This document advances to [next topic]. We'll revisit [flagged concept] in a future check.
```

### For Remediation (do NOT advance — generate a revisit document instead)

Do NOT put this at the top of the next topic's document. Generate a separate `XX-revisit.md`.

In chat, briefly say:

> "Your answer to [Q#] shows that [specific concept] hasn't quite clicked yet. I've prepared a different explanation. Read [XX-revisit.md] and try the new questions."

---

## 2-Sigma Adaptive Pacing

Like a 1-on-1 tutor, adapt to THIS user:

- **Breezing through**: Increase depth, add harder Q3s, cover more per document. Consider asking the user if they want to accelerate.
- **Struggling**: Slow down, more examples, easier Q1, consider splitting the next topic into two documents. Use chat probes more liberally to diagnose where exactly the block is.
- **Inconsistent** (some topics easy, some hard): Note the evidence in `_learning_log.md`. Add a preference to `_user_profile.md` only after the pattern is repeatedly validated; adjust analogies and examples accordingly.
- **Remediation succeeded**: Celebrate briefly in feedback ("The second angle clicked — nice work."). Record the evidence event, and promote the teaching approach to the profile only if repeated cycles validate it.
- **Remediation failed (second attempt still weak)**: Offer the user a choice:
  > "This concept seems tricky. We can try a third angle, or postpone it and move to an independent branch. Which would you prefer?"
  
  Only if the user explicitly chooses postponement, set the concept to `deferred`, record what remains unstable, and schedule a future retest. If it is a prerequisite, do not advance to dependent content; offer only an independent branch.

## Rich Progress Tracking

Use [progress-tracking.md](progress-tracking.md) as the single authority for record roles and templates. Store current concept state, residual confusion, open gaps, due reviews, and next action in the short `_progress.md` snapshot; store chronological assessment and teaching evidence as append-only schema v2 events in `_learning_log.md`; store only stable learner context and repeatedly validated teaching patterns in `_user_profile.md`.

Append the evidence event before publishing the new snapshot. If the append fails, `_progress.md` must remain unchanged. Normal startup reads are profile + short snapshot + concept-ID-targeted events; full-log and historical-course reads are not default context.
