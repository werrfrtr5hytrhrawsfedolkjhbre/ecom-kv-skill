---
platform: agent-cli
---

# CLI 型通用档（Claude Code / Codex / Qwen Code / Gemini CLI / Cursor）· 平台差异（增量）

> 只写与核心流程的差异；通用规则见 `SKILL.md` 与 `knowledge/`。
> **字段未生效兜底**：若本文件未被加载，按 SKILL.md 核心流程执行，生图走「提示词导出」，符号不内嵌。

## 一、生图方式

- 本类平台无对话内原生出图渠道（或能力未验证）→ **提示词导出（路径 A）**：
  - 输出中英双语生图提示词（含负面提示词），引导用户粘贴到任一主流生图工具（即梦/万相/Midjourney/混元等）生成。
  - 提示词中的画面文字要求：仅中文/英文/数字；**不内嵌符号**（符号一律留给后期排版）。
  - 用户把生成图发回对话 → 按 `knowledge/07-self-check-list.md` 执行自检 → 出《自检报告》。

## 二、安装

- Claude Code → `~/.claude/skills/`；Codex → OpenAI Skills 目录；Qwen Code → `.qwen/skills`；Gemini CLI / Cursor → 各自技能目录（以平台文档为准）。
- 安装后在人设/配置中写死一句：**当前运行平台：<平台名>**。
