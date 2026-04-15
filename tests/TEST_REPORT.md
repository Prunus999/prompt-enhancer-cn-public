# Prompt Enhancer CN Test Report

## 1. Summary

- Test date: 2026-04-15
- Target: `prompt-enhancer-cn`
- Method: specification-based manual execution
- Overall result: `PASS`

Total cases: 6
- Passed: 6
- Failed: 0
- Blocked: 0

## 2. Case results

### TC-01 Coding prompt uplift

Input:
`帮我修一下这个 Python 接口报错，顺便把代码写好`

Rewritten prompt:

```text
你是一名资深 Python 后端工程师。

目标：
定位并修复当前接口报错，并给出可直接落地的代码修改方案。

上下文：
- 当前项目是一个已有的 Python 服务
- 用户希望直接解决问题，而不是只要思路

输入材料：
- 报错信息
- 相关接口代码
- 相关日志
- 依赖版本与运行环境

约束：
- 尽量只改动与问题直接相关的文件
- 不要引入不必要的重构
- 保持与现有代码风格一致

输出要求：
1. 先判断报错根因及影响范围
2. 给出修复方案
3. 提供可直接使用的代码修改内容
4. 给出验证步骤和回归检查点

如果信息不足，请先列出关键假设，并在这些假设下继续完成修复方案。
```

Scores:
- Clarity: 5
- Completeness: 5
- Actionability: 5
- Format discipline: 5
- Fit to task type: 5

Result:
- PASS

Notes:
- Strongly aligned with the coding template and patch-oriented behavior.

### TC-02 Writing prompt uplift

Input:
`帮我写一篇介绍 AI Agent 的文章，专业一点`

Rewritten prompt:

```text
请写一篇面向技术管理者的中文文章，主题是“AI Agent 的核心概念、能力边界与典型落地场景”。

写作目标：
- 帮助读者快速理解 AI Agent 是什么
- 区分 AI Agent 与普通聊天机器人、工作流自动化、RPA 的差异
- 给出企业落地时的价值、风险与适用边界

风格要求：
- 语气专业、克制、清晰
- 避免营销腔和空泛表述
- 使用中文，适合公众号或行业文章

篇幅要求：
- 1500 至 2200 字

输出结构：
1. 标题
2. 导语
3. AI Agent 的定义
4. 与其他自动化方式的区别
5. 典型应用场景
6. 风险与限制
7. 总结

要求：
- 不要编造具体数据或案例
- 如提到趋势或效果，请使用审慎表述
- 优先保证逻辑清晰和可读性
```

Scores:
- Clarity: 5
- Completeness: 5
- Actionability: 4
- Format discipline: 5
- Fit to task type: 5

Result:
- PASS

Notes:
- Audience and output structure were added effectively.
- Could be even stronger if source material handling were requested explicitly.

### TC-03 Research prompt uplift

Input:
`帮我分析一下 SaaS 出海机会`

Rewritten prompt:

```text
请对 2026 年中国 SaaS 产品出海机会进行结构化分析。

分析目标：
- 判断当前是否存在值得进入的细分市场
- 识别增长机会、主要风险和进入门槛
- 输出可用于决策讨论的结论

分析范围：
- 时间范围：近 2 至 3 年
- 对比对象：中国 SaaS 团队、海外本地 SaaS 竞争者、跨境服务商
- 不包括：纯硬件出海和泛电商代运营业务

分析维度：
- 市场需求强度
- 客户付费能力
- 获客难度与渠道
- 产品本地化复杂度
- 合规与支付风险
- 客服与交付成本
- 竞争格局

输出格式：
1. 核心结论
2. 最值得关注的 3 个细分方向
3. 每个方向的机会与风险
4. 不确定性与需补充验证的信息
5. 建议

要求：
- 区分事实、推断、建议
- 若证据不足，请明确说明
- 避免空泛结论，尽量给出可执行判断框架
```

Scores:
- Clarity: 5
- Completeness: 5
- Actionability: 4
- Format discipline: 5
- Fit to task type: 5

Result:
- PASS

Notes:
- Good research structure.
- If used in a live web-research workflow, citation requirements could be made explicit.

### TC-04 Image generation prompt uplift

Input:
`帮我生成一张高级感的咖啡海报`

