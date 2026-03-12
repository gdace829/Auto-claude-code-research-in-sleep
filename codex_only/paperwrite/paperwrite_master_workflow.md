# PaperWrite 总控模板（串联两个 MD）

目标：一个入口同时使用以下两个模板。
- `conference_paper_prompts.md`：先生成 NeurIPS/ICML/ICLR 风格初稿
- `iterative_review_template.md`：再做多轮评审改写直到收敛

## 文件位置
- `/home/sjs/Auto-claude-code-research-in-sleep/codex_only/paperwrite/conference_paper_prompts.md`
- `/home/sjs/Auto-claude-code-research-in-sleep/codex_only/paperwrite/iterative_review_template.md`

## 使用方式（推荐）

把下面这段“总控 Prompt”直接发给我，并替换占位符。

```text
你现在执行一个两阶段论文写作流程，请严格按顺序完成。

【输入参数】
- 目标会议：{NeurIPS | ICML | ICLR}
- 课题：{你的课题}
- 方法名：{方法名}
- 数据集：{数据集列表}
- 指标：{指标列表}
- 基线：{基线列表}
- 当前已有内容：{可空，若无则从零开始}
- 目标分数：{例如 平均 >= 8.5/10}
- 最大轮次：{例如 3}
- 必保留约束：{例如 不虚构实验，不改核心设定}

【阶段1：调用 conference_paper_prompts.md】
1) 依据目标会议风格，生成完整论文草稿：
   - 摘要、引言、相关工作、方法、实验、结论、审稿自查清单
2) 输出为 Draft v1。
3) 若缺少关键信息，使用 [NEED_DATA] 标记，不得编造。

【阶段2：调用 iterative_review_template.md】
对 Draft v1 执行循环优化：
- 每轮都执行：评审打分 -> 风险排序 -> 定向改写 -> 复审
- 输出字段固定为：
  - Round {i}
  - Scores
  - Top Risks
  - Fix Plan
  - Revised Text
  - Re-Score
  - Decision
- 达到目标分数或关键风险清零则停止，否则继续到最大轮次。

【最终输出】
1) Final Draft（最终版）
2) Final Scores（各维度分数）
3) Remaining Risks（剩余风险）
4) Camera-ready TODO（投稿前待办，按优先级）

【硬性规则】
- 不得虚构实验数字、引用和结果
- 所有主张必须对应证据
- 优先修正低分高风险项，避免无关润色
```

## 极简调用版（一句话）

```text
请串联执行 `conference_paper_prompts.md` + `iterative_review_template.md`：先按 {ICLR} 生成“{你的课题}”全稿 Draft v1，再进行 {3} 轮评审改写，直到平均分 >= {8.5/10}，并输出 Final Draft + Final Scores + Remaining Risks。
```

## 实操建议
- 先跑 ICLR 版（动机和实验叙事更容易起稿），再切 NeurIPS/ICML。
- 如果你已有初稿，直接把“当前已有内容”贴进去，可跳过从零生成。
- 先优化摘要+引言到 8 分以上，再扩展方法和实验，效率更高。
