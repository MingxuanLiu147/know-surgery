---
name: inspect-repo
description: "选择或扩展知识更新工作流前，盘点模型、数据集、Trainer、配方和 Skills。"
---

# 仓库能力盘点

## 输入

当前仓库源码；目标操作或待查组件。

## 流程

在仓库根目录运行（占位符替换为真实值）：

```bash
python .claude/skills/inspect-repo/scripts/run.py --output artifacts/TASK/inventory.json
```

1. 执行盘点命令，获取已注册组件 ID 和配方。
2. 按 operation、modality、model、dataset、method 筛选相关条目。
3. 读取匹配的 `configs/` 和实现，核对方法资产、配置约束及已有证据。
4. 有精确配方时优先复用；没有时明确适配缺口，不猜测组件 ID。

## 完成标准

- 交付清单及可复用组件、限制。
- 注册或存在配置不等于已成功运行；盘点不修改源码或运行产物。

遵循[公共工作约定](../_shared/references/workflow.md)。
