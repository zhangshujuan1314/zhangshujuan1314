# Building practical AI systems

关注 **AI 工程工具、Agent 工作流、本地优先软件、知识系统与人机交互**。这里的项目以可运行原型和工程验证为主，优先解决真实工作流中的具体问题。

## Selected projects

### [MyBrain](https://github.com/zhangshujuan1314/mybrain)
个人第二大脑：URL 捕获 → LLM 理解 → FTS5 / 向量检索 → 每日回顾。强调本地优先、数据主权与安全边界。

### [CC Cockpit](https://github.com/zhangshujuan1314/cc-cockpit)
Claude Code 实时监控驾驶舱：会话、tool call、文件改动和 token / cost 可视化。

### [CineWeave Studio](https://github.com/zhangshujuan1314/cineweave-studio)
本地优先的影视拆解与创作知识工作台，覆盖媒体处理、镜头级结构化分析、AI Provider、备份与导出。

### [FrontierRadar](https://github.com/zhangshujuan1314/frontier-radar)
AI / 具身智能 / 无人机前沿情报流水线：自动抓取、翻译、评分、聚簇和精选 Feed。

### [Roundtable](https://github.com/zhangshujuan1314/roundtable)
多模型圆桌决策工具：异构模型独立盲审，提取共识与分歧，再进行对抗性审查；不让模型替人做最终裁决。

### [Star Scout Desktop Pet](https://github.com/zhangshujuan1314/star-scout-desktop-pet)
Electron 桌面宠物 + MCP Server，把 AI Agent 的状态、动作和对话反馈映射成可见的桌面交互。

## Other work

- **AI / Agent tooling** — `claude-code-skill-dashboard`, `douyin-mcp`, `ai-agent-status-light`
- **Local-first / personal software** — `time-memory`, `promptflow`
- **Visual / interactive experiments** — `earth-garden`, `cyber-flower`
- **Vertical prototypes** — `floodshield`, `quanttrader`, `nuanxingzhe-ai-next`

## Engineering preferences

- Prefer small, testable modules over large monoliths.
- Treat security boundaries, secret handling and failure modes as product requirements.
- Separate prototypes from maintained software; archive experiments after their learning goal is complete.
- Keep release binaries and deployment artifacts out of the source tree whenever possible.
