<h1 align="center">博弈论基础 Skill</h1>

<p align="center">中文 | <a href="README.en.md">English</a></p>

一套可直接使用的 AI skill 工具包——把罗伯特·吉本斯《博弈论基础（A Primer in Game Theory）》里的博弈建模与均衡求解方法，蒸馏成 19 张可单独触发、也可组合调用的能力卡。

它不是原书摘要，也不是读后感，而是把书中可复用的方法论拆成可触发、可执行、可测试的 skill 模块。

## 这套 skills 能解决什么问题

- 看到多方互动就想直接给结论，却说不清它属于四类博弈的哪一类——判错象限，后面配的均衡概念整套失效
- 会背纳什均衡的定义，但拿到"两家同时定产""竞拍该出多少价"这类具体场景，不知道第一步该写什么
- 把"威胁""承诺""公开宣布"当成既定事实，没意识到不可置信的威胁在均衡里根本不会发生作用
- 判断行业默契、价格同盟、长期供应关系能不能维持，只会说"看大家守不守规矩"，给不出贴现因子门槛、最脆弱方和参数敏感方向
- 一条回购、增持、增发公告摆在面前，分不清它是真金白银的分离信号，还是零成本的空谈
- 多重均衡摆在一起时，不知道该把哪个当主情景，也说不清自己的结论依赖了哪条路径外推断

## 蒸馏了什么

19 张能力卡，按"先判类建模、再按象限求解、最后回到可信性与机制"的顺序组织：

- **判类与建模（3）**：`game-type-classifier`（博弈类型判定与均衡概念选择）、`normal-form-modeling`（标准式建模三要素）、`extensive-form-modeling`（扩展式表述与博弈树建模）
- **完全信息静态求解（3）**：`iesda-procedure`（重复剔除严格劣战略）、`nash-equilibrium-solver`（纳什均衡三路求解：一阶条件法＋划线法＋混合无差异法）、`mixed-strategy-reinterp`（混合战略的正确解读）
- **动态博弈与可信性（3）**：`backward-induction`（逆向归纳法）、`subgame-perfection-check`（子博弈精炼判定与不可置信威胁排除）、`commitment-credibility`（承诺与威胁的可信性、先动优势与时间一致性）
- **长期关系（2）**：`repeated-game-cooperation`（触发战略与贴现因子门槛）、`reputation-mechanism`（KMRW 声誉机制与伪装合作）
- **不完全信息静态与机制设计（3）**：`bayesian-nash-solver`（贝叶斯博弈标准式与 BNE 求解）、`double-auction-linear-eq`（双向拍卖线性均衡与交易损失）、`revelation-principle`（显示原理与直接机制搜索压缩）
- **不完全信息动态与信号（4）**：`pbe-verification`（精炼贝叶斯均衡要求 1–4 逐条验证）、`signaling-equilibrium`（信号博弈分离/混同/杂合判定）、`signal-refinement-checklist`（路径外推断的再精炼检查单）、`cheap-talk-info-transmission`（空谈博弈的信息传递条件）
- **激励（1）**：`incentive-schemes`（锦标赛与效率工资两类模板）

## 两种打包模式：single 与 pack

同一套 19 张能力卡，按两种粒度各编译了一次。两者内容完全相同，区别只在"agent 能看到几个入口"。

| | single（单一入口） | pack（compact pack，多入口） |
|---|---|---|
| 可发现入口 | **1 个**：`game-theory-primer-skill` | **8 个**：1 个来源路由入口 + 7 个已晋级独立 skill |
| 19 张能力卡放在哪 | 全部在入口的 `references/capabilities/` 里，由入口按路由表按需加载 1–2 张 | 7 张高频卡各自独立成 skill；其余 12 张仍在 router 的 `references/` 里 |
| 触发方式 | 只有入口的 description 参与匹配，进入后靠路由表分流 | 7 个高频能力可被 description 直接命中，少一跳 |
| 升级维护 | 替换 1 个目录 | 替换 8 个目录 |

pack 里被晋级为独立 skill 的 7 张卡：

