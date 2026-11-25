---
name: run-edit
description: "预览、预检或执行已注册的知识编辑计划；检查目标编辑及副作用。"
---

# 运行知识编辑

## 输入

operation=edit 的计划；模型、方法、数据、资源和预算。

## 流程

在仓库根目录运行（占位符替换为真实值）：

```bash
python .claude/skills/run-edit/scripts/run.py --plan PLAN --output artifacts/TASK/edit_trace.json
```

1. 核对编辑案例、模型及方法；检查层映射、统计量、辅助 checkpoint 等方法前置资产。
2. 运行预览，再对同一选择追加 `--preflight`；读取阻塞原因及 review_hash。
3. 按[执行流程](../_shared/references/execution.md)执行；存在阻塞则停止并解释缺项，不擅自改算法。
4. 核查实际完成案例、预测和评测结果；按可用协议报告 Reliability、Generalization、Locality 及其他指标。

## 完成标准

- 交付轨迹、配置、实际产物及明确的阻塞/运行状态。
- 不以进程退出码代替编辑成功；不编造未测指标。

遵循[公共工作约定](../_shared/references/workflow.md)。
