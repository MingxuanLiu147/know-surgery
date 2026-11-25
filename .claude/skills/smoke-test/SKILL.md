---
name: smoke-test
description: "验证已规划的操作能否组合配置并可选执行极小规模模型任务；用于扩大实验前。"
---

# 最小冒烟验证

## 输入

合法 plan、选定方法、本地输入和受限运行授权（如执行）。

## 流程

在仓库根目录运行（占位符替换为真实值）：

```bash
python .claude/skills/smoke-test/scripts/run.py --plan PLAN --output artifacts/TASK/smoke_trace.json
```

1. 使用独立输出路径；当前 helper 限制最多2条案例，注入/遗忘限制1个训练步。
2. 运行预览并追加 `--preflight` 检查实际有界配置；完整计划的 hash 不可用于另一份冒烟配置。
3. 按[执行流程](../_shared/references/execution.md)使用对应方法 hash 执行；需要2步等不同预算时走受限正常 CLI/运行入口。
4. 检查真实样本数、步数、模型加载、产物及失败原因，标明验证覆盖范围。

## 完成标准

- 交付轨迹与验证证据；配置组合标 `configured`，真实有界验证按证据标 `verified_smoke`。
- 不将冒烟运行报告为完整基准结果，不启动整个实验矩阵。

遵循[公共工作约定](../_shared/references/workflow.md)。
