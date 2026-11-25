---
name: compare-methods
description: "比较 Know-Surgery 已有运行的指标与实验条件；用于方法对照、检查模型或数据是否一致，以及判断结果能否公平比较。"
---

# 比较方法与实验条件

## 输入

至少两个运行目录。输入是目录，不是 aggregate.json。

## 流程

在仓库根目录运行（占位符替换为真实值）：

```bash
python .claude/skills/compare-methods/scripts/run.py RUN_A RUN_B --output artifacts/TASK/comparison.json
```

1. 查看各运行的配置、轨迹和评价文件，明确比较目标效果、副作用或成本。
2. 运行比较命令，检查 `fairness`、`metric_alignment` 和 `comparable`；区分证据缺失（`known=false`）与已知条件不一致。
3. 另外读取 `resolved_config.yaml` 核查样本范围、更新步数和有效 batch；这些预算不由比较器完整保证。
4. 核对指标分母、方向及评分协议；比较耗时还需相同硬件和工作量。
5. 证据充分才给出有范围的结论；否则列出具体差异或待补信息。脚本输出比较数据，解释和作图由 Agent 完成。

## 完成标准

- 交付比较 JSON、具体差异及来源，说明哪些指标可比较。
- 不因文件夹同名或单个布尔值就断言公平，不把缺失条件补为相同。

遵循[公共工作约定](../_shared/references/workflow.md)。
