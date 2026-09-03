# Vibe-Tech-Decision

一个面向 Vibe Coding 的**技术决策库**。

它不试图重新写一套技术百科，也不替代官方文档。目标只有一个：

> 当你不知道“要不要做、该用什么、为什么这样选”时，让 AI 先走一套可验证的决策流程，再写代码。

## 核心原则

1. **先复用，后自研**：先查成熟开源项目、现成 API、SaaS/PaaS，再决定是否开发。
2. **先证明问题，再引入技术**：没有项目事实和瓶颈证据，不因为“流行”“高级”“以后可能需要”引入新技术。
3. **重大决策必须多源验证**：项目本地证据 + 官方资料 + 高市场验证来源/成熟实现。
4. **高星不是唯一标准，但低星个人仓库不能作为重大决策依据**。
5. **最小方案优先**：能用现有架构解决，就不增加新组件。

## AI 决策流程

~~~
需求
  ↓
1. 问题到底是什么？有代码/运行数据证据吗？
  ↓
2. 能不能不做？
  ↓
3. 有成熟开源 / API / SaaS 可以直接复用吗？
  ↓
4. 当前项目已有能力能不能解决？
  ↓
5. 如果必须新增技术，候选有哪些？
  ↓
6. 查官方资料 + 高星参考 + 成熟实现
  ↓
7. 比较收益、复杂度、维护成本、退出成本
  ↓
8. 选择最小可行方案
  ↓
9. 记录 ADR（重大决策）
  ↓
10. 再实现并验证
~~~

## 第一版内容

### 决策卡

- [是否应该自己开发](decisions/build-vs-buy.md)
- [前端框架怎么选](decisions/frontend-framework.md)
- [数据库怎么选](decisions/database.md)
- [实时通信怎么选](decisions/realtime.md)
- [缓存什么时候该引入](decisions/cache.md)
- [AI / RAG / Agent 怎么选](decisions/ai-architecture.md)

### 可信来源

见 [sources/trusted-sources.yaml](sources/trusted-sources.yaml)。

当前核心来源只收录经过大量市场验证的项目，或官方/标准组织资料。Star 只是准入信号之一，不代表技术结论本身。

### 模板

- [新决策卡模板](templates/decision-card.md)
- [ADR 模板](templates/adr.md)

## 给 AI 使用

本仓库的执行规则在 [AGENTS.md](AGENTS.md)。

在其他项目里做重大技术选型时，可以让 AI 先读取本仓库的：

1. `AGENTS.md`
2. `sources/trusted-sources.yaml`
3. 与问题对应的 `decisions/*.md`
4. 再读取目标项目自己的代码、文档、测试和运行证据

**目标项目事实永远优先于本仓库的一般建议。**

## 现在不做什么

第一版刻意不加入：

- Web UI
- 数据库
- MCP Server
- RAG / 向量数据库
- 自动改写技术结论
- 自动按 Star 选择技术

先验证这套决策流程是否真的能改善 Vibe Coding，再决定是否增加工具层。
