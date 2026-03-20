# 文献调研报告（仅 Codex）

## 1) Scope
- Topic: 面向 LLM 多智能体推理系统的强化学习训练与推理框架，核心关注在固定推理预算下实现可扩展协作。
- Keywords: multi-agent reinforcement learning for LLMs; centralized interaction distributed training; multi-agent debate RL; chain-of-agents RL; mixture-of-agents RL; credit assignment in multi-turn multi-agent systems; agent-wise reward normalization; asynchronous multi-agent rollouts; collaborative LLM post-training; self-play multi-agent reasoning; interaction rewards; test-time reinforcement learning for multi-agent reasoning.
- Target venues: NeurIPS, ICML, ICLR, ACL.
- Time window: 2025-03-17 to 2026-03-17.
- Max shortlist size: 20.

## 2) Source Quality Notes
- Primary sources used:
  - ICLR 2026 论文主要核对 OpenReview / ICLR virtual poster 页面。
  - ACL 2025 论文主要核对 ACL Anthology 页面与 PDF。
  - NeurIPS 2025 论文主要核对 NeurIPS virtual poster 页面及其关联的 OpenReview / arXiv 记录。
  - 预印本主要核对 arXiv 摘要页，以获得精确提交日期。
  - 复现信号主要核对官方 GitHub、作者主页或项目页，只在链接明显官方时采用。
- Known evidence gaps:
  - 最强的一批方法论文中仍有不少是预印本，实验结论尚未经过同行评审。
  - 部分 ICLR 2026 已接收论文的公开页面没有清晰暴露精确公开日期；因此我报告 venue year 和接收 track，并在日期精度不足时把置信度标为中等。
  - 该方向的评测仍高度偏向数学推理、规划、搜索和代码，真实复杂工具使用环境上的证据仍偏薄。
  - MAPoRL2 是同行评审论文且很强，但在本次使用的主来源中没有找到明确的官方代码仓库。

## 3) Seed-to-Literature Mapping
- Seed paper: MARTI: A Framework for Multi-Agent LLM Systems Reinforced Training and Inference（ICLR 2026 conference paper；seed PDF: `papers/marti.pdf`）。
- 从 seed 提取的问题定义:
  - 将多智能体推理与强化学习统一起来，让 LLM agent 团队的协作能力本身得到训练，而不只是依赖 prompt。
  - 在固定推理预算下，通过训练结构化多智能体 workflow，而不是只放大单智能体，来提升性能上限。
  - 通过集中式交互、credit assignment、reward shaping 和可扩展 rollout 基础设施，让多智能体 RL 变得可行。
- 从 seed 提取的方法族:
  - 集中式多智能体交互 + 分布式单智能体策略训练。
  - debate、chain-of-agents、mixture-of-agents 等 workflow 型协作。
  - 面向多轮轨迹的 reward shaping 与 credit assignment。
  - 基于 RL 或 RL-like 机制来适配协作策略，有的发生在训练期，有的发生在测试期。
- 从 seed 提取的搜索短语:
  - multi-agent llm reinforcement learning
  - multi-agent reinforced training and inference
  - collaborative llm post-training
  - multi-agent debate rl
  - multi-agent credit assignment llm
  - agent-wise advantage normalization
  - interaction rewards multi-agent llm
  - self-play multi-agent reasoning llm
  - multi-agent test-time reinforcement learning
  - collaborative llm reasoning benchmarks
  - asynchronous multi-agent rollout training
  - role-specialized llm collaboration rl
- Likely adjacent subtopics:
  - 用测试时经验注入替代参数更新
  - 通过博弈自博弈训练获得可迁移多智能体推理能力
  - 将代码生成环境作为多智能体 RL gymnasium
  - 多智能体 LLM 系统的失效诊断与分析
- Mapping note:
  - 入选的 8 篇论文里有 7 篇与 seed 的核心问题或方法族直接对齐（`same problem` 或 `same method family`）。唯一相关性稍弱的是 MATTRL：它把适配从训练期 RL 转移到了测试期经验注入，但它仍然直击同一个协作 / credit assignment 瓶颈，因此仍然值得放进核心阅读列表。

## 4) Shortlist (Top 8)

