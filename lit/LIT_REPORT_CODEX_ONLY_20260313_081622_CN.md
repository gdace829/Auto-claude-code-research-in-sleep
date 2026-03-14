# Literature Scout Report (Codex-Only)

## 1) Scope
- Topic: 用于长文档问答、agent 式阅读和长度外推的显式记忆长上下文 LLM；种子论文重点是基于 RL 的固定长度记忆代理。
- Keywords: long-context LLM, memory agent, RLVR, GRPO, DAPO, multi-conversation RL, memory overwrite, fixed-length memory, chunked reading, long-document QA, length extrapolation, linear-time inference, episodic memory attention, stateful language model, long-short alignment.
- Target venues: NeurIPS, ICML, ICLR, ACL.
- Time window: March 13, 2025 to March 13, 2026.
- Max shortlist size: 20.

## 2) Source Quality Notes
- Primary sources used:
  - 种子 PDF: [papers/memagent.pdf](/home/sjs/Auto-claude-code-research-in-sleep/papers/memagent.pdf)
  - ACL 2025 论文的 ACL Anthology 页面。
  - ICLR 2025 和 ICLR 2026 论文的 OpenReview forum/proceedings 页面。
  - ICML 2025 论文的 PMLR proceedings 页面。
  - arXiv 摘要页，用于确认预印本日期和版本。
  - 官方 GitHub 或 Hugging Face 项目页（如有）。
- Known evidence gaps:
  - ACL Anthology 通常只显示月份和年份，不一定给出精确发布日期；这类情况我降低了置信度。
  - 对部分 2025/2026 论文，具体数值结果来自摘要或搜索片段，而非完整结果表；仍然是基于一手来源，但完整性较弱。
  - NeurIPS 2025 中与种子最直接对齐的论文较少，因此 shortlist 更偏向 ACL/ICLR/ICML。

## 2.5) Seed-to-Literature Mapping
- Seed extraction:
  - Problem framing: 在受限上下文窗口下，让 LLM 以接近无损的方式处理无界长文档，同时保持近线性推理成本。
  - Method family: 显式记忆代理；分块读取；覆盖式记忆更新；基于 RL 的多步记忆轨迹优化。
  - Likely adjacent subtopics: episodic memory layers, latent-memory retrieval, stateful/recurrent language models, long-context alignment/training, long-context agentic decomposition.
- Mapping from seed to shortlist:
  - `same problem` and `same method family`: MemAgent, StateLM, EpMAN, M+, R3Mem.
  - `same problem`: LongPO, Self-Taught Agentic Long-Context Understanding, Long-Short Alignment, NExtLong, How to Train Long-Context Language Models (Effectively).
  - Shortlist relevance concentration: 10 篇中有 8 篇直接讨论长上下文理解或带记忆的长上下文建模；其中 5 篇是显式记忆/状态方法，满足 70% 的 seed-first 约束。

## 2.6) Rating Summary
- Chosen profile and weights:
  - `seed_focus`
  - Relevance-to-seed 0.45
  - Novelty 0.15
  - Evidence strength 0.15
  - Reproducibility 0.10
  - Practical impact 0.15

| Paper | Relation to Seed | Relevance | Novelty | Evidence | Reproducibility | Impact | Final Weighted Score |
|------|------------------|-----------|---------|----------|------------------|--------|----------------------|
| MemAgent | same problem, same method family | 10 | 9 | 8 | 9 | 10 | 9.45 |
| The Pensieve Paradigm | same problem, same method family | 10 | 9 | 8 | 7 | 10 | 9.25 |
| EpMAN | same method family | 9 | 8 | 8 | 5 | 8 | 8.15 |
| M+ | same method family | 8 | 8 | 8 | 9 | 8 | 8.10 |
| Self-Taught Agentic Long-Context Understanding | same problem | 8 | 8 | 8 | 6 | 8 | 7.80 |
| How to Train Long-Context Language Models (Effectively) | same problem | 7 | 7 | 9 | 9 | 9 | 7.80 |
| LongPO | same problem | 7 | 8 | 8 | 9 | 8 | 7.65 |
| Long-Short Alignment | same problem | 7 | 8 | 7 | 8 | 7 | 7.25 |
| R3Mem | same method family | 8 | 7 | 7 | 4 | 7 | 7.15 |
| NExtLong | same problem | 7 | 7 | 8 | 6 | 7 | 7.05 |

