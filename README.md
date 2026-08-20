# philosophy-review

[中文](#中文) · [English](#english)

动手前先用「哲学四问」审查方案。适合 Claude Code、Codex、Cursor。

Review a plan with the Four Questions before you execute it. Works with Claude Code, Codex, and Cursor.

```bash
npx skills add jarvis-xy/philosophy-review -g -y
```

---

## 中文

别一上来就执行。先问四件事：这到底是什么、我凭什么相信、它是怎么推出来的、即使成立适不适合我。

### 使用场景

| 场景 | 你可能会说 |
|---|---|
| 换技术栈 | 「看到一篇文章说 Mongo 更快，要把 Postgres 换掉」 |
| Agent 要大重构 | 「它提议先改成微服务 / monorepo / 整套 clean architecture」 |
| 照搬别人的方案 | 「这个 starter / SaaS / Agent 工作流很火，我们装上吧」 |
| 不可逆操作 | 「删表、迁生产数据、改登录、把接口公开」 |
| 要对外上线 | 「付费功能要上了」或「线上提示词要改，已经有用户在用」 |
| 两个方案吵不清 | 「A 和 B 选哪个，先别写代码」 |
| 要花钱或被锁定 | 「上新云、换模型供应商、加付费依赖、花两周重构换以后省事」 |

错字、改文案、加一行日志，不要走这套。

### 能带来什么

不保证决策正确。更可能发生的是：下一步更便宜、更清楚。

- 把口号收成一句话问题，避免从热词开工
- 把事实、假设、口味分开，少被一篇帖子带着整仓重写
- 拆出隐藏前提：「别人用过」不等于「我们该用」
- 在全面铺开前，先找到一个可逆的小验证
- 给明确结论：推进 / 有条件推进 / 先验证再推进 / 不推进
- 方案没漏洞就直说，不靠审查拖延

一次有用的审查，会改变明天做什么。如果读完还是不知道下一步，这段审查就太空了。

找不到真实问题，就直说没有明显漏洞，不要为了凑数硬找。审查是过滤器，不是为了显得谨慎而拦人。

### 安装

```bash
npx skills add jarvis-xy/philosophy-review -g -y
```

指定 Agent：

```bash
npx skills add jarvis-xy/philosophy-review -g -y -a claude-code -a codex -a cursor
```

手动克隆仅在 `npx` 不可用时再用：

```bash
git clone https://github.com/jarvis-xy/philosophy-review.git ~/.claude/skills/philosophy-review
```

### 怎么用

对 Agent 说：

```text
用哲学四问审一下这个方案：
（贴方案）
```

或者：

```text
/philosophy-review
```

它会先给结论（推进 / 有条件推进 / 先验证再推进 / 不推进），再回答四问，最后给一条最小下一步。用户用中文，它就用中文写。

### 四问

1. **这到底是什么？** 真正要解决的问题、范围、成功标准、非目标。
2. **我凭什么相信？** 事实、假设、偏好要分开；补上反例和风险。
3. **它是怎么推出来的？** 隐藏前提、逻辑跳跃、把个别案例当成普遍规律。
4. **即使它成立，适合我吗？** 目标、资源、代价、可逆性；有没有更小的验证步骤。

欢迎提 Issue。

---

## English

Do not execute first. Ask four things: what this really is, why you should believe it, how it was inferred, and even if true, whether it fits you.

### When to use it

| Scene | You might say |
|---|---|
| Swap the stack | “A post said Mongo is faster, let's leave Postgres” |
| Agent wants a rewrite | “It wants microservices / a monorepo / clean architecture first” |
| Copy a popular setup | “This starter / SaaS / agent workflow is hot, install it” |
| Irreversible ops | Drop a table, migrate prod data, change auth, open a public API |
| Ship in public | Launch a paid feature, or change a live prompt users already depend on |
| Two options, no decision | “Pick A or B. Don't write code yet.” |
| Spend or lock-in | New cloud, new model vendor, paid dependency, a 2-week refactor “to save time later” |

Skip typos, copy tweaks, and one-line logs.

### What you get

It does not guarantee a correct call. It makes the next step cheaper and clearer.

- One-sentence problem, so you don't start from a slogan
- Facts / assumptions / taste split, so one post doesn't trigger a rewrite
- Hidden premises named: “they used it” ≠ “we should”
- A small reversible test before a full rollout
- A verdict: proceed / proceed with conditions / verify first / stop
- If the plan is fine, it says so and does not stall

A useful review changes tomorrow's action. If you still don't know the next step, the review was too vague.

If there is no real problem, it should say there are no obvious holes. The review is a filter, not veto theater.

### Install

```bash
npx skills add jarvis-xy/philosophy-review -g -y
```

Pin agents:

```bash
npx skills add jarvis-xy/philosophy-review -g -y -a claude-code -a codex -a cursor
```

Clone by hand only if `npx` is unavailable:

```bash
git clone https://github.com/jarvis-xy/philosophy-review.git ~/.claude/skills/philosophy-review
```

### How to run it

```text
Use philosophy-review on this plan:
(paste the plan)
```

or:

```text
/philosophy-review
```

The agent leads with a verdict (proceed / proceed with conditions / verify first / do not proceed), answers the four questions, and gives one smallest next action. It matches the user's language.

### The Four Questions

1. **What is this, really?** Problem, scope, success, non-goals.
2. **Why should I believe it?** Separate facts, assumptions, and taste; name missing counterexamples.
3. **How was it inferred?** Hidden premises, jumps, anecdote-as-law.
4. **Even if true, is it right for us?** Goals, cost, reversibility, a cheaper test.

Issues welcome in this repo.