| Rank | Paper | Venue/Year | Why It Matters Now | Key Result | Reproducibility Signal | Links |
|------|-------|------------|--------------------|------------|------------------------|-------|
| 1 | MARTI: A Framework for Multi-Agent LLM Systems Reinforced Training and Inference | ICLR 2026 conference | 这是 seed，也是当前最强的“端到端多智能体 RL + 推理”基础设施锚点。 | 在一个 debate 设定中，AIME 从单智能体 RL baseline 的 53.5 提升到 65.0；在相同推理预算下，也把 Llama-3.2-3B 的平均分从 28.7 提升到 35.4。 | 官方 GitHub，含训练 / 推理脚本和文档。 | paper: https://openreview.net/pdf/4aa22a8e06de82401e250853fad2bce3d2ca43e8.pdf ; code: https://github.com/TsinghuaC3I/MARTI |
| 2 | CoMAS: Co-Evolving Multi-Agent Systems via Interaction Rewards | ICLR 2026 conference | 最近最值得关注的方向之一：从外部奖励转向“由交互本身生成”的内在奖励。 | 在大多数报告设定上优于未训练 agent 并达到 SOTA；消融实验表明奖励设计和 agent 多样性都很关键。 | 本次使用的主来源中未看到稳定公开代码链接。 | paper: https://openreview.net/pdf/f75a67569d81ce12c8ceb3e2bf9b960c9e0137a7.pdf ; arXiv: https://arxiv.org/abs/2510.08529 |
| 3 | Dr. MAS: Stable Reinforcement Learning for Multi-Agent LLM Systems | arXiv preprint, 2026-02-09 | 如果你的主要瓶颈是 RL 稳定性而不是 workflow 设计，这篇最该看。 | 相对 vanilla GRPO，在 math 上提升 +5.6 avg@16 和 +4.6 pass@16，在 search 上提升 +15.2 avg@16 和 +13.1 pass@16，并基本消除了梯度尖峰。 | 有官方项目页；代码存在，但主来源中暂未看到稳定公开仓库链接。 | paper: https://arxiv.org/abs/2602.08847 ; project: https://ltzheng.github.io/ |
| 4 | Stronger Together: On-Policy Reinforcement Learning for Collaborative LLMs | ICLR 2026 poster / arXiv 2025-10-13 | 最强的一批证据之一，说明 on-policy collaborative RL 可以超越 toy debate，覆盖 planning、coding、math、games。 | AT-GRPO 把长程规划准确率从 14.0-47.0 提到 96.0-99.5，同时在 coding 上平均提升 3.87-7.62，在 math 上提升 9.0-17.93。 | 官方代码和环境仓库可用。 | paper: https://arxiv.org/abs/2510.11062 ; code: https://github.com/pettingllms-ai/PettingLLMs |
| 5 | ReMA: Learning to Meta-think for LLMs with Multi-Agent Reinforcement Learning | NeurIPS 2025 poster | 这批论文里最适合看“角色分工”设计的一篇：一个 agent 负责规划 / 监控，另一个负责具体推理。 | 在高难数学推理和 LLM-as-a-Judge benchmark 上优于单智能体 RL baseline；并扩展到了多轮交互。 | 官方公开仓库可用。 | paper: https://neurips.cc/virtual/2025/poster/115462 ; code: https://github.com/ziyuwan/ReMA-public |
| 6 | Collaborative Multi-Agent Test-Time Reinforcement Learning for Reasoning | arXiv preprint, 2026-01-14 | 如果你想要 RL 式协作收益，但不想承担多智能体后训练的不稳定性，这篇最值得看。 | 在医学、数学和教育任务上，平均比 multi-agent baseline 高 3.67%，比可比 single-agent baseline 高 8.67%。 | 本次使用的主来源中未看到官方代码。 | paper: https://arxiv.org/abs/2601.09667 |
| 7 | MAPoRL2: Multi-Agent Post-Co-Training for Collaborative Large Language Models with Reinforcement Learning | ACL 2025 Long Papers | 这篇提供了最扎实的同行评审证据之一：协作能力可以被显式 post-train，而不是靠 prompt 碰运气。 | 在 GSM8K 和 ANLI 上，MAPoRL 训练后的 agent 会随着协作轮次增加而变好；而现成模型的协作不会稳定变好，naive SFT 甚至会把 turn-2/turn-3 准确率拉低。 | 在主来源中未找到官方代码。 | paper: https://aclanthology.org/2025.acl-long.1459/ |
| 8 | MARS: Reinforcing Multi-Agent Reasoning of LLMs through Self-Play in Strategic Games | ICLR 2026 poster / arXiv 2025-10-17 | 目前“用游戏自博弈学到可泛化多智能体推理能力”的最佳证据。 | 在 held-out games 上最高提升 28.7%，迁移到下游多智能体系统后，AIME 最高提升 +10.0%，GPQA-Diamond 最高提升 +12.5%。 | 官方 GitHub 提供 code/models。 | paper: https://arxiv.org/abs/2510.15414 ; code: https://github.com/thu-nics/MARS |

