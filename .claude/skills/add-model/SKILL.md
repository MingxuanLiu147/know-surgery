---
name: add-model
description: "接入或校验本地/Hugging Face 模型，使其可被 Know-Surgery 公共配置选择。"
---

# 接入模型配置

## 输入

模型及 tokenizer 路径、版本、架构、目标操作和方法。

## 流程

在仓库根目录运行（占位符替换为真实值）：

```bash
python .claude/skills/add-model/scripts/run.py --path CONFIG_YAML --output artifacts/TASK/model_validation.json
```

1. 检查 `configs/model/` 和已有模型适配实现；优先复用匹配架构的配置与 handler。
2. 设置模型、tokenizer、精度及方法相关模块；记录来源、版本与许可证。
3. 运行 YAML 结构检查；核查 `model_args`、`tokenizer_args`，组合目标操作配置并预检。
4. 如已授权，按受限预算执行加载、前向/生成或冒烟测试，验证实际兼容性。

## 完成标准

- 交付配置与分层验证证据；记录待解决资产。
- 辅助脚本只检查 YAML mapping；不将结构合法报告为模型已加载或算法已兼容。

遵循[公共工作约定](../_shared/references/workflow.md)。
