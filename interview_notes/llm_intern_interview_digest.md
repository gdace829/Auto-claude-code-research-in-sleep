# 大模型实习面试题整理

整理范围：本轮对话中你发送的全部截图题目。  
目标：形成一份可继续扩展的 `LLM / Agent / RLHF / 搜索推荐 / Infra` 面试题总表。

---

## 1. 高频主题总览

从这些面经里反复出现的主题看，当前大模型实习面试主要集中在以下方向：

1. `RLHF / RLVR / 后训练`
   - SFT、DPO、PPO、GRPO、DAPO、GSPO、VAPO
   - reward 设计、reward hacking、critic、advantage、GAE、KL、clipping
   - 训练稳定性、loss 聚合粒度、长 CoT、token-level vs sequence-level

2. `Agent / Function Call / Workflow`
   - 单 agent vs 多 agent
   - workflow、memory、planning、tool-use
   - function call 数据构造、训练流程、prompt 设计
   - MCP、A2A、AutoGen、ReAct agent、multi-agent

3. `应用评测 / Benchmark / 拟人性`
   - 没有 golden answer 如何评测
   - benchmark 如何设计
   - 拟人性、主动性、推动性定义与构造
   - 训练前后主观体验、case 分析、bad case 与观感提升

4. `检索 / 搜索 / 推荐 / RAG`
   - embedding vs reranker
   - 检索召回链路、结构化与非结构化召回、多路召回
   - 低质量网页处理、AI 搜索、Deep Search
   - 推荐系统链路、AUC / GAUC、PLE、InfoNCE、语义 ID

5. `训练与推理系统`
   - vLLM、SGLang、DeepSpeed、Megatron
   - dp / tp / pp 并行
   - 推理服务调度、server 启动、显存占用、训练框架
   - 首字延迟、链路延迟、性能测量与优化

6. `基础模型与架构`
   - LLaMA 3 结构、MLA 对 MHA 的优化
   - Transformer 之外的架构
   - 多头注意力复杂度、线性注意力
   - 从 word2vec 到 DeepSeek-R1 的发展

7. `项目表达`
   - 自我介绍、项目介绍、难点与解决
   - 数据构造、过滤、去重、质量与多样性
   - 是否上线、是否 oncall、是否有具体指标和延迟数字
   - SOP、主导部分 vs 参与部分、trade-off

8. `手撕 / 公式 / 基础题`
   - 归并排序、最长公共子序列、最长无重复子串、最短路径、反转链表、爬楼梯
   - 熵、交叉熵、KL、MSE、二分类 loss、next token prediction
   - batch norm vs layer norm

---

## 2. 按公司整理

## 快手大模型

### 快手大模型一面
- 自我介绍、项目介绍
- 微调数据构造、去重、微调细节、DPO 数据构造细节
- 强化奖励设计方法，训练过程 reward score 趋势
- GRPO -> DAPO -> GSPO
- 手撕：无重复字符最长子串

### 快手大模型二面
- 自我介绍、项目介绍
- 奖励设计方式，rule-based / model-based 选择
- 缓解 reward hacking
- GRPO 为什么不稳定，缓解方法
- 没有 golden answer 的回答如何评测
- 结果奖励和中间奖励的类型
- Deep Search 中推理模型和回复模型设计
- AI 搜中低质量网页问题

### 快手推荐算法一面
- 推荐系统链路，各部分方法
- 过拟合如何解决
- PLE
- AUC / GAUC 及公式
- 语义 ID 和传统 ID
- OneRec、Tiger
- 项目中对比学习如何做
- InfoNCE loss
- 大 batch size 怎么办
- 反转链表 II

---

## 中兴领军大模型

### 中兴领军大模型一面
- 自我介绍
- 拟人性定义、评测、区别、构造
- 强化学习奖励函数如何构造，考虑因素，输入输出
- 多 agent 选型与主要解决的问题
- 幻觉现象、原因、缓解方法
- 论文思路、实习对学业影响
- 本科硕士绩点
- 手撕：加权图最短路径

### 中兴领军大模型二面
- 自我介绍
- 遇到困难与解决
- 多 agent 与单 agent 对比
- 微调数据集来源、筛选、过滤
- 期望薪资

### 中兴领军大模型三面
- 自我介绍、项目介绍
- 多 agent 交互流程，与单 agent 区别
- Kimi K2 等最新报告细节
- 1000 个 tools，有 K2 可用时如何保证 FC 又快又准
- 现在做大模型的人很多，你的优势在哪里

