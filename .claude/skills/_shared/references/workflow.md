# 公共工作约定

适用于全部 Know-Surgery Skills。以仓库实际实现及当前配置为准，不发明参数或组件 ID。

1. 在仓库根目录执行命令；复用同一 Python 环境与已有配置。需要时先检查对应脚本 `--help` 和源码。
2. 示例中的 `TASK`、`PLAN`、`INPUT`、`RUN_DIR`、`CONFIG_YAML` 等为占位符，替换为实际路径；含空格的路径加引号。每次任务使用独立产物目录。
3. 规划、预览和预检不代表模型运行。模型执行遵循 [执行流程](execution.md)；不要自动确认未经授权的配置或扩大资源预算。
4. 原始输入、初始 checkpoint 与已有运行产物保持不变。记录配置差异和理由、数据来源/版本、种子、实际预算以及失败状态。
5. 编排产物放在 `artifacts/`；模型与评测产物使用公共引擎解析后的 `saves/` 输出路径。具体规则见[产物目录](artifact-layout.md)。
6. 证据等级见[证据等级](evidence-levels.md)：`planned`、`configured`、`local_validation`、`verified_smoke`、`verified_result`。缺失证据保持缺失；不得由文件名或 exit code 推断模型性能。
7. 已明确的参数不反复询问；仅在必要输入缺失或授权边界不明确时提出问题。报告具体错误与下一步，不隐瞒失败。
8. 不泄露密钥、私人输入或受限数据；分享前审查产物。
