---
name: run-inject
description: "预览、预检或执行已注册的知识注入计划；检查目标、泛化和保持能力。"
---

# 运行知识注入

## 输入

operation=inject 的计划；指定方法、数据、模型、设备及预算。

## 流程

在仓库根目录运行（占位符替换为真实值）：

```bash
python .claude/skills/run-inject/scripts/run.py --plan PLAN --output artifacts/TASK/inject_trace.json
```

1. 核对实际配方、模型、训练输入、适配器与预算；图文任务使用 `modality=multimodal`，绑定案例进入 `data.train_path`，独立保持探针通过计划的 `overrides.data.retain_path` 指定。
2. 运行预览；对同一参数追加 `--preflight`，检查结果与 review_hash。
3. 检查实际评价入口和数据：目标、泛化及保持能力（WikiDYK 的 locality/reference 等）；不要以计划 evaluator 名称代替评价配置。
4. 按[执行流程](../_shared/references/execution.md)完成授权与执行；可按需指定 `--method`、`--cuda`、`--timeout`。
5. 检查实际训练步数、输入范围、保存目录及评价结果；独立评价集与训练集诊断分开。

## 完成标准

- 交付真实状态、配置、轨迹及已产生的目标/副作用指标。
- 缺失指标标为不可用；仅预览或退出0不得当作有效实验结果。

遵循[公共工作约定](../_shared/references/workflow.md)。
