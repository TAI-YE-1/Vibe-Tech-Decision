# Vibe-Tech-Decision Agent Guidance

## 1. Current Project First

判断前优先恢复：

- 当前代码、依赖、运行方式和测试
- 指标、日志、可复现问题
- 当前 Project Authority / roadmap / ADR
- 用户目标和约束

当前项目事实高于本仓库的一般规则。

## 2. Classify the Task

先读取 `routes/task-entry.yaml`。

- `new_capability`：先判断 current capability / reuse / buy / integrate / build
- `refactor_or_migration`：先恢复现状和 Project Authority scope，再进入 domain route
- `bug`：先复现和定位
- `performance`：先测量
- `technology_selection`：恢复项目事实后进入 domain route
- `security_or_infrastructure`：恢复项目事实和相关 authority 后进入 domain route

不要把所有问题机械套入 Build-vs-Buy，也不要无证据把局部问题升级成架构问题。

## 3. Authority Scope

Project Authority 只在声明范围内生效。

以下表述不得自动解释为全项目永久禁止：

- `this program does not include ...`
- `this decision does not authorize ...`
- `non-goal`
- `out of scope`
- `deferred`

用某份 Authority 排除方案前，确认其 scope 覆盖当前问题。

## 4. Evidence Classes

- `fresh_external`：本轮实际访问并检查过的外部来源
- `inherited_external`：目标项目文档中已有的外部研究
- `model_knowledge`：模型已有知识

没有对应 `fresh_external` 时，不得声称“已查官方资料”“已基于当前外部可信来源验证”。

## 5. Source Roles

- discovery / ecosystem list：发现候选
- official / primary source：验证当前能力、状态、版本、限制
- comparison / trade-off：比较方案
- mature implementation / production case：验证真实落地模式
- methodology：组织决策过程

Discovery 来源不能单独支撑最终技术推荐。

## 6. Conclusion Binding

重大工程判断中：

- 关键外部事实必须来自实际检查过的来源
- 关键推荐必须能映射到项目事实和外部证据
- 外部证据实质支持结论时，最终回答应给出可见参考来源
- 来源应说明支持哪条关键结论
- 推论必须标明为推论，不得伪装成来源原文结论

## 7. Freshness

推荐具体第三方框架、库、平台、SaaS、数据库、基础设施产品或 AI SDK 时，若结论依赖其当前状态，优先核对官方一手来源：

- active / archived
- deprecated / sunset
- renamed / migrated
- current supported version
- current official recommendation

Catalog metadata 和项目历史文档均为时间点快照。

## 8. Research Quality

重大决策通常应覆盖：

- 当前项目事实 / 测量
- 候选技术官方一手资料
- 成熟实现、生产案例或可靠交叉验证
- 主要替代方案
- 验证与回滚

不要求固定来源数量。

## 9. Quantitative Claims

没有项目历史数据、PoC、等价 benchmark 或可解释计算依据时，不得把以下内容写成事实：

- 工期 / 人周
- 性能或效率提升百分比
- 代码量或成本下降百分比
- 资源体积变化
- “解决 X% 问题”

粗估必须标明为 heuristic estimate，并说明依据和不确定性。

## 10. Weak Reasoning

以下不能单独构成结论：

- 更现代 / 更企业级
- 以后可能需要
- 大厂都在用
- 高 Star
- 模型记忆
- 与当前场景不等价的 benchmark

## 11. Output

复杂判断应能区分：

- facts
- assumptions / unknowns
- candidates / trade-offs
- recommendation
- fresh external evidence
- inherited external evidence
- conclusion-to-evidence mapping
- visible references
- verification / rollback

不要求机械套模板。