## 5) Paper Cards

### [Rank 1] MARTI: A Framework for Multi-Agent LLM Systems Reinforced Training and Inference
- Authors: Kaiyan Zhang, Kai Tian, Runze Liu, Sihang Zeng, Xuekai Zhu, Guoli Jia, Yuchen Fan, Xingtai Lv, Yuxin Zuo, Che Jiang, Yuru Wang, Jianyu Wang, Ermo Hua, Xinwei Long, Junqi Gao, Youbang Sun, Zhiyuan Ma, Ganqu Cui, Ning Ding, Biqing Qi, Bowen Zhou.
- Venue/Track/Year: ICLR 2026 conference paper.
- Contribution (1 sentence): 提出一个开源框架，把集中式多智能体交互、reward shaping、credit assignment 和分布式 RL 训练统一到同一个 LLM agent 系统里。
- Method sketch (2-4 bullets):
  - 使用集中式 workflow 来支持 debate、chain-of-agents、mixture-of-agents 与自定义多智能体交互图。
  - 在集中式 rollout 收集之上执行分布式单智能体策略优化。
  - 同时支持 rule-based verifier 和 generative reward model。
  - 通过异步 rollout 和 workflow 抽象提升吞吐与可扩展性。
- Best evidence:
  - 在一个高亮设定中，基于 DeepScaleR-1.5B-Preview 的多智能体 debate 在 AIME 上达到 65.0，而单智能体 baseline 为 53.5。
  - 在 Llama-3.2-3B-Instruct 上，MARTI 多智能体 RL 的平均分达到 35.4，高于 single-agent RL 的 28.7 和 majority-vote RL 的 30.0。
- Limitations:
  - 证据仍主要集中在 reasoning-heavy benchmark，而不是广义真实 agent 部署环境。
  - 框架很强，但很多 workflow 选择仍然对工程实现较敏感。
- Why selected:
  - 这是本次调研的 seed，也是其余论文的方法族起点。
  - 如果你要搭建或扩展多智能体 RL 栈，这篇是当前最核心的锚点。
- Relation to seed: same problem.
- Confidence: High on relevance; medium-high on empirical strength.
- URLs:
  - paper: https://openreview.net/pdf/4aa22a8e06de82401e250853fad2bce3d2ca43e8.pdf
  - code: https://github.com/TsinghuaC3I/MARTI

### [Rank 2] CoMAS: Co-Evolving Multi-Agent Systems via Interaction Rewards
- Authors: Xiangyuan Xue, Yifan Zhou, Guibin Zhang, Zaibin Zhang, Yijiang Li, Chen Zhang, Zhenfei Yin, Philip Torr, Wanli Ouyang, Lei Bai.
- Venue/Track/Year: ICLR 2026 conference paper；arXiv preprint dated 2025-10-09.
- Contribution (1 sentence): 提出一种去中心化多智能体自演化框架，让 agent 依靠交互过程中生成的内在奖励，而不是外部监督信号，持续改进。
- Method sketch (2-4 bullets):
  - 把讨论动态本身当成内在奖励的原材料。
  - 用 LLM-as-a-judge 对 proposer / evaluator 交互进行打分。
  - 在去中心化协同演化设定下对每个 agent 做 RL 优化。
  - 研究不同 agent 数量与多样性下的扩展性。
- Best evidence:
  - 论文报告在大多数评测设定上达到 SOTA。
  - 消融实验表明，一旦移除 interaction-based reward 组件，方法会明显退化，这说明核心设计确实起作用。
- Limitations:
  - 本次使用的主来源中没有看到清晰稳定的公开代码链接。
  - 奖励生成依赖 judge 质量，因此对弱 judge 的鲁棒性仍是风险点。
- Why selected:
  - 这是近期最清晰的“放弃外部显式奖励工程、转向交互内生奖励”的代表作。
  - 它和 MARTI 互补：解决同一个问题，但奖励哲学完全不同。
