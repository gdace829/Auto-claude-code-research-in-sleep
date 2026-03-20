# Literature Scout Report (Codex-Only)

## 1) Scope
- Topic: Reinforcement-learning-based training and inference frameworks for LLM multi-agent reasoning systems, centered on scalable collaboration under a fixed inference budget.
- Keywords: multi-agent reinforcement learning for LLMs; centralized interaction distributed training; multi-agent debate RL; chain-of-agents RL; mixture-of-agents RL; credit assignment in multi-turn multi-agent systems; agent-wise reward normalization; asynchronous multi-agent rollouts; collaborative LLM post-training; self-play multi-agent reasoning; interaction rewards; test-time reinforcement learning for multi-agent reasoning.
- Target venues: NeurIPS, ICML, ICLR, ACL.
- Time window: 2025-03-17 to 2026-03-17.
- Max shortlist size: 20.

## 2) Source Quality Notes
- Primary sources used:
  - ICLR 2026 papers were checked from OpenReview/ICLR virtual poster pages.
  - ACL 2025 papers were checked from ACL Anthology pages/PDFs.
  - NeurIPS 2025 papers were checked from NeurIPS virtual poster pages and linked OpenReview/arXiv records.
  - Preprints were checked from arXiv abstract pages for exact submission dates.
  - Reproducibility signals were checked from official GitHub or author/project pages when directly linked or clearly official.
- Known evidence gaps:
  - Several of the strongest method papers are still preprints, so empirical claims are not yet peer-reviewed.
  - Exact public posting dates were not surfaced cleanly for some ICLR 2026 accepted papers; I report the venue year and accepted track, and mark confidence as medium where date precision is weak.
  - The literature is heavily benchmarked on math/reasoning, planning, search, and coding; evidence on messy real-world tool-use environments is still thin.
  - MAPoRL2 is peer-reviewed and strong, but I did not find an official code repository from the primary sources used here.

## 3) Seed-to-Literature Mapping
- Seed paper: MARTI: A Framework for Multi-Agent LLM Systems Reinforced Training and Inference (ICLR 2026 conference paper; seed PDF: `papers/marti.pdf`).
- Seed-extracted problem framing:
  - Unify multi-agent inference and reinforcement learning so LLM agent teams can improve collaborative reasoning rather than relying only on prompting.
  - Improve performance ceilings under a fixed inference budget by training structured multi-agent workflows instead of only scaling a single agent.
  - Make multi-agent RL practical through centralized interaction, credit assignment, reward shaping, and scalable rollout infrastructure.
- Seed-extracted method family:
  - Centralized multi-agent interaction with distributed per-agent policy training.
  - Workflow-based collaboration such as debate, chain-of-agents, and mixture-of-agents.
  - Reward shaping and credit assignment over multi-turn trajectories.
  - RL or RL-like adaptation of agent collaboration policies, sometimes at train time and sometimes at test time.
- Seed-extracted search phrases:
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
  - test-time experience injection instead of parameter updates
  - self-play game training for generalizable multi-agent reasoning
  - code-generation environments as multi-agent RL gymnasia
  - failure analysis and diagnosis of multi-agent LLM systems
- Mapping note:
  - 7 of the 8 shortlisted papers are direct matches to the seed’s core problem or method family (`same problem` or `same method family`). The only weaker match is MATTRL, which shifts adaptation from train-time RL to inference-time experience injection, but remains highly relevant because it tackles the same collaboration/credit-assignment bottleneck with a more stable mechanism.

## 4) Shortlist (Top 8)

