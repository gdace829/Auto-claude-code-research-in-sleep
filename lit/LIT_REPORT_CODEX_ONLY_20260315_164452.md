# Literature Scout Report (Codex-Only)

## 1) Scope
- Topic: Continual improvement for multimodal agents via externalized experience, skill, and workflow memory for tool use.
- Keywords: multimodal agents; continual learning without finetuning; experience replay for agents; skill library; procedural memory; agent workflow memory; tool-use optimization; multimodal web agents; visual grounding; long-horizon planning; trajectory synthesis; tool overuse mitigation.
- Target venues: NeurIPS, ICML, ICLR, ACL.
- Time window: 2025-03-15 to 2026-03-15.
- Max shortlist size: 20.

## 2) Source Quality Notes
- Primary sources used:
  - OpenReview venue pages for ICLR/NeurIPS papers when available.
  - ACL Anthology pages for ACL 2025 main/findings papers.
  - PMLR pages for ICML 2025 papers.
  - arXiv abstract/PDF pages for 2025-2026 preprints.
  - Official project pages and code repositories when linked by the paper or authors.
- Known evidence gaps:
  - Several high-relevance papers are still preprints, so empirical claims are not yet peer-reviewed.
  - ACL Anthology pages expose month/year but not always an exact publication day.
  - AGENTFLOW has a project-page year inconsistency (page text says ICLR 2025 while title/search metadata indicate ICLR 2026); I treat it as ICLR 2026 accepted status with medium confidence.
  - Some papers mention code or software, but the primary venue page does not expose a stable repo URL directly.

## 3) Seed-to-Literature Mapping
- Seed paper: XSKILL: Continual Learning from Experience and Skills in Multimodal Agents (`arXiv:2603.12056`, posted 2026-03-12; preprint).
- Problem framing extracted from seed:
  - Training-free continual improvement for multimodal agents in open-ended tool-use settings.
  - Fix inefficient tool use and inflexible orchestration by storing reusable external knowledge.
- Method family extracted from seed:
  - Dual-stream external memory: action-level experiences plus task-level skills.
  - Retrieval, adaptation, and prompt injection grounded in visual context.
  - Continual accumulation from rollouts instead of parameter updates.
- Seed-derived search phrases:
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
  - The shortlist falls into three clusters: direct external-memory papers (XSKILL, ProcMEM, MemSkill, Agent Workflow Memory, MemTool, EventMemAgent), multimodal/tool-use behavior papers that improve execution quality without explicit continual memory (SPORT, SMART, Explorer), and adjacent planning/data engines that can feed a future XSKILL-like loop (Magnet, Plan-and-Act, AGENTFLOW).

## 4) Shortlist (Top 12)

