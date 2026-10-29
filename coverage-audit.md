# coverage-audit.md — 覆盖审计（阶段1.5）

基准：BOOK_OVERVIEW.md 的13项原书关键任务（独立于候选池生成）。

| task_id | 任务 | 候选去向 | 判定 |
|---|---|---|---|
| task-01 | 判定博弈类型、选均衡概念 | 单元1 game-type-classifier | 有候选 |
| task-02 | 标准式/扩展式建模 | 单元2 normal-form-modeling、单元7 extensive-form-modeling | 有候选 |
| task-03 | 剔除劣战略+纳什均衡求解 | 单元3 iesda-procedure、单元4 nash-equilibrium-solver | 有候选 |
| task-04 | 子博弈精炼+不可置信威胁 | 单元6 backward-induction、单元8 subgame-perfection-check | 有候选 |
| task-05 | 重复博弈合作可持续性 | 单元10 repeated-game-cooperation | 有候选 |
| task-06 | 贝叶斯纳什均衡（拍卖/双向拍卖） | 单元12 bayesian-nash-solver、单元13 double-auction-linear-eq | 有候选 |
| task-07 | 信号博弈均衡与可信性 | 单元15 pbe-verification、单元16 signaling-equilibrium、单元17 signal-refinement-checklist | 有候选 |
| task-08 | 混合战略的市场含义 | 单元5 mixed-strategy-reinterp | 有候选 |
| task-09 | 承诺可信度/时间一致性 | 单元9 commitment-credibility | 有候选 |
| task-10 | 声誉与伪装合作 | 单元18 reputation-mechanism | 有候选 |
| task-11 | 空谈信息传递条件 | 单元19 cheap-talk-info-transmission | 有候选 |
| task-12 | 显示原理/机制设计 | 单元14 revelation-principle | 有候选 |
| task-13 | 激励结构（锦标赛/效率工资） | 单元11 incentive-schemes | 有候选 |

补充扫描结论：
- 应用节（1.2.A-D、2.1.B-D、2.2.B-D、2.3.C-E、3.2.A-C、4.2.B-D、4.3.A-C）全部有 case 候选（42条 worked_example）。
- 作者警告点（不可置信威胁、IESDA预测失灵、多重均衡、挤提恐慌、时间不一致、无交易损失、伪信号均衡）全部有反例候选（26条）。
- 附录纯证明（1.1.C/2.3.B/3.2.B/4.3.C）与习题/参考文献 → reference（不编译 active）。
- 未解释遗漏：无。待核查：无。