- `game-type-classifier` — 博弈类型判定与均衡概念选择
- `nash-equilibrium-solver` — 纳什均衡求解程序
- `backward-induction` — 逆向归纳法
- `subgame-perfection-check` — 子博弈精炼判定与不可置信威胁排除
- `repeated-game-cooperation` — 重复博弈合作可持续性判定
- `pbe-verification` — 精炼贝叶斯均衡验证程序
- `signaling-equilibrium` — 信号博弈三类均衡判定

### 该装哪一种

按你的工作方式选，**只装一种**：

| 你的工作方式 | 推荐 | 原因 |
|---|---|---|
| 用 DSH / Codex / Claude Code 等有 skills 目录，希望列表干净 | single | 只占 1 个入口，能力一张不少 |
| 日常问题高度集中在"判类 / 求均衡 / 逆向归纳 / 可信性 / 长期合作 / PBE / 信号" | pack | 这 7 类正是被晋级的独立 skill，能直接命中 |
| 要分发给多个 agent 或团队，各自按需取用 | pack | 可以只装其中几个独立 skill，不必整包 |
| 只想装一次、不想维护多个目录 | single | 升级时只替换 1 个目录 |

> 两版由同一个 Bundle 编译，能力内容一致。**同时安装会重复触发**，请只装一种。

## 效果示例

### 示例 1：行业高价默契能撑多久

**用户问题**

"两个寡头每期都在博弈，想维持高价默契。贴现因子多少以上默契才守得住？给我判断依据。"

**skill 如何判断**

- 先过 `game-type-classifier`：收益函数双方都知道 → 信息完全；每期都能观测到上一期的行动 → 动态。象限是"完全信息动态"，用子博弈精炼；把它当成一次性静态博弈会直接得出"价格战不可避免"的错误结论
- 进 `repeated-game-cooperation`：写出阶段博弈三元组——合谋每家 `πm/2=(a−c)²/8`、单方背离 `πd=9(a−c)²/64`、回到古诺 `πc=(a−c)²/9`，套通用门槛 `δ≥max(di−xi)/(di−ei)`，古诺情形化简为 `δ≥9/17`
- 复核卡内两条边界：一是惩罚强度——"永久回到古诺"不是最严厉的可信惩罚；二是再谈判漏洞——惩罚同时惩罚惩罚者，事后会被推翻时门槛结论作废
- 最后输出三档判定（可持续 / 临界 / 不可持续）＋最脆弱方＋参数敏感方向，不给点预测

**最终回答示例**

> 先把阶段博弈写清楚：合谋每家每期拿 `(a−c)²/8`，你单方背离能拿 `9(a−c)²/64`，撕破脸之后每期只剩古诺的 `(a−c)²/9`。套触发战略条件，门槛是 **δ≥9/17≈0.53**。但这个数只是"永久回到古诺"这一种惩罚下的门槛，不要当成行业的绝对生死线：如果你们能执行更严厉且可信的惩罚（背离后先短期剧烈减产、守罚就恢复合作），门槛会明显下降，δ 不到 0.53 也可能撑住垄断价。所以正确的动作不是问"δ 够不够"，而是先估三个参数——接单节奏（重复频率越高 δ 越大）、资本雄厚度（谁更能熬过惩罚期，弱势方 δ 低、最容易先动手）、声誉价值（未来利润流占比）。谁的 `πd−x` 最大，谁就是最脆弱的环节。最后一句必须带上：这套模型证明的是"合作可以是均衡"，不是"合作一定会实现"；δ 够了只说明背离不划算，具体落哪个均衡还得看焦点与惯例。

### 示例 2：回购公告是真信号还是空谈

**用户问题**

"某公司账上现金充裕却宣布大额回购，另一家负债却宣布增发。回购是真信号吗？怎么判断？"

**skill 如何判断**