| Rank | Paper | Venue/Year | Why It Matters Now | Key Result | Reproducibility Signal | Links |
|------|-------|------------|--------------------|------------|------------------------|-------|
| 1 | XSKILL: Continual Learning from Experience and Skills in Multimodal Agents | arXiv preprint, 2026-03-12 | Closest match to the seed problem: multimodal, training-free, dual-memory, visually grounded. | Reports Average@4 gains of 2.58 to 6.71 over tool-only baselines and up to 11.13 over the strongest baseline on hard settings. | Project page and GitHub repo available. | paper: https://arxiv.org/abs/2603.12056 ; code: https://github.com/XSkill-Agent/XSkill |
| 2 | ProcMEM: Learning Reusable Procedural Memory from Experience via Non-Parametric PPO for LLM Agents | arXiv preprint, 2026-02-02 | Strongest recent paper on reusable procedural memory learned from interaction histories. | Improves agent planning/execution through non-parametric procedural memory distilled from past trajectories. | No official repo surfaced from primary sources. | paper: https://arxiv.org/abs/2602.02433 |
| 3 | Agent Workflow Memory | ICML 2025, PMLR volume published 2025-10-06 | Best peer-reviewed analogue to XSKILL's reusable workflow/skill layer. | Shows workflow memory improves long-horizon task completion versus stateless prompting. | PMLR lists software; official code link available from the paper page. | paper: https://proceedings.mlr.press/v267/wang25di.html |
| 4 | AGENTFLOW: In-the-Flow Agentic System Optimization for Effective Planning and Tool Use | ICLR 2026 accepted status, arXiv 2025-10 | Strong planning/tool-use optimizer with high empirical strength; useful for the execution layer under an XSKILL-style memory loop. | Reports broad gains from system-level optimization of planning and tool use. | Official project page and GitHub are available. | paper: https://arxiv.org/abs/2510.05592 ; code: https://github.com/lupantech/AgentFlow |
| 5 | MemSkill: Learning and Evolving Memory Skills for Self-Evolving Agents | arXiv preprint, 2026-02-02 | Very close to the seed's "skills as external knowledge" axis, but with a self-evolving framing. | Uses explicit memory skills that evolve over time instead of static prompts. | Official project page is available. | paper: https://arxiv.org/abs/2602.03232 ; code/project: https://yueyang130.github.io/memskill/ |
| 6 | Iterative Tool Usage Exploration for Multimodal Agents via Step-wise Preference Tuning | NeurIPS 2025 poster, published 2025-09-18 | Directly relevant multimodal tool-use paper; useful if your next step is stronger execution before adding memory. | Improves multimodal agent tool use by iterative exploration plus step-wise preference tuning. | Project page available; repo link not consistently exposed on primary sources. | paper: https://arxiv.org/abs/2504.21561 ; project: https://sport-agents.github.io/ |
| 7 | Explorer: Scaling Exploration-driven Web Trajectory Synthesis for Multimodal Web Agents | ACL 2025 Findings, July 2025 | Best large-scale data engine for multimodal web agents; useful to create the rollouts that XSKILL-like systems need. | Builds 94K successful multimodal web trajectories and shows strong gains on Mind2Web-Live, Multimodal-Mind2Web, and MiniWob++. | Paper and arXiv are public; code link not clearly exposed on primary pages used here. | paper: https://aclanthology.org/2025.findings-acl.326/ ; arXiv: https://arxiv.org/abs/2502.11357 |
| 8 | EventMemAgent: Hierarchical Event-Centric Memory for Online Video Understanding with Adaptive Tool Use | arXiv preprint, 2026-02-17 | Highly relevant multimodal memory paper in the video setting; useful for extending XSKILL beyond static-image tasks. | Introduces hierarchical event-centric memory plus adaptive tool use for online video understanding. | Official project page and GitHub are available. | paper: https://arxiv.org/abs/2602.11878 ; code: https://github.com/lingcco/EventMemAgent |
| 9 | SMART: Self-Aware Agent for Tool Overuse Mitigation | ACL 2025 Findings, July 2025 | Good complementary paper on when not to call tools, which directly addresses one of XSKILL's efficiency claims. | Reduces tool use by 24% while improving performance by over 37% on its evaluation suite. | Official open-source code/data repo is available. | paper: https://aclanthology.org/2025.findings-acl.239/ ; code: https://github.com/qiancheng0/Open-SMARTAgent |
| 10 | Memtool: Optimizing Short-Term Memory Management for Dynamic Tool Calling in LLM Agent Multi-Turn Conversations | arXiv preprint, 2025-07-29 | Useful implementation-focused memory paper for dynamic tool-calling contexts. | Proposes short-term memory management targeted at multi-turn tool-calling agents. | No official repo surfaced from primary sources used here. | paper: https://arxiv.org/abs/2507.21870 |
| 11 | Plan-and-Act: Improving Planning of Agents for Long-Horizon Tasks | ICML 2025, PMLR volume published 2025-10-06 | Adjacent but valuable: strong planner-executor decomposition for long-horizon agents. | Reaches 57.58% on WebArena-Lite and 81.36% on WebVoyager. | PMLR lists related OpenReview/software links. | paper: https://proceedings.mlr.press/v267/erdogan25a.html |
| 12 | Magnet: Multi-turn Tool-use Data Synthesis and Distillation via Graph Translation | ACL 2025 Long Papers, July 2025 | Adjacent data-generation paper for building better multi-turn tool-use policies. | Magnet-14B-mDPO reports 68.01 on BFCL-v3 and 73.30 on ToolQuery, beating Gemini-1.5-pro-002 on the cited setup. | Paper public; code link not confirmed from the venue page used here. | paper: https://aclanthology.org/2025.acl-long.1566/ ; arXiv: https://arxiv.org/abs/2503.07826 |

