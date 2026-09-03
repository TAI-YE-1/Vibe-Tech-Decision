# Vibe-Tech-Decision

面向 Vibe Coding 的工程决策辅助仓库。

## Decision Flow

```text
用户问题
  ↓
当前项目事实
  ↓
Task Classification
  ↓
相关 Research Route
  ↓
项目证据 + 当前外部证据
  ↓
比较与判断
  ↓
结论 + 关键来源 + 验证
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

Source Catalog 是研究入口，不是白名单。重大外部结论应由实际检查过且适用的来源支撑。

需要长期使用时，可把 [project integration snippet](templates/project-integration-snippet.md) 加到目标项目自己的 agent instructions 中；无需复制整套规则。