---

## 美团大模型应用

### 美团大模型应用一面
- 项目外呼智能客服怎么评测
- function call 训练该用单轮 QA 还是多轮训练
- 上下文过长如何处理
- PPO 训练流程
- PPO 属于什么结构，value-based 还是 policy-based，为什么
- GAE 公式
- GRPO 训练时看哪些指标
- 手撕：小偷偷钱，单维动态规划

---

## 字节相关

### 字节抖音电商 AI 搜一面
- PPO、DPO、GRPO、DAPO 区别
- PPO 组成
- Qwen3-VL 和千问 2.5-VL 比较升级
- Qwen3-VL 对动态分辨率
- 对比学习温度系数
- Qwen3-VL embedding 和 reranker 区别

### 字节抖音主页搜索一面
- DAPO 是否使用奖励归一化
- token-level / sequence-level 聚合粒度：DAPO、GRPO、GSPO
- DAPO 生成超长序列过滤，参数如何设
- clip 上下界如何调
- PPO 的 critic model 如何更新

### 字节广告算法一面
- 分层聚类提取特征的方法，RQ-VAE、RQ-Kmeans、One-Rec
- XGBoost
- MGRPO 多模态位置编码
- LeetCode 475 供暖器（二分）
- 手写交叉熵损失函数

### 字节广告算法二面
- PPO 公式推导，重要性采样为何有效，变分推断解释
- DPO 公式、与 BPR Loss、InfoNCE 区别，`\pi_ref` 作用
- 详细复习 PPO 与 DPO 的推导和解释

### 字节广告算法三面
- 长度为 `2n+1` 的数组中，两个数字出现一次，其他出现两次，找出只出现一次的数字

### 字节搜索电商大模型一面
- 自我介绍
- 概括之前实习，从模型训练中学到什么
- 强化学习业务应用探索过程
- DPO / PPO / GRPO 主要思想和细节
- 各阶段大模型训练成功关键因素
- 除 R1 系列外，其他使用强化学习取得效果的模型
- 亿级词表的预训练 pipeline 如何优化
- 多头注意力结构、复杂度、线性注意力
- 算法题：5614 找出最具竞争力的子序列

### 字节搜索电商大模型二面
- 自我介绍
- 论文核心创新点
- 业务 function call 数据构造与训练细节，问题与解决
- 手撕公式和伪代码
- 对比学习 loss、三元组损失、直接对比损失
- 熵、交叉熵、KL 散度
- 二分类 loss
- MSE loss
- 预训练 next token prediction loss
- batch norm vs layer norm，为什么写后者
- 算法题：力扣 124 二叉树中的最大路径和

---

## 微信 / 腾讯 / 淘天 / 蚂蚁 / 高德

### 微信技术架构多模态一面
- Qwen3-VL 和千问 2.5-VL 比较升级
- Qwen3-VL embedding 与 GME 模型区别
- InfoNCE loss 原理推导
- Qwen3-VL embedding 和 reranker 区别
- Paddle OCR 切分版面的原理
- BST 最近公共祖先，空间复杂度 O(1)

### 腾讯 IEG 大模型应用研究暑期实习
- 项目拷打为主，二面 40 分钟项目拷打 + 八股
- MCP、A2A 是什么
- AutoGen
- DPO 数据怎么构建
- 是否用过推理加速框架，如 vLLM
- ReAct agent 与 multi-agent 区别
- MCP 和 function call 区别
- 如何判断歌词生成质量
- LLaMA 3 结构
- 歌词生成项目使用的显卡
- agent 用什么模型、一次耗时多久、成本高不高
- 10 分钟手写归并排序

### 腾讯大模型 infra 暑期实习一面
- 自我介绍
- 数据合成框架、调度策略如何实现
- 并行策略：dp、tp、pp 的作用
- 待推理数据如何分发给 server，输入参数包含哪些
- 起 server 用什么框架，何时用 vLLM，何时用 SGLang
- vLLM 原理
- SGLang 为什么快
- RAG 如何建库、检索，用到哪些存储技术、模型、切分算法
- 多模态 RAG，如图文对如何存储
- 是否做过 agent，工作流怎么做
- MCP、MCP server 如何实现
- Java 最新版本和特性，虚拟线程池
- Java 常用命令行
- Linux 常用命令、查看日志
- 文本中抽取数字与大小写字母
- LeetCode 34：排序数组查找元素首尾位置

