---
name: generate-report
description: "从已有汇总、比较或轨迹 JSON 生成 Markdown/JSON 报告，不虚构实验分析。"
---

# 生成可审查报告

## 输入

已有真实 JSON 输入；报告输出位置及用户需要的分析范围。

## 流程

在仓库根目录运行（占位符替换为真实值）：

```bash
python .claude/skills/generate-report/scripts/run.py --input INPUT_JSON --markdown-output artifacts/TASK/report.md --json-output artifacts/TASK/report.json
```

1. 检查输入类型、指标及原始运行来源；缺少结果时明确记录。
2. 运行报告命令，保留输入载荷及原始指标。
3. 基于证据补充简要解释，区分规划、预检、冒烟和完整协议。
4. 附实际可用的复现命令和限制；检查私有路径、密钥与数据分享权限。

## 完成标准

- 交付 Markdown 和 JSON，结论有来源且缺失指标保留 null/N/A。
- 脚本只渲染已有 JSON，不自动翻译、分析或抓取缺失运行。

遵循[公共工作约定](../_shared/references/workflow.md)。
