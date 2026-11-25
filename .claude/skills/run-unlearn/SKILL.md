---
name: run-unlearn
description: "预览、预检或执行已注册的机器遗忘计划，同时检查遗忘与保留效果。"
---

# 运行机器遗忘

## 输入

operation=unlearning 的计划；forget/retain、初始 checkpoint、方法与预算。

## 流程

在仓库根目录运行（占位符替换为真实值）：

```bash
python .claude/skills/run-unlearn/scripts/run.py --plan PLAN --output artifacts/TASK/unlearn_trace.json
```

1. 核对初始 checkpoint、forget/retain 角色、重叠情况以及方法损失和评价配置。
2. 运行预览，追加 `--preflight` 检查同一配置；记录阻塞原因和 review_hash。
3. 按[执行流程](../_shared/references/execution.md)在授权范围执行；输入变化后重新预检。
4. 核查实际训练与遗忘/保持评价；区分数据缺失、评价未执行、低分与程序错误。

## 完成标准

- 交付轨迹、配置和实际遗忘/保留指标或明确缺失。
- 回答质量降低不能证明知识完全删除；不把未测保持能力视为正常。

遵循[公共工作约定](../_shared/references/workflow.md)。