### 淘天大模型应用暑期实习一面
- 自我介绍
- 迁移学习原理，以及 NLP 里的经典迁移学习模型 / 任务
- 从 word2vec 到 DeepSeek-R1 的发展历程
- R1 的训练过程
- GRPO 的过程，与 PPO 相比的改进与优势
- SFT / RL 区别
- 作为算法工程师，LLM 技术发展迅速时该怎么做

### 淘天大模型应用暑期实习二面
- 自我介绍
- 项目介绍、难点、解决问题
- workflow 里增加一个 agent 后，回答耗时增加多少，是否测量
- DPO 数据集如何构造，效果如何，积累与启示
- 拟人性从哪些角度理解和建设
- 发散题：主流大模型研究方向、最近论文、未来想从事的方向

### 淘天集团搜推智能产品事业部 AI 助手算法一面
- 自我介绍
- function call 数据构造过程、额外处理
- 工具调用数据如何写 prompt，自动化流程如何构造，微调数据量、模型、卡数、训练细节
- benchmark 设计
- long-cot 和 short-cot 区别
- DPO 训练原理，与 RLHF 区别
- GRPO 与 PPO 区别
- DeepSpeed 与 Megatron 区别
- 算法题：最长公共子序列

### 淘天集团搜推智能产品事业部 AI 助手算法二面
- 自我介绍
- 用的是什么模型
- 在推理模型基础上，如何构建 agent 的工具调用能力
- think 和 answer 的部分怎么使用
- 训练数据量与类别
- 项目 SOP
- GRPO 原理、业务探索、难点与解决
- 强化训练前后，除了指标变化，观感是否提升，举 case
- 如何理解助手的拟人性

### 蚂蚁大模型暑期实习一面
- 自我介绍
- 项目介绍、难点与解决方法
- 数据构造，质量与多样性处理方法和流程，与其他方法对比
- 对话过程中的幻觉消解
- 修改 agent workflow 后，链路回复 / 首字延迟影响，给出具体数值
- R1 在代码、数学去训练时，没有验证器如何获取强化学习信号
- DPO 原理和训练过程
- 使用的训练框架
- 开放问题：MCP 理解与实际产品；端到端 agent 能力建设与优化（RL4Agent）
- 手撕：爬楼梯

### 蚂蚁大模型暑期实习二面
- 自我介绍
- 项目细节，困难与解决
- function call 数据构造与训练流程
- 一个 query 包含多个意图怎么处理，结合 SOP 说明
- 哪些内容是主要做的，哪些是参与的
- RLHF 流程，以及实践经验
- 大规模数据系统，如何优化检索 / 服务效率，尤其 C 端时延敏感
- 基于 LLM 的对话助手相对传统对话系统的优势
- DPO 和 GRPO 区别
- 手撕：矩阵坐标与 value 双向映射，优化到根号 n 复杂度
- 场景题：是否上线、是否 oncall、每周读多少论文、两周内冲指标除了训练还做什么

### 高德平台业务大模型暑期实习一面
- 自我介绍
- 对话助手的主动性、推动性、拟人性如何定义；从理解、技术探索、评测角度展开
- R1 的推理如何体现在数学、代码题上，怎么和项目结合
- 多轮对话中如何缓解幻觉
- workflow 和 agentic 的理解
- 从 agent 角度拆 memory、planning、tool-use
- 项目部署首字延迟是多少，从哪些角度缓解

### 高德平台业务大模型暑期实习二面
- 自我介绍
- 概述最熟悉的两个项目，负责部分
- 检索召回内容格式，结构化还是非结构化，几路召回，详细流程
- RLHF 流程与实践
- 开放题：基于 LLM 的对话助手相对已有十多年传统对话助手的最大优势

---

## 俄了么 / 米哈游

### 俄了么大模型暑期实习一面
- 大模型的 loss 在优化什么
- PPO、DPO、GRPO 及区别
- 介绍一个 LLM 架构（Transformer 除外）
- 是否了解 DeepSpeed
- 除 EB 外还用过哪些模型，如 Qwen、DeepSeek
- MLA 相比 MHA 的优化
- R1 训练为什么放弃 PRM