## 5) Paper Cards

### [Rank 1] XSKILL: Continual Learning from Experience and Skills in Multimodal Agents
- Relation to seed: same problem.
- Authors: Guanyu Jiang, Zhaochen Su, Xiaoye Qu, Yi R. (May) Fung.
- Venue/Track/Year: arXiv preprint, posted 2026-03-12; not peer-reviewed yet.
- Contribution (1 sentence): Introduces a dual-stream, visually grounded external memory system that lets multimodal agents continually improve from prior trajectories without parameter updates.
- Method sketch (2-4 bullets):
  - Distills action-level experiences and task-level skills from multi-path rollouts.
  - Grounds extraction and retrieval in visual observations rather than text alone.
  - Adapts retrieved knowledge to the current visual context before prompt injection.
  - Feeds usage history back into accumulation to support a continual loop.
- Best evidence:
  - Average@4 gains of 2.58 to 6.71 over tool-only baselines across four backbone models.
  - Up to 11.13-point gain over the strongest baseline on harder settings.
- Limitations:
  - Single-cycle accumulation/test evaluation is still weaker than a fully online continual-learning proof.
  - As a preprint, benchmark and prompt details still need outside replication.
- Why selected:
  - It is the exact anchor paper.
  - It defines the method family that most of the shortlist either extends or supports.
- Confidence: high for seed extraction; medium-high for empirical durability because the paper is still a preprint.
- URLs:
  - paper: https://arxiv.org/abs/2603.12056
  - code: https://github.com/XSkill-Agent/XSkill

### [Rank 2] ProcMEM: Learning Reusable Procedural Memory from Experience via Non-Parametric PPO for LLM Agents
- Relation to seed: same method family.
- Authors: See arXiv paper page.
- Venue/Track/Year: arXiv preprint, posted 2026-02-02; not peer-reviewed yet.
- Contribution (1 sentence): Proposes reusable procedural memory learned from experience using a non-parametric PPO-style framework for agents.
- Method sketch (2-4 bullets):
  - Extracts reusable procedures from successful and failed experience.
  - Stores those procedures externally instead of altering model weights.
  - Reuses memory at inference time to improve planning and execution.
- Best evidence:
  - The paper positions procedural memory as the central mechanism for better downstream agent behavior across tasks.
  - High novelty because it moves from generic memory snippets toward reusable procedures.
- Limitations:
  - Primary sources used here did not expose an official code release.
  - Evidence is preprint-only at this point.
- Why selected:
  - It is the cleanest recent complement to XSKILL's "skills" half.
  - It offers a potentially stronger procedural abstraction than ad hoc prompt memories.
- Confidence: medium.
- URLs:
  - paper: https://arxiv.org/abs/2602.02433
  - code: not surfaced on primary sources used

### [Rank 3] Agent Workflow Memory
- Relation to seed: same method family.
- Authors: See PMLR paper page.
- Venue/Track/Year: ICML 2025 main conference; conference held 2025-07-13 to 2025-07-19; proceedings volume published 2025-10-06; peer-reviewed.
- Contribution (1 sentence): Introduces workflow memory as an explicit reusable structure for long-horizon agents.
- Method sketch (2-4 bullets):
  - Stores higher-level workflows instead of only raw trajectories or summaries.
  - Retrieves workflow fragments for new tasks.
  - Uses memory to stabilize multi-step execution.
