# Remediation Patterns

When a user's core grasp is weak or a specific misconception is blocking future learning, do NOT advance. Re-teach from a fundamentally different angle. This reference provides patterns and examples.

## The Golden Rule of Remediation

**Never repeat the same explanation louder.** If it didn't click the first time, repeating it with slightly different words won't help. You must find a NEW entry point.

## Choosing a Different Angle

The original document used one approach. The remediation must use a DIFFERENT one:

| Original approach | Remediation approach (pick one you HAVEN'T used) |
|-------------------|--------------------------------------------------|
| Abstract definition → example | Concrete walkthrough → extract principle |
| Everyday analogy | Domain-specific analogy (from user's field) |
| Visual/spatial metaphor | Temporal/narrative metaphor |
| Single clean example | Compare/contrast TWO examples side by side |
| Prose explanation | Table or structured comparison |
| "What it is" | "What it is NOT" (boundary-first approach) |
| Top-down (big picture → details) | Bottom-up (start with a specific puzzle → build up) |

## Common Misconception Types & Remediation Strategies

### Type 1: Concept Blur (two related ideas merged into one)

**Signal**: User uses term A and term B interchangeably, or can't articulate the difference.

**Remediation strategy**: Side-by-side comparison table.

Example: User confuses "启发式问题" with "目标问题".

```markdown
# Revisit: 你到底在回答哪个问题？

## What wasn't quite clicking
"目标问题"和"启发式问题"的区分还不太清晰。

## Let's try a different approach

我不想从定义开始。我想让你看一个场景，然后对比两个版本。

**场景**：朋友创业，问你"我该不该投资这个项目？"

| 如果你的大脑在回答... | 你实际在评估... | 这是... |
|---|---|---|
| "这个项目五年内的预期回报率是多少？成功率多大？有哪些风险？" | 需要数据、概率、比较 | **目标问题**（真正的答案） |
| "这个创始人说话有没有感染力？他的演示让我兴奋吗？" | 情绪、印象、直觉感受 | **启发式问题**（替代问题） |

目标问题 ≈ 你真正应该回答的。启发式问题 ≈ 你的系统1偷偷换给你的简单版。

两者的关系不是"一个正确一个错误"。启发式问题常常包含有用信号（创始人确实该有感染力），但它只是目标问题的一小部分线索，不能直接替代。

## A quick check
你决定选哪门课时，目标问题是什么？你的系统1可能偷换成什么启发式问题？
```

### Type 2: Boundary Blindness (knows what it IS, not what it ISN'T)

**Signal**: User applies the concept correctly in the given example but overgeneralizes — doesn't see where it stops applying.

**Remediation strategy**: Counterexample-first teaching.

Example: User thinks regression to the mean means "everything evens out."

```markdown
# Revisit: 回归均值 — 它到底什么时候成立？

## What wasn't quite clicking
你把回归均值理解成了"所有极端都会自动回到正常"——这个理解窄了一点点。

## Let's try a different approach

回归均值不是魔法。它只在一个条件下成立：**结果中有随机成分**。

想想这三个场景：

| 场景 | 有随机成分吗？ | 下次会回归均值吗？ |
|---|---|---|
| 投篮：平时70%命中率，今天10投9中 | 有（运气、状态波动） | 很可能回到~70% |
| 身高：你比父母都高10cm | 有（基因表达的随机性） | 你的孩子可能回到家族均值 |
| 一道数学题：你算对了，答案是42 | **没有**（这是确定性计算） | 不会——正确答案永远是42 |

回归均值不是"好的会变差、差的会变好"。它是一个统计现象：**包含随机性的极端观测值，下一次更可能靠近平均值。**

## A quick check
一个学生连续三次考试都是95分以上。请判断：下次考试"很可能回归均值"吗？为什么？
（答案：不一定。如果这个学生确实能力很强，95分是ta的真实水平而非随机极端值，就不会回归。）
```

### Type 3: Surface Understanding (can parrot but can't apply)

**Signal**: User's answer uses the document's own words with minimal rephrasing. Cannot generate a novel example. The probing question reveals they can't transfer.

**Remediation strategy**: Walkthrough with forced generation.

```markdown
# Revisit: 用你自己的经历重新理解[概念]

## What wasn't quite clicking
你能说出定义，但在应用到自己生活中的场景时还不太顺。

## Let's try a different approach

这次我不给例子。我来引导你做一个练习。

**Step 1**: 回想过去24小时内，你做过的3个快速判断。
（写下来）

**Step 2**: 对每个判断，问自己：这里面哪个部分是系统1？哪个部分是系统2？

**Step 3**: 其中有没有一个判断，你后来发现是错的？那个错的判断里，系统1用的"快捷方式"是什么？

这个过程比任何我给的例子都更有用，因为你在用你自己的素材。

## A quick check
从你Step 3的那个例子中，如果你当时启动了系统2，你会多问自己什么问题？
```

### Type 4: Emotional Resistance ("This feels wrong / I don't buy it")

**Signal**: User's answer shows they understand the concept intellectually but are resisting its implications. Often appears in Q3 (challenge) answers.

**Remediation strategy**: Validate, then explore.

Acknowledge the resistance before re-explaining. The user needs to feel heard before they can reconsider.

Example: User resists the idea that intuition is often wrong.

```markdown
# Revisit: 直觉 — 不是敌人，是不可靠的朋友

## What wasn't quite clicking
你对"直觉不可靠"这个说法有保留——而且你的保留有道理。

## Let's try a different approach

你说得对：如果直觉总是错，人类早就灭绝了。我们的祖先靠直觉躲避危险、识别人心、判断天气。直觉大多数时候有用，而且是免费的。

问题不在于直觉"有害"，而在于它有**盲区**。就像你的眼睛在黑暗中很好用，但在某些光学错觉面前会被骗。直觉的盲区恰好在统计、概率和复杂系统里——这些恰好是现代决策中最需要谨慎的领域。

所以学习这些偏见，不是为了让你不再相信直觉，而是让你知道直觉在什么条件下容易出错。就像你知道自己近视，就在开车时戴上眼镜。你不讨厌自己的眼睛，你只是知道什么时候需要辅助。

## A quick check
想想一个你信任直觉的场景（比如判断朋友的情绪）。再想想一个你可能不该只靠直觉的场景（比如选投资或选专业）。它们的区别在哪里？
```

## Remediation Document Checklist

Before generating a remediation document, verify:

- [ ] This uses a DIFFERENT analogy/entry point from the original (check the original document)
- [ ] The specific misconception is named (without judgment) in "What wasn't quite clicking"
- [ ] "A quick check" directly targets the gap (a correct answer PROVES the gap is filled)
- [ ] The new Q1-Q3 are new questions, not rephrased versions of the original questions
- [ ] The tone is "let's figure this out together" not "you got this wrong"
- [ ] The document is NOT just the original document with different wording — it's a genuinely new approach

## When Remediation Doesn't Work

If the user completes a remediation document and STILL shows weak core grasp:

1. **Don't generate a third identical attempt.** Another round of the same pattern won't help.

2. **In chat, ask the user directly:**
   > "This concept seems to be a sticking point. Can you tell me in your own words what part feels confusing? Sometimes the way I'm explaining doesn't match how you're thinking about it."

3. **Offer a choice:**
   > "We can try one more angle, or we can flag this and move on. Sometimes concepts click later when you see them in a different context. Which would you prefer?"

4. **If user chooses to move on**, mark in `_progress.md`:
   ```
   - [!] [Concept] (01.md, 01-revisit.md) — still fuzzy after two attempts. Flagged for cross-check in future documents.
   ```
   Then include this concept in the NEXT document's Q2 or Q3 as a cross-check. Sometimes a concept only clicks when seen alongside related ideas.

## Escaping Remediation Loops

The worst outcome is a user stuck on the same topic for 3+ documents, getting frustrated. Prevention:
- Remediation documents should be SHORTER than regular documents (~60% of normal length)
- "A quick check" is ONE question, not three — make it fast
- If the second remediation also fails, the default should be "move on with flag" not "try again"
- Never make the user feel like they're failing. The frame is always: "This concept is tricky to explain. Let me try differently."