- Relation to seed: same problem.
- Confidence: Medium-high.
- URLs:
  - paper: https://openreview.net/pdf/f75a67569d81ce12c8ceb3e2bf9b960c9e0137a7.pdf
  - code: not surfaced on primary sources used

### [Rank 3] Dr. MAS: Stable Reinforcement Learning for Multi-Agent LLM Systems
- Authors: Lang Feng, Longtao Zheng, Shuo He, Fuxiang Zhang, Bo An.
- Venue/Track/Year: arXiv preprint, 2026-02-09.
- Contribution (1 sentence): 精确定位了 group-based RL 在异质多智能体 LLM 系统中的一个稳定性失效点，并用按 agent 归一化 advantage 的方式修复它。
- Method sketch (2-4 bullets):
  - 说明为什么全局归一化 baseline 会和不同 agent 的奖励分布失配。
  - 用按 agent 自身奖励统计归一化替代全局归一化。
  - 把算法修复与一个实用的多智能体训练框架、共享资源调度机制结合起来。
  - 同时评估同质和异质 agent-model 组合。
- Best evidence:
  - 相对 vanilla GRPO，在 math 上提升 +5.6 avg@16 和 +4.6 pass@16。
  - 在 search 上提升 +15.2 avg@16 和 +13.1 pass@16，并显著消除 gradient spikes。
- Limitations:
  - 仍然是预印本。
  - 它解决的是一个关键稳定性来源，但不是完整解决跨 agent、跨 turn 的 credit assignment 难题。
- Why selected:
  - 如果你当前最大的痛点是训练发散、方差大或梯度不稳，这篇应该排在 MARTI 之后优先读。
  - 它比“多智能体 RL 很难”这种泛泛结论更有操作性，因为它给出的干预非常具体，也容易迁移。
- Relation to seed: same method family.
- Confidence: High on usefulness; medium on long-run external validation.
- URLs:
  - paper: https://arxiv.org/abs/2602.08847
  - code: project page at https://ltzheng.github.io/

### [Rank 4] Stronger Together: On-Policy Reinforcement Learning for Collaborative LLMs
- Authors: Yujie Zhao, Lanxiang Hu, Yang Wang, Minmin Hou, Hao Zhang, Ke Ding, Jishen Zhao.
- Venue/Track/Year: ICLR 2026 poster；arXiv preprint dated 2025-10-13.
- Contribution (1 sentence): 提出 AT-GRPO，一种面向 collaborative LLM systems 的 agent-wise + turn-wise 分组 on-policy RL 算法，并配套支持 single-policy / multi-policy 的训练系统。
- Method sketch (2-4 bullets):
  - 针对多智能体 rollout 中 role 和 turn 的差异，重构 GRPO 的分组方式。
  - 同时支持共享策略和每个 agent 独立策略两种训练设定。
  - 在 games、long-horizon planning、coding 和 math 上做评估。
  - 提供环境和训练基础设施，而不只是一个算法点子。
- Best evidence:
  - 把 long-horizon planning 从 14.0-47.0 提升到 96.0-99.5。
  - 在 coding 上平均提升 3.87-7.62，在 math 上提升 9.0-17.93。
- Limitations:
  - 证据更偏文本协作任务，多模态或重工具使用环境不是其核心。
  - 规划任务上极大的增益值得后续复现实验重点核查。
- Why selected:
  - 在当前预印本里，这篇的跨任务实证包最强之一。
  - 如果你更关心一个 on-policy recipe，而不是像 MARTI 那样更强调总体框架，这篇特别有价值。
- Relation to seed: same method family.
- Confidence: Medium-high.
- URLs:
  - paper: https://arxiv.org/abs/2510.11062
  - code: https://github.com/pettingllms-ai/PettingLLMs

### [Rank 5] ReMA: Learning to Meta-think for LLMs with Multi-Agent Reinforcement Learning
- Authors: Ziyu Wan, Yunxiang Li, Xiaoyu Wen, Yan Song, Hanjing Wang, Linyi Yang, Mark Schmidt, Jun Wang, Weinan Zhang, Shuyue Hu, Ying Wen.
- Venue/Track/Year: NeurIPS 2025 poster；arXiv preprint dated 2025-03-12.
- Contribution (1 sentence): 用 multi-agent RL 将高层 meta-thinking 与底层 reasoning 显式拆开，让一个 agent 负责策略监督，另一个负责具体执行。
- Method sketch (2-4 bullets):
  - 构造一对层次化 agent：meta-thinking agent 与 reasoning agent。
  - 在 MARL 框架下联合训练二者。
  - 通过 turn-level ratio 等技巧把方法扩展到多轮场景。
  - 用消融分析两个角色在训练过程中的演化动态。