- Best evidence:
  - Peer-reviewed ICML paper with official PMLR publication.
  - Strong methodological overlap with XSKILL's task-level skill documents.
- Limitations:
  - Less explicitly multimodal than XSKILL.
  - The workflow abstraction may be less adaptive to noisy visual states than XSKILL's image-grounded rewrite stage.
- Why selected:
  - Best peer-reviewed support for the "external workflow/skill memory" design choice.
  - Strong candidate baseline or ablation reference for your next experiments.
- Confidence: high.
- URLs:
  - paper: https://proceedings.mlr.press/v267/wang25di.html
  - code: software link available from the PMLR paper page

### [Rank 4] AGENTFLOW: In-the-Flow Agentic System Optimization for Effective Planning and Tool Use
- Relation to seed: same method family.
- Authors: See arXiv/project page.
- Venue/Track/Year: accepted to ICLR 2026 per project/search metadata; arXiv preprint 2025-10; peer-review status accepted but project-page year labeling is inconsistent.
- Contribution (1 sentence): Optimizes agent planning and tool use as a system-level flow rather than as isolated prompt edits.
- Method sketch (2-4 bullets):
  - Refines planning and tool-use decisions jointly.
  - Focuses on agentic-system optimization rather than pure memory retrieval.
  - Provides an execution-focused layer that could pair well with XSKILL-like memory.
- Best evidence:
  - Strong empirical positioning for planning and tool-use effectiveness.
  - Official project page and code improve reproducibility.
- Limitations:
  - It is not primarily a continual-memory paper.
  - Source metadata for the exact ICLR year is slightly inconsistent across project materials.
- Why selected:
  - A likely high-value combination with XSKILL: memory for recall plus AgentFlow for execution control.
  - Strong evidence paper if your goal is deployment, not just memory design.
- Confidence: medium.
- URLs:
  - paper: https://arxiv.org/abs/2510.05592
  - code: https://github.com/lupantech/AgentFlow

### [Rank 5] MemSkill: Learning and Evolving Memory Skills for Self-Evolving Agents
- Relation to seed: same method family.
- Authors: See arXiv/project page.
- Venue/Track/Year: arXiv preprint, posted 2026-02-02; not peer-reviewed yet.
- Contribution (1 sentence): Treats reusable memory skills as first-class objects that agents can learn and evolve over time.
- Method sketch (2-4 bullets):
  - Builds explicit memory skills rather than one-off memory snippets.
  - Updates those skills as new experience arrives.
  - Frames agent improvement as self-evolution through externalized skill memory.
- Best evidence:
  - Very close conceptual match to the "skills" half of XSKILL.
  - Official project page makes the method easier to inspect.
- Limitations:
  - Preprint only.
  - Evidence appears earlier-stage than the strongest peer-reviewed papers.
- Why selected:
  - If you want to push the seed idea forward, this is one of the first papers to read side by side with XSKILL.
  - Useful for comparing whether "skill" should be document-like, procedural, or evolving.
- Confidence: medium.
- URLs:
  - paper: https://arxiv.org/abs/2602.03232
  - code: https://yueyang130.github.io/memskill/

### [Rank 6] Iterative Tool Usage Exploration for Multimodal Agents via Step-wise Preference Tuning
- Relation to seed: same problem.
- Authors: See paper/project page.
- Venue/Track/Year: NeurIPS 2025 poster, published 2025-09-18; peer-reviewed.
- Contribution (1 sentence): Improves multimodal tool use by iteratively collecting exploratory traces and then tuning with step-wise preferences.
- Method sketch (2-4 bullets):
  - Explores tool-usage trajectories rather than relying on static supervision.
  - Applies fine-grained preference signals at the step level.
  - Targets multimodal agents directly.
- Best evidence:
  - NeurIPS peer-reviewed paper in the same multimodal tool-use regime as the seed.
  - Good bridge between pure training approaches and external-memory approaches.
