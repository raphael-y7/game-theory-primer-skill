# verified.md — 阶段1.5 三重验证整合（博弈论基础）

> 详细判定见 candidates/verified-frameworks.md、verified-principles.md、verified-cases-ce-gloss.md（逐条核验，source_quote 全部逐字命中转写分块）。

## 判定总览

| 候选池 | 条数 | verified | reference | needs_review | rejected | 备注 |
|---|---|---|---|---|---|---|
| frameworks（fa16+fb24+fc16） | 56 | 56 | 0 | 0 | 0 | 跨分片重复按下方单元合并 |
| principles（pa22+pb31+pc32） | 85 | 83 | 2（pc21,pc27→并入相邻单元） | 0 | 0 | 3处抄录错误已修正（pa05/pb18/pc18） |
| cases（c01-c42） | 42 | 42 | 0 | 0 | 0 | 全部 worked_example；c42 类型归属已订正 |
| counter-examples（ce01-ce26） | 26 | 26 | 0 | 0 | 0 | ce08 章节号已订正（2.2.A→2.2.C） |
| glossary（g01-g42） | 42 | 42 | — | 0 | 0 | 2处定义原话校订；作为GLOSSARY素材不参与skill化 |

## 单元合并设计（候选 → 19个原子能力单元）

| # | capability slug | 吸收候选（主题） | 主要task |
|---|---|---|---|
| 1 | game-type-classifier | fa类型判定+四均衡概念递进关系 | task-01 |
| 2 | normal-form-modeling | 标准式三要素+建模程序（fa/pa） | task-02 |
| 3 | iesda-procedure | 严格劣战略剔除+逐层理性假设（fa/ce） | task-03 |
| 4 | nash-equilibrium-solver | NE定义(NE)式+2×2混合公式+猜硬币/性别战算例（fa/pa/c） | task-03 |
| 5 | mixed-strategy-reinterp | 混合战略=对手不确定性（1.3.A+3.2.A） | task-08 |
| 6 | backward-induction | 逆向归纳程序（fb） | task-04 |
| 7 | extensive-form-modeling | 扩展式五要素+信息集（fb） | task-02 |
| 8 | subgame-perfection-check | 子博弈精炼判定+不可置信威胁排除（fb/ce） | task-04 |
| 9 | commitment-credibility | 斯塔克尔贝里先动优势+时间一致性货币政策（fb/pb） | task-09 |
| 10 | repeated-game-cooperation | 触发战略+门槛δ（囚徒1/4、古诺9/17、通用式）+无名氏定理（fb/pb） | task-05 |
| 11 | incentive-schemes | 锦标赛β公式+效率工资条件（fb/pb） | task-13 |
| 12 | bayesian-nash-solver | 贝叶斯博弈标准式+BNE定义+拍卖出价（fa/pa） | task-06 |
| 13 | double-auction-linear-eq | 双向拍卖线性均衡+交易区间（fa/pa） | task-06 |
| 14 | revelation-principle | 显示原理+直接机制（fa/pa） | task-12 |
| 15 | pbe-verification | 精炼贝叶斯均衡要求1-4验证（fc/pc） | task-07 |
| 16 | signaling-equilibrium | 信号博弈分离/混同/杂合判定+斯彭斯+资本结构+货币（fc/pc） | task-07 |
| 17 | signal-refinement-checklist | 信号要求5/6+直观标准检查单（fc/pc） | task-07 |
| 18 | reputation-mechanism | KMRW声誉/伪装合作（fc/pc） | task-10 |
| 19 | cheap-talk-info-transmission | 空谈博弈分区条件（fc/pc） | task-11 |

## 覆盖缺口
- task-13 由单元11承担；task-01→单元1；task-08→单元5；task-10→单元18；task-11→单元19；task-12→单元14。13项任务全部有单元对应，无未解释遗漏。
- 原书纯证明性附录（1.1.C、2.3.B、3.2.B、4.3.C）作为 reference 素材保留在转写稿，不编译为 active 能力（见 references.md）。

## 覆盖审计基准对照（coverage-audit.md 摘要）
- 13项原书关键任务 → 有候选且去向明确：13/13。
- 全量扫描型候选（framework/principle）覆盖全部小节；case 覆盖全部应用节；反例覆盖可信性/精炼/多重均衡等全书警告点。
- 待核查项（needs_review）：0。
