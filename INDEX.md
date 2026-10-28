# Skill 地图 — 博弈论基础（A Primer in Game Theory）

19 张能力卡的地图：每张卡的能力 id、slug、中文标题、重要度与打包去向；`also_read` 是卡与卡之间的补读关系，决定了一次分析里第二、第三张卡该读谁。

## 能力总表

| capability_id | slug | 中文标题 | 重要度 | 去向 |
|---|---|---|---|---|
| `cap.gibbons-game-theory.game-type-classifier` | `game-type-classifier` | 博弈类型判定与均衡概念选择 | 关键（critical） | 独立 skill |
| `cap.gibbons-game-theory.normal-form-modeling` | `normal-form-modeling` | 标准式建模三要素 | 高（high） | 路由入口 |
| `cap.gibbons-game-theory.iesda-procedure` | `iesda-procedure` | 重复剔除严格劣战略程序 | 中（medium） | 路由入口 |
| `cap.gibbons-game-theory.nash-equilibrium-solver` | `nash-equilibrium-solver` | 纳什均衡求解程序（一阶条件法＋划线法＋混合无差异法） | 关键（critical） | 独立 skill |
| `cap.gibbons-game-theory.mixed-strategy-reinterp` | `mixed-strategy-reinterp` | 混合战略的正确解读：对手的不确定性与净化 | 中（medium） | 路由入口 |
| `cap.gibbons-game-theory.backward-induction` | `backward-induction` | 逆向归纳法：完全且完美信息动态博弈的回推求解 | 高（high） | 独立 skill |
| `cap.gibbons-game-theory.extensive-form-modeling` | `extensive-form-modeling` | 扩展式表述与博弈树建模：五要素、信息集与时序互动 | 高（high） | 路由入口 |
| `cap.gibbons-game-theory.subgame-perfection-check` | `subgame-perfection-check` | 子博弈精炼纳什均衡判定与不可置信威胁排除 | 关键（critical） | 独立 skill |
| `cap.gibbons-game-theory.commitment-credibility` | `commitment-credibility` | 承诺与威胁的可信性分析（先动优势与时间一致性） | 高（high） | 路由入口 |
| `cap.gibbons-game-theory.repeated-game-cooperation` | `repeated-game-cooperation` | 重复博弈合作可持续性判定（触发战略与贴现因子门槛） | 关键（critical） | 独立 skill |
| `cap.gibbons-game-theory.incentive-schemes` | `incentive-schemes` | 激励结构两类模板：锦标赛与效率工资 | 中（medium） | 路由入口 |
| `cap.gibbons-game-theory.bayesian-nash-solver` | `bayesian-nash-solver` | 贝叶斯博弈标准式与贝叶斯纳什均衡求解程序 | 高（high） | 路由入口 |
| `cap.gibbons-game-theory.double-auction-linear-eq` | `double-auction-linear-eq` | 双向拍卖线性均衡与交易损失模板 | 中（medium） | 路由入口 |
| `cap.gibbons-game-theory.revelation-principle` | `revelation-principle` | 显示原理与直接机制搜索压缩 | 中（medium） | 路由入口 |
| `cap.gibbons-game-theory.pbe-verification` | `pbe-verification` | 精炼贝叶斯均衡验证程序（要求1-4逐条） | 关键（critical） | 独立 skill |
| `cap.gibbons-game-theory.signaling-equilibrium` | `signaling-equilibrium` | 信号博弈三类均衡判定与四应用（分离/混同/杂合） | 关键（critical） | 独立 skill |
| `cap.gibbons-game-theory.signal-refinement-checklist` | `signal-refinement-checklist` | 均衡路径外推断的再精炼检查单（信号要求5/6与直观标准） | 高（high） | 路由入口 |
| `cap.gibbons-game-theory.reputation-mechanism` | `reputation-mechanism` | KMRW声誉机制（有限重复博弈中的伪装合作） | 中（medium） | 路由入口 |
| `cap.gibbons-game-theory.cheap-talk-info-transmission` | `cheap-talk-info-transmission` | 空谈博弈的信息传递条件（Crawford-Sobel分段交流） | 中（medium） | 路由入口 |