- Limitations:
  - It improves execution policy through tuning, not through continual non-parametric memory.
  - Project page exposes the framework, but code visibility is less explicit than for the strongest open-source papers.
- Why selected:
  - Strong baseline for the question: should you invest next in better policy tuning or better memory?
  - Directly relevant if your experiments still suffer from poor multimodal tool selection.
- Confidence: high.
- URLs:
  - paper: https://arxiv.org/abs/2504.21561
  - code/project: https://sport-agents.github.io/

### [Rank 7] Explorer: Scaling Exploration-driven Web Trajectory Synthesis for Multimodal Web Agents
- Relation to seed: same problem.
- Authors: See ACL Anthology page.
- Venue/Track/Year: ACL 2025 Findings; July 2025; peer-reviewed.
- Contribution (1 sentence): Builds a scalable recipe for synthesizing large multimodal web trajectories and uses them to train stronger web agents.
- Method sketch (2-4 bullets):
  - Uses web exploration and refinement to generate diverse task intents.
  - Produces a large multimodal trajectory corpus with screenshots and actions.
  - Trains a multimodal web agent on those trajectories.
- Best evidence:
  - 94K successful multimodal web trajectories over 49K URLs and 720K screenshots.
  - Strong benchmark gains on Mind2Web-Live, Multimodal-Mind2Web, and MiniWob++.
- Limitations:
  - Primarily a data-scaling paper, not a continual-memory paper.
  - Web-agent focus may not transfer cleanly to non-web multimodal tasks.
- Why selected:
  - XSKILL-like systems need rich rollouts; Explorer is one of the best recent sources for how to obtain them at scale.
  - High practical value if you need more trajectory data before changing the memory design.
- Confidence: high.
- URLs:
  - paper: https://aclanthology.org/2025.findings-acl.326/
  - code: not surfaced on the primary pages used

### [Rank 8] EventMemAgent: Hierarchical Event-Centric Memory for Online Video Understanding with Adaptive Tool Use
- Relation to seed: same method family.
- Authors: See arXiv/project page.
- Venue/Track/Year: arXiv preprint, posted 2026-02-17; not peer-reviewed yet.
- Contribution (1 sentence): Extends agent memory into streaming video by building hierarchical event-centric memory plus adaptive tool use.
- Method sketch (2-4 bullets):
  - Maintains hierarchical memories over events rather than single frames.
  - Adapts tool calls based on the evolving video context.
  - Targets online multimodal reasoning.
- Best evidence:
  - Strong conceptual extension from image-grounded memory to temporally grounded memory.
  - Official GitHub repo improves inspectability.
- Limitations:
  - Evidence is still preprint-only.
  - The task setting is more specialized than the seed's broader multimodal-agent framing.
- Why selected:
  - Useful if your next experiments involve video or temporally extended observations.
  - Shows how the XSKILL memory idea might need to change when the perceptual state evolves continuously.
- Confidence: medium.
- URLs:
  - paper: https://arxiv.org/abs/2602.11878
  - code: https://github.com/lingcco/EventMemAgent

### [Rank 9] SMART: Self-Aware Agent for Tool Overuse Mitigation
- Relation to seed: same method family.
- Authors: See ACL Anthology page.
- Venue/Track/Year: ACL 2025 Findings; July 2025; peer-reviewed.
- Contribution (1 sentence): Trains agents to decide when tools are unnecessary, reducing wasteful tool use while preserving or improving accuracy.
- Method sketch (2-4 bullets):
  - Builds self-awareness around tool necessity.
  - Adds rationale-enriched supervision for when to use tools.
  - Optimizes the balance between parametric knowledge and external tools.
- Best evidence:
  - Reports 24% fewer tool calls and over 37% performance gains on its evaluation setup.
  - Strong open-source reproducibility signal through released data and code.
- Limitations:
  - Less about memory accumulation than about decision calibration.
  - Mostly text/tool reasoning, not the full visually grounded continual-learning loop of XSKILL.
