# Stage 4 压力测试摘要

本文件是《博弈论基础》（A Primer in Game Theory）skill 包在 cangjie-skill v2.5 流水线阶段 4（触发与输出测试）的摘要，材料取自归档的 `审计过程/审计与测试/test-results.md`、`审计过程/PIPELINE_STATE.md`、`审计过程/needs-review.md`，以及对仓库内 test-prompts 与能力卡的实际清点结果。

## 测试范围

**被测对象**：19 张能力卡，编译为两种打包模式。

- single 模式：1 个入口 `game-theory-primer-skill`，19 张卡全部在它的 `references/capabilities/` 下
- pack 模式：8 个入口（1 个来源路由入口 `game-theory-primer-skill-router` + 7 个已晋级独立 skill），其中 12 张未晋级的卡仍在 router 的 `references/` 里
- 晋级关系：7 promoted（`game-type-classifier`、`nash-equilibrium-solver`、`backward-induction`、`subgame-perfection-check`、`repeated-game-cooperation`、`pbe-verification`、`signaling-equilibrium`）+ 12 router

**test-prompts 文件分布**：

| 位置 | 文件数 | 用例数 | 说明 |
|---|---|---|---|
| `evals/test-prompts.json` | 1 | 24 | suite 级用例（`skill` = `bundle.gibbons-game-theory`，`version` = 1.0.0） |
| `single/game-theory-primer-skill/test-prompts.json` | 1 | 24 | 入口用例副本，与 `evals/test-prompts.json` 逐字节相同（SHA256 一致） |

本包归档内只有 1 个 `test-prompts.json`（位于 `审计过程/审计与测试/`），没有按 skill 拆分的 `test-prompts__<skill名>.json`，因此 pack 下 7 个独立 skill 目录**没有**各自的 test-prompts 副本。

**覆盖类型**：`test-prompts.json` 的每条用例只含 `id` / `target` / `prompt` / `expected` 四个字段，**没有 `type` 字段**，下列分类是按 `id` 前缀归并的结果，不是文件里的原字段：

| 类型 | 条数 | 覆盖内容 |
|---|---|---|
| `should_trigger`（trig-01～07） | 7 | 7 张 promoted 卡的直接触发，逐条指定目标卡 |
| `should_trigger`（router-01～12） | 12 | 经路由入口可达 12 张未晋级卡，判"路由是否漂移" |
| `should_not_trigger`（decoy-01～03） | 3 | 诱饵题：纯数据查询应完全不激活；"看似复杂"的多方场景仍先判类；"毫无规律"的资金行为走混合战略解读卡 |
| `edge_case`（edge-01～02） | 2 | 个人琐事是否算博弈、多企业且成本为私人信息时是否要跨卡联动 |
| `output_case` | 0 | **本包 `test-prompts.json` 内没有输出质量用例** |

输出质量评测以另一套材料存在：归档 `审计过程/审计与测试/output-evals/` 下有 9 个任务文件（C-cournot、C-trigger-threshold、C-bargaining、D-spence、D-beer-hotdog、D-pbe、E-classify、E-double-auction、E-incentive），它们是带完整数值链的实测任务，**没有**并入 `test-prompts.json`，也**没有**随本仓库发布。

## 结构检查

以下为本次对仓库现状的实测结果，不是转述：

- **JSON 可解析性**：`evals/test-prompts.json` 与 `single/game-theory-primer-skill/test-prompts.json` 两个文件均通过 JSON 解析，0 个损坏；各含 24 条 `test_cases`，两份 SHA256 相同（`D01B80E9…EF39`）。
- **SKILL.md frontmatter**：single 入口 1 个 + pack 8 个，共 9 个 `SKILL.md` 全部以 `---` 开头且含 `name` / `description` 字段，9/9 合规。
- **六段完整性**：`bundle/cards/` 下 19 张能力卡全部含 `R 原文依据` / `I 自述` / `A1 书中案例` / `A2 触发与投资映射` / `E 执行步骤` / `B 边界` 六段，19/19 齐全；`single/…/references/capabilities/` 与 `pack/game-theory-primer-skill-router/references/capabilities/` 各 19 张，数量一致。
- **小节标题不统一（如实记录）**：六段齐全但标题写法有两套——14 张用 `## R 原文依据` 式，5 张（`game-type-classifier`、`iesda-procedure`、`mixed-strategy-reinterp`、`nash-equilibrium-solver`、`normal-form-modeling`）用 `## R — 原文依据` 式。按标题做机器切片时需要同时兼容这两种写法。
- **引用可回查**：R 段原文均附章节号与图表号（形如"（2.3.B，图2.3.6）"）。**本包卡片不附转写稿行号**（0 处 `L****` 形式引用），回查只能靠章节号定位到原书。
- **编号口径不一致（如实记录）**：`test-results.md` 用 `pA1`–`pA10` / `pB1`–`pB12` 编号，`test-prompts.json` 用 `trig` / `decoy` / `router` / `edge` 编号，两套**不能逐条一一对应**。可核对的差异有两处：报告诱饵表 `pA10`（三家企业、一家成本为私人信息）在 JSON 里对应的是 `edge-02` 而不是 decoy；JSON 的 `decoy-03`（游资操作是否随机）在报告的表格里没有单列判定。
- **未做的检查**：没有逐条用例的机器评分记录——归档与仓库内都没有 `test-results*.json` 或逐条 pass/fail 日志。

