# Ecom KV Skill v2.0

电商商品营销主视觉（KV）设计 Skill。面向没有设计背景的商家，按「商品信息确认 → 卖点提炼 → 2–3 个设计提案 → 用户确认 → 图像制作或提示词导出 → 自检」完成设计。

[English guide](README.en.md) · [中文 Skill](SKILL.md) · [English Skill](SKILL.en.md) · [安装说明](INSTALL.md)

## 运行前准备

这是供 AI 助手读取的 Markdown 技能包，不是独立程序；无需安装 Python、Node.js 或运行构建命令。需要一个支持技能导入或读取本地文件的 AI 助手，以及清晰的商品原图、商品名称、价格和促销信息。图片制作还需要宿主具备图像编辑能力，或由用户使用外部图像工具完成。

包内保留用户定稿的 20 份源文件。`SKILL.md` 是默认中文入口，`SKILL.en.md` 是英文主入口译文；知识库及平台配套资料仍为中文，并非全套英文翻译。

## 安装与启动

1. 下载仓库文件并解压，找到同时包含 `SKILL.md`、`knowledge/` 和 `platforms/` 的目录。
2. 本地目录安装：将整个技能目录放入宿主支持的技能目录，并按宿主要求重新加载技能。各平台的原版安装约定见 [INSTALL.md](INSTALL.md)。
3. ZIP 导入：压缩上述目录的**内部内容**，保证 ZIP 根目录直接包含 `SKILL.md`、`knowledge/` 和 `platforms/`。GitHub 的 **Code → Download ZIP** 通常带仓库外层目录，不能直接假定满足技能导入格式。
4. 在宿主人设、系统配置或启动消息中明确写入 `当前运行平台：<实际平台名>`。
5. 调用 `ecom-kv-designer`，或明确要求助手读取并执行本目录的 `SKILL.md`。手动读取模式需要助手能访问所有被引用文件；仅粘贴主文件不等于安装完整知识库。

英文入口：若宿主支持指定入口，选择 `SKILL.en.md`；若只识别 `SKILL.md`，请在**独立安装副本**中将原中文入口备份为 `SKILL.zh.md`，再将 `SKILL.en.md` 复制为 `SKILL.md`，保持 `knowledge/` 与 `platforms/` 的相对位置不变。两种语言的技能名相同，避免同时安装为两个同名技能。

## 最小运行示例

上传真实商品照片后，发送以下消息，并把示例字段替换为真实信息：

```text
当前运行平台：<实际平台名>
请使用 ecom-kv-designer 为商品制作电商主视觉。
商品名称与类目：<填写>
价格与促销：<填写；无促销请写“无”>
投放平台和位置：<填写或请先提出建议>
已核实卖点：<填写；不确定的内容请标记待核实>
品牌色、logo 与其他约束：<填写或写“无”>
请先确认商品信息卡，再提出 2–3 个方案，等我选择后再进入制作。
```

预期先得到商品信息卡和设计提案；用户确认方案后，进入对应平台的制作流程。没有可用图像编辑能力时，应交付中英提示词与排版指引，待用户回传图片后完成自检，不应声称已经生成成品。

本版本 [CLI 通用档](platforms/agent-cli.md) 规定采用提示词导出路径。其他平台按包内适配文档执行；这些文档记录的是本版本约定，不代表已验证所有平台当前版本的能力、目录、额度或导入方式。

## 文件导航

| 文件 | 用途 |
|---|---|
| [SKILL.md](SKILL.md) / [SKILL.en.md](SKILL.en.md) | 中文 / 英文主 Skill |
| [INSTALL.md](INSTALL.md) | 原版安装说明与验证清单 |
| [设计硬规则](knowledge/01-design-hard-rules.md) | P1–P10 与冲突优先级 |
| [卖点提炼规则](knowledge/02-selling-point-rules.md) | 三维评分与 FAB |
| [类目场景库](knowledge/03-kv-scenario-library.md) | 类目、人群与场景 |
| [文案模板](knowledge/04-copywriting-templates.md) | 标题、促销与 CTA |
| [违禁词清单](knowledge/05-ad-law-prohibited-words.md) | 文案检查资料 |
| [电商平台规范](knowledge/06-platform-specs.md) | 画布与平台约束 |
| [自检清单](knowledge/07-self-check-list.md) | 24 项检查及报告模板 |
| [信息采集脚本](knowledge/08-intake-questions.md) | 商品信息卡与提问顺序 |
| [豆包工作](platforms/doubao-work.md) | 豆包工作适配 |
| [WorkBuddy](platforms/workbuddy.md) | WorkBuddy 适配 |
| [千问办公](platforms/qwenwork.md) | 千问办公适配 |
| [CLI 通用档](platforms/agent-cli.md) | CLI 平台适配 |
| [豆包排版指引](platforms/assets/doubao-work-layout-guide.md) | 后期排版 |
| [豆包符号集](platforms/assets/doubao-work-renderable-symbols.md) | 符号资料 |
| [WorkBuddy 符号集](platforms/assets/workbuddy-renderable-symbols.md) | 符号资料 |
| [千问 Segoe UI Symbol](platforms/assets/qwenwork-symbols-segoe-ui-symbol.md) | 字体符号资料 |
| [千问微软雅黑](platforms/assets/qwenwork-symbols-microsoft-yahei.md) | 字体符号资料 |

包内文档用反引号标记的 `knowledge/...`、`platforms/...` 路径均以**技能根目录**为基准，供助手读取；这些文本本身并非 GitHub 可点击链接，可通过上表导航。

## 安装后检查

- 让助手复述 P1–P10，并说明读取了哪份平台文档。
- 不提供商品信息，只说「给我出图」：应先采集信息，不编造商品。
- 提供含「全网最低」的测试文案：应触发包内规则检查和改写。
- 提交真实商品信息：应先给方案并等待确认，之后才进入制作。
- 图像制作后检查商品主体、logo、文字及符号，按清单输出自检报告；未完成的项目不得伪报为「24/24 通过」。

## 已知边界

- 千问字体资料中的 `symbol_sweep.py` 是原文提及的符号复测工具，未包含在本次定稿目录中；日常运行不依赖它，重新复测字体需要另行取得该工具。`INSTALL.md` 中的 `platforms/_template.md` 是打包前应删除的开发模板，本包没有该文件。
- 本包不含 WorkBuddy 的 `.codebuddy-plugin/plugin.json` 插件清单；按技能包方式使用，不能将其视作完整插件工程。
- 平台文档中的目录示例和 `<对应平台>` 等占位路径不是随包文件。仓库不包含同级测试输出目录、课程课件或商品测试素材。
- 发布整理仅新增运行文档，保留定稿 Skill 的原有措辞和规则；不将仓库文件可访问视为跨平台实际运行验证。
