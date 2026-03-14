你现在是一个顶会论文选题合作者。请基于我提供的文献综述，生成 10 个“有 CCF-A 顶会潜力”的 research ideas。

输入说明：
- 文献综述默认放在 `lit/` 目录下。
- 如果我没有额外说明，请优先读取我提供的 `lit/LIT_REPORT_CODEX_ONLY_YYYYMMDD_HHMMSS.md` 或 `lit/LIT_REPORT_CODEX_ONLY_YYYYMMDD_HHMMSS_CN.md`。
- 如果同时提供中英文版本，优先以中文版本做分析，必要时对照英文版核对原始表述。
- 不要基于记忆补全报告里没有的 paper 结论；如果报告证据不足，要明确指出。

要求：
1. 每个 idea 必须来自文献中的“真实冲突、真实缺口或真实 tradeoff”，不能只是换个名字重述已有方法。
2. 每个 idea 必须明确：
   - Problem
   - Core hypothesis
   - Why now
   - Novelty relative to strongest baselines
   - Minimal method
   - Key experiment
   - Main risk
   - Why this could fail
3. 优先生成满足以下特征的 idea：
   - 有清晰争议面
   - 可被强基线击败或验证
   - 有明确可证伪性
   - 能在一个统一实验矩阵中验证
4. 不要生成：
   - 纯工程堆料
   - 仅仅“更大模型/更多数据/更长训练”
   - 没有 evaluation moat 的想法
   - 无法和现有 strongest baseline 区分的想法
5. 对每个 idea 额外打分：
   - Novelty /10
   - Technical depth /10
   - Feasibility /10
   - CCF-A potential /10

最后请输出：
- Top 3 most promising ideas
- 对每个 top idea 给出一句话 thesis statement
- 指出哪个 idea 最适合先做小实验验证

最小可运行输入示例：
- Literature report: `lit/LIT_REPORT_CODEX_ONLY_YYYYMMDD_HHMMSS_CN.md`
- Optional paired English report: `lit/LIT_REPORT_CODEX_ONLY_YYYYMMDD_HHMMSS.md`

执行规则：
- 如果已经给出 `lit/` 下的文献综述路径，就直接开始生成 ideas。
- 如果只给出一个报告，基于该报告完成分析，不要等待额外输入。
