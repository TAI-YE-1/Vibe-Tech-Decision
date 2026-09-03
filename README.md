# Vibe-Tech-Decision

一个面向 Vibe Coding 的**技术决策辅助库**。

它不试图重新写技术百科，也不替代官方文档，更不试图替 AI 规定答案。

> 目标：给 AI 更好的问题框架、研究起点和验证要求，让强模型能够基于当前项目事实自主判断，而不是临场猜测或机械套规则。

## 核心原则

1. **项目事实优先**：当前代码、运行数据、约束和已有架构优先于本仓库的一般经验。
2. **决策卡是提示，不是答案**：用于防止漏掉关键维度，不规定 PostgreSQL、Redis、SSE、React、Agent 等技术必须用或不能用。
3. **来源目录不是白名单**：它提供高质量研究起点，AI 可以主动发现更相关的新来源。
4. **多维评估来源**：官方性、市场验证、维护状态、与当前问题的相关性要分开看；Star 只反映市场验证的一部分。
5. **重大判断要可解释、可验证**：说明事实、假设、候选、trade-off、证据和验证方法。
6. **允许偏离启发式**：如果当前项目证据支持更不同或更复杂的方案，AI 应明确说明理由并采用更合适的方案。

## 推荐工作流

~~~
需求
  ↓
恢复当前项目事实
  ↓
明确问题、约束和成功标准
  ↓
读取相关 decision lens，检查是否遗漏关键维度
  ↓
主动发现候选方案（包括复用、自研、现有技术、新技术）
  ↓
查询官方一手资料 + source catalog + 更相关的新来源
  ↓
比较 trade-off、成本、风险、迁移/退出路径
  ↓
AI 根据项目事实自主判断
  ↓
重大决策记录 ADR
  ↓
实现并验证
~~~

这个流程不是固定流水线。简单问题可以缩短；复杂或高风险问题应增加研究深度。

## 第一版内容

### Decision lenses

- [Build vs Buy / Reuse](decisions/build-vs-buy.md)
- [前端框架与前端架构](decisions/frontend-framework.md)
- [数据库与数据存储](decisions/database.md)
- [实时通信](decisions/realtime.md)
- [缓存](decisions/cache.md)
- [AI / RAG / Agent 架构](decisions/ai-architecture.md)

### Source catalog

见 [sources/source-catalog.yaml](sources/source-catalog.yaml)。

它记录的是已经筛选过的研究入口及其不同质量信号，而不是“允许使用的唯一来源”。

### 模板

- [Decision lens 模板](templates/decision-card.md)
- [ADR 模板](templates/adr.md)

## 给 AI 使用

本仓库的过程规则在 [AGENTS.md](AGENTS.md)。

在其他项目做重大技术判断时，可优先读取：

1. 目标项目自己的治理文件、代码、测试和运行证据
2. 本仓库的 `AGENTS.md`
3. 与问题对应的 `decisions/*.md`
4. `sources/source-catalog.yaml`
5. 针对当前问题主动发现的官方资料、成熟项目和更相关证据

**不要因为来源不在 catalog 中就忽略它，也不要因为来源在 catalog 中就自动相信其结论。**

## 第一版刻意不做

- Web UI
- 数据库
- MCP Server
- RAG / 向量数据库
- 自动生成技术结论
- 自动按 Star 或固定规则选技术
- 把 decision lens 当成 policy engine

先验证这套结构是否真的提高技术判断质量，再决定是否工具化。
