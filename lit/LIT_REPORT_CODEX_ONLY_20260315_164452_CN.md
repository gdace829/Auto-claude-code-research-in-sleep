# 文献调研报告（仅 Codex）

## 1) Scope
- Topic: 通过外部化的经验、技能与工作流记忆来提升多模态智能体工具使用能力的持续改进。
- Keywords: multimodal agents; continual learning without finetuning; experience replay for agents; skill library; procedural memory; agent workflow memory; tool-use optimization; multimodal web agents; visual grounding; long-horizon planning; trajectory synthesis; tool overuse mitigation.
- Target venues: NeurIPS, ICML, ICLR, ACL.
- Time window: 2025-03-15 to 2026-03-15.
- Max shortlist size: 20.

## 2) Source Quality Notes
- Primary sources used:
  - ICLR/NeurIPS 论文优先使用 OpenReview 会场页面。
  - ACL 2025 论文优先使用 ACL Anthology 页面。
  - ICML 2025 论文优先使用 PMLR 页面。
  - 2025-2026 预印本优先使用 arXiv 摘要页/PDF 页。
  - 若论文或作者提供官方项目页和代码仓库，也一并纳入。
- Known evidence gaps:
  - 若干高相关论文仍是预印本，实验结论尚未经过同行评审。
  - ACL Anthology 往往只给出月份和年份，不总是给出精确发布日期。
  - AGENTFLOW 的项目页年份信息存在不一致（页面文案写 ICLR 2025，但标题/检索元数据指向 ICLR 2026）；本报告按 ICLR 2026 已接收处理，置信度为中等。
  - 部分论文提到代码或 software，但主会场页面未直接暴露稳定仓库链接。

## 3) Seed-to-Literature Mapping
- Seed paper: XSKILL: Continual Learning from Experience and Skills in Multimodal Agents (`arXiv:2603.12056`, 发布于 2026-03-12；预印本)。
- 从 seed 提取的问题定义:
  - 在开放式工具使用场景中，让多模态智能体在不微调参数的前提下持续改进。
  - 通过存储可复用的外部知识，缓解工具使用低效和编排僵化。
- 从 seed 提取的方法族:
  - 双流外部记忆：动作级 experience 与任务级 skill。
  - 基于视觉上下文的检索、改写与提示注入。
  - 通过 rollout 累积经验，而不是更新模型参数。
- 从 seed 提取的搜索短语:
  - multimodal agent continual learning
  - experience memory for agents
  - skill library for agents
  - procedural memory llm agents
  - workflow memory agents
  - multimodal tool use optimization
  - visual grounding agent memory
  - multimodal web agents trajectory synthesis
  - tool overuse mitigation agents
  - long-horizon planning agents
  - reusable skills agents
  - non-parametric memory agents
- Likely adjacent subtopics:
  - multimodal web agents
  - tool-use data synthesis
  - planner-executor agent systems
  - automatic tool discovery
- Mapping note:
  - 入选论文大致分成三类：直接的外部记忆论文（XSKILL, ProcMEM, MemSkill, Agent Workflow Memory, MemTool, EventMemAgent），不显式做持续记忆但直接改善多模态/工具使用行为的论文（SPORT, SMART, Explorer），以及可作为未来 XSKILL 式循环前端或后端能力的相邻论文（Magnet, Plan-and-Act, AGENTFLOW）。

## 4) Shortlist (Top 12)