- Best evidence:
  - 在高难数学推理与 LLM-as-a-Judge benchmark 上优于 single-agent RL baseline。
  - 它还扩展到了多轮交互，而不只是单轮 planning trick。
- Limitations:
  - 从当前可访问的主来源看，细粒度 benchmark 表格信息不如其他几篇丰富。
  - 相比简单的 normalization 修复，这种层次化角色拆分更难直接插入已有 MAS 栈。
- Why selected:
  - 这是这组论文中最清晰的角色分工设计论文。
  - 它给出了把“协作”变成结构化架构设计而不只是奖励工程的一条明确路径。
- Relation to seed: same method family.
- Confidence: Medium.
- URLs:
  - paper: https://neurips.cc/virtual/2025/poster/115462
  - code: https://github.com/ziyuwan/ReMA-public

### [Rank 6] Collaborative Multi-Agent Test-Time Reinforcement Learning for Reasoning
- Authors: Zhiyuan Hu, Yunhai Hu, Juncheng Liu, Shuyue Stella Li, Yucheng Wang, Zhen Xu, See-Kiong Ng, Anh Tuan Luu, Xinxing Xu, Bryan Hooi, Cynthia Breazeal, Hae Won Park.
- Venue/Track/Year: arXiv preprint, 2026-01-14.
- Contribution (1 sentence): 用测试时经验检索与回注，替代不稳定的多智能体 RL 后训练，但依然保留了 credit assignment 的核心思想来提升协作质量。
- Method sketch (2-4 bullets):
  - 组建由不同 specialist 构成的多专家 team，进行多轮讨论。
  - 从先前高质量 utterance 中构建 turn-level experience pool。
  - 在讨论过程中检索并注入这些经验。
  - 系统比较不同 credit-assignment 方案对经验池构建的影响。
- Best evidence:
  - 在医学、数学、教育任务上，平均比 multi-agent baseline 提升 3.67%，比 single-agent baseline 提升 8.67%。
  - 论文直接把 distribution shift 下的鲁棒性作为核心目标，并且不需要参数更新。
- Limitations:
  - 它不是 MARTI 意义上的训练期 RL，因此如果你的目标是端到端训练策略，它的直接价值稍弱。
  - 本次使用的主来源中没有看到官方代码发布。
- Why selected:
  - 这是当前文献里最强的“如果 RL 训练太不稳 / 太贵，那么最接近的可行替代方案是什么？”答案。
  - 即便你最后仍坚持训练期 RL，这篇的 experience pool 设计也很可能能和 MARTI 类系统融合。
- Relation to seed: same problem.
- Confidence: Medium-high.
- URLs:
  - paper: https://arxiv.org/abs/2601.09667
  - code: not surfaced on primary sources used

### [Rank 7] MAPoRL2: Multi-Agent Post-Co-Training for Collaborative Large Language Models with Reinforcement Learning
- Authors: Chanwoo Park, Rina Foygel Barber, Asuman Ozdaglar, Jacob Andreas.
- Venue/Track/Year: ACL 2025 Long Papers，July 2025.
- Contribution (1 sentence): 提出一种 post-training 范式，显式教多个 LLM 如何跨多轮协作，而不是假设 debate 能靠 prompt 自然涌现。
- Method sketch (2-4 bullets):
  - 使用 verifier-based reward，同时考虑即时正确性与协作激励。
  - 在多轮交互轨迹上训练 agent，而不是只优化单轮输出。
  - 评估 collaboration skill 在跨任务与异质模型对之间的迁移能力。
  - 与“高质量 debate 轨迹上的 naive SFT”做正面对比。
- Best evidence:
  - 在 GSM8K 和 ANLI 上，经过 MAPoRL 训练的 agent 会随协作轮次增长而持续变好，而 off-the-shelf debate 并不会稳定提升。
  - 论文还报告 naive SFT 会让 turn-2 / turn-3 准确率下降，这反过来强化了 RL 的必要性。
- Limitations:
  - 在本次主来源中没有找到明确代码。
  - 和更新的 2025-2026 系统相比，任务规模和覆盖面更窄一些。
