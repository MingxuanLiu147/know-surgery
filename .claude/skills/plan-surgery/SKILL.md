---
name: plan-surgery
description: "把知识注入、编辑、遗忘的自然语言需求转换为可审查的 SurgeryPlan；不直接运行模型。"
---

# 知识更新任务规划

## 输入

操作、模态、目标模型与数据、方法、案例预算；自定义案例路径（如有）。

## 流程

在仓库根目录运行（占位符替换为真实值）：

```bash
python .claude/skills/plan-surgery/scripts/run.py --intent "Edit one CounterFact fact with GPT2 and FT" --output artifacts/TASK/plan.json
```

1. 用 `inspect-repo` 确定实际注册 ID；明确操作为 `inject`、`edit` 或 `unlearning`。
2. 运行规划命令，按需指定 `--operation`、`--modality`、`--model-id`、`--dataset-id`、`--methods`、`--num-cases`；自定义案例用 `--cases PATH` 绑定。
3. 核查方案中的方法、配方、输入哈希及 warnings；遗忘必须有 forget/retain，秩更新编辑需明确 subject。
4. 多模态核对图片路径和模型适配；相对图片路径从案例文件所在目录解析。图文注入可用 `--modality multimodal --model-id Qwen2.5-VL-3B --methods MM_LoRA --dataset-id Canonical_MM_inject --cases PATH`。比较实验另核对有效 batch、更新步数、实际样本范围。
5. 计划中的 evaluator 不代表执行已启用：检查真实评价数据、参考模型和开关（例如 `do_eval`）；使用相应 run Skill 继续。

## 完成标准

- 交付 plan JSON 与关键配置/待解决问题。
- 只报告规划完成；不得把案例上限等同于独立事实数，也不得声称模型已运行。

计划字段见 [SurgeryPlan schema](../_shared/references/surgery-plan.schema.json)；遵循[公共工作约定](../_shared/references/workflow.md)。
