<p align="center">
  <img src="docs/images/logo.png" alt="2sigma" width="120"/>
</p>

<h1 align="center">2sigma</h1>

<p align="center">
  <b>Your AI private tutor. Learn anything 10x faster.</b><br/>
  AI 私教 · 十倍速进入任何领域
</p>

<p align="center">
  <a href="README_zh.md">中文版</a> · <a href="#install">Install</a>
</p>

---

> **1984**, educational psychologist Benjamin Bloom published a finding that shook the academic world: a student who receives **1-on-1 tutoring** with **mastery-based progression** outperforms **98% of students** in traditional classrooms. He called it the **2-sigma problem** — because the effect was two standard deviations above the mean.
>
> The catch? One tutor per student doesn't scale. For decades, this remained an unsolved problem. **Until now.**

---

## What is this?

**2sigma** is a skill for [Claude Code](https://docs.anthropic.com/en/docs/claude-code), [Codex](https://openai.com/index/codex/), and other AI agents. It turns your AI into a **Bloom-style private tutor** that:

- **Asks YOU questions** instead of waiting for you to ask — because when you're learning something new, you don't know what you don't know
- **Writes structured learning documents** to your local files — not trapped in a chat window that expires
- **Tracks concept-level evidence** — pick up accurately without confusing a teaching failure with your own learning gap
- **Adapts to your level** — struggling? it slows down. breezing through? it challenges you

### Why not just chat with AI?

Because chatting with AI gets the learning loop **backwards**.

|  | Traditional AI Chat | 2sigma |
|---|---|---|
| Who drives? | You ask, AI answers | **AI tutors, you respond** |
| Context | Chat dies after long conversations | **Files persist forever** |
| Progress | None. Start over every session. | **Current snapshot + append-only evidence log** |
| Difficulty | One-size-fits-all | **Adapts to YOUR comprehension** |
| Science | None | **Bloom's 2-sigma method** |

<p align="center">
  <img src="docs/images/comparison.png" alt="Traditional AI chat vs 2sigma" width="700"/>
</p>

## How it works

<p align="center">
  <img src="docs/images/learning-loop.png" alt="2sigma learning loop" width="500"/>
</p>

1. You say: **"Help me learn quantum computing"**
2. AI asks about your background and level
3. Generates `01.md` — written like a friend explaining, not a textbook lecturing
4. You answer questions at the end (designed to test *understanding*, not *memory*)
5. AI first checks that each scored question was actually taught, then evaluates evidence by concept
6. It records the result and generates the next lesson, a targeted supplement, or a revisit as appropriate
7. Repeat until mastery

## 6 Learning Modes

<p align="center">
  <img src="docs/images/six-modes.png" alt="Six learning modes" width="700"/>
</p>

| Mode | Trigger | What it does |
|------|---------|-------------|
| **Paper Reading** | "Help me read this paper" + PDF/DOI | Breaks down a research paper into digestible pieces |
| **Concept Learning** | "What is X?" / "Explain X" | Takes one concept from zero to mastery |
| **Domain Introduction** | "I want to learn about X field" | Builds a complete knowledge map with learning roadmap |
| **Tech Stack** | "How do I learn X framework?" | Understands a tool's philosophy and core usage |
| **Code Repo Reading** | Provide a GitHub URL or local path | Reads a codebase like reading a paper — architecture first, details on demand |
| **Exam Review** | "Quiz me on this book" + PDF/textbook | Progressive testing with weak-area drilling — feed it a whole book |

## Quality-first mastery

Most AI "tutors" ask you to recite what you just read. That's useless.

2sigma designs questions with an explicit teaching-and-evidence contract:

1. **Core** — directly tests a method the lesson has taught.
2. **Transfer** — applies the same method in a genuinely changed context.
3. **Exploration** — optional synthesis beyond the lesson; it never affects mastery.

Before a question can affect mastery, the tutor traces every required operation back to an execution rule and a worked example or guided practice. Missing teaching becomes an **instruction gap**; an ambiguous or out-of-scope question becomes an **assessment gap**. Neither is recorded as a learner failure.

### Concept states, not a single pass/fail

Each concept has its own evidence-backed state:

- `learning` — first teaching cycle; evidence is not sufficient yet
- `provisional` — directionally right, but transfer, boundaries, expression, or confidence is not stable
- `solid` — can explain, transfer, and identify a boundary with no substantive unresolved confusion
- `durable` — remains stable on a delayed, changed-context retest

Explicit confusion vetoes `solid` and triggers one focused diagnostic question when the evidence is ambiguous.

<p align="center">
  <img src="docs/images/progress-tree.png" alt="Knowledge tree" width="500"/>
</p>

### Durable, inspectable records

Course files have separate responsibilities:

- `_progress.md` is a short current snapshot: concept states, active confusion, open gaps, due reviews, and the next safe action.
- `_learning_log.md` is an append-only evidence log with answer references, coverage status, confidence, diagnosis, and review plans.
- `_user_profile.md` contains only stable preferences and validated teaching patterns.

At a normal restart, the tutor reads the profile, the snapshot, and only log events for the current and prerequisite concepts. It does not default-read prior lessons or the full history.

<a name="install"></a>

## Install

#### Claude Code

Or just tell Claude Code:

> Help me clone `https://github.com/chenly255/2sigma` to `~/.claude/skills/2sigma/`

Or run it yourself:

```bash
git clone https://github.com/chenly255/2sigma.git ~/.claude/skills/2sigma
```

#### Codex

Tell Codex:

> Clone `https://github.com/chenly255/2sigma` to `~/.codex/skills/2sigma/`

Or run it yourself:

```bash
git clone https://github.com/chenly255/2sigma.git ~/.codex/skills/2sigma
```

#### Other agents (Trae, etc.)

```bash
git clone https://github.com/chenly255/2sigma.git
# Copy SKILL.md and references/ to wherever your agent reads skill files
```

### PDF support (optional)

To feed PDFs (papers or textbooks), install [uv](https://docs.astral.sh/uv/):

```bash
curl -LsSf https://astral.sh/uv/install.sh | sh
```

First PDF conversion auto-downloads models. Subsequent runs use cache.

## First time setup

On first use, the skill asks a few questions to personalize your experience:

- **Language** — responds in whatever language you prefer
- **Your background** — so it picks analogies that click for you
- **Document length** — short (600w), medium (1000w), or long (1800w)
- **Paper source** — Zotero, PDF files, or online search

Saved once. Never asked again unless you want to change them.

## Extending

Want to add a new learning mode? See [references/extending.md](references/extending.md). Define trigger words, document sequence, and style rules. The mastery loop handles the rest.

## Project Structure

```
2sigma/
├── SKILL.md                  ← Core workflow (platform-agnostic)
├── references/
│   ├── onboarding.md         ← First-time user setup
│   ├── learning-modes.md     ← 6 mode specifications
│   ├── lesson-design.md      ← Coverage maps, question types & alignment
│   ├── grading.md            ← Concept states, evidence & advancement
│   ├── progress-tracking.md  ← Snapshot, append-only log & targeted reads
│   ├── remediation.md        ← Learner/instruction/assessment gap actions
│   ├── writing-style.md      ← Tone, analogies, terminology
│   └── extending.md          ← How to add new modes
└── scripts/
    └── pdf_to_sections.py    ← PDF → per-section markdown (uv + Marker)
```

## Author

**Liying Chen** — PhD student @ [Sun Yat-sen University](https://www.sysu.edu.cn/) & [Guangzhou National Laboratory](https://www.gzlab.ac.cn/)

## License

MIT

---

<p align="center">
  <b>Stop satisfying AI's ego. Let AI serve yours.</b>
</p>
