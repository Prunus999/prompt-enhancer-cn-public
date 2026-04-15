# Prompt Enhancer CN

A Chinese-first Codex skill for turning rough natural-language requests into clearer, more executable prompts.

## What it does

- Improves vague prompts into structured prompts
- Supports coding, writing, research, image generation, and agent workflow tasks
- Defaults to Chinese output
- Supports two output modes:
  - `只输出优化稿`
  - `优化稿 + 说明`

## Project structure

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

## Included files

- `skill/SKILL.md`: main skill definition
- `skill/references/templates.md`: reusable prompt templates
- `skill/agents/openai.yaml`: UI metadata
- `tests/*`: manual test plan and reports

## Example usage

```text
用 prompt-enhancer-cn 帮我把这段需求优化成 prompt
帮我把这个自然语言描述转成适合 Codex 的 prompt
优化这段提示词，给我一个严格版和简洁版
```

## Status

This project has been manually tested and includes a regression report for the latest rule updates.

## License

MIT