| Rank | Paper | Venue/Year | Why It Matters Now | Key Result | Reproducibility Signal | Links |
|------|-------|------------|--------------------|------------|------------------------|-------|
| 1 | XSKILL: Continual Learning from Experience and Skills in Multimodal Agents | arXiv preprint, 2026-03-12 | 与 seed 问题最贴近：多模态、免训练更新、双记忆、视觉 grounding。 | 报告称相对 tool-only baseline 的 Average@4 提升 2.58 到 6.71，在困难设定上相对最强基线最高提升 11.13。 | 有项目页与 GitHub。 | paper: https://arxiv.org/abs/2603.12056 ; code: https://github.com/XSkill-Agent/XSkill |
| 2 | ProcMEM: Learning Reusable Procedural Memory from Experience via Non-Parametric PPO for LLM Agents | arXiv preprint, 2026-02-02 | 最近最强的“可复用过程记忆”方向论文之一。 | 通过从交互历史中蒸馏过程记忆来改进智能体规划与执行。 | 在本次使用的主来源中未找到官方代码。 | paper: https://arxiv.org/abs/2602.02433 |
| 3 | Agent Workflow Memory | ICML 2025, PMLR volume published 2025-10-06 | 最适合作为 XSKILL 中 workflow/skill 层的同行评审参照。 | 证明 workflow memory 能提升长程任务完成表现。 | PMLR 页面列出了 software。 | paper: https://proceedings.mlr.press/v267/wang25di.html |
| 4 | AGENTFLOW: In-the-Flow Agentic System Optimization for Effective Planning and Tool Use | ICLR 2026 accepted status, arXiv 2025-10 | 在规划与工具使用优化上证据强，适合作为 XSKILL 记忆层之上的执行层。 | 报告在 planning 和 tool use 上都有广泛收益。 | 有官方项目页和 GitHub。 | paper: https://arxiv.org/abs/2510.05592 ; code: https://github.com/lupantech/AgentFlow |
| 5 | MemSkill: Learning and Evolving Memory Skills for Self-Evolving Agents | arXiv preprint, 2026-02-02 | 与 seed 的“技能作为外部知识”轴非常接近。 | 通过可演化的 memory skills 推动智能体持续改进。 | 有官方项目页。 | paper: https://arxiv.org/abs/2602.03232 ; code/project: https://yueyang130.github.io/memskill/ |
| 6 | Iterative Tool Usage Exploration for Multimodal Agents via Step-wise Preference Tuning | NeurIPS 2025 poster, published 2025-09-18 | 直接相关的多模态工具使用论文；若下一步先强化执行而非记忆，这篇价值很高。 | 通过迭代探索和 step-wise preference tuning 改进多模态工具使用。 | 有项目页；主来源里仓库链接不够稳定。 | paper: https://arxiv.org/abs/2504.21561 ; project: https://sport-agents.github.io/ |
| 7 | Explorer: Scaling Exploration-driven Web Trajectory Synthesis for Multimodal Web Agents | ACL 2025 Findings, July 2025 | 最强的大规模多模态 web trajectory 数据引擎之一。 | 构建了 94K 成功多模态网页轨迹，并在多个 web-agent benchmark 上取得强结果。 | 论文与 arXiv 公开；本次使用的主来源未清晰暴露代码链接。 | paper: https://aclanthology.org/2025.findings-acl.326/ ; arXiv: https://arxiv.org/abs/2502.11357 |
| 8 | EventMemAgent: Hierarchical Event-Centric Memory for Online Video Understanding with Adaptive Tool Use | arXiv preprint, 2026-02-17 | 视频场景下高度相关的多模态记忆论文，可视为 XSKILL 向时序场景延展。 | 引入层次化事件记忆与自适应工具使用。 | 有官方项目页和 GitHub。 | paper: https://arxiv.org/abs/2602.11878 ; code: https://github.com/lingcco/EventMemAgent |
| 9 | SMART: Self-Aware Agent for Tool Overuse Mitigation | ACL 2025 Findings, July 2025 | 对“何时不该调用工具”给出明确方案，正好补 seed 的效率问题。 | 在其评测设定中，工具调用减少 24%，同时性能提升超过 37%。 | 开源代码与数据仓库已发布。 | paper: https://aclanthology.org/2025.findings-acl.239/ ; code: https://github.com/qiancheng0/Open-SMARTAgent |
| 10 | Memtool: Optimizing Short-Term Memory Management for Dynamic Tool Calling in LLM Agent Multi-Turn Conversations | arXiv preprint, 2025-07-29 | 偏工程落地的短时记忆论文，对动态 tool-calling 很有参考价值。 | 针对多轮工具调用提出短期记忆管理方案。 | 在本次使用的主来源中未找到官方代码。 | paper: https://arxiv.org/abs/2507.21870 |
| 11 | Plan-and-Act: Improving Planning of Agents for Long-Horizon Tasks | ICML 2025, PMLR volume published 2025-10-06 | 相邻但重要：对长程任务的 planner-executor 分解很强。 | 在 WebArena-Lite 上达到 57.58%，在 WebVoyager 上达到 81.36%。 | PMLR 页面列出了 OpenReview/software。 | paper: https://proceedings.mlr.press/v267/erdogan25a.html |
| 12 | Magnet: Multi-turn Tool-use Data Synthesis and Distillation via Graph Translation | ACL 2025 Long Papers, July 2025 | 相邻的数据生成论文，适合为外部记忆智能体提供更强 rollout 数据。 | Magnet-14B-mDPO 在 BFCL-v3 上 68.01，在 ToolQuery 上 73.30，并超过文中引用的 Gemini-1.5-pro-002。 | 论文公开；本次使用的会场主页面未确认代码链接。 | paper: https://aclanthology.org/2025.acl-long.1566/ ; arXiv: https://arxiv.org/abs/2503.07826 |