- Why selected:
  - 这是 shortlist 里最干净的同行评审证据之一。
  - 如果你只想要一篇可靠论文来证明“协作本身是可以训练的能力”，就读它。
- Relation to seed: same method family.
- Confidence: High on concept, medium-high on generality.
- URLs:
  - paper: https://aclanthology.org/2025.acl-long.1459/
  - code: not surfaced on primary sources used

### [Rank 8] MARS: Reinforcing Multi-Agent Reasoning of LLMs through Self-Play in Strategic Games
- Authors: Huining Yuan, Zelai Xu, Zheyue Tan, Xiangmin Yi, Mo Guang, Kaiwen Long, Haojia Hui, Boxun Li, Xinlei Chen, Bo Zhao, Xiao-Ping Zhang, Chao Yu, Yu Wang.
- Venue/Track/Year: ICLR 2026 poster；arXiv preprint dated 2025-10-17.
- Contribution (1 sentence): 通过 cooperative + competitive games 的 self-play 训练 LLM agent，学习可以迁移到一般多智能体推理任务的协作能力。
- Method sketch (2-4 bullets):
  - 不是直接在 reasoning benchmark 上训练，而是在战略博弈中进行 self-play。
  - 加入 turn-level advantage estimation 做更细粒度 credit assignment。
  - 用 agent-specific advantage normalization 提高稳定性。
  - 评估从 games 向下游 reasoning systems 的迁移效果。
- Best evidence:
  - 在 held-out games 上最高提升 28.7%。
  - 注入下游 MAS 后，AIME 最高提升 10.0%，GPQA-Diamond 最高提升 12.5%。
- Limitations:
  - 从 game self-play 迁移到开放式 agent 任务，本质上仍是间接证据。
  - 不同主来源表面对 GPQA 增益数字有轻微差异，因此我对精确下游数值保持中等置信度。
- Why selected:
  - 这是目前“self-play 不只是玩具训练设置，而能产生可迁移 MAS reasoning 能力”的最佳证据。
  - 它在技术上也与 Dr. MAS 收敛到类似方向：细粒度 credit assignment + per-agent normalization。
- Relation to seed: same method family.
- Confidence: Medium-high.
- URLs:
  - paper: https://arxiv.org/abs/2510.15414
  - code: https://github.com/thu-nics/MARS

## 6) Not Selected but Notable
- Why Do Multi-Agent LLM Systems Fail?（arXiv, 2025-03-17）: 极好的诊断型论文，在 150+ tasks 上给出 14 类 failure taxonomy，但它主要是失效分析，而不是训练 / 推理改进方法。URL: https://arxiv.org/abs/2503.13657
- ReSo: A Reward-driven Self-organizing LLM-based Multi-Agent System for Reasoning Tasks（EMNLP 2025, November 2025）: reward model + agent selection 的设计很强，而且有 code，但它不在你指定的目标 venue 内，同时也更偏 self-organization，而不是 RL post-training。URL: https://aclanthology.org/2025.emnlp-main.808/
- AgentArk: Distilling Multi-Agent Intelligence into a Single LLM Agent（arXiv, 2026-02-03）: 如果你更在意部署成本而不是保留显式 MAS 推理形态，这篇很有价值，但它属于 distillation，而不是直接的 MAS training paper。URL: https://arxiv.org/abs/2602.03955
- MARTI-MARS^2: Scaling Multi-Agent Self-Search via Reinforcement Learning for Code Generation（arXiv, 2026-02）: 对代码生成特定场景非常相关，但过于领域化，不适合作为首轮核心阅读列表压过前面的通用系统论文。URL: https://arxiv.org/abs/2602.07848

## 7) Trends and Openings
- Trend 1: 该方向正在收敛到一个共同判断：细粒度 credit assignment 是核心技术瓶颈。MARTI、Dr. MAS、MAPoRL2、MATTRL、MARS 都是在不同层面解决同一个问题。
- Trend 2: 按 agent 归一化或按 role/turn 分组，正在成为多智能体 RL 的关键稳定化技巧，尤其是在 agent 角色异质、奖励分布不同的情况下。
- Contradictions/disagreements:
  - 一部分论文强调必须做训练期 RL 才能真正学到协作（MARTI、MAPoRL2、Dr. MAS、Stronger Together），而 MATTRL 则认为测试期经验注入可以以更稳定的方式拿到相当一部分收益。
  - CoMAS 认为交互内生奖励可能已经足够，而其他论文仍更依赖 verifier、外部奖励或任务正确性信号。
