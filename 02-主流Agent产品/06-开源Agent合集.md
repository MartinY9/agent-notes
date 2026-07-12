# 开源 Agent 合集：不花钱也能玩得很转

前面几篇讲的要么是官方付费的（Claude Code、Codex），要么是主打个人助理的（OpenClaw、Hermes）。这一篇我想聊聊另一大挂——**专注编程的开源 Agent**。它们的共同魅力就三个词：免费、可自带模型、一切可控。如果你预算敏感又爱折腾，这一挂几乎能覆盖你大部分需求。下面我按"你想要什么"来带你认识几个主力，顺手把安装命令给你。

在展开之前先提醒一句选型时容易忽略的事：**留意项目活跃度**。这个领域淘汰得很快，比如曾经挺火的 Roo Code 已经在 2026 年 5 月归档停更了，用户大多迁去了 Cline 或 Kilo Code。所以下面这几个，我挑的都是当下仍在活跃维护的。

## OpenHands：开源版的"数字员工"

如果你想要的不是一个编辑器助手，而是一个"给个目标就自己拆解、自己跑完"的家伙，那 OpenHands（就是原来的 OpenDevin）是开源里最接近这个理想的。它更像一个自主 Agent 平台，风格上就是奔着"开源版 Devin"去的。

装它需要 Python 3.12 和 uv，最省事的方式是用 uv 直接拉起来跑：

```bash
uvx openhands
# 或者
pip install openhands
```

不过我得提醒你，自主度高是把双刃剑——它越自动，你就越需要盯着，成本和不可控性也水涨船高，所以务必在能轻松回滚的环境里用。

## Cline：VS Code 里最稳的那个

Cline 是 VS Code 插件形态的 Agent，在编辑器里读写代码、跑命令、把 diff 清清楚楚摆给你看。2026 年它基本被公认为"开源 VS Code Agent 里最安全的默认选择"。

最常见的装法就是在 VS Code 扩展市场里搜 Cline 装上，或者走命令行 `npm i -g cline`。装完在设置里填你的模型 API Key 就行，它支持 Anthropic、OpenAI 乃至本地模型，属于典型的自带钥匙（BYOK）玩法。如果你喜欢在 VS Code 里可视化操作，又想要开源可控，它很对味。

## Aider：老派、轻量、和 git 焊死在一起

Aider 是最早成熟的终端编程 Agent 之一，走的是极简路线，最大特色是和 git 深度绑定——每次改动都自动 commit，回滚起来特别踏实。安装官方推荐这样：

```bash
pip install aider-install && aider-install
# 或者经典方式
python -m pip install aider-chat
```

装完在你的 git 仓库里直接敲 `aider` 就启动了，接各家模型 API 都行。喜欢轻量、命令行、强 git 工作流的人会爱上它。

## opencode：谁都不想被单一厂商锁死

opencode 是 SST 社区主导的终端原生开源 Agent，它最大的卖点是"模型自由"——支持 75 家以上的模型提供商，对话本地存在 SQLite 里，用哪个模型处理你的代码完全你说了算。装法很多，随便挑：

```bash
curl -fsSL https://opencode.ai/install | bash    # 一键脚本
npm i -g opencode-ai@latest                        # npm
brew install opencode                              # macOS
scoop install opencode                             # Windows
```

如果你最怕被某一家厂商绑架、想随时在云端和本地模型之间来回切，它就是为你准备的。

## Goose：有企业背书的可扩展选手

Goose 是 Block（也就是 Square 的母公司）开源的终端 Agent，强调可扩展和自动化，生态挺活跃。安装参考官方给的脚本或发行版，配好模型后端即可。它适合想要一个有企业背书、又能自由扩展的开源终端 Agent 的人。

## 到底怎么挑

说了这么多，其实一句话就能帮你定位：想让它自己跑完整个大任务，选 OpenHands；想在 VS Code 里可视化，选 Cline；想要轻量加 git 流，选 Aider；最怕被锁厂商、想多模型自由切换，选 opencode；想要可扩展加企业背书，选 Goose。

这几个的共同好处别忘了——全都免费、都能自带 API Key 或者接本地模型，对预算敏感、又在意可控和隐私的人来说简直是福音。想看它们和官方、国产产品放在一起的完整对比，直接翻 [横向对比与选型](08-横向对比与选型.md)。

---

参考：[OpenHands](https://github.com/OpenHands/openhands) ｜ [opencode 文档](https://opencode.ai/docs/) ｜ 综述来自 Pinggy / DEV / wetheflywheel 等 2026 年开源 Agent 对比文章

← [Hermes Agent](05-Hermes-Agent.md) ｜ 下一篇：[国内 AI 编程产品](07-国内AI编程产品.md)