## 5) Paper Cards

### [Rank 1] XSKILL: Continual Learning from Experience and Skills in Multimodal Agents
- Relation to seed: same problem.
- Authors: Guanyu Jiang, Zhaochen Su, Xiaoye Qu, Yi R. (May) Fung.
- Venue/Track/Year: arXiv 预印本，发布于 2026-03-12；尚未同行评审。
- Contribution (1 sentence): 提出一个视觉 grounding 的双流外部记忆系统，使多模态智能体无需参数更新即可从历史轨迹中持续改进。
- Method sketch (2-4 bullets):
  - 从多路径 rollout 中蒸馏动作级 experiences 和任务级 skills。
  - 在知识抽取与检索中显式利用视觉观察，而不是只依赖文本轨迹。
  - 在提示注入前，先根据当前视觉上下文改写检索到的知识。
  - 将使用历史再反馈回积累阶段，形成持续循环。
- Best evidence:
  - 在四个 backbone 上相对 tool-only baseline 的 Average@4 提升 2.58 到 6.71。
  - 在更困难设定上，相对最强 baseline 最高提升 11.13。
- Limitations:
  - 目前更像单轮 accumulation-then-test，而不是完整在线持续学习证明。
  - 作为预印本，benchmark 与 prompt 细节仍需外部复现。
- Why selected:
  - 这是本次调研的锚点论文。
  - 它定义了本报告大部分论文所在的方法族。
- Confidence: 对 seed 抽取为高；对实验稳健性的置信度为中高，因为论文仍是预印本。
- URLs:
  - paper: https://arxiv.org/abs/2603.12056
  - code: https://github.com/XSkill-Agent/XSkill

### [Rank 2] ProcMEM: Learning Reusable Procedural Memory from Experience via Non-Parametric PPO for LLM Agents
- Relation to seed: same method family.
- Authors: 见 arXiv 页面。
- Venue/Track/Year: arXiv 预印本，发布于 2026-02-02；尚未同行评审。
- Contribution (1 sentence): 提出通过非参数 PPO 风格框架从经验中学习可复用过程记忆。
- Method sketch (2-4 bullets):
  - 从成功与失败经验中抽取可复用 procedure。
  - 将 procedure 作为外部记忆，而不是修改模型权重。
  - 在推理时重用这些过程记忆来改善规划和执行。
- Best evidence:
  - 论文将 procedural memory 设为改善智能体行为的核心机制。
  - 相比一般记忆片段，它更强调“可复用过程”，新意较强。
- Limitations:
  - 本次使用的主来源未给出官方代码发布。
  - 目前只有预印本证据。
