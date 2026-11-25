---
name: add-multimodal-case
description: "为多模态知识更新检查本地 JSON/JSONL 引用图片，并准备相应模型输入。"
---

# 校验多模态案例

## 输入

JSON/JSONL、图片、目标文本、目标模型/processor。

## 流程

在仓库根目录运行（占位符替换为真实值）：

```bash
python .claude/skills/add-multimodal-case/scripts/run.py --input INPUT --output artifacts/TASK/mm_validation.json
```

1. 检查每条记录的 `image` 或 `images`，路径为绝对路径或相对于输入文件。
2. 执行图片校验；读取缺失文件、解码失败或空输入的诊断。
3. 另外核查 prompt、target、图文语义、processor 与模型方法兼容性；图片解码不证明语义一致。
4. 准备实际视觉有效性与文本保持探针，组合并预检目标多模态配置。

## 完成标准

- 交付校验报告、可用图片清单和未解决项。
- 不声称脚本自动注册案例、判断图文语义或运行模型；不公开私人图片。

遵循[公共工作约定](../_shared/references/workflow.md)。
