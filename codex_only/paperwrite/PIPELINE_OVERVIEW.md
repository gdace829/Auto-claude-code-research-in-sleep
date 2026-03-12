# PaperWrite Pipeline 总览（推荐）

这是一套面向 NeurIPS / ICML / ICLR 的最佳实践流水线。
目标：从题目到可投稿稿件，最小化“空写作”和“证据不足”风险。

## 流程图

1. `STAGE_0_INPUT_PACK.md`：统一输入与边界约束
2. `STAGE_1_VENUE_STRATEGY.md`：会议信号与叙事定位
3. `STAGE_2_DRAFT_GENERATION.md`：生成 Draft v1（全章节）
4. `STAGE_3_EVIDENCE_AND_EXPERIMENT.md`：补齐证据与实验设计
5. `STAGE_4_ITERATIVE_REVIEW.md`：多轮审稿式优化
6. `STAGE_5_CAMERA_READY.md`：定稿前检查与交付包

## 你已有模板的角色

- `conference_paper_prompts.md`：用于 Stage 2（按会议风格出全稿）
- `iterative_review_template.md`：用于 Stage 4（循环评审）
- `zhuanliwrite.md`：论文转专利时单独走专利支线

## 推荐执行顺序

1. 先跑 Stage 0，强制补全输入参数。
2. 再跑 Stage 1，确定会风格与拒稿风险优先级。
3. 用 Stage 2 产出 Draft v1。
4. 用 Stage 3 检查“主张-证据”闭环，补实验计划。
5. 用 Stage 4 做 2~3 轮迭代，收敛到目标分。
6. 最后 Stage 5 产出投稿包与清单。

## 一句话调用（总控）

```text
请按 `PIPELINE_RUN_PROMPT.md` 执行完整论文流水线：先做输入归一化与会议策略，再生成 Draft v1，随后做证据补强与3轮迭代评审，最后输出可投稿版本和 camera-ready TODO。
```