- Why selected:
  - 它是对 XSKILL 中“skills”部分最直接的近期补充。
  - 它提供了比临时 prompt memory 更强的过程抽象。
- Confidence: 中等。
- URLs:
  - paper: https://arxiv.org/abs/2602.02433
  - code: not surfaced on primary sources used

### [Rank 3] Agent Workflow Memory
- Relation to seed: same method family.
- Authors: 见 PMLR 页面。
- Venue/Track/Year: ICML 2025 主会；会议时间 2025-07-13 至 2025-07-19；PMLR 卷发布时间 2025-10-06；同行评审。
- Contribution (1 sentence): 将 workflow memory 作为长程智能体的显式可复用结构。
- Method sketch (2-4 bullets):
  - 存储高层 workflow，而不仅是原始轨迹或摘要。
  - 为新任务检索 workflow 片段。
  - 利用记忆稳定多步执行。
- Best evidence:
  - 属于同行评审的 ICML 论文。
  - 与 XSKILL 的任务级 skill document 在方法上高度相似。
- Limitations:
  - 没有 XSKILL 那么强调多模态。
  - 相比基于图像的改写阶段，它对噪声视觉状态的适配可能更弱。
- Why selected:
  - 它是支持“外部 workflow/skill memory”设计的最佳同行评审证据之一。
  - 很适合作为后续实验中的 baseline 或 ablation 参照。
- Confidence: 高。
- URLs:
  - paper: https://proceedings.mlr.press/v267/wang25di.html
  - code: software link available from the PMLR paper page

### [Rank 4] AGENTFLOW: In-the-Flow Agentic System Optimization for Effective Planning and Tool Use
- Relation to seed: same method family.
- Authors: 见 arXiv/项目页。
- Venue/Track/Year: 按项目页/检索元数据应为 ICLR 2026 已接收；arXiv 预印本时间为 2025-10；已接收但项目页年份标注不完全一致。
- Contribution (1 sentence): 不是单点改 prompt，而是从系统流的角度联合优化智能体的 planning 与 tool use。
- Method sketch (2-4 bullets):
  - 联合优化规划与工具使用决策。
  - 关注 agentic system optimization，而非单纯记忆检索。
  - 可与 XSKILL 式外部记忆形成互补。
- Best evidence:
  - 在 planning 与 tool-use effectiveness 上证据较强。
  - 官方项目页与代码增强了可复现性。
- Limitations:
  - 它不是以持续记忆为核心的论文。
  - 精确的 ICLR 年份在公开材料间存在小幅不一致。
- Why selected:
  - 很可能是 XSKILL 的高价值组合件：XSKILL 负责记忆，AgentFlow 负责执行控制。
  - 若目标更偏部署而非纯记忆设计，这篇值得优先读。
- Confidence: 中等。
- URLs:
  - paper: https://arxiv.org/abs/2510.05592
  - code: https://github.com/lupantech/AgentFlow

### [Rank 5] MemSkill: Learning and Evolving Memory Skills for Self-Evolving Agents
- Relation to seed: same method family.
- Authors: 见 arXiv/项目页。
- Venue/Track/Year: arXiv 预印本，发布于 2026-02-02；尚未同行评审。
- Contribution (1 sentence): 将可复用 memory skills 视作一等对象，并让它们随经验持续演化。
- Method sketch (2-4 bullets):
  - 构建显式的 memory skills，而不是一次性记忆片段。
  - 随新经验到来持续更新这些 skills。
  - 将智能体改进表述为通过外部 skill memory 实现的自演化。
- Best evidence:
  - 与 XSKILL 的“skills”侧非常接近。
  - 官方项目页便于快速理解方法。
- Limitations:
  - 仍是预印本。
  - 实证成熟度看起来不如最强同行评审论文。
- Why selected:
  - 如果你想继续推进 seed 的核心思路，这篇是最值得与 XSKILL 对读的论文之一。
  - 它有助于比较 skill 应该是 document-like、procedural，还是可演化对象。
