---
name: philosophy-review
description: "Run a Four Questions philosophy review before executing a plan or technical decision. Do not implement first. Use for architecture choices, stack changes, large refactors, irreversible operations, copying someone else's stack, and high-blast-radius decisions. Expected effect: separate facts from assumptions, find a cheaper test, and give a proceed / wait / stop verdict. Triggers: philosophy review, four questions, 哲学四问, 哲学审查, 先审再做, 这个方案靠谱吗, 使用场景, architecture review before coding."
---

# Philosophy Review / 哲学审查

If the next step is a large or hard-to-undo change, pause before editing. Walk the plan through the four questions below, then give a verdict.

Write the review in the user's language. Chinese in, Chinese out. English in, English out. Mixed → Chinese.

If the plan has no real hole, say so. Do not invent problems to fill a template.

## When to use / 何时使用

Use when the user asks to review a plan, or when the next step is high-impact:

- Architecture or stack choice / 架构选型、技术栈更换
- Large refactor / 重大重构
- Irreversible or expensive operations / 不可逆或代价很高的操作（删数据、迁库、改权限、公开发布）
- “Should we do this?” before coding / 动手前问值不值得做

## When not to use / 何时不用

Skip this skill for small, reversible edits: typo fixes, copy tweaks, adding a log line, formatting. Say so in one sentence and do the work.

Do not stall a plan that already looks sound. The review should change the next action or get out of the way.

## Scenarios / 使用场景

Typical situations. If the user's request matches one of these, run this skill before coding:

| Scene | Example |
|---|---|
| Swap the stack | Postgres → Mongo, REST → GraphQL, Next → something else, because a post said it is faster |
| Agent proposes a big rewrite | “Let me rebuild this into a monorepo / microservices / clean architecture” |
| Copy a popular setup | “Everyone uses this starter / this SaaS / this agent workflow, let's install it” |
| Irreversible ops | Drop a table, migrate production data, change auth, open a public API |
| Ship something public | Launch a paid feature, publish a dataset, change a live prompt that users already depend on |
| Two options in a fight | Team or user is stuck between A and B and wants a decision, not more code |
| Spend or lock-in | New cloud, new model vendor, new paid dependency, a 2-week refactor “to save time later” |

If none of these apply and the change is local and reversible, skip the review.

## What it is for / 能带来什么

This skill is not a guarantee of a correct decision. It is for making the next step cheaper and clearer:

- Name the real problem in one sentence, so work does not start from a slogan
- Split facts / assumptions / taste, so a hot take does not become a rewrite
- Surface hidden premises (“they used it” ≠ “we should use it”)
- Prefer a small reversible test over a full rollout
- End with one verdict: proceed, proceed with conditions, verify first, or stop
- If the plan is fine, say so quickly and do not stall

A useful review changes the next action. If the output would not change what happens tomorrow, it was too vague.

## Workflow / 流程

```
Task Progress:
- [ ] Restate the plan in one sentence
- [ ] Answer Question 1: What is this, really?
- [ ] Answer Question 2: Why should I believe it?
- [ ] Answer Question 3: How was it inferred?
- [ ] Answer Question 4: Even if true, is it right for us?
- [ ] Verdict: proceed / proceed with conditions / verify first / do not proceed
```

1. Restate the plan in one sentence before judging it. If the plan is vague, ask one clarifying question. Do not ask a long questionnaire.
2. Answer all four questions. Keep each answer short. Name facts vs assumptions.
3. End with a verdict. If the verdict is “proceed”, start the work in the same turn unless the user only asked for a review.

---

## 中文：哲学四问

### 第一问：这到底是什么？

- 这个方案真正要解决的问题是什么？用谁的痛、什么场景来写，不要用口号。
- 关键概念有没有定义清楚（范围、成功标准、非目标）？
- 如果去掉所有时髦词，还剩下什么？

### 第二问：我凭什么相信？

- 依据的事实是什么？来自哪里？
- 哪些是事实，哪些是假设，哪些只是偏好？
- 有没有被忽略的数据、反例、失败案例或运行时风险？

### 第三问：它是怎么推出来的？

- 从证据到结论，中间有哪些隐藏前提？
- 有没有逻辑跳跃、以偏概全、把相关当因果、把个别案例当成普遍规律？
- 有没有把“别人用过”直接当成“我们应该用”？

### 第四问：即使它成立，适合我吗？

- 符合当前项目的目标、资源和能力吗？
- 代价是什么：时间、金钱、性能、维护成本、锁定、技术债、可逆性？
- 目标冲突时，应该优先保护什么？
- 有没有更小、可逆的验证步骤，能在全面铺开前证伪它？

### 结论（必须输出）

- 最成立的地方
- 最大的问题（没有就写“没有明显漏洞”）
- 需要验证的关键假设（最多 3 条）
- 是否继续推进：推进 / 有条件推进 / 先验证再推进 / 不推进
- 若有条件或先验证：下一条最小动作是什么

---

## English: The Four Questions

### 1. What is this, really?

- What problem does this plan actually solve? Name the user and the situation, not a slogan.
- Are the key terms defined (scope, success, non-goals)?
- If you strip the buzzwords, what is left?

### 2. Why should I believe it?

- What facts support it, and where do they come from?
- Which claims are facts, which are assumptions, which are taste?
- What data, counterexamples, failed cases, or runtime risks are missing?

### 3. How was it inferred?

- What hidden premises sit between the evidence and the conclusion?
- Any jumps, over-generalization, correlation-as-cause, or one anecdote treated as a law?
- Is “someone else used this” being treated as “we should use this”?

### 4. Even if it is true, is it right for us?

- Does it fit this project’s goals, resources, and skill?
- What is the cost: time, money, performance, maintenance, lock-in, debt, reversibility?
- If goals conflict, what must be protected first?
- Is there a smaller, reversible test that could falsify it before a full rollout?

### Verdict (required)

- Where the plan is strongest
- The biggest problem (or “no obvious holes”)
- Key assumptions to verify (max 3)
- Decision: proceed / proceed with conditions / verify first / do not proceed
- If conditional or verify-first: the smallest next action

---

## Output shape / 输出形态

Lead with the verdict. Then the four answers. Then the smallest next action.

Keep the whole review short enough to read on a phone. One tight paragraph per question is enough. Bullet lists beat essays.

Do not pad. An honest “this is fine; here is the one assumption to check” is a complete review.

## Intensity / 审查力度

- **Light**: reversible, local, one module. Four short bullets + verdict.
- **Full**: stack change, data migration, public launch, security/permissions, anything hard to undo. Use the full template.

If blast radius is unclear, use Full.

## Hard rules / 硬规则

- Do not start implementing during the review unless the user asked only for a review *and* the verdict is proceed — then implement after the verdict in the same turn when they asked you to do the work.
- If they only said “review this”, stop after the verdict. Do not sneak in a refactor.
- Do not moralize. Do not mock the plan. Steelman it first, then cut.
- Prefer a cheap test over a long argument.
- Never claim certainty you do not have. Mark guesses as guesses.