- 先过 `game-type-classifier`：管理层知道自己的盈利前景、市场只能看公告后定价 → 不完全信息＋动态 → 精炼贝叶斯均衡，必须把"推断"这个要素引进来
- 进 `signaling-equilibrium`：列四个候选（混同于信号 A、混同于信号 B、两种分离），逐个"贝叶斯定推断 → 求接收者最优反应 → 逐类型查偏离动机 → 补路径外推断"。判定的第一问不是"公告说了什么"，而是"弱公司模仿这个动作的成本是什么"
- 核单交叉：分离的技术前提是低类型模仿同一信号的边际成本更高；成立的话分离水平由低类型 IC 钉死，且分离必扭曲——信号要"浪费"到低类型不愿模仿为止
- 接 `signal-refinement-checklist`：混同/杂合常有多条并存，用信号要求 5/6（直观标准）剔除那些依赖不合情理路径外推断的，剩下的才是条件性主情景

**最终回答示例**

> 回购是不是真信号，不看公告措辞，看弱公司模仿它的成本。注销式回购＋溢价＋长期锁定是真金白银，还摊薄了未来的财务弹性；现金流紧、融资难的公司照抄这一套代价很高，所以分离有可能成立。反过来，"回购意向""增持计划"这类零成本表态，弱公司抄一遍不花一分钱，均衡只能是混同——它和空谈没有区别，别按同一个逻辑解读。至于增发：按 Myers-Majluf 的逻辑，股权融资会逼着高利润类型出让更大份额去补贴低利润类型，所以绩优公司回避股权、转向债务或内部资金是均衡推论；增发公告的负反应、折价越深，说明市场推断发行方是低类型的概率越高（q 高），这是均衡属性，不是市场失灵。最后提醒一句：这类模型经常多条均衡并存，任何"市场会解读为……"的说法，都要先交代它依赖哪条路径外推断。

## 这些 skill 是怎么生成出来的