### 米哈游大模型暑期实习面经
- DPO 业务部署时温度和训练温度是否有差异
- 业务里是否见过 DPO 回答过长，如何解决
- DPO 的切分粒度并不一定取平均，有 session-level DPO
- DPO 学习率怎么调
- SFT、DPO、PPO 三阶段学习率差异，哪个更大，为什么
- 训练中是否出现 reward hacking
- 训练时加一层模型退火，收益在哪
- pointwise 和 pairwise 哪种更好，为什么
- 最新的 GRPO、DAPO、VAPO 是否了解，是否做过

---

## 文心一言 / 度小满

### 文心一言一面
- 直接用数据做 RL，和先用好数据做 SFT、再用坏数据做 RL 的区别
- 为什么 DS-R1 之前的强化学习像 PPO 效果没有很好
- 数据相关：数据产出怎么检测，CoT 训练时是否加点区分 thinking 模式

### 度小满大模型二面
- GRPO 训练显存占用及比例（参数、梯度、优化器）
- GRPO 与前身算法的区别
- 为什么 GRPO 可以去掉 critic
- rollout 时问题特别难或特别简单，导致回答全对或全错、reward 优势几乎都是 0，会怎样
- 去 verl 框架找 rollout 训练
- KL 约束加在 Loss 和 Reward 上，对稳定性的不同影响
- 相比 SFT，为什么强化学习训练通常不太稳定
- 提升大模型强化学习稳定性的方法
- TRPO / PPO 中为什么要约束更新幅度（信任域 / clipping）
- GSPO 相比 GRPO 做了哪些优化，为什么在 MoE 上更好
- 是否存在两个 MDP 奖励函数或状态转移不同，但最优策略相同
- 大模型训练里的并行策略（数据并行、模型并行等）
- 十几万 token 超长文本任务，现有并行策略不够时还能做什么

---

## 3. 高频补充问法

## RLHF / 对齐
- PPO、DPO、GRPO、DAPO、GSPO 的核心目标、公式、差异
- 为什么 PPO 要 actor-critic，为什么 GRPO 可以去掉 critic
- DPO 的 `\pi_ref` 起什么作用
- reward 设计：rule-based、model-based、结果奖励、中间奖励
- reward hacking 出现场景与缓解
- 长 CoT 下 token-level / sequence-level 聚合的利弊
- 直接 RL、先 SFT 再 RL、SFT + DPO + PPO 的取舍

## Agent / 工具调用
- function call 的数据是怎么构造的
- tool calling 的 prompt 怎么写
- MCP vs function call，MCP server 如何实现
- workflow / agentic / ReAct / multi-agent 的区别
- memory、planning、tool-use 分别怎么做
- 增加 agent 后时延如何变化，如何量化

## 评测 / 拟人性 / 搜索
- 没有标准答案时如何评测
- benchmark 的构成、采样、人工评测和 model-based 评测
- 拟人性、主动性、推动性如何定义和构建
- 低质量网页、幻觉、多轮对话失真如何缓解
- embedding 与 reranker 的边界、召回与重排的分工

## Infra / 性能
- vLLM、SGLang、DeepSpeed、Megatron 的定位和差异
- dp / tp / pp 怎么选
- rollout 显存和训练显存怎么估
- 首字延迟、全链路延迟怎么测与优化
- RAG 建库、切分、索引、存储与多模态扩展

---

## 4. 建议的复习优先级

### 第一优先级：必须熟
- PPO / DPO / GRPO / DAPO / GSPO
- DPO 数据构造、function call 数据构造
- 奖励设计、reward hacking、GRPO 稳定性
- Agent / workflow / 多 agent / tool-use
- 无 golden answer 的评测、benchmark 设计
- 检索召回、embedding / reranker、幻觉缓解
- 项目中的指标、耗时、首字延迟、上线和 oncall

### 第二优先级：必须懂
- GAE、critic 更新、importance sampling、clipping、KL
- vLLM、SGLang、DeepSpeed、Megatron
- InfoNCE、AUC / GAUC、PLE、语义 ID
- R1、LLaMA 3、MLA、线性注意力

### 第三优先级：可作为加分项
- MCP、A2A、AutoGen、RL4Agent
- 多模态 RAG、OCR、Qwen3-VL、图文检索
- Java / Linux / server / infra 细节
- 行业方向、近期论文、技术趋势

---

## 5. 后续可继续追加的格式

后面如果你还要补新面经，可以继续按下面模板往这个文档里加：

```md
## 公司名 / 岗位名

### 一面
- 题目 1
- 题目 2

### 二面
- 题目 1
- 题目 2

## 高频主题补充
- 某个新主题
```