## 结果

- **skills**: 19（7 promoted + 12 router；对应 single 1 个入口 + pack 8 个入口）
- **test_json**: 1（24 条用例），另有 1 份随入口目录发布的副本
- **通过情况**：本包**附带**了阶段 4 压力测试报告（`evals/test-results.md`），但记录的是能力卡级别的人工/盲测判定，不是 24 条用例逐条的机器跑分。报告原文的分项结论摘录如下：

| 项目 | 报告结论 | 方式 |
|---|---|---|
| 触发精度 | 7 / 7 通过 | 独立盲测 sub-agent，干净上下文，只给 19 张卡的 name + one_liner + description，不给 type/expected |
| 诱饵测试 | 3 / 3 通过（报告标注容错 = 0） | 同上 |
| 路由可达性 | 12 / 12 通过 | 同上（`pB1`–`pB12`） |
| 输出实测 | 9 / 9 通过 | 9 个代表任务逐项机械核对公式与数值 |

- **汇总口径有一处对不上（如实记录）**：报告写"计划 24+9=33，完成 33，全部断言通过"，`PIPELINE_STATE.md` 写"盲测 22/22 + 实测 9/9"。但分项明细只列了 7 + 3 + 12 = 22 条盲测与 9 个实测，合计 31；2 条 `edge` 用例没有单列逐条判定（其中 `edge-02` 疑似被计入诱饵表的 `pA10`）。因此"33/33"的分母包含了未单列的 edge 用例，引用时以分项明细为准。
- **已记录的一处纠错**：`D-pbe` 实测中，用户所称"路径外推断随便设"实际是定位错误——该剧本是分离均衡、路径上推断由要求 3 钉死。报告把这一处记为**任务设计问题，不是卡内公式错误**。
- **未覆盖项（报告与 needs-review 自述）**：12 张 router 卡以"盲测可达 + 公式核对"为准，其中只有 3 张高频卡做了完整实测任务，其余未逐一实测（成本考量）；promoted 卡全部实测。

## 可接入 darwin-skill 的后续动作

1. **把这 24 条用例当回归样本**：文件已是 darwin 兼容的骨架（`skill` / `version` / `test_cases[]`），但缺 `type` 与 `expected_behavior` 两个字段（现为 `target` + `expected`），接入前建议补字段并统一编号口径（`trig`/`decoy`/`router`/`edge` 或 `pA`/`pB` 只留一套）。
2. **补齐 output_case**：JSON 里 0 条输出质量用例，而归档 `output-evals/` 的 9 个任务已有完整数值链（如古诺 `q*=(100−10)/3=30`、`P*=40`、`π=900`；触发战略 `δ≥9/17≈0.529`；双向拍卖 `p_b=41/60`、`p_s=0.650`），可直接转成带期望数值的 `output_case`。
3. **把两条 edge 用例补上逐条判定**：`edge-01`（个人琐事是否算博弈）、`edge-02`（多企业 + 私人成本是否跨卡联动）目前没有单列结论，是"33/33"口径对不上的根源，补完即可让汇总自洽。
4. **补 router 卡的完整实测**：12 张里只有 3 张有实际执行记录，其余以可达性代替；接入前应逐张补一个代表任务演算。
5. **把 `D-pbe` 的纠错固化成用例注释**：这条"任务设计问题 vs 卡内错误"的区分是回归时最容易误判的一类，写进用例 `notes` 比留在报告正文更不易丢失。
