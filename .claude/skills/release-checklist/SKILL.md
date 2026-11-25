---
name: release-checklist
description: "在分享或使用工作区前核对入口、配置、依赖及 Skills 结构；不上传发布。"
---

# 源码结构与发布检查

## 输入

当前工作区和 Python 环境；拟发布范围。

## 流程

在仓库根目录运行（占位符替换为真实值）：

```bash
python .claude/skills/release-checklist/scripts/run.py --output artifacts/TASK/checklist.json
```

1. 运行结构与依赖检查，检查必要文件、许可证、配置及包装入口。
2. 区分必需检查和可选 UI/Codex 发现组件；记录具体失败和依赖缺项。
3. 对目标工作流另外执行环境检查、配置预检与已授权的冒烟测试。
4. 检查待分享产物中的许可证、私人信息、模型/数据权限及不应提交的文件。

## 完成标准

- 交付检查清单、失败项与尚未验证的范围。
- 检查通过不代表基准质量、模型兼容性或许可证获得认证；不自动发布。

遵循[公共工作约定](../_shared/references/workflow.md)。