- Why selected:
  - Directly useful if your current bottleneck is cost/latency from over-calling tools.
  - Complements XSKILL's efficiency story without requiring a memory rewrite.
- Confidence: high.
- URLs:
  - paper: https://aclanthology.org/2025.findings-acl.239/
  - code: https://github.com/qiancheng0/Open-SMARTAgent

### [Rank 10] Memtool: Optimizing Short-Term Memory Management for Dynamic Tool Calling in LLM Agent Multi-Turn Conversations
- Relation to seed: same method family.
- Authors: See arXiv paper page.
- Venue/Track/Year: arXiv preprint, posted 2025-07-29; not peer-reviewed yet.
- Contribution (1 sentence): Focuses on short-term memory management for dynamic tool-calling in multi-turn agent conversations.
- Method sketch (2-4 bullets):
  - Optimizes what recent interaction state to preserve.
  - Targets dynamic tool-calling rather than generic chat memory.
  - Treats memory as an execution-critical resource.
- Best evidence:
  - Strong implementation relevance for tool-calling agents.
  - Directly aligned with the seed's goal of improving tool orchestration without changing model weights.
- Limitations:
  - No official code surfaced in the primary sources used here.
  - Short-term memory scope is narrower than XSKILL's reusable cross-task knowledge.
- Why selected:
  - Useful engineering paper if you need a simpler intermediate step before building full dual-stream memory.
  - Could pair well with XSKILL as a short-horizon execution cache.
- Confidence: medium.
- URLs:
  - paper: https://arxiv.org/abs/2507.21870
  - code: not surfaced on primary sources used

### [Rank 11] Plan-and-Act: Improving Planning of Agents for Long-Horizon Tasks
- Relation to seed: adjacent.
- Why adjacent: included because explicit planning quality is a major upstream variable for whether external memories are actually useful at inference time.
- Authors: Lutfi Eren Erdogan, Nicholas Lee, Sehoon Kim, Suhong Moon, Hiroki Furuta, Gopala Anumanchipalli, Kurt Keutzer, Amir Gholami.
- Venue/Track/Year: ICML 2025 main conference; conference held 2025-07-13 to 2025-07-19; proceedings volume published 2025-10-06; peer-reviewed.
- Contribution (1 sentence): Separates planning from execution and trains a planner with synthetic data to improve long-horizon agent performance.
- Method sketch (2-4 bullets):
  - Uses planner-executor decomposition.
  - Generates synthetic plan annotations for training.
  - Evaluates on web-navigation long-horizon tasks.
- Best evidence:
  - 57.58% success on WebArena-Lite.
  - 81.36% on WebVoyager.
- Limitations:
  - Not multimodal-memory-centric.
  - Uses learned planning rather than non-parametric continual memory.
- Why selected:
  - Good adjacent reference for the question of how much of XSKILL's gain may really come from better planning structure.
  - High-impact execution baseline for deployment-minded experiments.
- Confidence: high.
- URLs:
  - paper: https://proceedings.mlr.press/v267/erdogan25a.html
  - code: software/OpenReview links available from the PMLR page

### [Rank 12] Magnet: Multi-turn Tool-use Data Synthesis and Distillation via Graph Translation
- Relation to seed: adjacent.
- Why adjacent: included because it is one of the strongest recent papers on generating the multi-turn tool-use trajectories that external-memory agents rely on.
- Authors: Fan Yin, Zifeng Wang, I-Hung Hsu, Jun Yan, Ke Jiang, Yanfei Chen, Jindong Gu, Long Le, Kai-Wei Chang, Chen-Yu Lee, Hamid Palangi, Tomas Pfister.
- Venue/Track/Year: ACL 2025 Long Papers; July 2025; peer-reviewed.
- Contribution (1 sentence): Synthesizes high-quality multi-turn tool-use trajectories via graph translation and distills them into better function-calling models.
- Method sketch (2-4 bullets):
  - Represents function interactions as graphs.
  - Builds positive and negative tool-use trajectories automatically.
  - Uses supervised fine-tuning plus preference optimization.
