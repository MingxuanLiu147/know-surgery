---
name: batch-sweep
description: "将方法与随机种子展开为待运行实验命令；用于批量配置与复现规划，不负责调度。"
---

# 展开批量实验计划

## 输入

合法 plan、种子列表、输出路径和总体预算。

## 流程

在仓库根目录运行（占位符替换为真实值）：

```bash
python .claude/skills/batch-sweep/scripts/run.py --plan PLAN --seeds 42,43,44 --output artifacts/TASK/sweep.json
```

1. 核对计划组件、方法列表、输入一致性和预算；种子去重。
2. 生成 sweep manifest，逐项核对方法×种子、独立任务名、命令及哈希。
3. 检查有效样本、更新预算、输出目录是否冲突；代表性任务先完成预检/冒烟。
4. 仅在已有授权后通过正常执行入口调度实际运行；保留失败和未完成项。

## 完成标准

- 交付待运行命令清单及配置差异/成本说明。
- 生成 pending 命令不等于完成实验；脚本不提交集群作业。

遵循[公共工作约定](../_shared/references/workflow.md)。
