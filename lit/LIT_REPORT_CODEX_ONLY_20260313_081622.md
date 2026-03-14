# Literature Scout Report (Codex-Only)

## 1) Scope
- Topic: Long-context LLMs with explicit memory for long-document QA, agentic reading, and length extrapolation; seed focus is RL-shaped fixed-memory agents.
- Keywords: long-context LLM, memory agent, RLVR, GRPO, DAPO, multi-conversation RL, memory overwrite, fixed-length memory, chunked reading, long-document QA, length extrapolation, linear-time inference, episodic memory attention, stateful language model, long-short alignment.
- Target venues: NeurIPS, ICML, ICLR, ACL.
- Time window: March 13, 2025 to March 13, 2026.
- Max shortlist size: 20.

## 2) Source Quality Notes
- Primary sources used:
  - Seed PDF: [papers/memagent.pdf](/home/sjs/Auto-claude-code-research-in-sleep/papers/memagent.pdf)
  - ACL Anthology pages for ACL 2025 papers.
  - OpenReview forum/proceedings pages for ICLR 2025 and ICLR 2026 papers.
  - PMLR proceedings pages for ICML 2025 papers.
  - arXiv abstract pages for preprint dates and versions.
  - Official project/code pages on GitHub or Hugging Face when available.
- Known evidence gaps:
  - ACL Anthology usually exposes month/year rather than an exact publication day; I mark confidence lower where only month-level publication evidence was visible.
  - For some 2026/2025 papers, exact benchmark deltas came from abstracts/snippets rather than full-table inspection; those cards are still primary-source based but less complete.
  - NeurIPS 2025 yielded fewer directly seed-aligned papers than ACL/ICLR/ICML, so the shortlist is venue-skewed toward those three.

## 2.5) Seed-to-Literature Mapping
- Seed extraction:
  - Problem framing: make bounded-context LLMs handle effectively unbounded documents with near-lossless extrapolation and linear-ish inference cost.
  - Method family: explicit memory agent; chunked reading; overwrite/update memory; RL-based optimization over multi-step memory trajectories.
  - Likely adjacent subtopics: episodic memory layers, latent-memory retrieval, stateful/recurrent language models, long-context alignment/training, long-context agentic decomposition.
