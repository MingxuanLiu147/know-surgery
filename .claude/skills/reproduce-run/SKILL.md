---
name: reproduce-run
description: "恢复已有运行的命令和配置；用于检查可复现性或在授权范围内重跑。"
---

# 恢复历史实验命令

## 输入

实际运行目录；非空 command.txt；可选重跑授权及独立目录。

## 流程

在仓库根目录运行（占位符替换为真实值）：

```bash
python .claude/skills/reproduce-run/scripts/run.py --run-dir RUN_DIR --output artifacts/TASK/reproduction.json
```

1. 确认运行目录和非空 `command.txt`，运行恢复命令。
2. 检查恢复出的命令、配置和环境引用；对照模型版本、数据哈希、种子和预算。
3. 重跑使用独立输出目录，重新组合配置并预检；按[执行流程](../_shared/references/execution.md)处理授权。
4. 如已实际重跑，比较对应指标与环境差异；若输入或初始 checkpoint 变化，标记为新实验。

## 完成标准

- 交付恢复 JSON 和缺失项；仅在真实重跑后提供差异分析。
- 辅助脚本不自动重跑；不根据目录名称猜测命令。

遵循[公共工作约定](../_shared/references/workflow.md)。
