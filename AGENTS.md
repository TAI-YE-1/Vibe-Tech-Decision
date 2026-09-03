# Vibe-Tech-Decision Agent Guidance

本仓库用于增强工程决策质量，不是技术政策引擎。

## 1. 当前项目事实优先

在具体项目里做判断前，优先恢复：

- 当前代码和依赖
- 运行方式
- 测试
- 已知指标、日志和可复现问题
- 正式治理/架构文档
- 用户明确的业务目标和约束

本仓库的一般流程不能覆盖当前项目事实。

## 2. 先识别问题类型

先读取 `routes/task-entry.yaml`，判断当前问题更接近：

- `new_capability`
- `refactor_or_migration`
- `bug`
- `performance`
- `technology_selection`
- `security_or_infrastructure`

不要把所有问题都机械套入 Build-vs-Buy。

### 新增能力

对于较大的新增能力、基础设施或系统组件，优先判断：

- 不修改 / 保持现状
- 使用或组合当前项目已有能力
- 对现有能力做有限扩展
- 复用成熟开源 / Self-hosted 项目
- 集成现成 API
- 使用 SaaS / PaaS / 托管服务
- 自研或深度定制

### 重构 / 迁移

先恢复当前架构事实和相关 Project Authority 的适用范围，再进入对应 research route。

### Bug / 性能

先复现、定位或测量。只有本地证据表明需要架构层变化时，才升级到架构研究。

## 3. Project Authority 只在声明范围内生效

读取项目治理或架构文档时，必须区分：

- authority scope
- current program / work package scope
- non-goal
- not authorized
- deferred
- project-wide invariant

不得把：

- `this program does not include ...`
- `this decision does not authorize ...`
- `non-goal`
- `out of scope`

自动解释成全项目永久禁止。

如果用某份 Project Authority 排除一个候选方案，必须确认该文档的 scope 确实覆盖当前用户问题。

## 4. Research Execution Contract

重大工程判断中，以下三类证据必须区分：

### fresh_external

本轮实际访问并检查过的外部来源。

包括：

- 官方文档
- 官方仓库
- 标准 / RFC
- 当前成熟开源项目
- 当前生产案例
- 当前 benchmark

### inherited_external

目标项目自己的文档、ADR、diagnostics 或历史研究中已经总结过的外部来源。

它可以作为项目上下文，但不等于本轮重新验证。

### model_knowledge

模型已有知识、经验或记忆。

它可以帮助发现方向，但不能冒充本轮外部研究。

### 声明约束

只有存在对应的 `fresh_external` 证据时，才能声称：

- “已基于外部可信来源研究”
- “已查官方资料”
- “经过当前外部资料验证”

如果本轮没有实际访问外部来源，应明确说明当前结论主要来自项目事实、Project Authority、inherited research 或模型知识。

不要求向用户机械输出完整 Research Trace，但复杂决策必须能够说明证据属于哪一类。

## 5. 结论必须和证据绑定

Source 的作用不是装饰回答，而是参与结论形成并让用户能够复核。

对于框架迁移、数据库、基础设施、认证、核心架构、重要第三方技术等重大工程判断：

- 关键外部事实必须来自实际检查过的来源；
- 关键推荐必须能说明由哪些项目事实和哪些外部证据支持；
- 如果外部证据 materially supports 最终结论，默认在最终回答中给出用户可见的参考来源；
- 来源应尽量贴近它所支持的结论，不要只在末尾堆一个与结论无映射的链接列表；
- 不要求每个常识句子都引用，也不要求固定来源数量。

一个来源只负责它能够证明的内容。

例如：

- discovery / ecosystem list：用于发现候选，不能单独证明候选适合当前项目；
- 官方/primary source：用于验证技术当前能力、状态、版本和正式约束；
- comparison / trade-off reference：用于比较相邻方案；
- mature implementation / production case：用于证明某种模式在真实系统中如何落地；
- methodology：用于帮助组织决策，不直接证明具体技术适配。

如果最终建议主要来自模型推理，应明确它是基于已列事实和证据作出的推论，不要把推论伪装成来源原文结论。

## 6. Source Catalog 不是白名单

`sources/source-catalog.yaml` 是研究起点，不是允许来源列表。

AI 可以并且应该主动发现：

- 候选技术自己的官方文档和官方仓库
- 标准、RFC、协议规范
- 与当前场景更接近的成熟项目
- 当前时间更近的生产案例、事故复盘或 benchmark
- catalog 尚未覆盖的高质量来源

不要因为来源不在 catalog 中就排除，也不要因为来源在 catalog 中就自动相信。

## 7. 推荐具体第三方技术前检查当前状态

当建议具体的外部：

- 框架
- 库
- 平台
- SaaS
- 数据库
- 基础设施产品
- AI framework / SDK

在结论依赖其“当前可用、仍维护、仍推荐”状态时，应优先检查当前官方一手来源。

至少关注：

- active / archived
- deprecated / sunset
- renamed / migrated
- current supported version
- current official recommendation

Source Catalog 的 metadata 和项目历史文档都只是时间点快照，不能自动视为当前状态。

## 8. Star 只是一种市场验证信号

30k / 10k 是本仓库用于筛选社区型研究入口的启发式，不是行业标准，也不是可信度分数。

官方一手资料、标准、技术自身仓库不受 Star 门槛限制。

高 Star 也不能替代：

- 场景相关性
- 当前维护状态
- 一手证据
- 当前项目测量

## 9. 重大工程决策的研究质量

对于更换框架、数据库、认证体系、核心存储/通信模型，或引入重要基础设施和 AI 架构等重大修改，通常应尽量获得：

- 当前项目事实 / 测量
- 候选技术官方一手资料
- 一个或多个成熟实现、生产案例或可靠交叉验证
- 对主要替代方案的公平比较
- 验证与回滚方式

不要求固定数量，也不要求来源必须来自本仓库。

## 10. 不伪造精确数字

没有目标项目历史数据、PoC、等价 benchmark 或可解释计算依据时，不要把以下内容写成事实：

- 开发工期 / 人周
- 性能提升百分比
- 开发效率提升百分比
- 代码量减少百分比
- 成本节省比例
- 资源体积变化
- “解决 X% 问题”

可以给出定性判断。

如果必须给粗估，应明确标记为 heuristic estimate，并说明依据和不确定性。

## 11. 避免弱推理

以下内容可以作为线索，但不能单独构成结论：

- “更现代”
- “更企业级”
- “以后可能需要”
- “大厂都在用”
- “高星项目这么做”
- “AI 以前见过类似项目这么做”
- benchmark 条件与当前场景不等价

## 12. 输出方式

复杂判断应尽量区分：

- 事实
- 假设
- 未知项
- 候选
- 关键 trade-off
- 建议
- fresh external evidence
- inherited external evidence
- 关键结论与证据的对应关系
- 用户可见参考来源
- 验证方式

不要求机械输出模板。

如果多个方案都合理，可以明确说多个方案都合理；不要为了显得确定而伪造唯一答案。