- Confidence: 中等。
- URLs:
  - paper: https://arxiv.org/abs/2602.03232
  - code: https://yueyang130.github.io/memskill/

### [Rank 6] Iterative Tool Usage Exploration for Multimodal Agents via Step-wise Preference Tuning
- Relation to seed: same problem.
- Authors: 见论文/项目页。
- Venue/Track/Year: NeurIPS 2025 poster，发布于 2025-09-18；同行评审。
- Contribution (1 sentence): 通过迭代式工具使用探索与 step-wise preference tuning 改进多模态智能体执行。
- Method sketch (2-4 bullets):
  - 主动探索工具使用轨迹，而非只用静态监督。
  - 在步骤级别施加偏好信号。
  - 直接面向多模态智能体。
- Best evidence:
  - 属于与 seed 同一多模态工具使用场景的 NeurIPS 同行评审论文。
  - 是连接“训练式改进”和“外部记忆式改进”的好桥梁。
- Limitations:
  - 它主要通过 tuning 改进执行策略，而不是通过持续性的非参数记忆。
  - 项目页公开了方法，但代码可见性不如最开放的几篇论文。
- Why selected:
  - 它是回答“下一步应投向更强 policy tuning，还是更强 memory”的关键对照。
  - 如果你当前痛点仍是多模态工具选择，这篇很直接。
- Confidence: 高。
- URLs:
  - paper: https://arxiv.org/abs/2504.21561
  - code/project: https://sport-agents.github.io/

### [Rank 7] Explorer: Scaling Exploration-driven Web Trajectory Synthesis for Multimodal Web Agents
- Relation to seed: same problem.
- Authors: 见 ACL Anthology 页面。
- Venue/Track/Year: ACL 2025 Findings；2025 年 7 月；同行评审。
- Contribution (1 sentence): 提出可扩展方案来合成大规模多模态网页轨迹，并用其训练更强的 web agent。
- Method sketch (2-4 bullets):
  - 通过网页探索与 refinement 生成多样任务意图。
  - 产出包含截图与动作的大规模多模态轨迹语料。
  - 用该语料训练多模态 web agent。
- Best evidence:
  - 构建了 94K 成功多模态网页轨迹、49K URL、720K 截图。
  - 在 Mind2Web-Live、Multimodal-Mind2Web 和 MiniWob++ 上有强表现。
- Limitations:
  - 它主要是数据扩展论文，不是持续记忆论文。
  - 以 web-agent 为中心，向非 web 多模态任务的迁移不一定顺滑。
- Why selected:
  - XSKILL 类系统需要大量 rollout，Explorer 是近期最值得看的数据来源之一。
  - 若你需要先扩数据再改记忆设计，这篇的实践价值很高。
- Confidence: 高。
- URLs:
  - paper: https://aclanthology.org/2025.findings-acl.326/
  - code: not surfaced on the primary pages used

### [Rank 8] EventMemAgent: Hierarchical Event-Centric Memory for Online Video Understanding with Adaptive Tool Use
- Relation to seed: same method family.
- Authors: 见 arXiv/项目页。
- Venue/Track/Year: arXiv 预印本，发布于 2026-02-17；尚未同行评审。
- Contribution (1 sentence): 将智能体记忆扩展到流式视频场景，通过层次化事件记忆和自适应工具使用进行在线理解。
- Method sketch (2-4 bullets):
  - 维护事件级而非单帧级的层次记忆。
  - 根据不断演化的视频上下文自适应调用工具。
  - 面向在线多模态推理。
- Best evidence:
  - 从图像 grounding 记忆自然扩展到时序 grounding 记忆，概念价值高。
  - 官方 GitHub 仓库增强了可检查性。
- Limitations:
  - 目前仍是预印本。
  - 任务场景比 seed 更专门。
- Why selected:
  - 如果下一步涉及视频或持续观测场景，这篇值得优先看。
  - 它展示了当感知状态持续变化时，XSKILL 式记忆需要如何调整。