| Rank | Paper | Venue/Year | Why It Matters Now | Key Result | Reproducibility Signal | Links |
|------|-------|------------|--------------------|------------|------------------------|-------|
| 1 | MARTI: A Framework for Multi-Agent LLM Systems Reinforced Training and Inference | ICLR 2026 conference | Seed paper and strongest current infrastructure anchor for end-to-end multi-agent RL plus inference. | Reports AIME 65.0 vs 53.5 for the single-agent RL baseline in one debate setting; also improves Llama-3.2-3B average benchmark score from 28.7 to 35.4 under the same inference budget. | Official GitHub with training/inference scripts and docs. | paper: https://openreview.net/pdf/4aa22a8e06de82401e250853fad2bce3d2ca43e8.pdf ; code: https://github.com/TsinghuaC3I/MARTI |
| 2 | CoMAS: Co-Evolving Multi-Agent Systems via Interaction Rewards | ICLR 2026 conference | Most interesting recent move away from externally specified rewards toward intrinsic interaction rewards. | Consistently outperforms untrained agents and reaches state-of-the-art performance across most reported evaluation settings; ablations show reward design and agent diversity both matter. | No stable public code link surfaced from primary sources used here. | paper: https://openreview.net/pdf/f75a67569d81ce12c8ceb3e2bf9b960c9e0137a7.pdf ; arXiv: https://arxiv.org/abs/2510.08529 |
| 3 | Dr. MAS: Stable Reinforcement Learning for Multi-Agent LLM Systems | arXiv preprint, 2026-02-09 | Best current paper if your bottleneck is RL stability rather than workflow design. | Beats vanilla GRPO by +5.6 avg@16 and +4.6 pass@16 on math, and by +15.2 avg@16 and +13.1 pass@16 on search, while largely removing gradient spikes. | Official project page; code exists but stable public repo link is not yet clean from primary sources. | paper: https://arxiv.org/abs/2602.08847 ; project: https://ltzheng.github.io/ |
| 4 | Stronger Together: On-Policy Reinforcement Learning for Collaborative LLMs | ICLR 2026 poster / arXiv 2025-10-13 | Strongest evidence that on-policy collaborative RL can scale beyond toy debate into planning, coding, math, and games. | AT-GRPO raises long-horizon planning accuracy from 14.0-47.0 to 96.0-99.5, with average gains of 3.87-7.62 on coding and 9.0-17.93 on math. | Official code and environment repo. | paper: https://arxiv.org/abs/2510.11062 ; code: https://github.com/pettingllms-ai/PettingLLMs |
| 5 | ReMA: Learning to Meta-think for LLMs with Multi-Agent Reinforcement Learning | NeurIPS 2025 poster | Best paper here for hierarchical role separation: one agent plans/monitors, the other executes reasoning. | Outperforms single-agent RL baselines on competitive math and LLM-as-a-Judge benchmarks; also extends to multi-turn interaction with turn-level ratio tricks. | Official public repo. | paper: https://neurips.cc/virtual/2025/poster/115462 ; code: https://github.com/ziyuwan/ReMA-public |
| 6 | Collaborative Multi-Agent Test-Time Reinforcement Learning for Reasoning | arXiv preprint, 2026-01-14 | Best adjacent paper if you want the collaboration gains of RL without unstable multi-agent post-training. | Improves accuracy by 3.67% over a multi-agent baseline and 8.67% over comparable single-agent baselines across medicine, math, and education. | No official code surfaced from primary sources used here. | paper: https://arxiv.org/abs/2601.09667 |
| 7 | MAPoRL2: Multi-Agent Post-Co-Training for Collaborative Large Language Models with Reinforcement Learning | ACL 2025 Long Papers | Strong peer-reviewed evidence that collaboration skills can be explicitly post-trained rather than hoped for via prompting. | MAPoRL-trained agents improve over turns on GSM8K and ANLI, while off-the-shelf collaboration fails to improve and naive SFT can even degrade turn-2/turn-3 accuracy. | Official code not found from the primary sources checked. | paper: https://aclanthology.org/2025.acl-long.1459/ |
| 8 | MARS: Reinforcing Multi-Agent Reasoning of LLMs through Self-Play in Strategic Games | ICLR 2026 poster / arXiv 2025-10-17 | Best evidence that self-play in games can transfer into more general multi-agent reasoning ability. | Reports up to 28.7% gains on held-out games and downstream multi-agent gains up to +10.0% on AIME and +12.5% on GPQA-Diamond. | Official GitHub with code/models. | paper: https://arxiv.org/abs/2510.15414 ; code: https://github.com/thu-nics/MARS |

## 5) Paper Cards

### [Rank 1] MARTI: A Framework for Multi-Agent LLM Systems Reinforced Training and Inference
- Authors: Kaiyan Zhang, Kai Tian, Runze Liu, Sihang Zeng, Xuekai Zhu, Guoli Jia, Yuchen Fan, Xingtai Lv, Yuxin Zuo, Che Jiang, Yuru Wang, Jianyu Wang, Ermo Hua, Xinwei Long, Junqi Gao, Youbang Sun, Zhiyuan Ma, Ganqu Cui, Ning Ding, Biqing Qi, Bowen Zhou.
- Venue/Track/Year: ICLR 2026 conference paper.
- Contribution (1 sentence): Proposes an open-source framework that unifies centralized multi-agent interaction, reward shaping, credit assignment, and distributed RL training for LLM agent teams.
- Method sketch (2-4 bullets):
  - Uses centralized workflows for debate, chain-of-agents, mixture-of-agents, and custom multi-agent interaction graphs.
  - Performs distributed per-agent policy optimization on top of centralized rollout collection.
  - Supports both rule-based verifiers and generative reward models.
  - Adds asynchronous rollouts and workflow abstractions to improve throughput and extensibility.
