# AI / RAG / Agent 架构

## 这张卡解决什么

帮助区分不同 AI 架构组件解决的问题，避免把 Prompt、Workflow、RAG、Agent、Multi-Agent、Vector DB 当成固定升级路线。

**这张卡不预设“简单确定性流程永远优先”，也不禁止 Agent 或 Multi-Agent。**

## 建议检查的维度

- 任务是否确定、可预先编排
- 是否需要动态选择工具或步骤
- 外部知识的规模、更新频率和检索方式
- 上下文长度与成本
- 质量指标和评测方式
- 延迟与吞吐
- 失败成本
- 可重复性
- 可观测性
- 权限与安全边界
- 模型能力
- 工具可靠性
- 人工确认要求
- token / API / 基础设施成本
- 状态和记忆需求

## 常见能力组件

- Prompt
- Structured Output
- Tool / Function Calling
- Deterministic Workflow
- RAG
- Search
- Memory
- Agent
- Multi-Agent
- Vector Search / Vector Database
- Model Routing
- Background / Async Execution

这些可以组合，不是互斥技术栈，也不是成熟度阶梯。

## 常见场景模式

- 明确输入输出的抽取/分类可能只需要 Prompt + Structured Output
- 可预先定义步骤的任务可能适合 Workflow + Tools
- 大量外部知识可能需要 Search / RAG
- 步骤取决于中间结果时 Agent 可能更自然
- 某些复杂协作任务可能值得 Multi-Agent
- 现有数据库扩展或独立 Vector DB 都可能适合向量检索

这些是模式，不是默认答案。

## 研究来源

- 模型/平台官方文档
- `developer-roadmap` 用于概念地图
- 目标 AI 框架/SDK 的官方实现
- 大规模成熟开源 Agent / RAG / workflow 项目
- 当前项目自己的离线评测、回放和成本数据

## 容易误导判断的说法

- “Agent 更智能”
- “Workflow 一定比 Agent 稳定”
- “Multi-Agent 一定是过度设计”
- “RAG 是 AI 项目标配”
- “Vector DB 专门做向量，所以一定最好”
- “现有数据库能做向量，所以永远不用专用产品”

这些都需要场景证据。

## 自主判断要求

AI 可以直接建议复杂方案，只要复杂度对应真实需求，并能说明为什么更简单或不同的架构在当前场景下不如它。

同样，如果简单方案已经满足目标，也不应为了体现 AI 架构复杂度而升级。