- Confidence: 中等。
- URLs:
  - paper: https://arxiv.org/abs/2602.11878
  - code: https://github.com/lingcco/EventMemAgent

### [Rank 9] SMART: Self-Aware Agent for Tool Overuse Mitigation
- Relation to seed: same method family.
- Authors: 见 ACL Anthology 页面。
- Venue/Track/Year: ACL 2025 Findings；2025 年 7 月；同行评审。
- Contribution (1 sentence): 训练智能体判断何时不需要工具，在降低无效工具调用的同时保持或提升准确率。
- Method sketch (2-4 bullets):
  - 建立关于“工具是否必要”的 self-awareness。
  - 用带 rationale 的监督数据学习何时使用工具。
  - 在参数知识与外部工具之间做更优平衡。
- Best evidence:
  - 报告工具调用减少 24%，性能提升超过 37%。
  - 代码与数据公开，复现信号强。
- Limitations:
  - 重点不在记忆积累，而在工具决策校准。
  - 更偏文本/工具推理，而不是 XSKILL 那种完整视觉 grounding 持续循环。
- Why selected:
  - 如果当前瓶颈是工具调用成本或延迟，这篇非常实用。
  - 它能补足 XSKILL 的效率故事，而不必先重写记忆系统。
- Confidence: 高。
- URLs:
  - paper: https://aclanthology.org/2025.findings-acl.239/
  - code: https://github.com/qiancheng0/Open-SMARTAgent

### [Rank 10] Memtool: Optimizing Short-Term Memory Management for Dynamic Tool Calling in LLM Agent Multi-Turn Conversations
- Relation to seed: same method family.
- Authors: 见 arXiv 页面。
- Venue/Track/Year: arXiv 预印本，发布于 2025-07-29；尚未同行评审。
- Contribution (1 sentence): 面向动态 tool-calling 的多轮智能体，重点优化短期记忆管理。
- Method sketch (2-4 bullets):
  - 优化保留哪些近期交互状态。
  - 关注动态工具调用，而不是一般聊天记忆。
  - 将 memory 视作执行关键资源。
- Best evidence:
  - 对工具调用型智能体的工程实现很有参考价值。
  - 与 seed 中“无需改权重、但提升工具编排”的目标一致。
- Limitations:
  - 本次使用的主来源未找到官方代码。
  - 其短期记忆范围比 XSKILL 的跨任务可复用知识更窄。
- Why selected:
  - 如果你在完整双流记忆之前想先做一个更简单的工程落地步骤，这篇很适合。
  - 它可以作为 XSKILL 之上的短时执行缓存。
- Confidence: 中等。
- URLs:
  - paper: https://arxiv.org/abs/2507.21870
  - code: not surfaced on primary sources used

### [Rank 11] Plan-and-Act: Improving Planning of Agents for Long-Horizon Tasks
- Relation to seed: adjacent.
- Why adjacent: 之所以纳入，是因为显式规划质量会显著影响外部记忆在推理时是否真正有用。
- Authors: Lutfi Eren Erdogan, Nicholas Lee, Sehoon Kim, Suhong Moon, Hiroki Furuta, Gopala Anumanchipalli, Kurt Keutzer, Amir Gholami.
- Venue/Track/Year: ICML 2025 主会；会议时间 2025-07-13 至 2025-07-19；PMLR 卷发布时间 2025-10-06；同行评审。
- Contribution (1 sentence): 通过 planner-executor 分解和合成规划数据来提升长程智能体任务表现。
- Method sketch (2-4 bullets):
  - 使用 planner-executor 结构分工。
  - 为训练 planner 生成合成 plan 标注。
  - 在 web navigation 长程任务上评估。
- Best evidence:
  - WebArena-Lite 成功率 57.58%。
  - WebVoyager 成功率 81.36%。
- Limitations:
  - 不是多模态记忆中心论文。
  - 主要依赖学习式规划，而不是非参数持续记忆。
