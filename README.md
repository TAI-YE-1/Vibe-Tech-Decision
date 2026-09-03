# Vibe-Tech-Decision

面向 Vibe Coding 的工程决策辅助仓库。

## Decision Flow

```text
用户问题
  ↓
恢复当前项目事实
  ↓
Task Classification
  ├─ new_capability → Need / Reuse / Buy / Integrate / Build
  ├─ refactor_or_migration → Project Authority + scope → domain research
  ├─ bug → reproduce / root cause → architecture only if needed
  ├─ performance → measure bottleneck → architecture only if needed
  └─ technology / security / infrastructure → domain research
  ↓
官方一手资料 + Source Catalog + 成熟实现 / 生产案例
  ↓
fresh_external / inherited_external / model_knowledge
  ↓
证据绑定结论
  ↓
decision_status + unresolved + change_my_mind_if
  ↓
简洁决策 + 可复核来源
  ↓
ADR / implementation / verification
```

## Structure

- [AGENTS.md](AGENTS.md)
- [routes/task-entry.yaml](routes/task-entry.yaml)
- [routes/reuse-and-build.yaml](routes/reuse-and-build.yaml)
- [routes/system-design.yaml](routes/system-design.yaml)
- [routes/frontend.yaml](routes/frontend.yaml)
- [routes/backend.yaml](routes/backend.yaml)
- [routes/data.yaml](routes/data.yaml)
- [routes/ai.yaml](routes/ai.yaml)
- [routes/infrastructure.yaml](routes/infrastructure.yaml)
- [sources/source-catalog.yaml](sources/source-catalog.yaml)
- [templates/decision-output.md](templates/decision-output.md)
- [templates/research-trace.yaml](templates/research-trace.yaml)
- [templates/adr.md](templates/adr.md)
- [templates/project-integration-snippet.md](templates/project-integration-snippet.md)
- [evals/frontend-refactor-existing-project.yaml](evals/frontend-refactor-existing-project.yaml)

## Decision Status

- `provisional`：当前最合理，但仍有可能改变结论的证据缺口
- `validated`：关键假设已有充分项目证据和适用外部证据验证
- `blocked_by_evidence`：缺少关键证据，继续下结论会影响正确行动

不使用置信度百分比。

## Source Rules

- Source Catalog 是研究入口，不是白名单。
- Discovery 来源用于发现候选，不能单独证明技术适配。
- 具体第三方技术的当前状态优先检查官方一手来源。
- 项目旧文档中的外部研究属于 `inherited_external`，不等于本轮重新验证。
- 重大外部结论应显示对应参考来源，并说明其支持的结论。

## Project Integration

需要长期使用时，把 [project integration snippet](templates/project-integration-snippet.md) 加到目标项目自己的 agent instructions 中。Vibe-Tech-Decision 保持单一规则来源，不需要把整套规则复制到每个项目。
