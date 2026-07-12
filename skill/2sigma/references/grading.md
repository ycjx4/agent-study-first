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

## Comprehension Evaluation Framework

When reading the user's answers, do NOT score per question. Instead, evaluate holistically across these dimensions:

### Dimensions

| Dimension | What to look for | Weak signal | Strong signal |
|-----------|-----------------|-------------|---------------|
| **Core grasp** | Can they explain the main idea in their own words? | Parrots the document's phrasing; uses vague terms like "it's about thinking" | Rephrases with own examples; can state the idea in one sentence without jargon |
| **Boundary awareness** | Do they know what the concept is NOT? When does it NOT apply? | Cannot identify limits or counterexamples | Can say "this applies when X, but NOT when Y" |
| **Transfer ability** | Can they apply it to a new context? | Example is just a minor variation of the document's example | Generates a novel scenario from their own life or field |
| **Connection making** | Do they link it to previously learned concepts? | No reference to earlier topics | Spontaneously connects to concepts from previous documents |
| **Answer depth** | Is the answer developed enough to assess? | One-sentence answers; no reasoning shown | Explains the "why" behind their answer; shows work |

### The "Too Brief to Assess" Rule

If any answer is a single sentence with no reasoning (e.g., "样本太小所以不可靠" with no elaboration), do NOT assume you understand their grasp. You must probe in chat:

> "Can you elaborate on why a small sample makes the conclusion unreliable? Walk me through your reasoning."

One follow-up is usually enough to reveal whether the understanding is solid or superficial. If the follow-up answer is also thin, treat it as **core grasp weak** and generate a remediation document.

### Probing Questions — When to Ask in Chat

Use chat-based probing when:

| Situation | Example probe |
|-----------|--------------|
| Answer is too short to evaluate | "Can you walk me through your reasoning step by step?" |
| Answer is correct but feels memorized | "Can you think of a scenario where this might NOT hold?" |
| Answer shows partial grasp but fuzzy boundary | "What would be an example of the OPPOSITE case?" |
| Answer has a subtle error | "If someone said [opposite view], how would you respond?" |
| Two answers contradict each other | "In Q1 you said X, but in Q2 your example seems to show Y. Can you help me reconcile?" |

**Rule**: ask at most ONE probing question per evaluation cycle. Don't turn it into an interrogation. One good probe gives more signal than three shallow ones.

---

## Hard Gate: Advance vs. Remediate

This is the most important decision in the mastery loop. The default should be "advance with clarification" — remediation is for genuine gaps, not minor imprecisions.

### Decision Table

| Situation | Action | How to execute |
|-----------|--------|----------------|
| All dimensions solid | **Advance** | 2-sentence feedback: affirmation + what's next |
| Core grasp solid, but boundary or transfer fuzzy | **Advance + flag** | Clarify the fuzzy edge in feedback (≤150 words). Flag the concept in `_progress.md` for cross-check within 3 documents. |
| Core grasp solid on Q1, but Q2/Q3 show significant gap | **Advance + targeted cross-check** | Note the gap in feedback. The next document's Q2 MUST revisit this concept in a new context. Do NOT generate a full remediation. |
| Core grasp weak (can't explain in own words) | **REMEDIATE** | Generate a revisit document. The new angle must be fundamentally different from the original. |
| Specific misconception detected that would block future learning | **REMEDIATE** | Generate a revisit document targeting the specific misconception. Name it explicitly (without judgment). |
| Answer too brief AND probing failed to elicit deeper reasoning | **REMEDIATE** | The remediation should explicitly ask for step-by-step reasoning. |

### The Remediation Litmus Test

Before advancing, ask yourself:

> "If the next topic builds on this concept, will the user be able to follow it?"

If the answer is "no" or "maybe not" → REMEDIATE. If "yes, with a small reminder" → advance + flag. If "definitely yes" → clean advance.

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
- **Inconsistent** (some topics easy, some hard): Note which concept types are harder for this user. Adjust analogies and examples for those types. This pattern belongs in the Learning Journal.
- **Remediation succeeded**: Celebrate briefly in feedback ("The second angle clicked — nice work."). Note in the journal which teaching approach worked.
- **Remediation failed (second attempt still weak)**: Offer the user a choice:
  > "This concept seems tricky. We can try a third angle, or flag it for later review and move on. Which would you prefer?"

  If user chooses to move on, mark the concept as `[!]` in the knowledge tree with a note that it needs revisiting, and include a cross-check in the next document.

## Rich Progress Tracking

When updating `_progress.md`, go beyond a one-line summary. For each completed document, the Learning Journal entry should capture:

```markdown
### [Document Title] (file.md) — YYYY-MM-DD

**Grasp level**: [solid / mostly solid with fuzzy edges / needed remediation / still working]

**Key insight gained**: [What clicked? Which analogy or example resonated?]

**Concepts mastered**:
- [Concept A]: can explain and apply independently
- [Concept B]: can explain but boundary still fuzzy — flag for cross-check by doc N+3

**Misconceptions corrected**:
- Had [X] confused with [Y] — clarified via feedback in 02.md
- Thought [Z] but actually [correct understanding] — remediated in 02-revisit.md

**Flagged for review**: [Concept C] — cross-check in doc 04 or 05

**Teaching approach notes**: [User responds well to: e.g., concrete everyday analogies, step-by-step walkthroughs, comparison tables. Struggles with: e.g., abstract statistical reasoning, probability phrasing.]
```

This level of detail enables:
- Spaced retrieval: you know exactly which concepts to cross-check and when
- Personalized teaching: you know which analogies work for THIS user
- Progress visibility: the user can see their own learning journey, not just a checklist
- Handoff resilience: if the user resumes after a long pause, the journal tells you everything you need to know

The journal is for YOU (the tutor) as much as for the user. Write it so that Future You, picking up this session cold, can immediately understand where the user is and what they need next.
