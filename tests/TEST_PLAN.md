# Prompt Enhancer CN Test Plan

## 1. Test target

- Skill: `prompt-enhancer-cn`
- Skill path: `/home/jerry/.codex/skills/prompt-enhancer-cn/SKILL.md`
- Reference template path: `/home/jerry/.codex/skills/prompt-enhancer-cn/references/templates.md`

## 2. Test goal

Verify that the skill can reliably convert rough natural-language requests into clearer, more executable prompts, and that it behaves consistently across the task types declared in the skill.

## 3. Scope

In scope:
- Trigger wording coverage
- Chinese-first rewrite behavior
- Output contract alignment
- Prompt quality uplift for major task types
- Assumption handling when details are missing

Out of scope:
- UI discovery behavior inside a freshly restarted Codex session
- Real model-performance benchmarking across external providers
- Token-cost optimization benchmarking

## 4. Test method

Use specification-based manual testing against the skill instructions.

For each case:
1. Provide a rough natural-language input.
2. Rewrite it according to the skill rules.
3. Score the rewritten prompt against the rubric below.
4. Record pass/fail and note gaps.

## 5. Pass criteria

A case passes when all of the following are true:
- The rewritten result is clearly better than the input.
- The output is primarily a usable prompt, not a lecture.
- Missing details are handled through explicit assumptions when reasonable.
- The rewritten prompt includes useful structure such as goal, constraints, inputs, or output format.
- The result matches the intended task type.

## 6. Rubric

Each case is scored on a 5-point scale for:
- Clarity
- Completeness
- Actionability
- Format discipline
- Fit to task type

Suggested interpretation:
- 5: strong
- 4: good
- 3: acceptable with gaps
- 2: weak
- 1: failed

## 7. Test cases

### TC-01 Coding prompt uplift

Input:
`帮我修一下这个 Python 接口报错，顺便把代码写好`

Expectation:
- Output should add objective, context assumptions, constraints, deliverable, and validation.
- Should bias toward patch-oriented execution rather than generic advice.

### TC-02 Writing prompt uplift

Input:
`帮我写一篇介绍 AI Agent 的文章，专业一点`

Expectation:
- Output should define audience, tone, length, structure, and factual boundaries.

### TC-03 Research prompt uplift

Input:
`帮我分析一下 SaaS 出海机会`

Expectation:
- Output should define timeframe, dimensions, evidence expectations, risks, and recommendation format.

### TC-04 Image generation prompt uplift

Input:
`帮我生成一张高级感的咖啡海报`

Expectation:
- Output should become visual and specific: subject, composition, lighting, palette, exclusions.

### TC-05 Agent workflow prompt uplift

Input:
`帮我做个自动修 bug 的 agent prompt`

Expectation:
- Output should define mission, boundaries, stop conditions, checkpoints, and deliverables.

### TC-06 Missing-information resilience

Input:
`优化一下这个 prompt，让它更好`

Expectation:
- Output should not stall.
- It should state assumptions or provide a reusable generalized prompt-improvement wrapper.

## 8. Risks

- This test validates the skill specification, not runtime registration in a newly restarted session.
- Scoring is human-evaluated and therefore somewhat subjective.