- Top-3 by each single dimension:
  - Relevance: MemAgent, The Pensieve Paradigm, EpMAN.
  - Novelty: MemAgent, The Pensieve Paradigm, LongPO.
  - Evidence: How to Train Long-Context Language Models (Effectively), MemAgent, The Pensieve Paradigm.
  - Reproducibility: M+, How to Train Long-Context Language Models (Effectively), LongPO.
  - Impact: MemAgent, The Pensieve Paradigm, How to Train Long-Context Language Models (Effectively).

## 3) Shortlist (Top 10)

| Rank | Paper | Venue/Year | Why It Matters Now | Key Result | Reproducibility Signal | Links |
|------|-------|------------|--------------------|------------|------------------------|-------|
| 1 | MemAgent: Reshaping Long-Context LLM with Multi-Conv RL-based Memory Agent | arXiv preprint, 2025 | 与种子最接近：基于 RL 的覆盖式记忆，用于百万 token 级问答。 | 8K 上下文训练可外推到 3.5M token QA，论文报告性能损失 <5%；512K RULER 平均分 95%+。 | 有项目页和 GitHub。 | [paper](https://arxiv.org/abs/2507.02259) / [code](https://github.com/thu-air/MemAgent) |
| 2 | The Pensieve Paradigm: Stateful Language Models Mastering Their Own Context | ICLR 2026 conference paper | 种子方向之后最强的验证信号之一：学习式记忆管理可以胜过单纯拉长上下文。 | 报告称在 NoLiMa 上比领先基线高 2.7x，并在 recall 与 infinite-context 场景上表现强。 | 提供 Hugging Face 模型；代码信号中等。 | [paper](https://arxiv.org/abs/2602.12108) / [code](https://huggingface.co/collections/lindsay21/statelm-mastering-your-own-context-67c2405675fa57606efec339) |
| 3 | EpMAN: Episodic Memory AttentioN for Generalizing to Longer Contexts | ACL 2025 Long Paper | 显式记忆的轻量替代路线，适合作为 RL agent 方法的架构基线。 | 摘要称在 Needle-in-a-Haystack 类设定上最高可比先前方法提升 99%。 | 官方论文有；主来源未清晰给出代码仓库。 | [paper](https://aclanthology.org/2025.acl-long.183/) / [code](https://research.ibm.com/publications/epman-episodic-memory-attention-for-generalizing-to-longer-contexts) |
| 4 | M+: Extending MemoryLLM with Scalable Long-Term Memory | ICML 2025 conference paper | 当前较强的 latent-memory 扩展方案，适合短期推理与超长长期记忆结合。 | 摘要称支持 160K active context 和 10M-token long-term memory，同时匹配或优于 dense-attention 基线。 | PMLR 正式论文、GitHub、模型权重齐全。 | [paper](https://proceedings.mlr.press/v267/wang25q.html) / [code](https://github.com/wangyu-ustc/MemoryLLM) |
| 5 | Self-Taught Agentic Long-Context Understanding | ACL 2025 Long Paper | 很实用的 agent 化分解路线：不是只拉长注意力，而是自生成子目标处理长上下文。 | 报告称在长上下文任务上最高比 GPT-4.1 高 15.7%，比 R1 高 19.0%，且用更少 token。 | GitHub 可用。 | [paper](https://aclanthology.org/2025.acl-long.6/) / [code](https://github.com/EvanZhuang/AgenticLU) |
| 6 | How to Train Long-Context Language Models (Effectively) | ACL 2025 Long Paper | 最强的执行导向训练配方；如果你要验证记忆方法是否真有增益，这篇是关键控制线。 | ProLong-8B 在同尺寸模型中达到 128K SOTA，且仅用 Llama-3.1 长训练 token 的 5% 就能处理到 512K。 | 代码、数据、模型全公开。 | [paper](https://aclanthology.org/2025.acl-long.366/) / [code](https://github.com/princeton-nlp/ProLong) |
| 7 | LongPO: Long Context Self-Evolution of Large Language Models through Short-to-Long Preference Optimization | ICLR 2025 conference paper | 证明偏好优化也能显著提升长上下文能力，而不仅仅是 continued pretraining。 | 摘要称在 long-context understanding、QA、summarization 上达到新 SOTA，同时保留短上下文能力。 | OpenReview + GitHub。 | [paper](https://openreview.net/forum?id=qTrEq31Shm) / [code](https://github.com/DAMO-NLP-SG/LongPO) |
| 8 | Long-Short Alignment for Effective Long-Context Modeling in LLMs | ICML 2025 conference paper | 非常贴近种子问题的训练想法：提升长上下文时避免短上下文退化。 | 在长数据不足的设定下提升长上下文建模，且论文与代码都可获得。 | 代码可用性较好。 | [paper](https://proceedings.mlr.press/v267/xiao25m.html) / [code](https://github.com/PKU-ML/LongShortAlignment) |
| 9 | R3Mem: Bridging Memory Retention and Retrieval via Reversible Compression | Findings of ACL 2025 | 与种子相关的显式记忆设计，试图把 retention 和 retrieval 在低延迟下统一起来。 | 摘要称相对先前基线可带来 96.3% perplexity reduction，且无额外 retrieval latency。 | 官方 anthology 页面有；代码不清晰。 | [paper](https://aclanthology.org/2025.findings-acl.1004/) / [code](https://aclanthology.org/2025.findings-acl.1004/) |
| 10 | NExtLong: Toward Effective Long-Context Training without Long Documents | ICML 2025 conference paper | 如果缺少原生长文档数据，这篇很重要；它试图用短文档训练出长上下文行为。 | 摘要称在 long-context understanding 上最高可比已有方法提升 46%。 | 有官方代码仓库。 | [paper](https://proceedings.mlr.press/v267/li25bj.html) / [code](https://github.com/caskcsg/longcontext) |

## 4) Paper Cards

### [Rank 1] MemAgent: Reshaping Long-Context LLM with Multi-Conv RL-based Memory Agent
- Authors: Hongli Yu, Tinghong Chen, Jiangtao Feng, Jiangjie Chen, Weinan Dai, Qiying Yu, Ya-Qin Zhang, Wei-Ying Ma, Jingjing Liu, Mingxuan Wang, Hao Zhou.
- Venue/Track/Year: arXiv preprint, cs.CL, first posted July 3, 2025; project page dated July 4, 2025.
- Contribution (1 sentence): 提出一个基于 RL 训练的记忆代理，按块读取长文档并覆盖更新固定长度 token memory，从而把长文档问答外推到百万 token 级别。
- Method sketch (2-4 bullets):
  - 把文档切成多个 chunk，并配一个固定长度 token memory。
  - 每读完一个 chunk，用 overwrite prompt 更新 memory。
  - 用 Multi-Conv DAPO/GRPO 风格 RL 训练完整多步记忆轨迹。
  - 最终答案仅由问题和 learned memory 生成。
- Best evidence:
  - 论文报告从 8K 训练上下文外推到 3.5M-token QA，性能损失低于 5%。
  - 报告在 512K RULER 上达到 95%+ 平均表现，并在 3.5M token HotpotQA 派生 QA 上保持稳定。
- Limitations:
  - 尚未经过同行评审。
  - 证据主要集中在 QA 型长上下文任务，泛化到更广的生成或工具使用场景还不充分。
  - RL 训练配方可能计算成本较高，并依赖特定数据构造。
- Why selected:
  - Relation to seed: `same problem`, `same method family`.
  - 现在值得读，因为它就是种子锚点，也是当前这一方向里最清晰的显式 RL-memory 方案。
  - Confidence: high for seed extraction, medium-high for external impact because peer review is pending.
- URLs:
  - paper: https://arxiv.org/abs/2507.02259
  - code: https://github.com/thu-air/MemAgent

### [Rank 2] The Pensieve Paradigm: Stateful Language Models Mastering Their Own Context
- Authors: Xiaoyuan Liu, Tong Yu, Weichao Qiu, Matei Zaharia, Danqi Chen.
- Venue/Track/Year: ICLR 2026 conference paper; arXiv preprint February 2026.
- Contribution (1 sentence): 把长上下文建模改写为学习式 stateful memory management，让模型自己决定保留、淘汰和召回哪些上下文状态。
- Method sketch (2-4 bullets):
  - 维护显式状态，而不是反复重喂全部原始上下文。
  - 学习记忆管理策略，而不是使用固定截断或固定检索启发式。
  - 在 recall、infinite-context 和噪声长上下文任务上评测。
- Best evidence:
  - 搜索片段显示其在 NoLiMa 上比领先基线高 2.7x。
  - OpenReview/arXiv 材料表明其能与近期长上下文和线性注意力模型竞争。
- Limitations:
  - 本次运行没有完整检查主论文里的全部结果表。
  - 可复现性弱于 GitHub-first 论文，公开信号目前主要是模型集合。
- Why selected:
  - Relation to seed: `same problem`, `same method family`.
  - 现在值得读，因为这是记忆管理本身成为一等建模对象的强同行评审信号。
  - Confidence: medium-high.
- URLs:
  - paper: https://arxiv.org/abs/2602.12108
  - code: https://huggingface.co/collections/lindsay21/statelm-mastering-your-own-context-67c2405675fa57606efec339

### [Rank 3] EpMAN: Episodic Memory AttentioN for Generalizing to Longer Contexts
- Authors: Oriol Nieto, Mostafa Elhoushi, Bilal Piot, Xiang Lisa Li, Mona Diab.
- Venue/Track/Year: ACL 2025 Long Paper; July 2025.
- Contribution (1 sentence): 增加 episodic memory attention 机制，使模型能够缓存并复用跨超长上下文的压缩关键信息。
- Method sketch (2-4 bullets):
  - 存储压缩后的 episodic traces，而不是对全历史做密集注意力。
  - 解码时重新访问 episodic store。
  - 目标是提高超出训练长度后的泛化能力。
- Best evidence:
  - IBM/ACL 摘要称在 NIAH 类评测上相对先前方法最高提升 99%。
  - 论文明确聚焦“更长长度上的泛化”，而不是单纯扩大记忆容量。
- Limitations:
  - 来源片段中的证据主要是 benchmark-specific。
  - 在一手来源中没有清晰暴露官方代码仓库。
- Why selected:
  - Relation to seed: `same method family`.
  - 现在值得读，因为它是一个较轻量、已同行评审的显式记忆基线，可与 MemAgent 这类 RL-heavy 方法正面对比。
  - Confidence: medium.
- URLs:
  - paper: https://aclanthology.org/2025.acl-long.183/
  - code: https://research.ibm.com/publications/epman-episodic-memory-attention-for-generalizing-to-longer-contexts

### [Rank 4] M+: Extending MemoryLLM with Scalable Long-Term Memory
- Authors: Yu Wang, Dmitry Krotov, Yuanzhe Hu, Yifan Gao, Wangchunshu Zhou, Julian McAuley, Dan Gutfreund, Rogerio Feris, Zexue He.
- Venue/Track/Year: ICML 2025 conference paper; PMLR volume published October 6, 2025; arXiv preprint February 1, 2025.
- Contribution (1 sentence): 在 latent-space memory LLM 上加入可扩展、可检索的长期记忆，使记忆容量远超活跃上下文窗口。
- Method sketch (2-4 bullets):
  - 在模型内部保留 latent short-term memory。
  - 通过 retriever 访问外部长时记忆。
  - 在不对全历史做 dense attention 的情况下交换相关 memory block。
- Best evidence:
  - 摘要报告支持 160K active context 和 10M-token memory。
  - 官方仓库公开了权重和评测脚本，显著提升了可信度。
- Limitations:
  - 相比 token-memory overwrite，架构复杂度更高。
  - 检索质量会成为关键瓶颈。
- Why selected:
  - Relation to seed: `same method family`.
  - 现在值得读，因为它是当前最具可扩展性和可复现性的 memory-augmented 替代路线之一。
  - Confidence: high.
- URLs:
  - paper: https://proceedings.mlr.press/v267/wang25q.html
  - code: https://github.com/wangyu-ustc/MemoryLLM

### [Rank 5] Self-Taught Agentic Long-Context Understanding
- Authors: Yifeng Zhuang, Arka Das, Yoon Kim.
- Venue/Track/Year: ACL 2025 Long Paper; July 2025.
- Contribution (1 sentence): 通过自生成的 agent 式任务分解提升长上下文理解，而不是要求基础模型一次性吃下全部证据。
- Method sketch (2-4 bullets):
  - 把长上下文问题拆成更小的 agent-generated 子问题。
  - 先对局部片段查询或推理，再做综合。
  - 训练或提示系统改进自己的分解策略。
- Best evidence:
  - ACL 摘要称其在长上下文 benchmark 上最高比 GPT-4.1 提升 15.7%，比 DeepSeek-R1 提升 19.0%。
  - 据称 token 使用量也低于直接长上下文基线。
- Limitations:
  - 更偏 agentic，而不是 memory-native，因此不是种子方法的纯替代品。
  - 效果可能依赖任务分解质量和任务格式。
- Why selected:
  - Relation to seed: `same problem`.
  - 现在值得读，因为它代表了一条清晰的“不要只拉长上下文，而要重构任务”的路线，并且来自目标会议。
  - Confidence: medium-high.
- URLs:
  - paper: https://aclanthology.org/2025.acl-long.6/
  - code: https://github.com/EvanZhuang/AgenticLU

### [Rank 6] How to Train Long-Context Language Models (Effectively)
- Authors: Tianyu Gao, Kush Bhatia, Zifan Shen, Xian Li, J. Zico Kolter, Danqi Chen, Christopher De Sa.
- Venue/Track/Year: ACL 2025 Long Paper; July 2025.
- Contribution (1 sentence): 给出一套强实证训练配方，使长上下文模型真正“利用”长上下文，而不是只“支持”更长窗口。
- Method sketch (2-4 bullets):
  - 在 instruction tuning 之后做稳健长上下文评估，而不是只看 perplexity 或 NIAH。
  - 在 continued training 中混合长数据和高质量短数据。
  - 训练长度超过目标评测长度。
  - SFT 只用短 instruction data 也能迁移到长上下文。
- Best evidence:
  - ProLong-8B 在同尺寸模型中达到 128K SOTA。
  - 它在多数长上下文任务上超过 Llama-3.1-8B-Instruct，同时只使用其 5% 的长训练 token。
  - 代码、数据、模型全公开，执行价值很高。
- Limitations:
  - 不是显式记忆方法。
  - 效果依赖高质量数据配比和较长训练预算。
- Why selected:
  - Relation to seed: `same problem`.
  - 现在值得读，因为它是任何 memory-agent 项目的关键控制基线；不用这条线，你无法判断记忆机制到底多买来了多少收益。
  - Confidence: high.
- URLs:
  - paper: https://aclanthology.org/2025.acl-long.366/
  - code: https://github.com/princeton-nlp/ProLong

### [Rank 7] LongPO: Long Context Self-Evolution of Large Language Models through Short-to-Long Preference Optimization
- Authors: Guangxuan Xiao, Chenhui Hu, Yikai Zhou, Xiaodan Liang, Shuang Li, Yizhe Zhang, Tianyu Liu, Baobao Chang.
- Venue/Track/Year: ICLR 2025 conference paper.
- Contribution (1 sentence): 用 preference optimization 把短上下文能力迁移成强长上下文行为，同时尽量不损伤短上下文表现。
- Method sketch (2-4 bullets):
  - 构建 short-to-long preference data。
  - 用 preference learning，而不是只用 LM loss。
  - 同时提升长上下文 QA、理解和总结。
- Best evidence:
  - OpenReview 摘要称其在多个长上下文任务上达到新 SOTA。
  - 明确声称保留短上下文能力，而这通常是长上下文调优中的常见失败点。
- Limitations:
  - 仍然不是显式记忆架构。
  - 结果结论较宽泛，做直接复现前仍需深入读论文设置。
- Why selected:
  - Relation to seed: `same problem`.
  - 现在值得读，因为它提供了一个干净的对照：如果 preference optimization 已经逼近 memory-agent，额外记忆机制是否值得就需要重新审视。
  - Confidence: medium-high.
- URLs:
  - paper: https://openreview.net/forum?id=qTrEq31Shm
  - code: https://github.com/DAMO-NLP-SG/LongPO

### [Rank 8] Long-Short Alignment for Effective Long-Context Modeling in LLMs
- Authors: Yucheng Xiao, Guangxuan Xiao, Hai Zhao, Baobao Chang.
- Venue/Track/Year: ICML 2025 conference paper; PMLR volume published October 6, 2025; arXiv preprint June 2025.
- Contribution (1 sentence): 通过 long-context 与 short-context 的对齐目标，减少“长变强、短变差”的副作用。
- Method sketch (2-4 bullets):
  - 把长短能力差异视为 alignment 问题。
  - 使用显式保留短上下文能力的训练目标。
  - 面向长数据不足或噪声较大的场景。
- Best evidence:
  - 论文和代码都可获取。
  - 对实践很重要，因为短上下文退化是长上下文调优中常见但容易被忽略的成本。
- Limitations:
  - 相比种子，方法不够 memory-centric。
  - headline improvement 没有 MemAgent 或 M+ 那么强。
- Why selected:
  - Relation to seed: `same problem`.
  - 现在值得读，因为种子式记忆方法仍然必须与 alignment-first 的训练修正路线做直接对比。
  - Confidence: medium.
- URLs:
  - paper: https://proceedings.mlr.press/v267/xiao25m.html
  - code: https://github.com/PKU-ML/LongShortAlignment

### [Rank 9] R3Mem: Bridging Memory Retention and Retrieval via Reversible Compression
- Authors: Zhen Qin, Yiran Zhao, Lanxiang Hu, Rui Meng, Sarathkrishna Swamynathan, Mahesh Vyas, Dan Roth, Hao Peng.
- Venue/Track/Year: Findings of ACL 2025; July 2025.
- Contribution (1 sentence): 通过 reversible compression 把 memory retention 和 retrieval 统一起来，试图在不增加延迟的前提下实现持久记忆。
- Method sketch (2-4 bullets):
  - 把上下文压缩成可逆记忆状态。
  - 将存储与检索耦合，而不是拆成两个独立模块。
  - 重点关注低延迟 memory 使用。
- Best evidence:
  - Anthology 摘要称相对先前基线可实现 96.3% perplexity reduction，且无额外 retrieval latency。
- Limitations:
  - 属于 Findings track，不是 ACL main track。
  - 本次运行中外部代码信号较弱。
  - 其最强证据更偏语言建模，而不是长文档 QA。
- Why selected:
  - Relation to seed: `same method family`.
  - 现在值得读，因为 reversible compression 是 overwrite memory 和 latent retrieval 之外的具体替代思路。
  - Confidence: medium-low.
- URLs:
  - paper: https://aclanthology.org/2025.findings-acl.1004/
  - code: https://aclanthology.org/2025.findings-acl.1004/

### [Rank 10] NExtLong: Toward Effective Long-Context Training without Long Documents
- Authors: Tianyang Li, Minjie Chen, Christian Wolf, Caiming Xiong, Wenqiang Lei, Heng Ji.
- Venue/Track/Year: ICML 2025 conference paper; PMLR volume published October 6, 2025; arXiv preprint January 2025.
- Contribution (1 sentence): 说明即使没有大规模原生长文档，也可以通过训练设计获得较强的长上下文行为。
- Method sketch (2-4 bullets):
  - 从短文档出发。
  - 构造能够模拟长上下文监督的训练过程。
  - 以更低的数据采集成本提升有效长上下文能力。
- Best evidence:
  - 摘要称在 long-context understanding 上最高比已有方法提升 46%。
  - 有官方代码仓库。
- Limitations:
  - 收益依赖特定 synthetic/extended 训练设置。
  - 不是显式记忆方法，因此只在问题层面与种子竞争。
- Why selected:
  - Relation to seed: `same problem`.
  - 现在值得读，因为它直接攻击 seed-style 系统的一个主要现实阻碍：昂贵的长序列训练数据。
  - Confidence: medium.
- URLs:
  - paper: https://proceedings.mlr.press/v267/li25bj.html
  - code: https://github.com/caskcsg/longcontext

## 5) Not Selected but Notable
- LongMemEval: A Benchmark for Long-term Interactions with Language Models: 对对话型长期记忆评测很有价值，但与种子的长文档分块阅读设定不如已入选论文直接对齐。
- NoLiMa: Long-Context Evaluation Beyond Literal Matching: 很重要的评测基准，因为它能惩罚浅层 lexical retrieval，但它是评测资产而不是方法论文。
- UltraMemV2: Memory at Native Capacity: 来自 ICLR 2025 的相关记忆架构，但与长文档 QA 的直接关联弱于 M+、EpMAN 或 MemAgent。
- PaceLLM: Brain-Inspired Long-Context Language Modeling by Spatial-Temporal Segment Recurrent: NeurIPS 2025 邻近方向里有趣的 recurrent 设计，但从一手来源看到的证据和工具链不如已入选集合成熟。
- MIRIX: 在 agent memory systems 和实用部署上很强，但不在目标会议集合内，而且更偏系统而不是种子方法问题本身。

## 6) Trends and Openings
- Trend 1: 显式记忆正在回归，但形式变成了可学习的策略或状态管理，而不是静态外挂模块。
- Trend 2: 强长上下文表现越来越多地来自任务分解、偏好优化或记忆管理，而不只是更大的原始窗口。
- Contradictions/disagreements:
  - 一部分工作认为更好的训练本身就足够。
  - 另一部分工作认为更长窗口仍然无法真正利用信息，因此显式记忆/状态是必要的。
  - 这是你下一轮实验最值得直接验证的主要分歧点。
- Potential research openings:
  - 在同一长文档 QA 和 multi-hop reasoning 流水线上，统一比较 token-memory overwrite、latent-memory retrieval 和 stateful-memory management。
  - 在引入 ProLong/LongPO 这类最强训练控制线后，测试 RL memory agents 是否仍然领先。
  - 用 NoLiMa 这类非字面匹配 benchmark 来评估 memory quality，而不只看 NIAH 或 RULER。
  - 研究可编辑、可检查的 memory states，用于调试，而不只看最终准确率。

## 7) Coverage Gaps and Blind Spots
- Missing sub-areas:
  - 同时间窗内的 sparse/linear-attention 竞争路线没有重点展开，因为它们与种子对齐度较低。
  - 多模态记忆与长时程 agent memory systems 基本被排除在外。
- Venue bias risk:
  - shortlist 明显偏 ACL/ICML/ICLR，因为从一手来源证据看，NeurIPS 2025 中与种子直接相关的论文更少或更不成熟。
- Time-window risk:
  - 由于时间窗从 March 13, 2025 开始，很多仍然很重要的 2024 论文被有意排除。
  - 一些 2026 论文非常新，代码和复现证据后续可能会快速增强。

## 8) Action Plan (2 Weeks)
- Day 1-3: 通读 #1、#2、#4，提炼精确的 memory state 定义、更新规则、训练目标和 benchmark protocol，整理成对比表。
- Day 4-7: 阅读 #6、#7、#8，建立你这个主题下最强的非记忆控制线，从而区分“训练更好”与“记忆更好”。
- Day 8-10: 阅读 #3、#5、#9、#10，重点看 episodic memory、agentic decomposition、reversible compression 和低数据长上下文训练。
- Day 11-14: 汇总成 idea memo，并设计一套主实验矩阵：
  - MemAgent 风格 overwrite RL memory vs StateLM 风格 learned state vs M+ 风格 latent retrieval vs ProLong/LongPO 控制线。
  - 同时用一个 literal benchmark 和一个 non-literal benchmark。
  - 决定下一步项目应重点优化 memory policy、memory representation，还是 training data mix。
