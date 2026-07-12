# AI Agent 知识与实战博客文集

> 一套系统梳理 AI Agent（智能体）背景、原理、主流产品与实用技巧的中文文集。
> 定位：**科普 + 实操**——既讲清楚"为什么这样设计"，也给出能照着跑的安装/使用步骤。
> 最后更新：2026-07

---

## 这套文集适合谁

- 想系统搞懂"AI Agent 到底是什么、和 ChatGPT 有啥区别"的人
- 想在终端 / IDE 里用上一个能替你干活的编程 Agent，但被一堆产品名绕晕的人
- 科研 / 数据 / 写作工作者，想用 Agent 提效但不知从哪下手的人

不需要你是资深工程师。会用命令行、装过软件，就够了。

---

## 目录

### 一、背景与原理（先看这个）

| 文章 | 一句话 |
|---|---|
| [什么是 AI Agent](01-背景与原理/01-什么是AI-Agent.md) | 从"聊天机器人"到"能自己干活的智能体"，到底变了什么 |
| [Agent 核心概念与架构](01-背景与原理/02-Agent核心概念与架构.md) | ReAct 循环、工具调用、MCP、记忆、Skill——一次讲透 |

### 二、主流 Agent 产品（先看全景，再挑一个上手）

| 文章 | 覆盖产品 |
|---|---|
| [Agent 产品全景](02-主流Agent产品/01-Agent产品全景.md) | **先读这篇**：所有产品的形态、脾气、优势总览，理清格局 |
| [Claude Code](02-主流Agent产品/02-Claude-Code.md) | **"claude 是哪个"= Claude Code**，Anthropic 官方终端 Agent |
| [OpenAI Codex](02-主流Agent产品/03-OpenAI-Codex.md) | OpenAI 官方编程 Agent（2026-07 已并入 ChatGPT） |
| [OpenClaw](02-主流Agent产品/04-OpenClaw.md) | 2026 年爆火的开源个人 Agent（不止编程） |
| [Hermes Agent](02-主流Agent产品/05-Hermes-Agent.md) | Nous Research 的"会成长"的自托管 Agent |
| [开源 Agent 合集](02-主流Agent产品/06-开源Agent合集.md) | OpenHands、Aider、Cline、opencode、Goose |
| [国内 AI 编程产品](02-主流Agent产品/07-国内AI编程产品.md) | 通义灵码/Qwen Code、Trae、iFlow、CodeBuddy、文心快码、CodeGeeX |
| [横向对比与选型](02-主流Agent产品/08-横向对比与选型.md) | 一张表 + 场景化推荐，帮你做决定 |

### 三、Skill 与科研技巧（进阶玩法）

| 文章 | 内容 |
|---|---|
| [Skill 与 MCP 入门](03-Skill与科研技巧/01-Skill与MCP入门.md) | 让 Agent 获得"专业技能"和"外部工具"的两种机制 |
| [科研工作流 Skill](03-Skill与科研技巧/02-科研工作流.md) | 文献综述、数据分析、论文写作/审稿的落地流程 |
| [有意思的 Skill 合集](03-Skill与科研技巧/03-有意思的Skill.md) | PDF/Excel/PPT、浏览器自动化、日常自动化等 |

---

## 快速上手建议

- **不知从何看起**：先读 [Agent 产品全景](02-主流Agent产品/01-Agent产品全景.md)，理清格局。
- **只想写代码 / 做科研**：直接看 [Claude Code](02-主流Agent产品/02-Claude-Code.md) 或 [国内产品](02-主流Agent产品/07-国内AI编程产品.md)（免费额度友好）。
- **想要一个管生活+自动化的个人助理**：看 [OpenClaw](02-主流Agent产品/04-OpenClaw.md)。
- **纠结选哪个**：直接跳 [横向对比与选型](02-主流Agent产品/08-横向对比与选型.md)。

---

## 免责与时效声明

- Agent 领域变化极快，本文集内的**安装命令、价格、模型版本**均以 2026 年年中的公开信息为准，使用前请以各产品官方文档为准。
- 涉及第三方/自托管 Agent 时请注意**安全与隐私**：给 Agent 的 API Key、文件读写权限、浏览器/命令执行权限，都意味着真实的攻击面。详见各产品页的"注意事项"。