- Why selected:
  - 适合作为相邻参照，帮助判断 XSKILL 的收益里有多少其实来自更好的规划结构。
  - 对偏部署的实验很有价值。
- Confidence: 高。
- URLs:
  - paper: https://proceedings.mlr.press/v267/erdogan25a.html
  - code: software/OpenReview links available from the PMLR page

### [Rank 12] Magnet: Multi-turn Tool-use Data Synthesis and Distillation via Graph Translation
- Relation to seed: adjacent.
- Why adjacent: 纳入它是因为它是近期最强的多轮工具使用轨迹生成论文之一，而外部记忆智能体本质上依赖这类轨迹。
- Authors: Fan Yin, Zifeng Wang, I-Hung Hsu, Jun Yan, Ke Jiang, Yanfei Chen, Jindong Gu, Long Le, Kai-Wei Chang, Chen-Yu Lee, Hamid Palangi, Tomas Pfister.
- Venue/Track/Year: ACL 2025 Long Papers；2025 年 7 月；同行评审。
- Contribution (1 sentence): 通过图翻译合成高质量多轮工具使用轨迹，并蒸馏成更强 function-calling 模型。
- Method sketch (2-4 bullets):
  - 将函数交互表示成图。
  - 自动构建正负工具使用轨迹。
  - 结合监督微调和偏好优化。
- Best evidence:
  - Magnet-14B-mDPO 在文中报告的设定上，BFCL-v3 为 68.01，ToolQuery 为 73.30。
  - 超过文中引用的 teacher model Gemini-1.5-pro-002。
- Limitations:
  - 它主要是数据生成/训练论文，不是持续记忆论文。
  - 多轮 function calling 的问题设置比 seed 的多模态 grounding 焦点更宽。
- Why selected:
  - 适合为 XSKILL 类系统构建更好的 rollout 语料。
  - 对改进教师数据管线很有帮助。
- Confidence: 高。
- URLs:
  - paper: https://aclanthology.org/2025.acl-long.1566/
  - code: not confirmed from the primary venue page used

## 6) Rating Summary
- Chosen profile and weights:
  - `seed_focus`
  - Relevance-to-seed 0.45
  - Novelty 0.15
  - Evidence strength 0.15
  - Reproducibility 0.10
  - Practical impact 0.15

| Rank | Paper | Relation | Relevance | Novelty | Evidence | Reproducibility | Impact | Final weighted score |
|------|-------|----------|-----------|---------|----------|-----------------|--------|----------------------|
| 1 | XSKILL | same problem | 10 | 9 | 8 | 9 | 9 | 9.25 |
| 2 | ProcMEM | same method family | 9 | 9 | 7 | 6 | 8 | 8.25 |
| 3 | Agent Workflow Memory | same method family | 8 | 8 | 8 | 9 | 8 | 8.10 |
| 4 | AGENTFLOW | same method family | 7 | 9 | 9 | 8 | 9 | 8.00 |
| 5 | MemSkill | same method family | 8 | 8 | 7 | 8 | 8 | 7.85 |
| 6 | SPORT | same problem | 8 | 8 | 7 | 7 | 8 | 7.75 |
| 7 | Explorer | same problem | 7 | 8 | 8 | 9 | 8 | 7.65 |
| 8 | SMART | same method family | 7 | 7 | 8 | 8 | 8 | 7.40 |
| 9 | EventMemAgent | same method family | 8 | 8 | 6 | 6 | 7 | 7.35 |
| 10 | Memtool | same method family | 8 | 7 | 6 | 5 | 8 | 7.25 |
| 11 | Plan-and-Act | adjacent | 6 | 8 | 8 | 7 | 9 | 7.15 |
| 12 | Magnet | adjacent | 6 | 8 | 8 | 7 | 8 | 7.00 |

