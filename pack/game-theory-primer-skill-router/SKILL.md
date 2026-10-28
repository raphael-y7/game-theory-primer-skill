---
name: game-theory-primer-skill-router
description: |
  吉本斯《博弈论基础》来源路由入口：按任务（建模/求解/动态可信性/重复博弈/不完全信息/信号/声誉/激励/机制设计）把请求路由到19张能力卡；也承担查术语（GLOSSARY 42词条）与定位原书章节（合并转写稿）。
metadata:
  cangjie.generated-by: cangjie-tools v2.5.0
  cangjie.variant: router
  cangjie.bundle-id: bundle.gibbons-game-theory
  cangjie.capability-count: 19
  cangjie.entrypoint-count: 8
---
# 博弈论基础（A Primer in Game Theory） — 来源路由入口（compact pack）

## 触发与不触发

**适用**：与本书能力域相关的咨询与任务（见下方路由表的意图列）。
**不适用**：
- 行为博弈与实验经济学偏离（1992年成书未覆盖）
- 需要真实收益函数数据而只有定性描述的场景（建模前先问，不代拟收益）
- 均衡之外的动态调整过程（学习/演化/高频微观结构）

## 核心原则（常驻速览，概览类问题读到这里即可回答）

1. 先判博弈类型（信息×时序两问）再选均衡概念，判错象限全套结论失效
2. 均衡是互相最优反应的稳定点，是条件性剧本而非点预测；多重均衡时用再精炼收敛
3. 动态博弈中只有可信的威胁与承诺起作用（子博弈精炼剔除不可置信行为）
4. 长期关系中合作能否自我维持由贴现因子门槛决定（触发战略条件）
5. 信号的可信性来自不同类型模仿成本的差异（单交叉），分离必扭曲
6. 限完全/不完全信息静态与动态博弈的教科书模型框架，收益函数须可写出

## 能力路由（先读本表，按意图加载 1 张能力卡）