- Best evidence:
  - In one highlighted setting, multi-agent debate based on DeepScaleR-1.5B-Preview reaches 65.0 on AIME versus 53.5 for a single-agent baseline.
  - On Llama-3.2-3B-Instruct, MARTI-based multi-agent RL reaches 35.4 average score versus 28.7 for single-agent RL and 30.0 for majority-vote RL.
- Limitations:
  - Evidence is concentrated in reasoning-heavy benchmarks rather than broad real-world agent deployments.
  - The paper gives a strong framework and promising results, but many workflow choices remain engineering-sensitive.
- Why selected:
  - This is the seed and defines the main method family for the rest of the reading list.
  - If you want to build or extend a multi-agent RL stack, this is the current anchor paper.
- Relation to seed: same problem.
- Confidence: High on relevance; medium-high on empirical strength.
- URLs:
  - paper: https://openreview.net/pdf/4aa22a8e06de82401e250853fad2bce3d2ca43e8.pdf
  - code: https://github.com/TsinghuaC3I/MARTI

### [Rank 2] CoMAS: Co-Evolving Multi-Agent Systems via Interaction Rewards
- Authors: Xiangyuan Xue, Yifan Zhou, Guibin Zhang, Zaibin Zhang, Yijiang Li, Chen Zhang, Zhenfei Yin, Philip Torr, Wanli Ouyang, Lei Bai.
- Venue/Track/Year: ICLR 2026 conference paper; arXiv preprint dated 2025-10-09.
- Contribution (1 sentence): Introduces a decentralized multi-agent self-evolution framework where agents learn from intrinsically generated interaction rewards instead of relying on external supervision.
- Method sketch (2-4 bullets):
  - Uses discussion dynamics themselves as the raw material for intrinsic rewards.
  - Applies an LLM-as-a-judge module to score proposer/evaluator interactions.
  - Optimizes each agent with RL under decentralized co-evolution.
  - Studies scaling by varying the number and diversity of agents.
- Best evidence:
  - The paper reports state-of-the-art performance across most of its evaluation settings.
  - Ablations show that removing the interaction-based reward components breaks the method, which is strong evidence that the central idea matters.
- Limitations:
  - Public code availability is unclear from the primary sources I used.
  - Because reward generation depends on judge quality, robustness to weak judges remains a risk.
- Why selected:
  - It is the clearest recent alternative to externally verified or fully hand-crafted reward pipelines.
  - It complements MARTI: same problem, different reward philosophy.
- Relation to seed: same problem.
- Confidence: Medium-high.
- URLs:
  - paper: https://openreview.net/pdf/f75a67569d81ce12c8ceb3e2bf9b960c9e0137a7.pdf
  - code: not surfaced on primary sources used

### [Rank 3] Dr. MAS: Stable Reinforcement Learning for Multi-Agent LLM Systems
- Authors: Lang Feng, Longtao Zheng, Shuo He, Fuxiang Zhang, Bo An.
- Venue/Track/Year: arXiv preprint, 2026-02-09.
- Contribution (1 sentence): Identifies and fixes a specific stability failure in group-based RL for heterogeneous multi-agent LLM systems through agent-wise advantage normalization.
- Method sketch (2-4 bullets):
  - Shows why global normalization baselines are mismatched to diverse agent reward distributions.
  - Replaces global normalization with per-agent reward-statistic normalization.
  - Couples the algorithm with a practical multi-agent training framework and shared-resource scheduling.
  - Evaluates both homogeneous and heterogeneous agent-model assignments.
- Best evidence:
  - Improves over vanilla GRPO by +5.6 avg@16 and +4.6 pass@16 on math.
  - Improves by +15.2 avg@16 and +13.1 pass@16 on search while largely eliminating gradient spikes.
- Limitations:
  - Still a preprint.
  - Fixes one major source of instability, but not the full credit-assignment problem across agents and turns.