- Top-3 papers by each single dimension:
  - Relevance: XSKILL; ProcMEM; Agent Workflow Memory.
  - Novelty: XSKILL; ProcMEM; AGENTFLOW.
  - Evidence strength: AGENTFLOW; Agent Workflow Memory; Explorer.
  - Reproducibility: XSKILL; Agent Workflow Memory; Explorer.
  - Practical impact: XSKILL; AGENTFLOW; Plan-and-Act.

## 7) Not Selected but Notable
- Agent Reviewers: Domain-specific Multimodal Agents with Shared Memory for Paper Review (ICML 2025): 共享记忆的多模态系统很有意思，但任务过于局限在论文审稿场景，不适合核心 shortlist。
- MCP-Zero: Automatic Discovery and Invocation of Any Function for AI Agents (arXiv 2025): 对工具发现与调用基础设施有价值，但不够聚焦于持续多模态记忆。
- Multi-modal Agent Tuning: Building a VLM-Driven Agent for Efficient Tool Usage (ICLR 2025 Spotlight): 与主题高度相关，但 ICLR 2025 的发布时间早于 2025-03-15，因此落在窗口外。
- WAVE: Building Multimodal Web Agents via Iterative Real-World Exploration (2026 under-review/open work): 真实网页探索方向有潜力，但同行评审状态更弱，且主来源元数据不够稳定，因此未进入主榜单。

## 8) Trends and Openings
- Trend 1: 外部记忆正从简单的检索片段，转向可复用的 procedure、workflow 与 skill object。
- Trend 2: 多模态工具使用能力的提升，越来越依赖更强的数据引擎，而不只是更强的记忆机制。
- Contradictions/disagreements:
  - 一部分工作强调通过训练和 preference optimization 改善策略，另一部分工作强调免训练的外部记忆；当前领域尚未形成关于跨任务变化下哪种方案更高效的共识。
  - 工具使用效率既可能来自更好的记忆召回（XSKILL, Memtool），也可能来自更好的 abstention/calibration（SMART）；两者交互仍缺少系统验证。
- Potential research openings:
  - 将 XSKILL 式双记忆与 AGENTFLOW 或 Plan-and-Act 式执行控制结合。
  - 在视频/web 场景中，用时序 grounding 的事件记忆替换纯文本 experience vector。
  - 做真正多批次任务的在线持续循环评测，而不只是一次 accumulation pass。
  - 构建一个能分别衡量 retrieval quality、adaptation quality 和 execution quality 的多模态记忆 benchmark。

## 9) Coverage Gaps and Blind Spots
- Missing sub-areas:
  - 直接面向“视觉 grounding 的多模态持续记忆”的强同行评审论文仍然很少，最直接的几篇还主要是预印本。
  - 在该时间窗口内，工具增强的视频智能体和具身多模态智能体仍然偏少。
- Venue bias risk:
  - 该 shortlist 相对偏向 ICML/ACL，因为这些 venue 在时间窗口内给出了更稳定、更清晰的主来源元数据。
- Time-window risk:
  - 严格限制在 2025-03-15 到 2026-03-15，会把一个很近的相关工作 T3-Agent 排除在外。

## 10) Action Plan (2 Weeks)
- Day 1-3: 按顺序阅读 #1、#2、#3、#5，先锁定记忆设计空间：双记忆、过程记忆、工作流记忆、可演化技能。
- Day 4-5: 阅读 #6、#9、#10，定位执行层痛点，尤其是工具选择、工具过用和短时记忆管理。
- Day 6-7: 阅读 #4 和 #11，比较“改 planning/control”与“改 memory”哪条路收益更大。
- Day 8-9: 阅读 #7 和 #12，判断当前瓶颈是否其实在数据生成，而不是记忆设计。
- Day 10-11: 若视频/流式任务重要，则阅读 #8；否则把这两天用于把 XSKILL 映射到你自己的 agent stack。
- Day 12-14: 产出一个短实验备忘录，至少包含三条实验线：
  - 只做 XSKILL 式双记忆。
  - 双记忆加更强执行控制器。
  - 在重做记忆前，先增强轨迹/数据生成。
