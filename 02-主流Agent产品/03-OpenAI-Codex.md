# OpenAI Codex：并进 ChatGPT 之后的那个编程 Agent

如果说 Claude Code 是 Anthropic 那边的当家花旦，那 Codex 就是 OpenAI 摆在对面的那位对手。它的定位和 Claude Code 几乎是镜像的——同样是官方出品、同样能扎进代码库改到测试通过，只不过背后换成了 OpenAI 面向 Agent 和编程优化的那套模型。不过在聊它怎么用之前，有件 2026 年 7 月刚发生的大事得先讲清楚，否则你对今天的 Codex 会有认知偏差。

先顺手消个歧：这里说的 Codex 是 2025 到 2026 年这一代的 Codex Agent，不是 2021 年那个早就下线的老 Codex 补全模型，别搞混了。

## 2026 年 7 月 9 日：Codex 搬进了 ChatGPT

这是理解今天 Codex 的头等大事。就在 2026 年 7 月 9 日，OpenAI 把原本独立的 Codex 编程 Agent **并进了 ChatGPT 桌面 App**，同一天还顺势发布了 GPT-5.6 和一个叫 ChatGPT Work 的新智能体模式——后者直接给你产出文档、表格、网页应用，而不再只是回你一段聊天文字。

对你我这样的用户来说，这次合并有几层实际影响。首先是入口变了，Codex 不再是一个单独的 App，而是变成 ChatGPT 桌面 App 里的一个专门编程模式，跟 Chat、Work 三个模式并排站着；这个合并后的 App 现在是唯一的 ChatGPT 桌面端，Mac 和 Windows 上、连 Free 套餐在内的所有档位都能用。其次是钱的算法变了，**过去那种单独的 Codex 订阅没有了**，Codex 的使用权直接捆进了 ChatGPT 的各档套餐里，按套餐额度用，不用再单买。

好消息是，命令行版的 Codex 并没有消失，`@openai/codex` 这个包还在，下面讲的安装方式照旧管用——真正变的只是"账号和计费这条线统一收归到了 ChatGPT 那边"。至于新发布的 GPT-5.6，分成 Sol、Terra、Luna 三档，分别对应旗舰级的强推理、性价比最高的日常主力、以及最快最便宜的轻量档，ChatGPT Work 就跑在它上面。

一句话总结这次变化：**只要你有 ChatGPT 订阅，现在打开桌面 App 就能直接用 Codex，不必再单独订；想在终端里用，仍然可以装 CLI。**

## 它是个什么东西

抛开合并这层不谈，Codex 的内核和其他终端编程 Agent 是一路货色：理解代码库、编辑文件、执行 shell、跑测试、操作 git、通过 MCP 接外部工具。它的风格我觉得可以概括为"给任务、自己跑完"，自主度调得比较高。OpenAI 官方给的数据也挺能说明它的普及程度——每周有超过五百万人在用 Codex，而且其中大约五分之一的人已经把它用在了软件开发之外的活儿上。

## 桌面客户端怎么装（多数人现在走这条路）

自从并进 ChatGPT 之后，对大部分人来说，用 Codex 最省事的方式已经不是装命令行，而是**装那个 ChatGPT 桌面客户端**——因为合并后 Codex 就是这个 App 里的一个内置模式，装好 App 相当于顺带就有了 Codex。整个过程比 CLI 简单得多，基本是"下载、安装、登录"三下。