- Why selected:
  - This is the highest-priority read after MARTI if training collapse or noisy gradients are your current blocker.
  - It is more actionable than broader “multi-agent RL is hard” papers because the intervention is precise and easy to transplant.
- Relation to seed: same method family.
- Confidence: High on usefulness; medium on long-run external validation.
- URLs:
  - paper: https://arxiv.org/abs/2602.08847
  - code: project page at https://ltzheng.github.io/

### [Rank 4] Stronger Together: On-Policy Reinforcement Learning for Collaborative LLMs
- Authors: Yujie Zhao, Lanxiang Hu, Yang Wang, Minmin Hou, Hao Zhang, Ke Ding, Jishen Zhao.
- Venue/Track/Year: ICLR 2026 poster; arXiv preprint dated 2025-10-13.
- Contribution (1 sentence): Proposes AT-GRPO, an agent- and turn-wise grouped on-policy RL algorithm for collaborative LLM systems, with a training stack that supports both single-policy and multi-policy regimes.
- Method sketch (2-4 bullets):
  - Adapts GRPO grouping to account for role and turn differences in multi-agent rollouts.
  - Supports shared-policy and per-agent-policy training setups.
  - Evaluates collaborative RL across games, long-horizon planning, coding, and math.
  - Ships environments and infrastructure rather than only reporting algorithmic results.
- Best evidence:
  - Boosts long-horizon planning from 14.0-47.0 to 96.0-99.5.
  - Reports 3.87-7.62 average gains on coding tasks and 9.0-17.93 on math.
- Limitations:
  - Evidence leans toward text-based collaboration tasks; multimodal or tool-heavy settings are not the center of the paper.
  - The very large planning gains warrant close reproduction scrutiny.
- Why selected:
  - Among the current preprints, this has one of the strongest breadth-of-domain empirical packages.
  - It is directly useful if you care about an on-policy recipe instead of MARTI’s broader framework emphasis.
- Relation to seed: same method family.
- Confidence: Medium-high.
- URLs:
  - paper: https://arxiv.org/abs/2510.11062
  - code: https://github.com/pettingllms-ai/PettingLLMs

### [Rank 5] ReMA: Learning to Meta-think for LLMs with Multi-Agent Reinforcement Learning
- Authors: Ziyu Wan, Yunxiang Li, Xiaoyu Wen, Yan Song, Hanjing Wang, Linyi Yang, Mark Schmidt, Jun Wang, Weinan Zhang, Shuyue Hu, Ying Wen.
- Venue/Track/Year: NeurIPS 2025 poster; arXiv preprint dated 2025-03-12.
- Contribution (1 sentence): Uses multi-agent RL to split high-level meta-thinking from low-level reasoning, so one agent supervises strategy while another performs execution.
- Method sketch (2-4 bullets):
  - Creates a hierarchical pair of agents: meta-thinking and reasoning.
  - Trains them jointly with aligned objectives under MARL.
  - Extends the design from single-turn to multi-turn settings with turn-level ratio handling.
  - Analyzes the dynamics of the two roles through ablations.
- Best evidence:
  - Outperforms single-agent RL baselines on difficult mathematical reasoning and LLM-as-a-Judge benchmarks.
  - The multi-turn extension suggests the method is not only a one-step planning trick.
- Limitations:
  - Evidence in the accessible primary sources is more abstract-level than benchmark-table detailed.
  - The hierarchical decomposition may be harder to integrate into arbitrary existing MAS stacks than simpler normalization fixes.
- Why selected:
  - It is the cleanest role-specialization paper in this slice of the literature.
  - It gives a concrete way to turn “coordination” into architectural separation rather than only reward engineering.
- Relation to seed: same method family.
- Confidence: Medium.
- URLs:
  - paper: https://neurips.cc/virtual/2025/poster/115462
  - code: https://github.com/ziyuwan/ReMA-public

### [Rank 6] Collaborative Multi-Agent Test-Time Reinforcement Learning for Reasoning
- Authors: Zhiyuan Hu, Yunhai Hu, Juncheng Liu, Shuyue Stella Li, Yucheng Wang, Zhen Xu, See-Kiong Ng, Anh Tuan Luu, Xinxing Xu, Bryan Hooi, Cynthia Breazeal, Hae Won Park.
- Venue/Track/Year: arXiv preprint, 2026-01-14.
- Contribution (1 sentence): Replaces unstable multi-agent RL post-training with inference-time experience retrieval and reinjection, while still using credit assignment to improve collaboration quality.
- Method sketch (2-4 bullets):
  - Forms a multi-expert specialist team for multi-round discussion.
  - Builds a turn-level experience pool from prior successful utterances.
  - Retrieves and injects those experiences during deliberation.
  - Studies different credit-assignment schemes for building the experience pool.