共 19 张：7 张 promoted（在 pack 里各自独立成 skill），12 张 router（只在路由入口的 references 里被调用）。

## 依赖关系（also_read）

读一张卡时，若问题跨到相邻能力，按此表补读。右侧一列是该卡在 `bundle/verified.yaml` 里声明的补读清单，顺序即建议阅读顺序。

| 能力 | 补读（also_read） |
|---|---|
| `game-type-classifier` | `normal-form-modeling`、`extensive-form-modeling`、`bayesian-nash-solver`、`signaling-equilibrium`、`nash-equilibrium-solver` |
| `normal-form-modeling` | `nash-equilibrium-solver`、`iesda-procedure`、`game-type-classifier`、`extensive-form-modeling` |
| `iesda-procedure` | `nash-equilibrium-solver`、`game-type-classifier`、`normal-form-modeling` |
| `nash-equilibrium-solver` | `game-type-classifier`、`mixed-strategy-reinterp`、`iesda-procedure`、`normal-form-modeling`、`repeated-game-cooperation` |
| `mixed-strategy-reinterp` | `nash-equilibrium-solver`、`bayesian-nash-solver` |
| `backward-induction` | `extensive-form-modeling`、`subgame-perfection-check`、`commitment-credibility` |
| `extensive-form-modeling` | `backward-induction`、`subgame-perfection-check`、`pbe-verification`、`game-type-classifier` |
| `subgame-perfection-check` | `backward-induction`、`commitment-credibility`、`repeated-game-cooperation`、`extensive-form-modeling`、`incentive-schemes` |
| `commitment-credibility` | `subgame-perfection-check`、`backward-induction`、`signaling-equilibrium`、`repeated-game-cooperation` |
| `repeated-game-cooperation` | `subgame-perfection-check`、`reputation-mechanism`、`nash-equilibrium-solver` |
| `incentive-schemes` | `subgame-perfection-check`、`repeated-game-cooperation` |
| `bayesian-nash-solver` | `signaling-equilibrium`、`mixed-strategy-reinterp`、`pbe-verification`、`double-auction-linear-eq`、`game-type-classifier` |
| `double-auction-linear-eq` | `bayesian-nash-solver`、`revelation-principle` |
| `revelation-principle` | `bayesian-nash-solver`、`double-auction-linear-eq` |
| `pbe-verification` | `signaling-equilibrium`、`signal-refinement-checklist`、`extensive-form-modeling`、`bayesian-nash-solver`、`game-type-classifier` |
| `signaling-equilibrium` | `pbe-verification`、`signal-refinement-checklist`、`bayesian-nash-solver`、`commitment-credibility`、`cheap-talk-info-transmission` |
| `signal-refinement-checklist` | `signaling-equilibrium`、`pbe-verification`、`cheap-talk-info-transmission` |
| `reputation-mechanism` | `repeated-game-cooperation`、`signaling-equilibrium` |
| `cheap-talk-info-transmission` | `signaling-equilibrium`、`signal-refinement-checklist` |

## 加载顺序

1. **先读入口**：single 读 `single/SKILL.md`；pack 读 `pack/game-theory-primer-skill-router/SKILL.md`（命中了 7 个独立 skill 之一时直接读它自己的 SKILL.md）。
2. **按路由表定位 1 张主卡**：入口的意图表把问题映射到一张能力卡，只读那一张。
3. **按 also_read 补 1–2 张**：主卡给出结论后，跨到相邻能力时按上表补读，不要一次加载三张以上。
4. **非能力类查询走旁路**：书名/章节/整书概览读 `references/overview.md`，术语读 `references/glossary.md`，规则速查读 `references/cheatsheet.md`，索引读 `references/capability-index.md`。

> 卡与卡之间不是并列关系：`game-type-classifier` 是全书入口判定，其余 18 张的结论都以它的象限判定为前置输入。
