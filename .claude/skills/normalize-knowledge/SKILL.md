---
name: normalize-knowledge
description: "将自定义 JSON、JSONL、CSV 或 TXT 规范化为指定操作的知识记录；用于数据接入前。"
---

# 知识数据规范化

## 输入

原始文件、operation、知识类型与角色；原始目标答案及来源信息。

## 流程

在仓库根目录运行（占位符替换为真实值）：

```bash
python .claude/skills/normalize-knowledge/scripts/run.py --input INPUT --operation edit --knowledge-type fact --output artifacts/TASK/normalized.jsonl
```

1. 先查看输入记录和目标数据契约；保留原文件。
2. 执行规范化；注入使用 train，编辑使用 edit；遗忘保留 `dataset_role`，或分别提供 `--role forget` / `--role retain`。
3. 检查 JSONL 及对应 `.rejected.json`、`.manifest.json`；非零退出或空输入时定位错误。
4. 保持 ID、来源、时间、条件和已有探针；TXT 仅按空行分段，不自动抽取缺失问答。

## 完成标准

- 交付规范化文件及接受/拒绝统计和来源清单。
- 缺失值明确报告；不得编造答案或覆盖原始数据。

遵循[公共工作约定](../_shared/references/workflow.md)。
