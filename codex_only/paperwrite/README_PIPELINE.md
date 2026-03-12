# PaperWrite Pipeline 使用说明（从 0 到投稿）

## 1. 你现在有哪些文件

核心入口：
- `PIPELINE_RUN_PROMPT.md`
- `PIPELINE_OVERVIEW.md`

阶段模板：
- `STAGE_0_INPUT_PACK.md`
- `STAGE_1_VENUE_STRATEGY.md`
- `STAGE_2_DRAFT_GENERATION.md`
- `STAGE_3_EVIDENCE_AND_EXPERIMENT.md`
- `STAGE_4_ITERATIVE_REVIEW.md`
- `STAGE_5_CAMERA_READY.md`

底层模板：
- `conference_paper_prompts.md`
- `iterative_review_template.md`

专利支线：
- `zhuanliwrite.md`

## 2. 推荐执行路径

1. 先复制 `PIPELINE_RUN_PROMPT.md` 的总控模板。
2. 替换你的参数后直接发给模型跑完整流程。
3. 如果一次输出太长，就按 Stage 逐段执行。

## 3. 一次跑完整流程（推荐）

把下面这段直接复制使用：

```text
请按 `PIPELINE_RUN_PROMPT.md` 执行完整论文流水线。

参数如下：
- 目标会议：ICLR
- 课题：多模态长上下文推理中的 KV Cache 稳定压缩
- 方法名：MM-ShiftKV
- 任务设定：多模态生成 + 长序列问答
- 数据集：MMBench-Long, VideoMME, 自建长上下文指令集
- 指标：Accuracy, F1, Latency, Memory Footprint
- 基线：Full KV, StreamingLLM, SnapKV, H2O
- 资源约束：8xA100, 2周实验窗口, 主文8页
- 已有内容：摘要草稿 + 方法草图
- 目标分数：平均 >= 8.5/10
- 最大迭代轮次：3
- 不可违反约束：不得虚构实验结果，不改核心机制
```

## 4. 分阶段跑（输出更可控）

### Stage 0
使用 `STAGE_0_INPUT_PACK.md`，先拿到输入归一化和缺失项列表。

### Stage 1
使用 `STAGE_1_VENUE_STRATEGY.md`，确定该会最容易被拒的风险点。

### Stage 2
使用 `STAGE_2_DRAFT_GENERATION.md` 生成 Draft v1。

### Stage 3
使用 `STAGE_3_EVIDENCE_AND_EXPERIMENT.md` 建立 claim-evidence matrix。

### Stage 4
使用 `STAGE_4_ITERATIVE_REVIEW.md` 做 2-3 轮评审式改写。

### Stage 5
使用 `STAGE_5_CAMERA_READY.md` 产出投稿前最终清单。

## 5. 高质量输出的最小规则

- 缺失信息统一用 `[NEED_DATA]`，不要编数据。
- 每个贡献点都要绑定一个可验证实验。
- 先把摘要/引言打磨到 8 分以上，再扩展全稿。
- 每轮只改高风险段落，避免全篇重写。

## 6. 论文转专利（可选）

当论文结构稳定后，把方法与实验结论输入 `zhuanliwrite.md`，生成技术交底书初稿，再由代理师二次加工。
