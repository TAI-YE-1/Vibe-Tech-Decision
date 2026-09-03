# Vibe-Tech-Decision

一个面向 Vibe Coding 的**工程决策辅助仓库**。

它不重新发明技术百科，也不替 AI 规定答案。它主要做两件事：

1. 在新增较大能力前，先提醒 AI 判断：**现有能力、成熟开源、API、SaaS/PaaS 是否已经足够，是否真的需要新增开发。**
2. 如果仍然需要开发，再把问题路由到经过筛选的高质量研究来源，让 AI 基于当前项目事实自主完成架构与技术判断。

## 顶层 Engineering Decision Flow

~~~
需求出现
  ↓
恢复当前项目事实
  ↓
确认真正目标、约束和成功标准
  ↓
Need / Reuse / Buy / Integrate / Build
  ├─ 当前项目已经能满足？
  ├─ 组合或扩展现有能力即可？
  ├─ 成熟开源 / Self-hosted 可复用？
  ├─ 现成 API 可集成？
  ├─ SaaS / PaaS 更合适？
  └─ 自研 / 深度定制更合适？
  ↓
如果需要 Build / 深度集成
  ↓
Architecture / Technology Research
  ↓
官方一手资料 + Source Catalog + 成熟实现 / 生产案例
  ↓
AI 根据项目事实自主判断
  ↓
重大决策记录 ADR
  ↓
实现并验证
~~~

这不是死板流水线。明显属于核心自研能力、或约束已经排除外部方案时，AI 不需要为了流程形式而穷举所有产品；说明依据后可以直接进入 Build / Architecture。

## 仓库结构

### 过程规则

- [AGENTS.md](AGENTS.md)：约束研究质量和证据方式，不规定技术答案。

### Source Catalog

- [sources/source-catalog.yaml](sources/source-catalog.yaml)：经过筛选的高质量研究起点。

Source Catalog 不是白名单。AI 可以使用更直接、更相关、更新的一手资料。

### Research Routes

Research Route 只负责：

> **“这个问题应该优先去哪几类来源研究？”**

它不写 Redis、SSE、React、Agent 等具体技术的自创判断规则。

- [Reuse / Buy / Integrate / Build](routes/reuse-and-build.yaml)
- [System Design](routes/system-design.yaml)
- [Frontend](routes/frontend.yaml)
- [Backend](routes/backend.yaml)
- [Data](routes/data.yaml)
- [AI](routes/ai.yaml)
- [Infrastructure](routes/infrastructure.yaml)

### ADR

- [ADR 模板](templates/adr.md)

## 来源在什么时候起效

来源不是自动灌入上下文。

AI 应按当前问题选择少量最相关来源。例如：

- 新增一个较大的产品能力 → 先走 `reuse-and-build`
- 确认需要自研，而且涉及缓存/通信/扩展性 → `system-design`
- 前端框架或架构问题 → `frontend`
- Python / Node.js / Go / Rust 后端生态 → `backend`
- 数据库 / 存储问题 → `data`
- RAG / Agent / Model / AI 工程 → `ai`
- Kubernetes / Cloud Native / 平台基础设施 → `infrastructure`

Route 只是研究导航。最终判断仍来自：

> 当前项目事实 + 官方一手资料 + 相关成熟证据 + AI 自主推理