- Best evidence:
  - Average gains of 3.67% over a multi-agent baseline and 8.67% over single-agent baselines across medicine, math, and education.
  - The paper directly targets distribution-shift robustness without parameter tuning.
- Limitations:
  - It is not train-time RL in the MARTI sense, so it is less useful if your goal is to train policies end to end.
  - I did not find an official code release from the primary sources checked.
- Why selected:
  - It is the strongest “if RL training is too unstable or too expensive, what is the closest practical substitute?” paper in this pool.
  - It is strategically relevant even if you ultimately stay with train-time RL, because its experience-pool design could be merged into a MARTI-like system.
- Relation to seed: same problem.
- Confidence: Medium-high.
- URLs:
  - paper: https://arxiv.org/abs/2601.09667
  - code: not surfaced on primary sources used

### [Rank 7] MAPoRL2: Multi-Agent Post-Co-Training for Collaborative Large Language Models with Reinforcement Learning
- Authors: Chanwoo Park, Rina Foygel Barber, Asuman Ozdaglar, Jacob Andreas.
- Venue/Track/Year: ACL 2025 Long Papers, July 2025.
- Contribution (1 sentence): Introduces a post-training paradigm that explicitly teaches multiple LLMs to collaborate over multiple turns instead of assuming debate behavior emerges from prompting.
- Method sketch (2-4 bullets):
  - Uses a verifier-based reward model for both immediate correctness and collaborative incentives.
  - Trains agents over multi-turn interactions rather than isolated outputs.
  - Evaluates transfer of collaboration skill across tasks and heterogeneous model pairs.
  - Compares RL against naive supervised fine-tuning on high-quality debate traces.
- Best evidence:
  - MAPoRL-trained agents improve as collaboration proceeds on GSM8K and ANLI, while off-the-shelf debate does not reliably improve across turns.
  - The paper also reports that naive SFT on collaboration trajectories can degrade turn-2 and turn-3 accuracy, which strengthens the case for RL specifically.
- Limitations:
  - Code availability was not clear from the primary sources I checked.
  - Compared with newer 2025-2026 systems, the scale and breadth of tasks are narrower.
- Why selected:
  - It is the cleanest peer-reviewed paper in this shortlist.
  - If you need one trustworthy reference for “collaboration is a trainable capability,” this is it.
- Relation to seed: same method family.
- Confidence: High on concept, medium-high on generality.
- URLs:
  - paper: https://aclanthology.org/2025.acl-long.1459/
  - code: not surfaced on primary sources used

### [Rank 8] MARS: Reinforcing Multi-Agent Reasoning of LLMs through Self-Play in Strategic Games
- Authors: Huining Yuan, Zelai Xu, Zheyue Tan, Xiangmin Yi, Mo Guang, Kaiwen Long, Haojia Hui, Boxun Li, Xinlei Chen, Bo Zhao, Xiao-Ping Zhang, Chao Yu, Yu Wang.
- Venue/Track/Year: ICLR 2026 poster; arXiv preprint dated 2025-10-17.
- Contribution (1 sentence): Trains LLM agents through self-play in cooperative and competitive games to learn generalizable multi-agent reasoning skills.
- Method sketch (2-4 bullets):
  - Uses self-play over strategic games rather than only reasoning benchmarks.
  - Adds turn-level advantage estimation for credit assignment.
  - Uses agent-specific advantage normalization for stability.
  - Evaluates transfer from games to downstream reasoning systems.
- Best evidence:
  - Reports up to 28.7% improvement on held-out games.
  - When plugged into downstream MASs, improves AIME by up to 10.0% and GPQA-Diamond by up to 12.5%.
- Limitations:
  - Transfer from game self-play to open-ended agent tasks is promising but still indirect.
  - The reported GPQA gain differs slightly across source surfaces, so I treat exact downstream numbers with medium confidence.
- Why selected:
  - This is the best evidence that self-play can be more than a toy training setup for MAS reasoning.
  - It also converges on the same technical pattern as Dr. MAS: fine-grained credit assignment plus per-agent normalization.
- Relation to seed: same method family.
- Confidence: Medium-high.
- URLs:
  - paper: https://arxiv.org/abs/2510.15414
  - code: https://github.com/thu-nics/MARS

