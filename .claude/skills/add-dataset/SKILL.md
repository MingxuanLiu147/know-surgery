---
name: add-dataset
description: "将自定义数据集接入现有数据契约、配置和公共 CLI；支持复用已有适配器。"
---

# 接入数据集

## 输入

数据文件、operation、字段、来源/划分、目标加载与评测要求。

## 流程

在仓库根目录运行（占位符替换为真实值）：

```bash
python .claude/skills/add-dataset/scripts/run.py --path CONFIG_YAML --output artifacts/TASK/dataset_validation.json
```

1. 查看 `src/data/`、`configs/data/datasets/` 与目标操作契约；语义匹配时复用现有 adapter（如 `Canonical_edit`）。
2. 准备可被配置系统选择的数据集配置；仅在必要时新增 handler 和相应注册。
3. 用辅助命令检查 YAML mapping；用实际加载器读取少量样本，核查目标、探针及角色。
4. 组合公共 CLI 配置、预检，并在已授权范围完成小规模实际执行；保留原始文件、来源、版本和划分。

## 完成标准

- 交付配置、加载验证和已请求的运行/评价证据。
- 结构校验不等于注册、加载或运行成功；不另建训练框架。

遵循[公共工作约定](../_shared/references/workflow.md)。