- Best evidence:
  - 68.01 on BFCL-v3 and 73.30 on ToolQuery for Magnet-14B-mDPO in the reported setup.
  - Beats the cited teacher model Gemini-1.5-pro-002 on those evaluations.
- Limitations:
  - Primarily a data-synthesis/training paper, not a continual-memory paper.
  - Multi-turn function calling is broader than the seed's multimodal grounding focus.
- Why selected:
  - Good source of ideas for generating rollout corpora before memory extraction.
  - Useful for improving the teacher data pipeline behind XSKILL-like systems.
- Confidence: high.
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
- Agent Reviewers: Domain-specific Multimodal Agents with Shared Memory for Paper Review (ICML 2025): useful shared-memory multimodal system, but too domain-specific to paper review for a core shortlist slot.
- MCP-Zero: Automatic Discovery and Invocation of Any Function for AI Agents (arXiv 2025): promising for tool discovery and invocation infrastructure, but less about continual multimodal memory.
- Multi-modal Agent Tuning: Building a VLM-Driven Agent for Efficient Tool Usage (ICLR 2025 Spotlight): highly relevant multimodal tool-use paper, but outside the requested 12-month window because the ICLR 2025 publication date predates 2025-03-15.
- WAVE: Building Multimodal Web Agents via Iterative Real-World Exploration (2026 under-review/open work): interesting real-world web-agent direction, but I deprioritized it because the peer-review status was weaker and the primary metadata was less stable.

## 8) Trends and Openings
- Trend 1: External memory is shifting from raw retrieval snippets toward reusable procedures, workflows, and skill objects.
- Trend 2: Multimodal tool-use performance is being improved through better data engines as much as through better memory mechanisms.
- Contradictions/disagreements:
  - Some papers push policy improvement through training and preference optimization, while others push training-free external memory; the field has not settled which is more sample-efficient across task shifts.
  - Tool-use efficiency can come from better memory recall (XSKILL, Memtool) or better abstention/calibration (SMART), and the interaction between the two is still under-tested.
- Potential research openings:
  - Combine XSKILL-style dual memory with AGENTFLOW or Plan-and-Act style execution control.
  - Replace text-only experience vectors with temporally grounded event memory for video/web settings.
  - Evaluate true online continual loops over many task batches, not just one accumulation pass.
  - Build a benchmark that separately scores retrieval quality, adaptation quality, and execution quality for multimodal memories.

## 9) Coverage Gaps and Blind Spots
- Missing sub-areas:
  - Few strong peer-reviewed papers directly target visually grounded continual memory for multimodal agents; most direct matches are still preprints.
  - Tool-augmented video agents and embodied multimodal agents remain thin in this window.
- Venue bias risk:
  - The shortlist leans toward ICML/ACL because those venues exposed the clearest recent primary-source metadata in the requested window.
- Time-window risk:
  - Restricting to 2025-03-15 through 2026-03-15 excludes an important near-neighbor paper, T3-Agent, that would otherwise belong on the shortlist.

## 10) Action Plan (2 Weeks)
- Day 1-3: read papers #1, #2, #3, #5 in order to lock down the memory design space: dual memory, procedural memory, workflow memory, evolving skills.
- Day 4-5: read papers #6, #9, #10 to isolate execution pain points around tool selection, overuse, and short-term memory.
- Day 6-7: read papers #4 and #11 to compare whether planning/control changes deliver larger gains than memory changes.
- Day 8-9: read papers #7 and #12 to decide whether your next bottleneck is data generation rather than memory design.
- Day 10-11: read paper #8 if video/streaming tasks matter; otherwise use the time to map XSKILL against your own current agent stack.
- Day 12-14: produce a short internal memo with three concrete experiment tracks:
  - XSKILL-style dual memory only.
  - Dual memory plus improved execution controller.
  - Better trajectory/data generation before any memory redesign.
