<h1 align="center">博弈论基础 Skill</h1>

<p align="center">中文 | <a href="README.en.md">English</a></p>

一套可直接使用的 AI skill 工具包——把罗伯特·吉本斯《博弈论基础》（A Primer in Game Theory）里的博弈建模与均衡求解方法，蒸馏成 19 张可单独触发、也可组合调用的能力卡。

它不是原书摘要，也不是读后感，而是把书中可复用的方法论拆成可触发、可执行、可测试的 skill 模块。

## 这套 skills 能解决什么问题

- 面对"竞争对手降价、管理层承诺、大股东与散户"这类多方互动，先说不清它属于哪一类博弈，就直接套结论——判错象限，后面的分析全部作废
- 一份行业自律价、限产默契、供应商互惠安排能不能守住，只能凭感觉；算不出贴现因子门槛，也分不清"守不住"是惩罚不可信，还是对方本来就没打算守
- 分不清哪些威胁、承诺、政策表态是可信的——"业绩不达标就换高管""未来三年不减持"，到了执行节点还成立吗
- 回购、增持、股利、增发这些公告，判断不了是真信号还是空谈：弱公司模仿它的成本到底是多少，为什么分离信号看起来总是"过度"
- 大宗议价、做市报价明明有共赢空间却谈崩，说不清是人品问题还是信息租金保护下的结构性损失
- 路演、业绩指引、调研沟通里"说了很多但没有信息"，是诚信问题，还是利益结构决定的必然结果

## 蒸馏了什么

19 张能力卡，按"先判类、再按 2×2 象限选工具、最后处理信息与可信性"的顺序组织：

- **判类与建模地基**：`game-type-classifier`（博弈类型判定与均衡概念选择）、`normal-form-modeling`（标准式建模三要素）、`extensive-form-modeling`（扩展式表述与博弈树建模：五要素、信息集与时序互动）
- **完全信息静态：求解与清理**：`iesda-procedure`（重复剔除严格劣战略程序）、`nash-equilibrium-solver`（纳什均衡求解程序：一阶条件法＋划线法＋混合无差异法）、`mixed-strategy-reinterp`（混合战略的正确解读：对手的不确定性与净化）
- **完全信息动态：可信性**：`backward-induction`（逆向归纳法：完全且完美信息动态博弈的回推求解）、`subgame-perfection-check`（子博弈精炼纳什均衡判定与不可置信威胁排除）、`commitment-credibility`（承诺与威胁的可信性分析：先动优势与时间一致性）
- **重复博弈与激励结构**：`repeated-game-cooperation`（重复博弈合作可持续性判定：触发战略与贴现因子门槛）、`incentive-schemes`（激励结构两类模板：锦标赛与效率工资）
- **不完全信息静态：类型与机制**：`bayesian-nash-solver`（贝叶斯博弈标准式与贝叶斯纳什均衡求解程序）、`double-auction-linear-eq`（双向拍卖线性均衡与交易损失模板）、`revelation-principle`（显示原理与直接机制搜索压缩）
- **不完全信息动态：信号与声誉**：`pbe-verification`（精炼贝叶斯均衡验证程序：要求 1-4 逐条）、`signaling-equilibrium`（信号博弈三类均衡判定与四应用：分离 / 混同 / 杂合）、`signal-refinement-checklist`（均衡路径外推断的再精炼检查单：信号要求 5/6 与直观标准）、`reputation-mechanism`（KMRW 声誉机制：有限重复博弈中的伪装合作）、`cheap-talk-info-transmission`（空谈博弈的信息传递条件：Crawford-Sobel 分段交流）

## 两种打包模式：single 与 pack

同一套 19 张能力卡，按两种粒度各编译了一次。两者内容完全相同，区别只在"agent 能看到几个入口"。

| | single（单一入口） | pack（compact pack，多入口） |
|---|---|---|
| 可发现入口 | **1 个**：`game-theory-primer-skill` | **8 个**：1 个来源路由入口 + 7 个已晋级独立 skill |
| 19 张能力卡放在哪 | 全部在入口的 `references/capabilities/` 里，由入口按路由表按需加载 1–2 张 | 7 张高频卡各自独立成 skill；其余 12 张仍在 router 的 `references/` 里 |
| 触发方式 | 只有入口的 description 参与匹配，进入后靠路由表分流 | 7 张高频能力可被 description 直接命中，少一跳 |
| 升级维护 | 替换 1 个目录 | 替换 8 个目录 |

pack 里被晋级为独立 skill 的 7 张卡：