| 用户意图 | 先读 | 补读/备注 |
|---|---|---|
| 判定互动场景的博弈类型；选择匹配的均衡概念；校验分析所用均衡概念与场景是否错配 | references/capabilities/game-type-classifier.md | 已晋级为独立 Skill `game-type-classifier`（已安装时优先直接使用；本卡仅作原文与背景补充） |
| 把语言描述的互动写成标准式；检查战略空间与收益函数的完备性；判别囚徒困境式收益结构 | references/capabilities/normal-form-modeling.md | references/capabilities/nash-equilibrium-solver.md、references/capabilities/iesda-procedure.md、references/capabilities/game-type-classifier.md、references/capabilities/extensive-form-modeling.md |
| 剔除严格劣战略缩小博弈；核查逐层理性共同知识假设；判断IESDS预测力是否足够并升级求解 | references/capabilities/iesda-procedure.md | references/capabilities/nash-equilibrium-solver.md、references/capabilities/game-type-classifier.md、references/capabilities/normal-form-modeling.md |
| 求连续选择变量博弈的纳什均衡；用划线法求两人有限博弈的纯战略NE；用无差异法求混合战略均衡概率；检验协议是否为纳什均衡 | references/capabilities/nash-equilibrium-solver.md | 已晋级为独立 Skill `nash-equilibrium-solver`（已安装时优先直接使用；本卡仅作原文与背景补充） |
| 解读对手无规律行为是噪音还是均衡性质；从混合均衡概率反推对手收益/信息结构；校准己方策略消除可被利用的规律 | references/capabilities/mixed-strategy-reinterp.md | references/capabilities/nash-equilibrium-solver.md、references/capabilities/bayesian-nash-solver.md |
| 求完全且完美信息动态博弈的逆向归纳解；识别并剔除不可置信威胁；判定先动优势是否成立及大小 | references/capabilities/backward-induction.md | 已晋级为独立 Skill `backward-induction`（已安装时优先直接使用；本卡仅作原文与背景补充） |
| 把语言描述的时序性互动形式化为博弈树；依据信息集结构选择后续解概念；区分行动与完整应变计划（战略） | references/capabilities/extensive-form-modeling.md | references/capabilities/backward-induction.md、references/capabilities/subgame-perfection-check.md、references/capabilities/pbe-verification.md、references/capabilities/game-type-classifier.md |
| 判定纳什均衡/威胁是否子博弈精炼；对两阶段动态博弈执行先解后段再替入程序；把含同时行动环节的动态博弈正确路由到子博弈精炼 | references/capabilities/subgame-perfection-check.md | 已晋级为独立 Skill `subgame-perfection-check`（已安装时优先直接使用；本卡仅作原文与背景补充） |
| 评估一项宣布是否锁定行为且事后会被兑现；判断规则vs相机抉择哪种可信并识别锁定机制；计算支撑承诺的贴现因子门槛与参数敏感方向 | references/capabilities/commitment-credibility.md | references/capabilities/subgame-perfection-check.md、references/capabilities/backward-induction.md、references/capabilities/signaling-equilibrium.md、references/capabilities/repeated-game-cooperation.md |
| 判断行业默契/共谋/长期互惠能否自我维持并算贴现因子门槛；把现实参数映射为δ做合作可持续性三档判定；核查惩罚强度与再谈判漏洞 | references/capabilities/repeated-game-cooperation.md | 已晋级为独立 Skill `repeated-game-cooperation`（已安装时优先直接使用；本卡仅作原文与背景补充） |
| 用锦标赛公式设计/解读排名考核与相对业绩薪酬；用不偷懒条件判断高薪+严淘汰均衡是否可持续；解读管理层薪酬结构的激励含义与失效条件 | references/capabilities/incentive-schemes.md | references/capabilities/subgame-perfection-check.md、references/capabilities/repeated-game-cooperation.md |
| 把私人信息场景写成G={A;T;p;u}并逐类型建立期望收益max问题；用类型依赖FOC联立求BNE；对竞价场景做出价折算与存在性/多重性前置检查 | references/capabilities/bayesian-nash-solver.md | references/capabilities/signaling-equilibrium.md、references/capabilities/mixed-strategy-reinterp.md、references/capabilities/pbe-verification.md、references/capabilities/double-auction-linear-eq.md、references/capabilities/game-type-classifier.md |
| 推导或核对双边报价机制的线性均衡并算成交门槛；用交易区间vs有效区间差额量化交易损失；映射做市价差/大宗议价/并购谈判该成未成的结构性解释 | references/capabilities/double-auction-linear-eq.md | references/capabilities/bayesian-nash-solver.md、references/capabilities/revelation-principle.md |
| 评估一条规则/制度下参与者会不会如实申报；检验申报类机制的IC不等式与参与约束；用显示原理把否定性结论推广到一切机制 | references/capabilities/revelation-principle.md | references/capabilities/bayesian-nash-solver.md、references/capabilities/double-auction-linear-eq.md |
| 验证候选"战略+市场推断"剧本是否自洽；分析偏离/公告事件后推断应如何更新；标注哪些结论依赖随意指定的路径外推断 | references/capabilities/pbe-verification.md | 已晋级为独立 Skill `pbe-verification`（已安装时优先直接使用；本卡仅作原文与背景补充） |
| 判定公告/行为是否构成可信分离信号；求解两类型信号博弈四候选均衡并核IC与单交叉条件；用Myers-Majluf逻辑解读股权融资与增发折价 | references/capabilities/signaling-equilibrium.md | 已晋级为独立 Skill `signaling-equilibrium`（已安装时优先直接使用；本卡仅作原文与背景补充） |
| 判定混同/杂合信号均衡能否通过信号要求5/6检验；在多重信号均衡清单中筛出条件性主情景；对公告执行"哪类公司发它是均衡劣的"直观标准检验 | references/capabilities/signal-refinement-checklist.md | references/capabilities/signaling-equilibrium.md、references/capabilities/pbe-verification.md、references/capabilities/cheap-talk-info-transmission.md |
| 判定长期关系中声誉型合作能否成为均衡；定位对手处于伪装期还是末段并输出分期行为剧本；区分声誉型合作与触发战略承诺型合作 | references/capabilities/reputation-mechanism.md | references/capabilities/repeated-game-cooperation.md、references/capabilities/signaling-equilibrium.md |
| 判定口头表态/指引是空谈还是有成本信号并估计信息含量上限；用偏好分歧档位把管理层沟通折算成至多n段区间；判定沟通失败源于利益结构而非诚信 | references/capabilities/cheap-talk-info-transmission.md | references/capabilities/signaling-equilibrium.md、references/capabilities/signal-refinement-checklist.md |

**非能力类查询**：
- 书名/作者/章节/整书概览 → references/overview.md
- 术语解释 → references/glossary.md
- 决策规则速查（不需要原文依据时） → references/cheatsheet.md
- 完整意图与关键词索引（本表未覆盖的意图先查这里） → references/capability-index.md

## 加载规则

- 每次任务先读本文件，再按路由表加载 **1** 张能力卡；任务明确跨域时最多加载 2 张。
- 概览/书名类问题不加载能力卡，用「核心原则」与 overview.md 回答。
- 路由表与 capability-index.md 都无法命中的意图，明确告知超出本书范围，不要硬套。

## 边界与判停

- 收益函数或类型分布无法合理给出且用户拒绝假设时，停止并说明缺失
- 判定出博弈类型后若用户场景与全部四类都不匹配，停止并声明本入口不适用
- 多重均衡经再精炼仍无法收敛时，输出条件性剧本清单而非强行点预测
