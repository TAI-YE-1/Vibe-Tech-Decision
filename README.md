# Vibe-Tech-Decision

一个面向 Vibe Coding 的**工程决策辅助仓库**。

它不重新发明技术百科，也不替 AI 规定答案。它主要做两件事：

1. 先识别当前到底是在讨论新增能力、重构迁移、Bug、性能，还是技术选型。
2. 再把问题路由到合适的研究路径和高质量来源，让 AI 基于当前项目事实自主判断。

## 顶层 Engineering Decision Flow

~~~
用户问题
  ↓
恢复当前项目事实
  ↓
Task Classification
  ├─ new_capability
  │    → Need / Reuse / Buy / Integrate / Build
  │
  ├─ refactor_or_migration
  │    → Project Authority + scope
  │    → 对应技术研究
  │
  ├─ bug
  │    → 复现 / 根因
  │    → 必要时升级架构研究
  │
  ├─ performance
  │    → 测量瓶颈
  │    → 必要时升级架构研究
  │
  └─ technology / security / infrastructure
       → 对应 Research Route
  ↓
官方一手资料 + Source Catalog + 成熟实现 / 生产案例
  ↓
区分 fresh_external / inherited_external / model_knowledge
  ↓
AI 根据项目事实自主判断
  ↓
重大决策记录 ADR
  ↓
实现并验证
~~~

## 仓库结构

### 过程规则

- [AGENTS.md](AGENTS.md)：研究真实性、Authority scope、来源 freshness、证据和验证要求。

### Task Entry

- [routes/task-entry.yaml](routes/task-entry.yaml)：先判断问题类型，避免所有问题都机械进入 Build-vs-Buy。

### Source Catalog

- [sources/source-catalog.yaml](sources/source-catalog.yaml)：经过筛选的高质量研究起点。

Source Catalog 不是白名单。AI 可以使用更直接、更相关、更新的一手资料。

### Research Routes

Research Route 只负责：

> **“这个问题应该优先去哪几类来源研究？”**

- [Reuse / Buy / Integrate / Build](routes/reuse-and-build.yaml)
- [System Design](routes/system-design.yaml)
- [Frontend](routes/frontend.yaml)
- [Backend](routes/backend.yaml)
- [Data](routes/data.yaml)
- [AI](routes/ai.yaml)
- [Infrastructure](routes/infrastructure.yaml)

### Evals

- [Frontend Refactor Existing Project](evals/frontend-refactor-existing-project.yaml)

Evals 用真实问题检查模型是否真的执行了研究流程，而不是只复述方法论名称。

### ADR

- [ADR 模板](templates/adr.md)

## 来源在什么时候起效

来源不是自动灌入上下文。

AI 应按当前问题选择少量最相关来源，并区分：

- `fresh_external`：本轮实际访问并验证
- `inherited_external`：目标项目文档以前已经研究过
- `model_knowledge`：模型已有知识

项目内部 ADR 对外部项目的总结不能自动冒充本轮 fresh research。

推荐具体第三方技术时，如果结论依赖其当前状态，应重新检查官方一手来源。
