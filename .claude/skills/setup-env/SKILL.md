---
name: setup-env
description: "检查 Know-Surgery 的 Python、依赖、GPU 和本地模型缓存；用于运行前检查或环境排障。"
---

# 环境检查

## 输入

仓库根目录；目标 Python 解释器；可选本地模型路径。

## 流程

在仓库根目录运行（占位符替换为真实值）：

```bash
python .claude/skills/setup-env/scripts/run.py --output artifacts/TASK/environment.json
```

1. 确认工作目录和 Python 解释器；后续命令使用同一个环境。
2. 运行辅助脚本，必要时添加可重复的 `--model-cache PATH`。
3. 阅读缺失依赖和 `gpu_query`；选择可用设备，核查本地模型配置、分片与 tokenizer 文件完整性。无 GPU 或 `nvidia-smi` 不妨碍配置规划。
4. 仅在用户授权后安装依赖或下载权重；本脚本不安装、不下载。

## 完成标准

- 交付环境报告、解释器、可用设备与具体缺项。
- 区分环境检查通过和目标模型/算法兼容；不泄露密钥。

遵循[公共工作约定](../_shared/references/workflow.md)。
