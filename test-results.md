# test-results.md — 阶段4压力测试报告（bundle.gibbons-game-theory v1.0.0）

- 宿主/模型：ZCode（session模型 GLM-5.3-Flash 系），独立盲测 sub-agent 干净上下文
- 日期：2026-10-28
- 用例：audit/test-prompts.json（24条：7触发+3诱饵+12路由可达+2边界）
- 盲测材料：audit/skill-list-for-blindtest.md（仅19卡name+one_liner+description，不给type/expected）
- 判卷对照：blindtest-A.md（A组触发+诱饵）、blindtest-B.md（B组路由）；实测 9 个输出任务文件

## 一、触发精度（7个promoted卡，独立盲测）

| 用例 | 目标卡 | 盲测激活 | 判定 |
|---|---|---|---|
| pA1 | game-type-classifier | game-type-classifier ✓ | 通过 |
| pA2 | nash-equilibrium-solver | nash-equilibrium-solver ✓ | 通过 |
| pA3 | repeated-game-cooperation | repeated-game-cooperation ✓ | 通过 |
| pA4 | signaling-equilibrium | signaling-equilibrium ✓ | 通过 |
| pA5 | pbe-verification | pbe-verification ✓ | 通过 |
| pA6 | backward-induction | backward-induction ✓ | 通过 |
| pA7 | subgame-perfection-check | subgame-perfection-check ✓ | 通过 |

## 二、诱饵测试（容错=0）

| 用例 | 预期 | 盲测 | 判定 |
|---|---|---|---|
| pA8 纯数据查询 | NONE | NONE ✓ | 通过 |
| pA9 多方+不对称"看似复杂"场景 | game-type-classifier（先判类，不用单点工具） | game-type-classifier ✓ | 通过 |
| pA10 三家同时产量+一家成本私人信息（跨卡边界） | bayesian-nash-solver（联动） | bayesian-nash-solver ✓ | 通过 |

## 三、路由可达性（12个router卡）

pB1-pB12 全部命中目标卡（bayesian-nash-solver/double-auction-linear-eq/signal-refinement-checklist/commitment-credibility/reputation-mechanism/cheap-talk-info-transmission/incentive-schemes/normal-form-modeling/extensive-form-modeling/iesda-procedure/mixed-strategy-reinterp/revelation-principle）→ 12/12 通过。

## 四、实际输出评测（9个代表任务，含边界/缺输入场景）

| 任务文件 | 覆盖卡 | 机械核对结果 |
|---|---|---|
| C-cournot.md | nash-equilibrium-solver | q*=(100-10)/3=30、P*=40、π=900；贝特兰德同质p=c=10 ✓ |
| C-trigger-threshold.md | repeated-game-cooperation | 每家22.5、πm/2家=1012.5、πd=1139.06、πc=900、δ≥9/17≈0.529 ✓ |
| C-bargaining.md | backward-induction | s1*=1−δ(1−δs)自相似锚 s*=1/(1+δ)=10/19 ✓ |
| D-spence.md | signaling-equilibrium | e_s=(w差)/c_L=1、低类型IC在e_s处恰无差异、单交叉成立、分离必扭曲 ✓ |
| D-beer-hotdog.md | signal-refinement-checklist | q≥1/2=混同存在条件；直观标准剔除镜像混同（m2）✓ |
| D-pbe.md | pbe-verification | 要求1-4逐条：剧本实为分离均衡、路径上推断由要求3钉死（有效纠偏：用户所称"路径外推断"定位错误）✓ |
| E-classify.md | game-type-classifier | (a)NE (b)PBE (c)BNE (d)PBE ✓ |
| E-double-auction.md | double-auction-linear-eq | pb=41/60、ps=0.650、成交于2/3；损失区间(0,1/4]结构性 ✓ |
| E-incentive.md | incentive-schemes | 奖金差4√π≈7.09（并主动指出任务参数不满足最优条件，最优e*=0.5、差√π）；缺输入场景12项必问清单、不静默代值 ✓ |

- 边界/缺输入场景：E-incentive 任务B 按卡内输入契约先问后算，未静默代值 → 通过。
- 汇总：触发7/7、诱饵3/3、路由12/12、实测9/9（其中1处实测员纠错为任务设计问题已记录，非卡内公式错误）。
- 计划24+9=33，完成33，全部断言通过。
- 未覆盖说明（写入needs-review的缺口）：12张router卡中以盲测可达+公式核对为准，未逐一做完整实测任务（成本考量）；promoted卡全部实测。

## 五、回归集
- 将pA1-pA10、pB1-pB12与9个实测任务全部加入回归集（audit/test-prompts.json即回归基线）。
- 后续修改卡A2/E/B后，须用未参与调优的保留用例重跑（当前无调优记录，首轮全过）。