## 6) Not Selected but Notable
- Why Do Multi-Agent LLM Systems Fail? (arXiv, 2025-03-17): excellent diagnostic paper with a 14-failure-mode taxonomy across 150+ tasks, but it is primarily failure analysis rather than a training or inference-improvement method. URL: https://arxiv.org/abs/2503.13657
- ReSo: A Reward-driven Self-organizing LLM-based Multi-Agent System for Reasoning Tasks (EMNLP 2025, November 2025): strong reward-model-plus-agent-selection paper with code, but it falls outside the requested target venues and emphasizes self-organization more than RL post-training. URL: https://aclanthology.org/2025.emnlp-main.808/
- AgentArk: Distilling Multi-Agent Intelligence into a Single LLM Agent (arXiv, 2026-02-03): promising if deployment cost matters more than keeping an explicit MAS at inference time, but it is a distillation paper rather than a direct MAS training paper. URL: https://arxiv.org/abs/2602.03955
- MARTI-MARS^2: Scaling Multi-Agent Self-Search via Reinforcement Learning for Code Generation (arXiv, 2026-02): highly relevant for code-generation-specific multi-agent RL, but too domain-specific to outrank the broader systems above for a first-pass core reading list. URL: https://arxiv.org/abs/2602.07848

## 7) Trends and Openings
- Trend 1: The field is converging on fine-grained credit assignment as a central technical bottleneck. MARTI, Dr. MAS, MAPoRL2, MATTRL, and MARS all attack the same issue from different angles.
- Trend 2: Per-agent normalization or role-aware grouping is emerging as a practical stability trick for multi-agent RL, especially once agents have heterogeneous roles or reward distributions.
- Contradictions/disagreements:
  - Some papers argue for explicit train-time RL over collaborative rollouts (MARTI, MAPoRL2, Dr. MAS, Stronger Together), while MATTRL argues that inference-time experience injection can capture a substantial fraction of the benefit more stably.
  - CoMAS suggests intrinsic interaction rewards may be enough, while other papers still rely on verifiers, external rewards, or task-grounded correctness signals.
- Potential research openings:
  - Combine MARTI-like workflow infrastructure with Dr. MAS-style stability fixes and MATTRL-style experience pools.
  - Test whether intrinsic interaction rewards from CoMAS can replace part of verifier engineering in a MARTI pipeline.
  - Move beyond math/search/coding into tool-use or web environments with the same rigor as the reasoning benchmarks.
  - Study heterogeneous agent specialization more seriously: MARS, Dr. MAS, and CoMAS all hint that policy diversity matters, but it is not yet systematically mapped.

## 8) Coverage Gaps and Blind Spots
- Missing sub-areas:
  - Very little peer-reviewed work in the requested venue set directly studies multi-agent RL for real-world tool use, web navigation, or multimodal interaction.
  - There is also limited coverage of safety, verification, and cost-aware orchestration during training.
- Venue bias risk:
  - The strongest recent papers are concentrated in ICLR 2026 and arXiv, so the shortlist is skewed toward fresh but partially unvalidated work.
  - ICML 2025 contributes little in this exact slice, which may reflect a real venue gap rather than a search failure.
- Time-window risk:
  - The last-12-month window captures a fast-moving wave of preprints and workshop/poster-stage systems; some rankings may shift quickly once replication or camera-ready versions appear.

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
- Day 1-3: Read MARTI, Dr. MAS, and MAPoRL2 closely; extract the exact training loop, reward/advantage computation, and workflow abstractions into a one-page comparison memo.
- Day 4-5: Read CoMAS and Stronger Together; focus on whether intrinsic interaction rewards and AT-GRPO can be merged with the MARTI stack.
- Day 6-7: Read MATTRL and MARS; decide whether test-time experience injection or self-play pretraining is the more plausible auxiliary path for your target tasks.
- Day 8-10: Re-read ReMA plus the seed; map which agent roles in your own system should be trained separately versus normalized separately.
- Day 11-12: Build a minimal design proposal for “MARTI + Dr. MAS stabilization + optional MATTRL memory pool,” including one benchmark suite and one ablation grid.
- Day 13-14: Produce an idea memo ranking the next experiment in this order: (1) Dr. MAS-style agent-wise normalization inside MARTI, (2) MATTRL-style experience pool on top of MARTI inference, (3) CoMAS-style intrinsic interaction rewards, (4) MARS-style self-play transfer if the first three plateau.
