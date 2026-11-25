---
name: aggregate-results
description: "收集已有运行目录的机器可读指标并保留来源；用于结果整理，不推断缺失数据。"
---

# 汇总实验结果

## 输入

一个或多个实际运行目录。

## 流程

在仓库根目录运行（占位符替换为真实值）：

```bash
python .claude/skills/aggregate-results/scripts/run.py RUN_A RUN_B --output artifacts/TASK/aggregate.json
```

1. 核对各运行目录、命令、配置、范围、输入清单与指标文件。
2. 运行汇总命令；检查指标键、源文件、评测器和 checkpoint 位置。脚本读取根目录及已保存的最终 Trainer step 对应的 checkpoint，不混入中间结果。
3. 区分最终结果与中间 checkpoint；核对分母、样本范围和证据等级。
4. 缺失指标保留 null/N/A；若要排名，先用 `compare-methods` 核查可比性。

## 完成标准

- 交付汇总 JSON 与缺失/失败项说明。
- 不从任意日志猜数，不混合冒烟与完整运行得出排名。

遵循[公共工作约定](../_shared/references/workflow.md)。