- `game-type-classifier` — 博弈类型判定与均衡概念选择
- `nash-equilibrium-solver` — 纳什均衡求解程序
- `backward-induction` — 逆向归纳与不可置信威胁识别
- `subgame-perfection-check` — 子博弈精炼判定与不可置信威胁排除
- `repeated-game-cooperation` — 重复博弈合作可持续性与贴现因子门槛
- `pbe-verification` — 精炼贝叶斯均衡要求 1-4 验证
- `signaling-equilibrium` — 信号博弈分离 / 混同 / 杂合判定

### 该装哪一种

按你的工作方式选，**只装一种**：

| 你的工作方式 | 推荐 | 原因 |
|---|---|---|
| 用 DSH / Codex / Claude Code 等有 skills 目录，希望列表干净 | single | 只占 1 个入口，能力一张不少 |
| 日常问题高度集中在"这是什么博弈 / 均衡怎么解 / 威胁可信吗 / 默契守得住吗 / 这个公告是不是信号" | pack | 这 7 类正是被晋级的独立 skill，能直接命中 |
| 要分发给多个 agent 或团队，各自按需取用 | pack | 可以只装其中几个独立 skill，不必整包 |
| 只想装一次、不想维护多个目录 | single | 升级时只替换 1 个目录 |

> 两版由同一个 Bundle 编译，能力内容一致。**同时安装会重复触发**，请只装一种。

## 效果示例

### 示例 1：行业价格默契还能撑多久

**用户问题**

"两家寡头这几年价格一直很稳，没人先降价。这种默契还能撑多久？"

**skill 如何判断**

- `game-type-classifier`：先过两问——收益函数是不是共同知识（完全 / 不完全），行动有没有先后且后行者可观察（静态 / 动态）。每期同时定价、反复打交道，落进"完全信息重复博弈"，不该按一次性价格博弈处理
- `repeated-game-cooperation`：写出阶段博弈与利润三元组（合谋 πm/2、背离 πd、阶段纳什 πc），套触发战略条件 (πm/2)/(1−δ) ≥ πd + δπc/(1−δ)。古诺结构下解出 δ ≥ 9/17
- 同一张卡接着查惩罚强度：9/17 只是"永久回到阶段纳什产量"这一种惩罚的门槛，书里同时给出阿布勒式胡萝卜加大棒在 δ = 1/2 就能支撑垄断产量
- `subgame-perfection-check`：核对惩罚在执行节点是否仍最优、事后会不会被重新谈判推翻

**最终回答示例**

> 先定性：这是完全信息重复博弈，不是一次性的价格博弈。若按书里的古诺三元组，触发战略下合作能自我维持的门槛是 δ ≥ 9/17 ≈ 0.53。但书里的 δ 是外生参数，它没告诉你现实中的"耐心"怎么折算成 δ——接单节奏、现金储备、声誉价值只能当代理变量，取多少必须你自己定并写进判断，这一步没有标准答案。而且 9/17 不是唯一答案：换成更严厉的可信惩罚（书里的两面战略），δ = 1/2 也能撑住合谋，所以"δ 低于 9/17 就一定打价格战"是错误推论——下"默契守不住"之前必须先核惩罚强度。最后还要过再谈判检验：如果惩罚期对双方都更差、事后能重谈，这个威胁本身会被推翻。结论按三档给：δ 明显高于门槛且惩罚可信 → 默契可持续；临界 → 看谁最有偏离动机（πd − x 最大的那一方最脆弱）；明显低于门槛 → 短视竞争是常态。

### 示例 2：回购是真信号，增发是不是利空

**用户问题**

"一家公司账上现金充裕，宣布大额回购；另一家负债很高却宣布增发。回购算可信信号吗？增发是不是利空？"

**skill 如何判断**

- `signaling-equilibrium`：先建信号博弈五要素（发送者 / 接收者 / 类型与先验 / 信号集 / 行动集与双方收益），再问关键一问——**弱公司模仿它的成本是什么**。注销式回购＋溢价＋长期锁定是真金白银且摊薄未来财务弹性，弱公司模仿代价高；"回购意向 / 增持计划"这类无成本表态接近空谈
- 单交叉检验：成本必须类型依存（低类型发同一信号的成本更高），否则分离不可能，只能考虑混同或杂合
- 分离必扭曲：分离信号的水平由低类型的不模仿约束决定，必然高于完全信息下的最优——所以"恰到好处"的信号反而可疑
- `signaling-equilibrium` 的 Myers-Majluf 分支：股权融资按平均质量定价，高利润类型出让份额等于补贴低利润类型，绩优公司因此回避股权、转向债务或内部资金
- `signal-refinement-checklist`：信号博弈的均衡常常多重，用信号要求 5/6 与直观标准筛掉那些依赖随意路径外推断的候选

**最终回答示例**