- Potential research openings:
  - 将 MARTI 式 workflow 基础设施与 Dr. MAS 式稳定化，以及 MATTRL 式 experience pool 结合起来。
  - 测试 CoMAS 的 intrinsic interaction rewards 能否替代 MARTI 流水线中的部分 verifier 工程。
  - 以与 reasoning benchmark 同等严谨的方式，推进到真实 tool-use 或 web 环境。
  - 更系统地研究 heterogeneous agent specialization：MARS、Dr. MAS、CoMAS 都暗示 policy diversity 很重要，但当前还没有被系统刻画清楚。

## 8) Coverage Gaps and Blind Spots
- Missing sub-areas:
  - 在你指定 venue 的近 12 个月论文里，直接研究“真实工具使用 / 网页导航 / 多模态交互”的多智能体 RL 论文很少。
  - 同时，训练阶段的 safety、verification、cost-aware orchestration 也覆盖不足。
- Venue bias risk:
  - 最强的一批近期论文高度集中在 ICLR 2026 与 arXiv，因此 shortlist 偏向“新但尚未完全验证”的工作。
  - ICML 2025 在这个非常具体的切片上贡献较少，这更像真实的 venue gap，而不太像检索失败。
- Time-window risk:
  - “最近 12 个月”恰好覆盖了一个快速爆发期，包含大量 preprint 与 poster / workshop 阶段系统；随着复现和正式版出现，排序可能会很快变化。

## 9) Rating Summary
- Chosen profile and weights:
  - `seed_focus`
  - Relevance-to-seed 0.45
  - Novelty 0.15
  - Evidence strength 0.15
  - Reproducibility 0.10
  - Practical impact 0.15
- Per-paper score breakdown table:

| Paper | Relation to seed | Relevance | Novelty | Evidence | Reproducibility | Impact | Final weighted score |
|------|------------------|-----------|---------|----------|-----------------|--------|----------------------|
| MARTI | same problem | 10 | 8 | 8 | 9 | 9 | 9.15 |
| CoMAS | same problem | 9 | 8 | 8 | 7 | 8 | 8.35 |
| Dr. MAS | same method family | 9 | 8 | 7 | 6 | 8 | 8.10 |
| Stronger Together | same method family | 8 | 8 | 7 | 9 | 8 | 7.95 |
| ReMA | same method family | 8 | 8 | 7 | 8 | 7 | 7.70 |
| MATTRL | same problem | 8 | 7 | 7 | 8 | 8 | 7.70 |
| MAPoRL2 | same method family | 8 | 7 | 8 | 5 | 8 | 7.55 |
| MARS | same method family | 7 | 8 | 7 | 9 | 7 | 7.35 |
- Top-3 papers by each single dimension:
  - Relevance: MARTI; CoMAS; Dr. MAS.
  - Novelty: CoMAS; Dr. MAS; Stronger Together.
  - Evidence: MARTI; CoMAS; MAPoRL2.
  - Reproducibility: MARTI; Stronger Together; MARS.
  - Impact: MARTI; CoMAS; Dr. MAS.

## 10) Action Plan (2 Weeks)
- Day 1-3: 精读 MARTI、Dr. MAS、MAPoRL2，把训练循环、reward / advantage 计算、workflow 抽象整理成一页对比备忘录。
- Day 4-5: 阅读 CoMAS 和 Stronger Together，重点判断 intrinsic interaction rewards 和 AT-GRPO 能否并入 MARTI 栈。
- Day 6-7: 阅读 MATTRL 与 MARS，判断对你的目标任务来说，“测试时经验注入”还是“自博弈预训练”更可能成为有效辅助路径。
- Day 8-10: 回读 ReMA 与 seed，明确在你自己的系统里，哪些 agent 角色应单独训练，哪些角色应单独做归一化。
- Day 11-12: 写一份最小设计提案，主题是 “MARTI + Dr. MAS stabilization + optional MATTRL memory pool”，包括一套 benchmark 与一组 ablation grid。
- Day 13-14: 形成下一步实验 idea memo，优先级按以下顺序： (1) 在 MARTI 中加入 Dr. MAS 式 agent-wise normalization，(2) 在 MARTI inference 之上加 MATTRL 式 experience pool，(3) 尝试 CoMAS 式 intrinsic interaction rewards，(4) 如果前三项平台期明显，再评估 MARS 式 self-play transfer。
