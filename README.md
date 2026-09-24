# 墨坊 · 网文生产线

你的 AI agent 当写手，你当主编。墨坊把一本网文从灵感、选题、设定、大纲到逐章写作、试读、自改、定稿拆成一步步的任务书；agent 按任务书写，遇到需要你拍板的地方（选题、选稿、审批）就停下来等你。

- 不需要 API Key：用你已经在用的 agent（Claude Desktop、Claude Code、Codex、Cursor、Gemini CLI……）和它的模型。
- 番茄向：都市、仙侠、女频、规则怪谈等题材包，黄金三章、爽点节奏、去 AI 味都内置在任务书里。
- 长篇不崩：分层记忆，写到几百章，任务书大小基本不变；伏笔、人物状态、已确立事实都有账本。
- 短剧剧本：原创短剧剧本 + 动态漫 / 真人 / AI 视频分镜，导出 Excel 拍摄表。
- 工作台：浏览器里读稿、改稿、审批、看进度。
- 书都在你自己电脑上的一个文件夹里，是普通的 Markdown 文件。

![墨坊工作台 · 书库总览](https://raw.githubusercontent.com/hweiei/mofang/main/docs/images/library.jpg)

## 看看它长什么样

agent 在后台写，你在工作台（`novel ui`）里读稿、拍板、下指令。下面都是真实界面，书是用墨坊写的演示书。

**读稿与终审**：左边章节，中间正文，右边是程序数出来的体检（字数、对话占比、句长、AI 腔）和这一章的账本。不满意可以直接改稿，你的改动会被记下来，之后的章节会学你的语感。

![读稿与终审](https://raw.githubusercontent.com/hweiei/mofang/main/docs/images/chapters.jpg)

**多稿对比**：每章可以出多稿，初稿和自改稿逐句对比，挑一稿定稿。

![多稿对比](https://raw.githubusercontent.com/hweiei/mofang/main/docs/images/drafts.jpg)

| 大纲与规划 | 伏笔看板 |
|---|---|
| ![大纲](https://raw.githubusercontent.com/hweiei/mofang/main/docs/images/plan.jpg) | ![伏笔看板](https://raw.githubusercontent.com/hweiei/mofang/main/docs/images/threads.jpg) |
| 选题、设定、卷纲、大纲都在这里审，主线和每章的事件 / 爽点 / 钩子一目了然。 | 每章埋下和回收的伏笔自动记账，太久没推进的会提醒。 |

| 质量体检 | 短剧剧本 |
|---|---|
| ![体检](https://raw.githubusercontent.com/hweiei/mofang/main/docs/images/health.jpg) | ![短剧剧本](https://raw.githubusercontent.com/hweiei/mofang/main/docs/images/drama.jpg) |
| 作者改动率、穿帮、返工、坏例复发……只报数字、不打分，改了提示词可以和基线比。 | 原创短剧剧本，配读者试读反馈；可再出动态漫 / 真人 / AI 视频分镜和 Excel 拍摄表。 |

| 本书总览 | 夜读模式 |
|---|---|
| ![本书总览](https://raw.githubusercontent.com/hweiei/mofang/main/docs/images/overview.jpg) | ![夜读模式](https://raw.githubusercontent.com/hweiei/mofang/main/docs/images/chapters-dark.jpg) |
| 书脊式书架、节奏曲线、下一步由谁来做。 | 写到深夜也不刺眼。 |

## 下载

到 [Releases](../../releases) 下载对应系统的压缩包，解压得到 `novel`（Windows 上是 `novel.exe`）。

| 系统 | 文件 |
|---|---|
| Windows 10 / 11 | `mofang-windows-x64.zip` |
| macOS（M 系列芯片） | `mofang-macos-arm64.tar.gz` |
| macOS（Intel） | `mofang-macos-x64.tar.gz` |
| Linux | `mofang-linux-x64.tar.gz` / `mofang-linux-arm64.tar.gz` |

建议把 `novel` 放进一个固定的位置（例如 `D:\墨坊\novel.exe` 或 `/usr/local/bin/novel`），后面的配置里要填它的路径。

## 三步开始

**1. 建书房**（放你所有书的文件夹）

```
novel setup D:\我的书房
```

它会打印好接入各个 agent 的配置，照着复制就行。

**2. 接上你的 agent**（任选一种）

- **Claude Desktop**：设置 → 开发者 → 编辑配置，把 `novel setup` 打印的那段 `mcpServers` 粘进去，重启 Claude Desktop。之后在对话框里说“用墨坊帮我开一本都市神医文”即可。
- **Claude Code**：`claude mcp add mofang -- <novel 路径> mcp --root <书房路径>`；或者直接在书房目录里打开 Claude Code，它会读 `CLAUDE.md` / `AGENTS.md`，用命令行干活。
- **Cursor**：把那段 `mcpServers` 放进书房里的 `.cursor/mcp.json`；或者直接打开书房文件夹。
- **Codex**：把打印的 `[mcp_servers.mofang]` 放进 `~/.codex/config.toml`；或者在书房目录里运行 Codex。
- **其他能跑命令的 agent**：在书房目录里打开，让它先读 `AGENTS.md`。

**3. 开写**

告诉 agent 你的题材和一句话灵感。它会先整理灵感卡、问你几个问题，再出三个选题方案给你挑。之后每到需要你决定的地方，它会停下来告诉你怎么选：

```
novel pick premise 2      选第 2 个选题
novel approve bible       批准设定
novel pick 1 2            第 1 章选第 2 稿
novel ui                  打开工作台（浏览器里读稿、改稿、审批）
```

这些也可以直接在工作台里点。

## 常见问题

**Windows 提示“Windows 已保护你的电脑”**：点“更多信息” → “仍要运行”。

**macOS 提示“无法打开，因为无法验证开发者”**：在终端运行 `xattr -d com.apple.quarantine <novel 路径>`，或在“系统设置 → 隐私与安全性”里点“仍要打开”。

**我的书在哪？** 都在书房文件夹的 `novels/` 下，每本书一个文件夹。建议用网盘或 git 备份这个文件夹。

**怎么升级？** 下载新版本覆盖 `novel` 即可，书房不用动。第一次运行新版本时，内置提示词和题材包会解到 `~/.mofang/engine/` 下对应版本的目录。

**能改提示词吗？** 能。`novel prompt list` 看每个提示词用的哪一层，`novel prompt edit` 保存你自己的版本（全局或只对某本书），随时可以 `novel prompt reset` 回到内置版。

**卸载**：删掉 `novel` 程序和 `~/.mofang/` 文件夹。书房是你的数据，不会被动到。

## 许可

墨坊是闭源软件，免费使用，详见 [LICENSE](LICENSE)。用墨坊写出来的作品，版权归你。
