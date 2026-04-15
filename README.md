# Prompt Enhancer CN

将粗糙的自然语言需求，改写成更清晰、更可执行、更适合大模型使用的高质量 Prompt。

这是一个中文优先的 Codex skill，适合把一句话想法、模糊需求、零散笔记，转换成结构化提示词，用于 ChatGPT、OpenAI API、Codex、Claude、写作、调研、图像生成和 Agent 工作流等场景。

`Status: Tested`
`Language: Chinese-first`
`Type: Codex Skill`

## Overview

`prompt-enhancer-cn` 的目标不是解释 Prompt 工程，而是直接给出更好的 Prompt。

它主要解决的是这些问题：
- 用户输入太短，只有一句话想法
- 用户需求太口语化，缺少结构
- 用户说“更专业一点”，但没有写清楚标准
- 原始 Prompt 混杂了目标、背景、限制和输出要求
- 想直接拿到可以复制使用的最终版本

这个 skill 会自动补齐常见缺口：
- 目标
- 输入材料
- 约束条件
- 输出格式
- 质量要求
- 引用或来源要求

## Quick Example

原始输入：

```text
帮我做一个调研，看看 AI 编程产品还有没有机会，写得专业一点
```

优化后可能得到：

```text
请对中国 AI 编程产品市场机会进行一份结构化调研分析，输出面向产品负责人和创业团队的专业结论。

调研目标：
- 判断当前 AI 编程产品是否仍存在可进入的市场机会
- 识别最值得关注的细分方向
- 分析主要竞争压力、产品门槛与商业化难点

输出格式：
1. 核心结论
2. 市场机会判断
3. 值得关注的 3 个细分方向
4. 风险与不确定性
5. 建议
```

## Features

- 中文优先：默认输出中文优化稿
- 面向实战：优先直接给可用 Prompt，不堆 Prompt 工程理论
- 任务分型：覆盖编码、写作、调研、图像生成、Agent 工作流
- 自动补全：补充目标、输入、约束、输出格式、质量要求
- 输出可控：支持 `只输出优化稿` 和 `优化稿 + 说明`
- 调研增强：支持来源、引用、可核查性要求

## Best For

- `优化提示词`
- `自然语言转 prompt`
- `帮我改写 prompt`
- `把这段中文需求整理成适合 AI 的指令`
- `生成更专业 / 更严格 / 更稳定的 prompt`

## Example Requests

```text
用 prompt-enhancer-cn 帮我把这段需求优化成 prompt
帮我把这个自然语言描述转成适合 Codex 的 prompt
优化这段提示词，给我一个严格版和简洁版
把这句话改成适合 Claude 做调研的 prompt
不要解释，直接给我最终 prompt
```

## Supported Task Types

### Coding / debugging

把模糊的“帮我修 bug”“帮我写代码”改成更像工程任务的 Prompt，通常会补上：
- 上下文
- 文件范围
- 约束条件
- 验收标准
- 验证步骤

### Writing / summarization

适合把“帮我写篇文章”“帮我总结一下”改成更明确的写作任务，通常会补上：
- 目标读者
- 语气风格
- 篇幅长度
- 输出结构
- 禁止事项

### Research / analysis

适合把“帮我调研一下”“分析一下有没有机会”改成可执行分析任务，通常会补上：
- 时间范围
- 比较维度
- 结论结构
- 风险与不确定性
- 来源 / 引用要求

### Image generation

把“做一张高级感海报”“生成某种风格图片”改成更可渲染的图像 Prompt，通常会补上：
- 主体
- 构图
- 光线
- 材质
- 色板
- Negative constraints

### Agent / workflow

适合生成更稳的 Agent 提示词，通常会补上：
- 目标
- 工具边界
- 阶段汇报点
- 停止条件
- 交付物

## Output Modes

### `只输出优化稿`

适合直接复制使用。

示例：

```text
把这段需求优化成 prompt，不要解释，直接给我成品
```

### `优化稿 + 说明`

适合既想看最终结果，也想知道关键改动逻辑的场景。

示例：

```text
帮我优化这个 prompt，并告诉我你做了哪些关键改动
```

## Prompt Styles

根据请求类型不同，这个 skill 倾向生成不同风格的 Prompt：

- `简洁版`：适合快速复制使用
- `严格版`：强调边界、格式和检查点
- `调研版`：强调分析维度、证据、来源和不确定性
- `实现版`：强调可执行、可验证、可交付

## Repository Layout

```text
skill/
  SKILL.md
  agents/openai.yaml
  references/templates.md
tests/
  TEST_PLAN.md
  TEST_REPORT.md
  REGRESSION_TEST_REPORT_ROUND2.md
```

- `skill/SKILL.md`: 核心 skill 定义与触发规则
- `skill/agents/openai.yaml`: UI metadata
- `skill/references/templates.md`: 各任务类型的 Prompt 模板
- `tests/TEST_PLAN.md`: 测试计划
- `tests/TEST_REPORT.md`: 初始测试报告
- `tests/REGRESSION_TEST_REPORT_ROUND2.md`: 第二轮回归测试报告

## Install

这个仓库当前以 skill 源文件仓库形式发布。

如果你正在维护本地 Codex skills 目录，可以把 `skill/` 下内容放入：

```text
~/.codex/skills/prompt-enhancer-cn/
```

然后在新会话中直接触发，例如：

```text
用 prompt-enhancer-cn 帮我把这段需求优化成 prompt
```

## Testing

本项目当前包含：
- 1 份测试计划
- 1 份主测试报告
- 1 份回归测试报告

当前测试结论：
- `PASS`

测试重点覆盖：
- 中文优先输出
- 任务类型分类
- Prompt 结构提升
- 引用规则
- 输出模式切换

## Roadmap

- 增加更多中文示例
- 补充图像 Prompt 的中英双模板
- 增加面向不同模型的定制版本
- 提供更清晰的安装说明

## License

MIT
