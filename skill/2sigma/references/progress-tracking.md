# Progress Tracking

Use three Markdown records with mutually exclusive responsibilities. The current-state snapshot and the evidence history are separate layers; the profile is stable learner context.

| File | Contains | Must not contain |
|---|---|---|
| `_progress.md` | current position, concept-state rows, active confusion, open gaps, due reviews, current teaching strategy, handoff summary | chronological per-lesson journal |
| `_learning_log.md` | append-only assessment and teaching evidence events | mutable current-state summary or copied full lessons |
| `_user_profile.md` | stable background, goals, preferences, repeatedly validated teaching patterns | one-off confusion or current mastery state |

The state names and mastery rules come only from [grading.md](grading.md); gap sources and their teaching actions come only from [remediation.md](remediation.md). This file defines storage and access, not a second state machine.

## `_progress.md`: Current Snapshot

Keep this file short enough to read at every course start. Replace stale current-state facts instead of accumulating history. Use exactly these nine fields in the concept table:

```markdown
# [Topic] Progress

> Last updated: YYYY-MM-DD HH:MM

## Current position

- Current branch:
- Current document:
- Next dependency:

## Concepts

| Concept ID | State | Tutor confidence | User confidence | Latest evidence | Residual confusion | Coverage | Next action | Review due |
|---|---|---|---|---|---|---|---|---|
| concept.id | learning | medium | not recorded | EVT-YYYYMMDD-NNN; file.md#answer | none reported | pass | aligned changed-context check | before NN.md |

## Active confusion

- [Concept ID]: [current substantive or low-risk confusion]

## Open gaps

- [Concept ID / question reference]: instruction gap | assessment gap — [repair action]

## Due reviews

- [Concept ID]: [deadline and changed-context retest]

## Current teaching strategy

[Only the strategy currently in use.]

## Handoff summary

[A compact statement of what is ready, what is blocked, and the next safe action.]
```

`Latest evidence` points to the newest relevant event and, when needed, its precise answer location. `Coverage` records the applicable reverse-alignment result; it does not replace the detailed event. `User confidence` is `high`, `medium`, `low`, or `not recorded`. For old evidence that did not collect confidence, write `not recorded`; never infer it from answer quality, tone, mastery state, or tutor confidence.

Do not put per-document narrative, completed-event chronology, or copied lesson text in `_progress.md`. Older state is recoverable from the append-only log.

## `_learning_log.md`: Append-Only Evidence

Create the file with this schema marker and event shape. Preserve the field names exactly:

```markdown
schema_version: 2

### EVT-YYYYMMDD-NNN

- Timestamp:
- Document:
- Concept IDs:
- Question type:
- Answer reference:
- Evidence summary:
- User confidence:
- Residual confusion:
- Coverage status:
- Gap source:
- Tutor confidence:
- Decision:
- Teaching action:
- Outcome:
- Next review:
```

Events are append-only: never edit, reorder, or delete an earlier event to make it match the current snapshot. If an earlier record is wrong, append a correction event that cites it. Use a stable event ID, one or more stable concept IDs, and a precise `Answer reference` such as `07.md#q2-answer` or a line/section anchor.

Full learner answers remain in course documents. The log stores the precise reference, only the short excerpt needed to preserve diagnostic evidence, and the reasoning needed for coverage, gap-source, state, teaching-action, and review decisions. It must not copy a full answer or lesson. If user confidence was not explicitly collected, record `not recorded`; do not backfill or infer it.

## `_user_profile.md`: Stable Learner Context

Keep only information expected to guide many future lessons:

```markdown
# User Profile

- Language:
- Background:
- Goals:
- Length preference:
- Interaction preferences:
- Repeatedly validated teaching patterns:
```

Do not add a one-off confusion, a current concept state, or a teaching tactic that worked once. Update `Repeatedly validated teaching patterns` only after the pattern has succeeded across multiple teaching cycles.

## Targeted Read Contract

At a normal course start:

1. Read `_user_profile.md`.
2. Read the short `_progress.md` snapshot.
3. Take the current and prerequisite concept IDs from the snapshot, then search `_learning_log.md` for matching event headings and `Concept IDs` fields. Read only those relevant events.

Read the full `_learning_log.md` only for an explicit audit or migration. Never default-read document N, previous lessons, history lessons, or the full log before generating N+1. If a decision requires the learner's exact prior answer, open only the course-document section named by `Latest evidence` or `Answer reference`; do not browse historical course documents.

For a new course with no records, create the three files from these templates. For an existing course, do not migrate or rewrite records merely because this schema exists; migration is a separate, explicit operation.

## Write Ordering

For every evaluation or teaching decision, use this irreversible order:

1. Finish coverage/alignment, gap-source, concept-state, teaching-action, and next-review decisions.
2. Append the complete evidence event to the `schema_version: 2` `_learning_log.md`; the schema marker remains once at the top of the file.
3. Confirm that the append succeeded.
4. Only then update `_progress.md` to publish the new current snapshot.

If the log append fails, do not publish the new snapshot state. Retry or report the write failure while leaving `_progress.md` unchanged. This prevents a current state from existing without its evidence trail.

Update `_user_profile.md` independently and only when a stable preference or teaching pattern has been repeatedly validated; it is never part of the per-lesson snapshot update.
