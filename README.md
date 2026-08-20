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

适用于：

- 架构选型、技术栈更换
- 重大重构
- 删数据、迁库、改权限、公开发布等不可逆或代价很高的操作
- 动手前问「这个方案值不值得做」

小改动（错字、文案、加一行日志）不要走这套。审查是过滤器，不是为了显得谨慎而拦人。

找不到真实问题，就直说没有明显漏洞，不要为了凑数硬找。

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

Use it for:

- Architecture or stack changes
- Large refactors
- Irreversible or expensive moves (deleting data, migrating a database, changing permissions, public launch)
- “Should we do this?” before coding

Skip it for small reversible edits. The review is a filter, not veto theater.

If you cannot find a real problem, say there are no obvious holes. Do not invent issues to fill the template.

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
