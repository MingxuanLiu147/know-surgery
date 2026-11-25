---
name: build-cases
description: "将已规范化知识转换为注入、编辑或遗忘案例，并检查已有评价探针的覆盖。"
---

# 构建实验案例

## 输入

规范化 JSONL；同一 operation；已有目标、改写和副作用探针。

## 流程

在仓库根目录运行（占位符替换为真实值）：

```bash
python .claude/skills/build-cases/scripts/run.py --input NORMALIZED --operation edit --output artifacts/TASK/cases.jsonl
```

1. 核对操作、记录角色与目标字段；遗忘需独立 forget 和 retain 记录。
2. 运行案例构建；读取输出及 `.manifest.json`，遗忘检查 `.forget.jsonl` 与 `.retain.jsonl`。
3. 检查记录数、来源以及 rephrase、locality、portability 等已有探针；报告缺失。
4. 将通过检查的案例交给 `plan-surgery --cases PATH` 绑定输入。

## 完成标准

- 交付案例文件、清单与探针覆盖信息。
- 脚本不会生成缺失问答；不得把缺失的副作用评价视为满分。

遵循[公共工作约定](../_shared/references/workflow.md)。