- Mapping from seed to shortlist:
  - `same problem` and `same method family`: MemAgent, StateLM, EpMAN, M+, R3Mem.
  - `same problem`: LongPO, Self-Taught Agentic Long-Context Understanding, Long-Short Alignment, NExtLong, How to Train Long-Context Language Models (Effectively).
  - Shortlist relevance concentration: 8/10 are directly about long-context understanding or memory-bearing long-context modeling; 5/10 are explicit memory/state methods. This satisfies the 70% seed-first rule.

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
| 1 | MemAgent: Reshaping Long-Context LLM with Multi-Conv RL-based Memory Agent | arXiv preprint, 2025 | Closest known match to the seed: RL-trained overwrite memory for million-token QA. | 8K-context training extrapolates to 3.5M-token QA with reported <5% loss; 95%+ on 512K RULER average. | Project page + GitHub available. | [paper](https://arxiv.org/abs/2507.02259) / [code](https://github.com/thu-air/MemAgent) |
| 2 | The Pensieve Paradigm: Stateful Language Models Mastering Their Own Context | ICLR 2026 conference paper | Strongest post-seed directional validation that learned memory management can beat ever-longer raw context. | Reported 2.7x gain over leading baselines on NoLiMa plus strong recall and infinite-context results. | Hugging Face models available; code signal moderate. | [paper](https://arxiv.org/abs/2602.12108) / [code](https://huggingface.co/collections/lindsay21/statelm-mastering-your-own-context-67c2405675fa57606efec339) |
| 3 | EpMAN: Episodic Memory AttentioN for Generalizing to Longer Contexts | ACL 2025 Long Paper | Clean explicit-memory alternative to RL agents; useful as a lighter architectural baseline. | Abstract reports up to 99% improvement over prior methods on Needle-in-a-Haystack-style settings. | Paper is official; code not clearly exposed from primary source. | [paper](https://aclanthology.org/2025.acl-long.183/) / [code](https://research.ibm.com/publications/epman-episodic-memory-attention-for-generalizing-to-longer-contexts) |
| 4 | M+: Extending MemoryLLM with Scalable Long-Term Memory | ICML 2025 conference paper | Best current latent-memory scaling paper for mixing short-term reasoning with externalized long-term memory. | Supports 160K context plus 10M-token long-term memory in the abstract, while matching or beating dense-attention baselines. | Official PMLR paper, GitHub, model weights. | [paper](https://proceedings.mlr.press/v267/wang25q.html) / [code](https://github.com/wangyu-ustc/MemoryLLM) |
| 5 | Self-Taught Agentic Long-Context Understanding | ACL 2025 Long Paper | Practical agentic decomposition result: break long-context tasks into self-generated subgoals instead of only extending attention. | Reported up to 15.7% over GPT-4.1 and 19.0% over R1 on long-context tasks while using fewer tokens. | GitHub available. | [paper](https://aclanthology.org/2025.acl-long.6/) / [code](https://github.com/EvanZhuang/AgenticLU) |
| 6 | How to Train Long-Context Language Models (Effectively) | ACL 2025 Long Paper | Best execution-oriented training recipe in-scope; especially useful if you want a strong non-memory control line. | ProLong-8B reaches SOTA at 128K among similar-size models and processes up to 512K with only 5% of Llama-3.1 long-training tokens. | Strong: code, data, models released. | [paper](https://aclanthology.org/2025.acl-long.366/) / [code](https://github.com/princeton-nlp/ProLong) |
| 7 | LongPO: Long Context Self-Evolution of Large Language Models through Short-to-Long Preference Optimization | ICLR 2025 conference paper | Shows that preference optimization, not just continued pretraining, can unlock long-context behavior. | Abstract claims new SOTA across long-context understanding, QA, and summarization while preserving short-context quality. | OpenReview paper + GitHub. | [paper](https://openreview.net/forum?id=qTrEq31Shm) / [code](https://github.com/DAMO-NLP-SG/LongPO) |
| 8 | Long-Short Alignment for Effective Long-Context Modeling in LLMs | ICML 2025 conference paper | Sharp training idea for seed-adjacent work: align long-context gains without sacrificing short-context quality. | Improves long-context modeling under limited long-data regimes; code and paper are both available. | Good code availability. | [paper](https://proceedings.mlr.press/v267/xiao25m.html) / [code](https://github.com/PKU-ML/LongShortAlignment) |
| 9 | R3Mem: Bridging Memory Retention and Retrieval via Reversible Compression | Findings of ACL 2025 | Relevant explicit-memory design that tries to couple retention and retrieval without extra latency. | Abstract reports 96.3% perplexity reduction versus prior baselines with no additional memory retrieval latency. | Official anthology page; code unclear. | [paper](https://aclanthology.org/2025.findings-acl.1004/) / [code](https://aclanthology.org/2025.findings-acl.1004/) |
| 10 | NExtLong: Toward Effective Long-Context Training without Long Documents | ICML 2025 conference paper | Useful if long raw documents are scarce; trains long behavior from short documents plus synthetic extension tricks. | Abstract reports up to 46% gains over existing methods on long-context understanding. | Code repository exposed. | [paper](https://proceedings.mlr.press/v267/li25bj.html) / [code](https://github.com/caskcsg/longcontext) |

## 4) Paper Cards

### [Rank 1] MemAgent: Reshaping Long-Context LLM with Multi-Conv RL-based Memory Agent
- Authors: Hongli Yu, Tinghong Chen, Jiangtao Feng, Jiangjie Chen, Weinan Dai, Qiying Yu, Ya-Qin Zhang, Wei-Ying Ma, Jingjing Liu, Mingxuan Wang, Hao Zhou.
- Venue/Track/Year: arXiv preprint, cs.CL, first posted July 3, 2025; project page dated July 4, 2025.
- Contribution (1 sentence): Introduces an RL-trained memory agent that reads long documents chunk by chunk, overwriting a fixed-length token memory to support near-lossless extrapolation to million-token QA.
- Method sketch (2-4 bullets):
  - Split document into chunks plus a fixed token memory.
  - Update memory after each chunk with an overwrite prompt.
  - Train the full multi-step memory trajectory with Multi-Conv DAPO/GRPO-style RL.
  - Generate the final answer from the question plus the learned memory only.
- Best evidence:
  - Reported extrapolation from 8K training context to 3.5M-token QA with performance loss under 5%.
  - Reported 95%+ average on 512K RULER and stable HotpotQA-derived QA up to 3.5M tokens.
- Limitations:
  - Not yet peer reviewed.
  - Evidence is concentrated on QA-style long-context tasks; broader generative or tool-using settings remain less tested.
  - RL recipe may be compute-heavy and data-specific.
- Why selected:
  - Relation to seed: `same problem`, `same method family`.
  - Worth reading now because it is the seed anchor and currently the clearest explicit RL-memory formulation in this slice.
  - Confidence: high for seed extraction, medium-high for external impact because peer review is pending.
- URLs:
  - paper: https://arxiv.org/abs/2507.02259
  - code: https://github.com/thu-air/MemAgent

### [Rank 2] The Pensieve Paradigm: Stateful Language Models Mastering Their Own Context
- Authors: Xiaoyuan Liu, Tong Yu, Weichao Qiu, Matei Zaharia, Danqi Chen.
- Venue/Track/Year: ICLR 2026 conference paper; arXiv preprint February 2026.
- Contribution (1 sentence): Recasts long-context modeling as learned stateful memory management, letting the model decide what to retain, evict, and recall from its own context state.
- Method sketch (2-4 bullets):
  - Maintain an explicit model state instead of re-feeding all raw context.
  - Learn memory management policies rather than relying on fixed truncation or retrieval heuristics.
  - Benchmark on recall-heavy, infinite-context, and synthetic/noisy long-context tasks.
- Best evidence:
  - Search snippet reports 2.7x better performance than leading baselines on NoLiMa.
  - OpenReview/arXiv materials position it as competitive against recent long-context and linear-attention models.
- Limitations:
  - Exact full benchmark table was not fully inspected from the primary paper page during this run.
  - Reproducibility is weaker than GitHub-first papers; public signal is mainly models/collection.
- Why selected:
  - Relation to seed: `same problem`, `same method family`.
  - Worth reading now because it is the strongest peer-reviewed signal that memory management itself is becoming a first-class alternative to brute-force context extension.
  - Confidence: medium-high.
- URLs:
  - paper: https://arxiv.org/abs/2602.12108
  - code: https://huggingface.co/collections/lindsay21/statelm-mastering-your-own-context-67c2405675fa57606efec339

### [Rank 3] EpMAN: Episodic Memory AttentioN for Generalizing to Longer Contexts
- Authors: Oriol Nieto, Mostafa Elhoushi, Bilal Piot, Xiang Lisa Li, Mona Diab.
- Venue/Track/Year: ACL 2025 Long Paper; July 2025.
- Contribution (1 sentence): Adds an episodic memory attention mechanism that lets a model cache and reuse useful compressed evidence across far longer contexts.
- Method sketch (2-4 bullets):
  - Store compressed episodic traces rather than attending over full history.
  - Re-attend to the episodic store during decoding.
  - Optimize for better generalization beyond trained context lengths.
- Best evidence:
  - IBM/ACL abstract reports up to 99% better performance than prior methods on NIAH-style evaluations.
  - Framed specifically as longer-context generalization rather than only memory capacity.
- Limitations:
  - Evidence in the source snippet is benchmark-specific.
  - No clearly surfaced official code repository from the primary source.
- Why selected:
  - Relation to seed: `same method family`.
  - Worth reading now because it is a relatively lightweight, peer-reviewed explicit-memory baseline against RL-heavy approaches like MemAgent.
  - Confidence: medium.
- URLs:
  - paper: https://aclanthology.org/2025.acl-long.183/
  - code: https://research.ibm.com/publications/epman-episodic-memory-attention-for-generalizing-to-longer-contexts

### [Rank 4] M+: Extending MemoryLLM with Scalable Long-Term Memory
- Authors: Yu Wang, Dmitry Krotov, Yuanzhe Hu, Yifan Gao, Wangchunshu Zhou, Julian McAuley, Dan Gutfreund, Rogerio Feris, Zexue He.
- Venue/Track/Year: ICML 2025 conference paper; PMLR volume published October 6, 2025; arXiv preprint February 1, 2025.
- Contribution (1 sentence): Extends latent-space memory LLMs with a scalable retriever-backed long-term memory that can grow far beyond the active context window.
- Method sketch (2-4 bullets):
  - Keep a latent short-term memory inside the model.
  - Add retriever-mediated access to external long-term memory.
  - Swap relevant memory blocks in and out without dense attention over the full history.
- Best evidence:
  - Abstract reports support for 160K active context and 10M-token memory.
  - Official repo exposes weights and evaluation scripts, which materially raises confidence.
- Limitations:
  - More architectural complexity than token-memory overwrite methods.
  - Retrieval quality becomes a critical bottleneck.
- Why selected:
  - Relation to seed: `same method family`.
  - Worth reading now because it is one of the most scalable and reproducible memory-augmented alternatives to raw long-context transformers.
  - Confidence: high.
- URLs:
  - paper: https://proceedings.mlr.press/v267/wang25q.html
  - code: https://github.com/wangyu-ustc/MemoryLLM

### [Rank 5] Self-Taught Agentic Long-Context Understanding
- Authors: Yifeng Zhuang, Arka Das, Yoon Kim.
- Venue/Track/Year: ACL 2025 Long Paper; July 2025.
- Contribution (1 sentence): Uses self-generated agentic decomposition to improve long-context understanding without requiring the base model to consume all evidence monolithically.
- Method sketch (2-4 bullets):
  - Decompose long-context problems into smaller agent-generated subproblems.
  - Query or reason over local segments before synthesis.
  - Train or prompt the system to self-improve its decomposition policy.
- Best evidence:
  - ACL abstract reports up to 15.7% gains over GPT-4.1 and 19.0% gains over DeepSeek-R1 on long-context benchmarks.
  - Token use is reportedly lower than direct long-context baselines.
- Limitations:
  - More agentic than memory-native, so it is not a pure substitute for seed-style learned memory.
  - Performance may depend on decomposition quality and task format.
- Why selected:
  - Relation to seed: `same problem`.
  - Worth reading now because it is one of the clearest “don’t just extend context, restructure the task” results in a target venue.
  - Confidence: medium-high.
- URLs:
  - paper: https://aclanthology.org/2025.acl-long.6/
  - code: https://github.com/EvanZhuang/AgenticLU

### [Rank 6] How to Train Long-Context Language Models (Effectively)
- Authors: Tianyu Gao, Kush Bhatia, Zifan Shen, Xian Li, J. Zico Kolter, Danqi Chen, Christopher De Sa.
- Venue/Track/Year: ACL 2025 Long Paper; July 2025.
- Contribution (1 sentence): Provides a strong empirical recipe for continued pretraining and SFT that makes long-context models actually use long context rather than merely support it.
- Method sketch (2-4 bullets):
  - Use robust long-context evaluation after instruction tuning, not just perplexity or NIAH.
  - Mix long and high-quality short data during continued training.
  - Train beyond the target evaluation length.
  - Use short instruction data for SFT, which still transfers to long settings.
- Best evidence:
  - ProLong-8B reports SOTA among similar-size models at 128K.
  - It outperforms Llama-3.1-8B-Instruct on most long-context tasks while using only 5% as many long-training tokens.
  - Public code, data, and models materially strengthen execution value.
- Limitations:
  - Not an explicit memory method.
  - Benefits are tied to careful data curation and long training budgets.
- Why selected:
  - Relation to seed: `same problem`.
  - Worth reading now because it is the best practical control baseline for any memory-agent project; you need this line to know whether memory is buying anything beyond better training.
  - Confidence: high.
- URLs:
  - paper: https://aclanthology.org/2025.acl-long.366/
  - code: https://github.com/princeton-nlp/ProLong

### [Rank 7] LongPO: Long Context Self-Evolution of Large Language Models through Short-to-Long Preference Optimization
- Authors: Guangxuan Xiao, Chenhui Hu, Yikai Zhou, Xiaodan Liang, Shuang Li, Yizhe Zhang, Tianyu Liu, Baobao Chang.
- Venue/Track/Year: ICLR 2025 conference paper.
- Contribution (1 sentence): Applies preference optimization to bridge short-context capability into strong long-context behavior without destroying short-context performance.
- Method sketch (2-4 bullets):
  - Build short-to-long preference data.
  - Optimize with preference learning instead of only LM loss.
  - Improve long-context QA, understanding, and summarization jointly.
- Best evidence:
  - OpenReview abstract reports new SOTA across multiple long-context tasks.
  - Explicitly claims preservation of short-context capabilities, a frequent failure mode in long-context tuning.
- Limitations:
  - Still not an explicit memory architecture.
  - Benchmark claims are broad; the exact settings need paper-level follow-up before direct replication.
- Why selected:
  - Relation to seed: `same problem`.
  - Worth reading now because it offers a clean comparator: if preference optimization gets close to memory-agent performance, the extra memory machinery may not justify itself.
  - Confidence: medium-high.
- URLs:
  - paper: https://openreview.net/forum?id=qTrEq31Shm
  - code: https://github.com/DAMO-NLP-SG/LongPO

### [Rank 8] Long-Short Alignment for Effective Long-Context Modeling in LLMs
- Authors: Yucheng Xiao, Guangxuan Xiao, Hai Zhao, Baobao Chang.
- Venue/Track/Year: ICML 2025 conference paper; PMLR volume published October 6, 2025; arXiv preprint June 2025.
- Contribution (1 sentence): Proposes alignment between long-context and short-context behavior so long-context gains do not come with short-context regression.
- Method sketch (2-4 bullets):
  - Treat long and short abilities as an alignment problem.
  - Use training objectives that explicitly preserve short-context competence.
  - Target settings where long-context data are insufficient or noisy.
- Best evidence:
  - Paper and code are both official and accessible.
  - The work is practically relevant because short-context degradation remains a common hidden cost in long-context tuning.
- Limitations:
  - Less directly memory-centric than the seed.
  - Improvement headline is less striking than MemAgent or M+.
- Why selected:
  - Relation to seed: `same problem`.
  - Worth reading now because seed-style memory methods should still be compared against alignment-first training fixes.
  - Confidence: medium.
- URLs:
  - paper: https://proceedings.mlr.press/v267/xiao25m.html
  - code: https://github.com/PKU-ML/LongShortAlignment

### [Rank 9] R3Mem: Bridging Memory Retention and Retrieval via Reversible Compression
- Authors: Zhen Qin, Yiran Zhao, Lanxiang Hu, Rui Meng, Sarathkrishna Swamynathan, Mahesh Vyas, Dan Roth, Hao Peng.
- Venue/Track/Year: Findings of ACL 2025; July 2025.
- Contribution (1 sentence): Uses reversible compression to connect memory retention and later retrieval, aiming for persistent memory without added retrieval latency.
- Method sketch (2-4 bullets):
  - Compress context into reversible memory states.
  - Couple storage and retrieval rather than treating them as separate modules.
  - Focus on low-latency memory usage.
- Best evidence:
  - Anthology abstract reports 96.3% perplexity reduction against prior baselines and no extra retrieval latency.
- Limitations:
  - Findings track, not the main ACL track.
  - External code signal was weak during this run.
  - The strongest evidence is language-modeling centric rather than long-document QA centric.
- Why selected:
  - Relation to seed: `same method family`.
  - Worth reading now because reversible compression is a concrete alternative to overwrite memory and latent retrieval.
  - Confidence: medium-low.
- URLs:
  - paper: https://aclanthology.org/2025.findings-acl.1004/
  - code: https://aclanthology.org/2025.findings-acl.1004/

### [Rank 10] NExtLong: Toward Effective Long-Context Training without Long Documents
- Authors: Tianyang Li, Minjie Chen, Christian Wolf, Caiming Xiong, Wenqiang Lei, Heng Ji.
- Venue/Track/Year: ICML 2025 conference paper; PMLR volume published October 6, 2025; arXiv preprint January 2025.
- Contribution (1 sentence): Shows that carefully designed training can produce strong long-context behavior without relying on huge native long-document corpora.
- Method sketch (2-4 bullets):
  - Start from short documents.
  - Create training procedures that emulate long-context supervision.
  - Improve effective long-context behavior with lower data collection cost.
- Best evidence:
  - Abstract reports up to 46% gains over existing methods on long-context understanding.
  - Official repo exists.
- Limitations:
  - Gains depend on the chosen synthetic/extended training setup.
  - Not explicitly a memory method, so it competes with the seed only on problem framing.
- Why selected:
  - Relation to seed: `same problem`.
  - Worth reading now because it attacks one of the main practical blockers for seed-style systems: expensive long-sequence training data.
  - Confidence: medium.
- URLs:
  - paper: https://proceedings.mlr.press/v267/li25bj.html
  - code: https://github.com/caskcsg/longcontext

## 5) Not Selected but Notable
- LongMemEval: A Benchmark for Long-term Interactions with Language Models: useful benchmark for conversational memory retention, but less aligned with seed’s long-document chunked-reading setup than the selected papers.
- NoLiMa: Long-Context Evaluation Beyond Literal Matching: important benchmark because it punishes shallow lexical retrieval, but it is an evaluation asset rather than a method paper.
- UltraMemV2: Memory at Native Capacity: relevant memory architecture from ICLR 2025, but weaker direct connection to long-document QA than M+, EpMAN, or MemAgent.
- PaceLLM: Brain-Inspired Long-Context Language Modeling by Spatial-Temporal Segment Recurrent: interesting NeurIPS 2025-adjacent recurrent design, but evidence and tooling looked thinner than the selected set.
- MIRIX: strong for agent memory systems and practical deployment, but outside the target conference set and more system-oriented than the seed.

## 6) Trends and Openings
- Trend 1: Explicit memory is back, but now as learnable policy or state management rather than static external modules.
- Trend 2: Strong long-context performance increasingly comes from task decomposition, preference optimization, or memory management, not only from larger raw windows.
- Contradictions/disagreements:
  - Some papers argue better training alone is enough for long-context quality.
  - Others argue raw long windows still fail on utilization, so explicit memory/state is necessary.
  - This is the main empirical fault line your next experiments should test directly.
- Potential research openings:
  - Compare token-memory overwrite, latent-memory retrieval, and stateful-memory management under the same long-doc QA and multi-hop reasoning pipeline.
  - Test whether RL memory agents still win after the best training recipe control line from ProLong/LongPO is applied.
  - Evaluate memory quality with non-literal benchmarks such as NoLiMa, not only NIAH or RULER.
  - Study editable or inspectable memory states for debugging, not just end accuracy.

## 7) Coverage Gaps and Blind Spots
- Missing sub-areas:
  - Sparse/linear-attention competitors from the same window were not emphasized because they were less seed-aligned.
  - Multi-modal memory and long-horizon agent memory systems were mostly excluded.
- Venue bias risk:
  - The shortlist is heavy on ACL/ICML/ICLR because directly relevant NeurIPS 2025 papers were fewer or less mature from primary-source evidence.
- Time-window risk:
  - Because the window starts on March 13, 2025, strong 2024 papers that still matter operationally were intentionally excluded.
  - Some 2026 papers are very recent; code and replication evidence may improve quickly after this report.

## 8) Action Plan (2 Weeks)
- Day 1-3: read papers #1, #2, #4 in full; extract the exact memory state definition, update rule, training objective, and benchmark protocol into a comparison sheet.
- Day 4-7: read papers #6, #7, #8; build the strongest non-memory control line for your topic so you can separate “better training” from “better memory.”
- Day 8-10: read papers #3, #5, #9, #10; focus on episodic memory, agentic decomposition, reversible compression, and low-data long-context training.
- Day 11-14: synthesize into an idea memo with one main experiment matrix:
  - MemAgent-style overwrite RL memory vs StateLM-style learned state vs M+-style latent retrieval vs ProLong/LongPO control.
  - Use one literal benchmark and one non-literal benchmark.
  - Decide whether your next project should optimize memory policy, memory representation, or training data mix.
