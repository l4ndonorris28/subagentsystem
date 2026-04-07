# Team Collaboration Rules (Mandatory)

本仓库启用了多 Agent 协作机制。

## Mandatory Policy

- 所有任务都必须走多角色协作流程，不区分任务大小。
- 不允许任何单个 Agent 独立完成从分析到决策的全流程。
- `team-orchestrator` 必须先收集四个角色输入，再推进实施。
- 若某角色判断“无影响”，也必须输出“无影响 + 理由”，不能跳过。
- 代码审查发现问题后，不允许审查员直接改代码，必须回到团队进行二次讨论后再修改。

## Required Participants For Every Task

1. `product-manager`：定义目标、范围、验收标准。
2. `art-designer`：评估交互和视觉影响（即使无 UI 变更也要确认）。
3. `programmer`：给出实现方案并执行修改。
4. `code-reviewer`：给出风险分级和回归验证建议。

## Execution Sequence (Always)

1. 并行收集四角色初版意见。
2. 交叉评议并收敛分歧。
3. 形成统一方案后再修改代码。
4. 审查发现问题时，进入 Review-to-Fix 协作回合：
	- `code-reviewer` 输出问题与证据。
	- `product-manager` 判断是否影响验收范围。
	- `art-designer` 判断是否影响交互/视觉（无影响也要给理由）。
	- `programmer` 提交修复方案与改动清单。
5. 四角色对修复方案达成一致后，由 `programmer` 实施修改。
6. 修改后由 `code-reviewer` 和 `product-manager` 复核。
7. 由 `team-orchestrator` 给出最终可交付结论。

## Output Requirements

最终汇报必须包含：

- 四角色输入摘要
- 分歧与决策记录
- 修改清单与影响面
- 回归验证范围与结果
- 未解决风险与下一步计划

## Trigger Phrase

当用户消息包含“按.github里规则”时，自动套用以下超短模板并执行：

请严格按仓库多 Agent 机制协作处理此任务：必须 product-manager、art-designer、programmer、code-reviewer 并行参与并交叉评议，禁止任何单角色独立决策或直接改完。若审查发现问题，必须先进入 Review-to-Fix 团队讨论达成一致后再由 programmer 修改，最后由 code-reviewer + product-manager 复核并输出完整闭环记录。