先去官方下载页 [chatgpt.com/download](https://chatgpt.com/download/) 拿安装包，Mac 和 Windows 都有；Windows 用户嫌麻烦的话，直接在微软商店（Microsoft Store）搜 ChatGPT 装也一样。装完打开，用你的 ChatGPT 账号登录进去，你会看到界面里并排着 **Chat、Work、Codex** 三个模式，切到 Codex 那个就是编程 Agent 了。它能直接对接你本地的文件、代码仓库、终端和各类开发者工具，干的还是那套"理解代码库、改文件、跑命令"的活，只是包在一个图形界面里，对不爱折腾命令行的人友好很多。

有两类人要特别说一句。一类是**以前装过那个独立 Codex App 的老用户**，你不用从头来过，直接把它更新到新的 ChatGPT App、再打开里面的 Codex 就行，官方给了平滑迁移的路子。另一类是**平台党**：Windows 上可以用 `Alt + Space` 快捷键随时唤出 ChatGPT，Mac 上则支持语音输入，跟它开口说话，这些小便利也算是桌面端相比 CLI 多出来的甜头。

至于该选桌面客户端还是命令行，其实很好判断：想要图形界面、开箱即用、顺带把 Chat 和 Work 一起用上，就装桌面客户端；如果你要的是脚本化、进 CI、或者在远程服务器上跑，那还是往下看 CLI。两者用的是同一个账号、同一套额度，随时切换，不冲突。

## 怎么装 CLI

如果你想走终端这条路，前提是本机有 Node.js，建议直接上 22 或更新的版本（有些版本 18 也能跑，但新版本对 22+ 更稳当），外加一个有额度的 OpenAI 账号——ChatGPT 的 Plus、Pro 订阅都自带额度，新账号一般还送一点免费额度够你试水。

安装就一条命令：

```bash
npm install -g @openai/codex
```

这里我必须重点圈一个坑，因为踩的人实在太多：**一定要装带 scope 的 `@openai/codex`**。你要是手一抖装成了不带前缀的 `npm i -g codex`，装到的是 2012 年一个毫不相干的老项目，然后对着一脸懵。装完 `codex --version` 验一下，再敲 `codex` 进去，第一次会引导你认证。万一提示找不到命令，多半是 npm 的全局 bin 目录没进 PATH，`npm bin -g` 打出来那个路径加进你的 shell 配置（Windows 就加进系统环境变量）即可。

用起来和别的终端 Agent 差不多，直接下达任务，比如"给这个仓库加一套跑 lint 和测试的 GitHub Actions CI"，或者"重构 payment 模块但保持现有测试通过"。它支持从"每步都确认"到"比较自主地一路跑完"的不同审批级别，具体开到多松，还是那句话——看你这个仓库能不能轻松回滚。

## 它适合谁，以及要不要和 Claude Code 二选一

最顺理成章的用户，就是本来就泡在 OpenAI 生态里、手握 ChatGPT 订阅、用惯了 GPT 系列的开发者，对你们来说现在打开 ChatGPT 就有 Codex，几乎没有额外门槛。

至于"Codex 和 Claude Code 到底选哪个"，我的实用建议是——**别纠结，两个都装**。它们在能力上互有胜负，很多时候我会同一个任务分别丢给两边，看谁的手感更对。真要细抠优劣，我在最后那篇 [横向对比与选型](08-横向对比与选型.md) 里摊开讲。

## 钱怎么算（合并后已统一）

前面说了，Codex 现在没有独立订阅，跟着 ChatGPT 套餐走。2026 年 7 月这会儿的档位大致是这样：Free 免费但 Codex 用量有限；Go 每月八美元算入门；Plus 二十美元是常规主力；Pro 一百美元给到五倍用量、两百美元给到二十倍，重度开发者往这挑；团队则是 Business，每人每月二十五美元起（原来三十美元的 Team 套餐已经在 4 月 2 号被 Business 替换，最少两人起订）；再往上就是定制的 Enterprise 了。

还有个变化值得留意：从 2026 年 4 月起，用量改成了 API 风格的 token 计费，区分输入、缓存输入和输出——你买的是额度，但具体烧得快不快取决于实际消耗的 token。当然你也可以完全绕开订阅，直接拿 API Key 按 token 调用。价格这东西变得勤，认真掏钱前还是以 [官方定价页](https://developers.openai.com/codex/pricing) 为准。

## 几句安全提醒

老三样，但每一条都真会咬人：认准 `@openai/codex` 别装错；自主级别开得越高越省心也越危险，请配合可回滚的环境；以及和所有 Agent 一样，警惕提示注入、保管好你的密钥。

---

参考：[ChatGPT 桌面客户端下载](https://chatgpt.com/download/) ｜ [迁移到新版 ChatGPT 桌面 App](https://help.openai.com/en/articles/20001276) ｜ [npm 包](https://www.npmjs.com/package/@openai/codex) ｜ [Codex CLI 文档](https://developers.openai.com/codex/cli) ｜ [用 ChatGPT 套餐使用 Codex](https://help.openai.com/en/articles/11369540) ｜ Codex 并入 ChatGPT 报道（2026-07-09，TechTimes / Silicon Report 等）

← [Claude Code](02-Claude-Code.md) ｜ 下一篇：[OpenClaw](04-OpenClaw.md)
