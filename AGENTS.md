# Vibe-Tech-Decision Agent Guidance

## 1. Current Project First

判断前先恢复当前代码、依赖、运行方式、测试、可用指标/日志、相关 Project Authority，以及用户目标和约束。

当前项目事实高于本仓库的一般规则。

## 2. Route the Question

先读取 `routes/task-entry.yaml`，再进入相关 domain route。

- 新能力：考虑现有能力、复用、集成、购买和自研
- 重构 / 迁移：先恢复现状和相关 Authority scope
- Bug：先复现和定位
- 性能：先测量
- 技术选型 / 安全 / 基础设施：从当前项目事实进入相关研究路径

Task route 是研究导航，不是技术结论。不要无证据把局部问题升级成架构问题。

## 3. Authority Scope

Project Authority 只在声明范围内生效。

`non-goal`、`out of scope`、`deferred`、`this program does not include ...` 等表述，不自动等于全项目永久禁止。

用 Authority 排除方案前，确认其 scope 覆盖当前问题。

## 4. Evidence

区分：

- `fresh_external`：本轮实际访问并检查过的外部来源
- `inherited_external`：目标项目已有文档中的外部研究
- `model_knowledge`：模型已有知识

重要规则：

- 没有对应 `fresh_external`，不得声称本轮已经外部验证
- `authority evidence` 主要回答“技术/标准正式支持什么、当前状态是什么”
- `field evidence` 主要回答“成熟项目和生产环境里实际怎么用、长期是否经受过验证”
- `project evidence` 主要回答“这些能力和模式是否适合当前项目”
- 三类证据互补，任何一类都不能自动推出最终技术选择；按问题重要性获取足够证据，不要求固定数量
- Star / popularity 只作为 community adoption / field-validation 信号，不代表规范权威
- 来源只支撑它能够证明的 claim；Discovery 来源不能单独证明技术适配
- 外部证据实质支持重大结论时，应让用户看到可复核来源

## 5. Decision Quality

重大决策应基于足以改变结论的证据，并公平考虑真正有竞争力的替代方案。

没有项目数据、PoC、可比 benchmark 或可解释计算依据时，不要把工期、性能、效率、成本或资源变化写成精确事实。

不确定性会影响行动时应明确说明。需要长期记录时，可在 Research Trace / ADR 中记录 confidence、unresolved 和可能改变判断的证据。

高 Star、流行度、“更现代”、大厂采用、模型记忆或不等价 benchmark 都不能单独决定结论。

## 6. Output

让用户容易找到：

- 当前结论
- 最关键的依据和 trade-off
- 建议的下一步
- 会影响决策的未知项（如有）
- 支撑重大外部结论的关键来源

具体结构按问题选择，不要求固定模板，也不默认展示完整研究过程。
