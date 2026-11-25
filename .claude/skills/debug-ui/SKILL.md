---
name: debug-ui
description: "检查 Know-Surgery 后端健康状态；用于定位 UI 问题并按需验证界面与 CLI 一致性。"
---

# 检查 WebUI 后端与行为

## 输入

实际后端 URL；待检查的功能及日志。

## 流程

在仓库根目录运行（占位符替换为真实值）：

```bash
python .claude/skills/debug-ui/scripts/run.py --url http://127.0.0.1:17860 --output artifacts/TASK/health.json
```

1. 确认实际后端地址和服务状态，不假定默认端口一定有效。
2. 运行健康检查，读取 `/api/v1/health` 响应和错误。
3. 如需 UI 验证，操作受影响控件，核对导出命令与 CLI 预览、语言、校验及结果渲染。
4. 仅在用户授权和任务需要时运行模型；不为检查布局启动训练。

## 完成标准

- 交付健康报告及实际检查的功能、问题证据。
- HTTP 健康不等于浏览器、上传、训练或全部交互已通过；隐藏 provider 密钥。

遵循[公共工作约定](../_shared/references/workflow.md)。
