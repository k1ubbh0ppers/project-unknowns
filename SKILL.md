---
name: project-unknowns
description: Find and manage project unknowns before, during, and after substantial work. Use when starting a new project, entering an unfamiliar repo/module/domain, planning a feature, doing a design/prototype task, receiving a vague goal, preparing implementation, noticing repeated rework, or when the user asks for blind spots, unknown unknowns, "找到未知项", "盲点扫描", "开始项目", "做项目前", or "帮我想清楚再做".
---

# Project Unknowns

Use this skill to reduce the gap between the user's map (prompt, context, assumptions, skill instructions) and the territory (real repo, users, constraints, edge cases, business rules, deploy surface).

The goal is not to block execution with endless questions. The goal is to surface high-impact unknowns early, ask only questions that can change the work, and keep moving with explicit assumptions.

## Default Workflow

1. Build starting context.
   - Read available project instructions, memory, docs, relevant files, and prior artifacts before guessing.
   - Identify what the user wants to advance, not only what the literal request says.
   - State whether each important fact is verified, memory-derived, or inferred when that distinction matters.

2. Classify unknowns.
   - Known knowns: what the user already specified.
   - Known unknowns: questions the user or repo already exposes.
   - Unknown knowns: standards the user will recognize only after seeing examples, prototypes, or options.
   - Unknown unknowns: missing context, failure modes, constraints, or quality bars the user has not named yet.

3. Run a blindspot pass.
   - Search code/docs/history when a repo or files exist.
   - Look for adjacent modules, naming patterns, data contracts, user flows, validation rules, deployment constraints, tests, and previous decisions.
   - For non-code work, inspect examples, references, audience, channel, quality bar, and approval path.
   - Output the few unknowns most likely to change architecture, scope, UX, data model, cost, risk, or acceptance criteria.

4. Choose one of four actions.
   - Execute now when unknowns are low risk or can be handled with conservative assumptions.
   - Ask one question when a user answer would materially change direction.
   - Prototype or brainstorm when the user likely has "unknown knowns" and needs to see options.
   - Write an implementation plan when execution has enough shape but major decisions remain.

5. During implementation, track deviations.
   - If reality conflicts with the plan, choose a conservative option, keep moving when safe, and record the deviation in the update or a temporary `implementation-notes.md` when the work is long-running.
   - Record: original assumption, discovered fact, decision, reason, and follow-up.

6. After implementation, close the loop.
   - Explain what changed and why, especially decisions that resolved unknowns.
   - Include verification evidence.
   - If the change is complex, offer or create a short review artifact or quiz that helps the user confirm they understand the result before merging/shipping.

## Blindspot Pass Output

Keep the pass compact unless the user asks for a full report:

```markdown
**已确认**
- ...

**关键未知项**
- [影响: 架构/数据/UX/验收/成本/风险] ...

**建议处理**
- 现在直接做: ...
- 需要先问: ...
- 适合先原型/头脑风暴: ...

**我的默认假设**
- ...
```

## Question Rules

Ask fewer, better questions.

- Ask at most one question at a time by default.
- Prioritize questions whose answer changes architecture, data model, UX flow, public behavior, cost, legal/safety risk, or acceptance criteria.
- Do not ask questions whose answer can be found by reading the repo/docs/history.
- When blocked by missing user input, recommend a default answer and explain the tradeoff briefly.

## Prototype Rules

Use prototypes when the user likely cannot fully specify the target until they see it.

- Prefer isolated throwaway artifacts before touching real app code when layout, copy, interaction, or information architecture is uncertain.
- Offer clearly different directions, not tiny variants.
- Label which decisions each prototype is meant to test.
- After feedback, convert chosen direction into concrete implementation constraints.

## Implementation Plan Rules

When planning before implementation, put volatile decisions first:

1. Data model, API contract, permission model, business rules.
2. User-facing flow, copy, states, empty/error cases.
3. Integration boundaries, migration/deploy impact, test strategy.
4. Mechanical refactors and low-risk file moves last.

## Completion Memory

At the end of substantial work, summarize reusable learning:

- Confirmed user preference.
- Reusable path, command, workflow, or judgment.
- Pitfall to avoid.
- Follow-up item, if any.

Only treat stable preferences, project structure, verified workflows, explicit decisions, and reusable pitfalls as memory-worthy. Do not elevate temporary logs or one-off commands into durable lessons.