> 判断顺序不是"回购 = 利好"，而是先问弱公司模仿这笔回购的成本是多少。如果只是公告里一句回购意向、没有金额约束和锁定安排，模仿成本接近零，那它在均衡里只会是混同信号，市场无法据此区分类型。书里没有给"回购金额多大才算可信"的阈值——这个量级要你按公司的现金流、融资能力和回购的锁定条款自己定义并声明，别把某个百分比当成书上写的判据。还要注意分离必扭曲：能起区分作用的信号一定"过度"，超过当期最优规模才构成低类型不愿模仿的门槛，所以"回购规模太夸张"不能直接读作非理性。增发那边是 Myers-Majluf 的均衡推论：股权融资要按平均质量定价，高利润类型出让股份等于补贴低利润类型，于是绩优公司转向债务或内部资金，增发公告的负面反应是均衡属性，不是市场失灵。最后，同一份公告往往能支撑多组均衡，先跑再精炼检查单，把依赖"市场见到没回购就一定认为是坏公司"这类随意推断的版本剔掉，剩下的才是条件性主情景。

## 这些 skill 是怎么生成出来的

这套 skill 使用 **[cangjie-skill](https://github.com/kangarooking/cangjie-skill)** 的 RIA-TV++ 流水线生成，整个流程分六个阶段：

1. **整书理解（Adler 分析）**——用 Mortimer Adler 的分析阅读法，对全书做结构、解释、批判、应用四步拆解
2. **并行提取**——同时派多个专项提取器（框架、原则、案例、反例、术语），从原文中提取候选方法论单元
3. **三重验证筛选**——每个候选必须通过三项检验：书内至少有 2 处独立佐证（跨域）、能回答书中未明说的新问题（预测力）、不是常识（独特性）
4. **RIA++ 构造**——按 R（原文引用）/ I（用自己的话重写）/ A1（书中案例）/ A2（未来触发场景）/ E（可执行步骤）/ B（边界与盲点）六个维度结构化
5. **Zettelkasten 链接**——找出能力卡之间的依赖、对比、组合关系，生成能力索引与路由表
6. **触发与输出测试**——为每张卡设计触发盲测题（含诱饵题：该触发时要触发，不该触发时要沉默）与输出评测场景，未通过的卡回炉重做，回炉后再做回归验证

这本书的特点也影响蒸馏：它是 1992 年的研究生教科书，方法论边界很清楚——只处理完全 / 不完全信息 × 静态 / 动态四类博弈，且要求收益函数能写出来。所以每张卡的 B 段都写明了"什么时候不该用"，能力卡的 A2 段另附投资场景映射（编译时补充，不是原书内容）。

## 测试与验证

本仓库连生成过程的测试材料一起发布：`evals/test-prompts.json` 是 24 条触发、诱饵、路由与边界用例，`evals/blindtest-A.md`、`evals/blindtest-B.md` 是两组盲测记录，`evals/skill-list-for-blindtest.md` 是盲测时只给卡片名与描述的清单，`evals/output-evals/` 下是 9 个实测任务，`evals/test-results.md` 是逐项评分结果。

- **触发精度**：7 个晋级卡独立盲测，7 / 7 命中
- **诱饵测试**：3 / 3 通过（容错为 0）——纯数据查询不激活任何卡，多对手场景先判类而不直接上单点工具
- **路由可达性**：12 张 router 卡，12 / 12 命中目标卡
- **输出实测**：9 个代表任务（含边界与缺输入场景）全部通过；其中 1 处是任务设计问题被实测员纠正并记录，不是卡内公式错误
- **计划 24 + 9 = 33 条，完成 33 条**。需要如实说明的缺口：12 张 router 卡以"盲测可达 + 公式核对"为准，没有逐一做完整实测任务（成本考量）；7 张晋级卡全部做了实测
- **盲测环境**：独立盲测 sub-agent 干净上下文，宿主 ZCode（GLM-5.3-Flash 系），日期 2026-10-28；材料原样发布，包含记录在案的缺口

## 仓库结构

```text
game-theory-primer-skill/
├── README.md                      ← 你正在看的
├── README.en.md                   ← English version
├── LICENSE                        ← MIT
├── BOOK_OVERVIEW.md               ← 整书理解（Adler 四步拆解，阶段 0 产出）
├── verified.md                    ← 19 个能力单元的三重验证结论
├── single/                        ← 单一入口模式
│   └── game-theory-primer-skill/
│       ├── SKILL.md               ← 入口：触发条件 + 路由表 + 加载规则
│       ├── BUILD_MANIFEST.json    ← 编译清单与文件哈希
│       └── references/
│           ├── overview.md        ← 整书概览
│           ├── capability-index.md  ← 完整意图与关键词索引
│           ├── cheatsheet.md      ← 决策规则速查
│           ├── glossary.md        ← 术语表
│           └── capabilities/      ← 19 张能力卡
├── pack/                          ← 多入口模式（compact pack）
│   ├── BUILD_MANIFEST.json
│   ├── capability-destinations.json
│   ├── gibbons-game-theory-router/
│   │   ├── SKILL.md               ← 来源路由入口
│   │   └── references/            ← 19 张卡 + 索引，供 router 内部调用
│   ├── game-type-classifier/
│   │   └── SKILL.md
│   ├── nash-equilibrium-solver/
│   │   └── SKILL.md
│   ├── backward-induction/
│   │   └── SKILL.md
│   ├── subgame-perfection-check/
│   │   └── SKILL.md
│   ├── repeated-game-cooperation/
│   │   └── SKILL.md
│   ├── pbe-verification/
│   │   └── SKILL.md
│   └── signaling-equilibrium/
│       └── SKILL.md
└── evals/                          ← 触发盲测与输出实测记录
    ├── test-results.md             ← 逐项评分与缺口说明
    ├── test-prompts.json           ← 24 条触发 / 诱饵 / 路由 / 边界用例
    ├── blindtest-A.md              ← A 组盲测（触发 + 诱饵）
    ├── blindtest-B.md              ← B 组盲测（路由）
    ├── skill-list-for-blindtest.md ← 盲测材料：仅卡名与描述
    └── output-evals/
        ├── C-cournot.md
        ├── C-trigger-threshold.md
        ├── C-bargaining.md
        ├── D-spence.md
        ├── D-beer-hotdog.md
        ├── D-pbe.md
        ├── E-classify.md
        ├── E-double-auction.md
        └── E-incentive.md
```

## 如何使用

先把仓库克隆下来：

```bash
git clone https://github.com/raphael-y7/game-theory-primer-skill.git
```

### 装 single（推荐先试这个）

```bash
# macOS / Linux
cp -r game-theory-primer-skill/single/game-theory-primer-skill ~/.agents/skills/
```

```powershell
# Windows
Copy-Item -Recurse .\game-theory-primer-skill\single\game-theory-primer-skill "$env:USERPROFILE\.agents\skills\"
```

### 装 pack

只复制含 `SKILL.md` 的目录，不要把 `pack/` 下的两个 json 一起拷进 skills 目录：

```bash
# macOS / Linux
cd game-theory-primer-skill/pack
cp -r gibbons-game-theory-router \
      game-type-classifier \
      nash-equilibrium-solver \
      backward-induction \
      subgame-perfection-check \
      repeated-game-cooperation \
      pbe-verification \
      signaling-equilibrium ~/.agents/skills/
```

```powershell
# Windows
$pack = ".\game-theory-primer-skill\pack"
$dest = "$env:USERPROFILE\.agents\skills"
@('gibbons-game-theory-router','game-type-classifier','nash-equilibrium-solver','backward-induction','subgame-perfection-check','repeated-game-cooperation','pbe-verification','signaling-equilibrium') |
  ForEach-Object { Copy-Item -Recurse -LiteralPath (Join-Path $pack $_) -Destination $dest }
```

> `~/.agents/skills` 是 DSH 的 skill 目录；用别的 agent 时换成它自己的 skills 目录即可（例如 Claude Code 是 `~/.claude/skills`）。

### 怎么确认装好了

装完问一句"两家寡头的价格默契守不守得住，贴现因子门槛怎么算"，看 agent 是否直接进入重复博弈的门槛计算流程（阶段博弈三元组、δ 门槛、惩罚强度核对），而不是给你一段泛泛的行业竞争分析。装的是 single 时，它会先读入口再按路由表进能力卡；装的是 pack 时，对应能力会被直接命中。

## 来源

- 《博弈论基础》罗伯特·吉本斯 著
- 全书蒸馏，共产出 19 张能力卡

## 声明

本仓库只发布蒸馏后的 skill、索引与规则速查材料，不包含原书 PDF、EPUB、OCR 文件、截图或全书转写稿。能力卡中出现的原文引用仅用于标注方法论出处和保持可审计性。

书中所有数字判据（贴现因子门槛 9/17、囚徒困境的 1/4、拍卖出价折价、锦标赛奖金差、双向拍卖的 1/4 成交门槛等）都是特定函数形式下的模型解——线性需求、均匀分布、风险中性之类的前提一换，数值就不自动平移，原书也未提供统计回测背书。使用时需按自己的场景重算并声明所用假设。本仓库内容不构成投资建议。


## License

[MIT](./LICENSE)