这套 skill 使用 **[cangjie-skill](https://github.com/kangarooking/cangjie-skill)** 的 RIA-TV++ 流水线生成，整个流程分六个阶段：

1. **整书理解（Adler 分析）**——用 Mortimer Adler 的分析阅读法，对全书做结构、解释、批判、应用四步拆解
2. **并行提取**——同时派多个专项提取器（框架、原则、案例、反例、术语），从原文中提取候选方法论单元
3. **三重验证筛选**——每个候选必须通过三项检验：书内至少有 2 处独立佐证（跨域）、能回答书中未明说的新问题（预测力）、不是常识（独特性）
4. **RIA++ 构造**——按 R（原文引用）/ I（用自己的话重写）/ A1（书中案例）/ A2（未来触发场景）/ E（可执行步骤）/ B（边界与盲点）六个维度结构化
5. **Zettelkasten 链接**——找出能力卡之间的依赖、对比、组合关系，生成能力索引与路由表
6. **触发与输出测试**——为每张卡设计触发盲测题（含诱饵题：该触发时要触发，不该触发时要沉默）与输出评测场景，未通过的卡回炉重做，回炉后再做回归验证

这本 1992 年成书的教科书只覆盖完全/不完全信息 × 静态/动态这四类博弈，蒸馏时也把这条边界写进了每张卡：行为博弈、实验偏离、均衡之外的动态调整过程都明确划在范围之外。

## 测试与验证

本仓库把生成过程的测试材料一起发布：`evals/test-prompts.json` 是触发、诱饵、路由与边界用例，`evals/test-results.md` 是逐项评分报告——包含未覆盖项与纠错记录，不是只留通过记录。

- **触发盲测**：7 个 promoted 卡独立盲测 7 / 7，sub-agent 干净上下文、只给卡名与描述
- **诱饵测试**：容错为 0，3 / 3——纯数据查询不激活任何卡，"看似复杂"的多方场景仍先判类而不直接上单点工具
- **路由可达**：12 个 router 卡 12 / 12，全部命中目标卡
- **输出实测**：9 个代表任务（含边界与缺输入场景）9 / 9，公式逐项机械核对；其中 1 处为任务设计问题，已在报告中标注，不计为卡内错误
- **回归集**：触发、诱饵、路由用例与 9 个实测任务全部并入 `evals/test-prompts.json` 作为回归基线
- **未覆盖**：12 张 router 卡以盲测可达＋公式核对为准，未逐一做完整实测任务

## 仓库结构

```text
game-theory-primer-skill/
├── README.md                      ← 你正在看的
├── README.en.md                   ← English version
├── LICENSE                        ← MIT
├── BOOK_OVERVIEW.md               ← 整书理解（Adler 四步拆解，阶段 0 产出）
├── verified.md                    ← 19 个规范单元的三重验证结论
├── INDEX.md                       ← skill 地图：能力总表 + also_read 依赖 + 加载顺序
├── bundle/                        ← 编译前的规范 Bundle（verified.yaml 是唯一事实源）
│   ├── verified.yaml              ← 19 张能力卡的元数据、判据与去向
│   ├── cards/                     ← 19 张能力卡（R/I/A1/A2/E/B 六段结构）
│   └── book/
│       ├── overview.md            ← 整书概览
│       └── glossary.md            ← 术语表
├── single/                        ← 单一入口模式
│   ├── SKILL.md                   ← 入口：触发条件 + 路由表 + 加载规则
│   ├── BUILD_MANIFEST.json        ← 编译清单与文件哈希
│   └── references/
│       ├── overview.md            ← 整书概览
│       ├── capability-index.md    ← 完整意图与关键词索引
│       ├── cheatsheet.md          ← 决策规则速查
│       ├── glossary.md            ← 术语表
│       └── capabilities/          ← 19 张能力卡
├── pack/                          ← 多入口模式（compact pack）
│   ├── BUILD_MANIFEST.json
│   ├── capability-destinations.json
│   ├── game-theory-primer-skill-router/
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
└── evals/                          ← 测试与评分材料
    ├── test-prompts.json          ← 24 条触发 / 诱饵 / 路由 / 边界用例
    └── test-results.md            ← 逐项评分与失败修复记录
```

## 如何使用

先把仓库克隆下来：

```bash
git clone https://github.com/raphael-y7/game-theory-primer-skill.git
```

### 装 single（推荐先试这个）

```bash
# macOS / Linux
cp -r game-theory-primer-skill/single ~/.agents/skills/game-theory-primer-skill
```

```powershell
# Windows
Copy-Item -Recurse .\game-theory-primer-skill\single "$env:USERPROFILE\.agents\skills\game-theory-primer-skill"
```

### 装 pack

只复制含 `SKILL.md` 的目录，不要把 `pack/` 下的两个 json 一起拷进 skills 目录：

```bash
# macOS / Linux
cd game-theory-primer-skill/pack
cp -r game-theory-primer-skill-router \
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
@('game-theory-primer-skill-router','game-type-classifier','nash-equilibrium-solver','backward-induction','subgame-perfection-check','repeated-game-cooperation','pbe-verification','signaling-equilibrium') |
  ForEach-Object { Copy-Item -Recurse -LiteralPath (Join-Path $pack $_) -Destination $dest }
```

> `~/.agents/skills` 是 DSH 的 skill 目录；用别的 agent 时换成它自己的 skills 目录即可（例如 Claude Code 是 `~/.claude/skills`）。

### 怎么确认装好了

装完问一句"两家企业成本 c=10、需求 P=100−Q，同时定产量，各自产多少"，看 agent 是否先判类再给 `q*=(a−c)/3=30`，而不是给你一段泛泛的纳什均衡定义。装的是 single 时，它会先读入口再按路由表进能力卡；装的是 pack 时，对应能力会被直接命中。

## 来源

《博弈论基础》（A Primer in Game Theory）罗伯特·吉本斯 著

## 声明

本仓库只发布蒸馏后的 skill、索引与规则速查材料，不包含原书 PDF、EPUB、OCR 文件、截图或全书转写稿。能力卡中出现的原文引用仅用于标注方法论出处和保持可审计性。

书中所有数字判据（贴现因子门槛、分离信号水平、拍卖出价系数、锦标赛奖金差等）都是教科书算例的推导结果，原书未提供统计回测背书，使用时需按自身场景自行测试并声明所用口径。本仓库内容不构成投资建议。


## License

[MIT](./LICENSE)
