# Prompt Templates

Load only the section that matches the user's task.

## Coding / debugging

```text
你是一名资深{language}/{framework}工程师。

目标：
{goal}

上下文：
{context}

输入材料：
{inputs}

约束：
- 不要改动：{do_not_touch}
- 必须满足：{must_have}
- 兼容性要求：{compatibility}

输出要求：
1. 先给出问题判断或实现方案
2. 然后给出可直接执行的代码/补丁
3. 说明关键权衡
4. 给出验证步骤

如果信息不足，请先列出最关键的假设，再在这些假设下继续完成任务。
```

## Writing / summarization

```text
请基于以下材料完成{deliverable}。

目标读者：
{audience}

写作目标：
{goal}

输入材料：
{inputs}

风格要求：
- 语气：{tone}
- 长度：{length}
- 禁止事项：{forbidden}

输出格式：
{format}

要求：
- 不要编造材料中没有的信息
- 若存在不确定内容，请明确标注
- 优先保证清晰、准确、可直接使用
```

## Research / analysis

```text
请对{topic}进行结构化分析。

分析目标：
{goal}

范围：
- 时间范围：{time_range}
- 对比对象：{comparisons}
- 不包括：{out_of_scope}

分析维度：
{dimensions}

输出格式：
1. 核心结论
2. 关键证据
3. 风险与不确定性
4. 建议

要求：
- 区分事实、推断、建议
- 若证据不足，请明确说明不足之处
- 如果用户要求来源，请在关键结论后补充引用链接、来源名称或可核查出处
```

## Image generation

```text
Create an image of {subject}.

Composition:
{composition}

Visual style:
{style}

Lighting and mood:
{lighting}

Materials / texture:
{materials}

Camera / lens / framing:
{camera}

Color palette:
{palette}

Negative constraints:
{negative_prompt}
```

## Agent / workflow

```text
你是一个负责{mission}的代理。

目标：
{goal}

可用资源：
{tools_and_context}

执行边界：
- 可以做：{allowed}
- 不可以做：{disallowed}
- 遇到以下情况必须停止并汇报：{stop_conditions}

交付物：
{deliverable}

工作方式：
1. 先确认假设和计划
2. 再执行关键步骤
3. 在关键节点汇报进展
4. 最终输出结果与残余风险
```