Rewritten prompt:

```text
Create a premium coffee poster featuring a single cup of freshly brewed black coffee on a dark stone surface.

Composition:
- Vertical poster layout
- Hero object centered slightly lower than mid-frame
- Steam visible but restrained
- Include negative space for headline placement

Visual style:
- Luxury editorial advertising
- Minimalist, refined, tactile

Lighting and mood:
- Soft directional side light
- Deep contrast with controlled highlights
- Warm, cinematic atmosphere

Materials / texture:
- Matte ceramic cup
- Dark stone tabletop
- Subtle coffee bean texture in the background

Camera / lens / framing:
- 50mm commercial product shot
- Slight top-front angle
- Crisp focus on cup rim and coffee surface

Color palette:
- Espresso brown, charcoal black, warm cream, muted gold

Negative constraints:
- No clutter
- No cartoon style
- No overly bright cafe scene
- No crowded text elements
```

Scores:
- Clarity: 5
- Completeness: 5
- Actionability: 5
- Format discipline: 5
- Fit to task type: 5

Result:
- PASS

Notes:
- Strong visual specificity and good conversion from abstract adjective to renderable details.

### TC-05 Agent workflow prompt uplift

Input:
`帮我做个自动修 bug 的 agent prompt`

Rewritten prompt:

```text
你是一个负责自动定位并修复软件缺陷的工程代理。

目标：
在给定代码仓库、报错信息和测试结果的前提下，尽可能独立地完成问题定位、修复实现、验证和结果汇报。

可用资源：
- 代码仓库
- 测试命令
- 日志与报错信息
- 项目说明文档

执行边界：
- 可以做：阅读代码、提出修复方案、修改相关文件、运行必要测试、输出验证结果
- 不可以做：无依据地大规模重构、删除无关模块、伪造测试结果
- 遇到以下情况必须停止并汇报：需求不清、修复会影响核心架构、测试环境不可用、存在多个互斥修复路径

交付物：
1. 问题根因
2. 修复方案
3. 修改后的关键代码
4. 验证结果
5. 剩余风险

工作方式：
1. 先总结已知信息和关键假设
2. 再给出修复计划
3. 执行最小必要修改
4. 运行验证并汇报结果
```

Scores:
- Clarity: 5
- Completeness: 5
- Actionability: 5
- Format discipline: 5
- Fit to task type: 5

Result:
- PASS

Notes:
- Boundary and stop-condition handling is strong and consistent with skill intent.

### TC-06 Missing-information resilience

Input:
`优化一下这个 prompt，让它更好`

Rewritten prompt:

```text
请将我接下来提供的原始 prompt 优化为一个更清晰、更可执行的高质量版本。

优化目标：
- 明确任务目标
- 补全必要约束
- 指定输出格式
- 删除模糊、重复或无效表达

输出要求：
1. 先给出优化后的 prompt
2. 再补充你做了哪些关键改进
3. 如果原始信息不足，请明确写出你的假设

优化原则：
- 保留原始意图
- 不编造事实
- 优先提升可执行性和结果稳定性
- 如果适合，可提供一个简洁版和一个严格版
```

Scores:
- Clarity: 5
- Completeness: 4
- Actionability: 4
- Format discipline: 5
- Fit to task type: 4

Result:
- PASS

Notes:
- This is a good fallback wrapper.
- It is intentionally generic, so task-type fit is slightly weaker than the typed cases.

## 3. Findings

### Strengths

- The skill consistently upgrades vague requests into structured prompts.
- The task-type split is useful and visible in results.
- The output contract pushes the result toward practical prompt delivery instead of explanation-heavy answers.
- Assumption-first behavior works well for incomplete inputs.

### Remaining gaps

- The image template is English-first, which is acceptable for many image models, but the skill still relies on a rule rather than separate CN/EN image templates.
- There is no dedicated test hook for runtime registration after restarting Codex, so discoverability is not validated here.

## 4. Recommendations

1. After restarting Codex, run one live invocation to verify trigger behavior in a real session.
2. If image prompting becomes a frequent use case, split image templates into explicit Chinese and English variants.

## 5. Final verdict

`prompt-enhancer-cn` is usable now and performs well on representative cases. The previously identified three improvement items have been implemented and passed a focused regression round.
