# Codex_Only 专用工作流（论文与专利）

目标：只用 `codex_only` 目录内模板，完成论文写作、循环评审、论文转专利。

## 适用场景

- 你要投 `NeurIPS / ICML / ICLR`
- 你要对草稿做多轮审稿式优化
- 你要把论文方案转成专利技术交底书

## 目录与用途

- `paperwrite/`：主流程（建议默认使用）
- `review_loop/`：独立循环评审
- `lit_scout/`：文献侦察与竞品对比
- `paper_reader/`：单篇论文深读

## 最推荐流程（先论文，后专利）

1. 先跑 `paperwrite/PIPELINE_RUN_PROMPT.md`
2. 再用 `paperwrite/STAGE_4_ITERATIVE_REVIEW.md` 做 2~3 轮收敛
3. 定稿后用 `paperwrite/zhuanliwrite.md` 转专利交底书

## 一键调用模板（可直接复制）

```text
请严格基于 `codex_only/paperwrite` 执行完整流程：
1) 按 `PIPELINE_RUN_PROMPT.md` 生成论文 Draft v1；
2) 按 `STAGE_4_ITERATIVE_REVIEW.md` 迭代 3 轮；
3) 输出 Final Draft + Final Scores + Remaining Risks；
4) 再按 `zhuanliwrite.md` 将最终方法转为技术交底书初稿。

约束：
- 不得虚构实验数字或引用
- 缺失信息统一标记 [NEED_DATA]
- 优先修正高风险低分项
```

## MM-ShiftKV 专用调用（当前项目）

```text
请基于 `codex_only/paperwrite` 执行：
- 目标会议：ICLR
- 课题：多模态长上下文推理中的 KV Cache 稳定压缩
- 方法名：MM-ShiftKV
- 数据集：MMBench-Long, VideoMME, 自建长上下文指令集
- 指标：Accuracy, F1, Latency, Memory Footprint
- 基线：Full KV, StreamingLLM, SnapKV, H2O
- 目标分数：平均 >= 8.5/10
- 最大轮次：3
- 约束：不虚构实验结果，不改核心机制
```

## 输出要求（统一）

- 每轮必须给：`Scores / Top Risks / Fix Plan / Revised Text / Decision`
- 最终必须给：`Final Draft / Final Scores / Remaining Risks / Camera-ready TODO`

