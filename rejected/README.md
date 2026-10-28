# rejected/ — 阶段1.5淘汰单元（本书记录）

## 结论：0 条淘汰

本书候选池共251条，阶段1.5三重验证结果：

| 类别 | 条数 | 处置 |
|---|---|---|
| frameworks | 56 | 全部 verified |
| principles | 85 | 83 verified + 2 reference（pc21、pc27，定性原则，并入相邻单元 summary，不淘汰） |
| cases | 42 | 全部 verified（均为 worked_example，无冒充真实事件） |
| counter-examples | 26 | 全部 verified（ce08 章节号订正后通过） |
| glossary | 42 | 全部通过（2处定义原话校订；术语不参与skill化判定） |

- 无 rejected：没有"无原文依据"或"纯重复"的候选需要淘汰。
- 2条 reference 的去向见 `references.md` 与 `verified.md` 判定汇总。
- 阶段1.6 未晋级为独立入口的12个单元**不是淘汰**——它们保留为 router 能力卡，经来源路由入口可达（destinations.json 中 served_by）。
- 候选原文、判定理由与修正记录：`candidates/verified-frameworks.md`、`verified-principles.md`、`verified-cases-ce-gloss.md`。

本目录作为审计留档保留（按 cangjie-skill 目录规范），无淘汰文件即审计结论本身。
