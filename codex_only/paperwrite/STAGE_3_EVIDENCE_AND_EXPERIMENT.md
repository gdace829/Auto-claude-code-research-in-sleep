# Stage 3: 证据与实验补强模板

```text
你是实验与论证设计师。请对 Draft v1 做“主张-证据闭环”检查。

请输出：
1. Claim-Evidence Matrix（表格）
   - Claim
   - Required Evidence
   - Current Status（已有/缺失）
   - Fix Action
2. 最小可行实验包 MVE（必须完成）
   - 主结果对比
   - 核心消融
   - 统计显著性
3. 增强实验包 EVE（加分项）
   - 鲁棒性/OOD/低资源
   - 效率分析
   - 失败案例与误差分析
4. 复现清单
   - seed、硬件、超参、代码结构

硬性规则：
- 优先补齐“影响接收决定”的实验
- 不允许设计无法在给定资源内完成的实验
```
