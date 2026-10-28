<h1 align="center">Game Theory Primer Skill</h1>

<p align="center"><a href="README.md">中文</a> | English</p>

An AI skill pack for immediate use — it distills the game modeling and equilibrium-solving methods from Robert Gibbons' *A Primer in Game Theory* into 19 capability cards that can be triggered individually or combined.

It is not a book summary, nor a reading response — it breaks the reusable methodology in the book into skill modules that can be triggered, executed and tested.

## What these skills solve

- You see a multi-party interaction and want to jump straight to a conclusion, but cannot say which of the four game classes it belongs to — pick the wrong quadrant and every equilibrium concept downstream is wrong
- You can recite the definition of Nash equilibrium, but faced with "two firms set output simultaneously" or "how much should I bid at auction", you do not know what to write first
- You treat threats, promises and public announcements as given facts, without realizing that a non-credible threat never takes effect in equilibrium
- You judge whether industry tacit collusion, price alliances or long-term supplier relationships can hold, but can only say "it depends on whether people keep the rules" — no discount-factor threshold, no weakest player, no sensitivity direction
- A buyback, an increase-in-holding or a share-issuance announcement sits in front of you, and you cannot tell a costly separating signal from costless cheap talk
- When several equilibria coexist, you do not know which one to take as the main scenario, nor which off-path belief your conclusion depends on

## What was distilled

19 capability cards, organized in the order "classify and model first, solve by quadrant second, return to credibility and mechanisms last":

- **Classification and modeling (3)**: `game-type-classifier` (game-type test and equilibrium-concept choice), `normal-form-modeling` (the three elements of normal form), `extensive-form-modeling` (extensive form and game-tree modeling)
- **Complete-information static solving (3)**: `iesda-procedure` (iterated elimination of strictly dominated strategies), `nash-equilibrium-solver` (three solving routes: first-order conditions, cell-by-cell underlining, mixed-strategy indifference), `mixed-strategy-reinterp` (the correct reading of mixed strategies)
- **Dynamic games and credibility (3)**: `backward-induction`, `subgame-perfection-check` (subgame perfection and eliminating non-credible threats), `commitment-credibility` (commitment, first-mover advantage and time consistency)
- **Long-run relationships (2)**: `repeated-game-cooperation` (trigger strategies and the discount-factor threshold), `reputation-mechanism` (KMRW reputation and disguised cooperation)
- **Incomplete-information static games and mechanism design (3)**: `bayesian-nash-solver` (Bayesian normal form and BNE solving), `double-auction-linear-eq` (linear equilibrium and trading loss), `revelation-principle` (the revelation principle and compressing the mechanism search)
- **Incomplete-information dynamic games and signaling (4)**: `pbe-verification` (PBE requirements 1–4, item by item), `signaling-equilibrium` (separating / pooling / hybrid), `signal-refinement-checklist` (refining off-path beliefs), `cheap-talk-info-transmission` (when cheap talk carries information)
- **Incentives (1)**: `incentive-schemes` (tournaments and efficiency wages)

## Two packaging modes: single and pack

The same 19 capability cards are compiled twice, at two granularities. The content is identical; the only difference is how many entries an agent can discover.

| | single (one entry) | pack (compact pack, multiple entries) |
|---|---|---|
| Discoverable entries | **1**: `game-theory-primer-skill` | **8**: one source router + 7 promoted standalone skills |
| Where the 19 cards live | All inside the entry's `references/capabilities/`, loaded 1–2 at a time by the router table | 7 high-frequency cards become standalone skills; the other 12 stay in the router's `references/` |
| Triggering | Only the entry description participates in matching; routing happens after entry | The 7 high-frequency capabilities are matched directly, one hop fewer |
| Upgrades | Replace 1 directory | Replace 8 directories |

The 7 cards promoted to standalone skills in the pack:

- `game-type-classifier` — game-type test and equilibrium-concept choice
- `nash-equilibrium-solver` — Nash equilibrium solving procedure
- `backward-induction` — backward induction
- `subgame-perfection-check` — subgame perfection and non-credible threats
- `repeated-game-cooperation` — sustainability of cooperation in repeated games
- `pbe-verification` — perfect Bayesian equilibrium verification
- `signaling-equilibrium` — the three equilibrium classes in signaling games

### Which one to install

Pick by the way you work, and **install only one**:

| How you work | Recommended | Why |
|---|---|---|
| You use DSH / Codex / Claude Code with a skills directory and want a clean list | single | Takes 1 slot, loses no capabilities |
| Your daily questions concentrate on "which game type / solve the equilibrium / backward induction / credibility / long-run cooperation / PBE / signaling" | pack | Those are exactly the promoted standalone skills, matched directly |
| You distribute to several agents or teammates who pick what they need | pack | They can install only the standalone skills they want |
| You want to install once and maintain one directory | single | Upgrades replace a single directory |

> Both builds come from the same bundle and carry identical capabilities. **Installing both will double-trigger**, so pick one.

## Examples

### Example 1: how long can an industry's high-price tacit collusion hold?

**User question**

"Two oligopolists play against each other every period and want to sustain a high price. Above what discount factor does the tacit deal hold? Give me the reasoning."

**How the skill reasons**

- First `game-type-classifier`: both firms know the payoff functions → complete information; each period's action is observed → dynamic. The quadrant is "complete information, dynamic", solved with subgame perfection; treating it as a one-shot static game would wrongly conclude that a price war is inevitable
- Then `repeated-game-cooperation`: write the stage-game triple — collusive profit per firm `πm/2=(a−c)²/8`, best deviation `πd=9(a−c)²/64`, reversion to Cournot `πc=(a−c)²/9` — and apply the general threshold `δ≥max(di−xi)/(di−ei)`, which reduces to `δ≥9/17` in the Cournot case
- Then check two boundaries from the card: punishment strength (reverting to Cournot forever is not the harshest credible punishment), and the renegotiation hole (punishment also punishes the punisher, so a threat that would be renegotiated away voids the threshold)
- Finally output a three-tier verdict (sustainable / borderline / not sustainable) plus the weakest player and the sensitivity direction — never a point prediction

**Sample answer**

> Start by writing the stage game: under collusion each firm earns `(a−c)²/8` per period, a unilateral deviation pays `9(a−c)²/64`, and after the relationship breaks each period is worth only the Cournot `(a−c)²/9`. Under a trigger strategy the threshold is **δ≥9/17≈0.53**. But that number is the threshold for one specific punishment — permanent reversion to Cournot — not an absolute lifeline for the industry: if you can execute a harsher and still credible punishment (a sharp short output cut after a deviation, with cooperation restored on compliance), the threshold drops clearly, and collusion can hold below 0.53. So the right move is not to ask "is δ high enough" but to estimate three parameters first — order rhythm (higher repetition frequency means higher δ), balance-sheet strength (who can survive the punishment phase; the weaker side has lower δ and defects first), and reputation value (the share of future profit flow). Whoever has the largest `πd−x` is the weakest link. Close with this: the model proves that cooperation *can be* an equilibrium, not that it *will* happen; a sufficient δ only means deviation does not pay — which equilibrium is played still depends on focal points and conventions.

### Example 2: is a buyback announcement a real signal or cheap talk?

**User question**

"One company with plenty of cash announces a large buyback; another with debt announces a share issuance. Is the buyback a real signal? How do I judge?"

**How the skill reasons**

- First `game-type-classifier`: management knows its own earnings prospects while the market can only price after the announcement → incomplete information plus dynamic → perfect Bayesian equilibrium, so beliefs must enter the analysis
- Then `signaling-equilibrium`: enumerate the four candidates (pooling on signal A, pooling on signal B, and the two separating patterns) and test each one — Bayes gives on-path beliefs, then the receiver's best response, then each type's deviation incentive, then off-path beliefs. The first question is not "what does the announcement say" but "what does it cost a weak firm to mimic this"
- Check single crossing: separation requires that the low type's marginal cost of the same signal be higher; if it holds, the low type's incentive-compatibility constraint pins the separating level, and separation is always distorted — the signal must be "wasted" up to the point where the low type refuses to mimic
- Then `signal-refinement-checklist`: pooling and hybrid equilibria often coexist, so requirements 5/6 (the intuitive criterion) strip out the ones resting on implausible off-path beliefs, and what survives becomes the conditional main scenario

**Sample answer**

> Whether a buyback is a real signal does not depend on the wording — it depends on what it costs a weak firm to mimic. A cancellation buyback with a premium and a long lock-up is real money and it thins out future financial flexibility; a cash-strapped, financing-constrained firm copying that pays a lot, so separation is possible. By contrast, costless gestures such as a "buyback intention" or an "increase-in-holding plan" cost a weak firm nothing to copy, so the only equilibrium is pooling — it is indistinguishable from cheap talk and must not be read with the same logic. As for the issuance: under Myers-Majluf, equity financing forces high-profit types to hand over a larger stake and subsidize low-profit types, so well-performing firms avoiding equity in favor of debt or internal funds is an equilibrium implication; a negative announcement reaction and a deeper discount mean the market assigns a higher probability (q) that the issuer is the low type — an equilibrium property, not a market failure. One last warning: these models usually admit several equilibria at once, so any claim that "the market will read it as…" must first state which off-path belief it relies on.

## How these skills were generated

These skills were produced with the **[cangjie-skill](https://github.com/kangarooking/cangjie-skill)** RIA-TV++ pipeline, in six stages:

1. **Whole-book comprehension (Adler analysis)** — apply Mortimer Adler's analytical reading method to the book: structure, interpretation, criticism, application
2. **Parallel extraction** — several specialized extractors (frameworks, principles, cases, counter-examples, terminology) mine candidate methodology units from the source text
3. **Triple verification** — every candidate must pass three checks: at least two independent in-book supports (cross-domain), the ability to answer questions the book never explicitly addresses (predictive power), and not being common sense (distinctiveness)
4. **RIA++ construction** — structure each unit along R (quotation) / I (restatement in own words) / A1 (in-book case) / A2 (future trigger scenario) / E (executable steps) / B (boundaries and blind spots)
5. **Zettelkasten linking** — map dependencies, contrasts and combinations between cards, producing the capability index and routing table
6. **Trigger and output testing** — write trigger blind tests (including decoy questions: fire when they should, stay silent when they should not) and output evaluation scenarios for every card; failing cards go back for rework and are re-verified afterwards

Because this 1992 textbook covers only the four classes of complete/incomplete information × static/dynamic games, that boundary is written into every card: behavioral game theory, experimental deviations and adjustment processes outside equilibrium are explicitly out of scope.

## Testing and verification

This repository publishes the test material from the generation process alongside the skills: `evals/test-prompts.json` holds the trigger, decoy, routing and boundary cases, and `evals/test-results.md` is the item-by-item scoring report — including the uncovered gaps and a correction note, not just the passes.

- **Trigger blind tests**: 7 promoted cards, 7 / 7, run by a sub-agent in a clean context given only card names and descriptions
- **Decoy tests**: zero tolerance, 3 / 3 — a pure data lookup activates no card, and a "looks complicated" multi-party scenario still goes to classification rather than to a single-point tool
- **Routing reachability**: 12 router cards, 12 / 12, every case reached its target card
- **Output evaluation**: 9 representative tasks (including boundary and missing-input cases), 9 / 9, with each formula checked mechanically; 1 case was a task-design issue, recorded as such and not counted as a card error
- **Regression set**: the trigger, decoy and routing cases plus the 9 evaluated tasks all became the regression baseline in `evals/test-prompts.json`
- **Not covered**: the 12 router cards were verified by blind-test reachability plus formula checks, not by a full evaluated task each

## Repository layout

```text
game-theory-primer-skill/
├── README.md                      ← Chinese version
├── README.en.md                   ← you are reading this
├── LICENSE                        ← MIT
├── BOOK_OVERVIEW.md               ← whole-book comprehension (Adler four-step, stage 0 output)
├── verified.md                    ← triple-verification conclusions for the 19 canonical units
├── INDEX.md                       ← skill map: capability table + also_read dependencies + load order
├── TEST_SUMMARY.md                ← stage 4 pressure-test summary: scope, structure checks, results, next steps
├── CANGJIE_ADAPTATION.md          ← cangjie adaptation notes: text status, distillation goals, evidence rules, boundaries
├── candidates/                    ← stage 1 candidate pool (14 files, 251 candidates in total)
│   ├── frameworks.md              ← all framework candidates (56)
│   ├── frameworks-part-a.md       ← framework candidates, shard A
│   ├── frameworks-part-b.md       ← framework candidates, shard B
│   ├── frameworks-part-c.md       ← framework candidates, shard C
│   ├── principles.md              ← all principle candidates (85)
│   ├── principles-part-a.md       ← principle candidates, shard A
│   ├── principles-part-b.md       ← principle candidates, shard B
│   ├── principles-part-c.md       ← principle candidates, shard C
│   ├── cases.md                   ← case candidates (42)
│   ├── counter-examples.md        ← counter-example candidates (26)
│   ├── glossary.md                ← glossary candidates (42)
│   ├── verified-frameworks.md     ← item-by-item verification: frameworks
│   ├── verified-principles.md     ← item-by-item verification: principles (with formula corrections)
│   └── verified-cases-ce-gloss.md ← item-by-item verification: cases / counter-examples / glossary
├── bundle/                        ← the canonical bundle before compilation (verified.yaml is the source of truth)
│   ├── verified.yaml              ← metadata, criteria and destinations for the 19 cards
│   ├── cards/                     ← 19 capability cards (R/I/A1/A2/E/B structure)
│   └── book/
│       ├── overview.md            ← whole-book overview
│       └── glossary.md            ← glossary
├── single/game-theory-primer-skill/            ← single-entry build
│   ├── SKILL.md                   ← entry: triggers + routing table + loading rules
│   ├── BUILD_MANIFEST.json        ← build manifest and file hashes
│   ├── test-prompts.json          ← entry copy of the cases, byte-identical to evals/test-prompts.json
│   └── references/
│       ├── overview.md            ← whole-book overview
│       ├── capability-index.md    ← full intent and keyword index
│       ├── cheatsheet.md          ← decision-rule quick reference
│       ├── glossary.md            ← glossary
│       └── capabilities/          ← 19 capability cards
├── pack/                          ← multi-entry build (compact pack)
│   ├── BUILD_MANIFEST.json
│   ├── capability-destinations.json
│   ├── game-theory-primer-skill-router/
│   │   ├── SKILL.md               ← source router entry
│   │   └── references/            ← 19 cards + indexes, called by the router
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
├── (note) ← every skill directory also ships a test-prompts.json (trigger and boundary cases)
└── evals/                          ← test and scoring material
    ├── test-prompts.json          ← 24 trigger / decoy / routing / boundary cases
    └── test-results.md            ← item-by-item scoring and rework log
```

## Usage

Clone the repository first:

```bash
git clone https://github.com/raphael-y7/game-theory-primer-skill.git
```

### Install single (recommended first try)

```bash
# macOS / Linux
cp -r game-theory-primer-skill/single/game-theory-primer-skill ~/.agents/skills/game-theory-primer-skill
```

```powershell
# Windows
Copy-Item -Recurse .\game-theory-primer-skill\single "$env:USERPROFILE\.agents\skills\game-theory-primer-skill"
```

### Install pack

Copy only the directories that contain a `SKILL.md`; do not copy the two JSON files under `pack/` into your skills directory:

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

> `~/.agents/skills` is the DSH skills directory; with another agent, use its own skills directory (for example `~/.claude/skills` for Claude Code).

### How to verify the install

Ask: "Two firms with cost c=10 and demand P=100−Q set output simultaneously — how much does each produce?" If the agent classifies the game first and then returns `q*=(a−c)/3=30` instead of a generic definition of Nash equilibrium, the install works. With the single build it reads the entry first and then routes to a card; with the pack build the matching capability is hit directly.

## Sources

- *A Primer in Game Theory* by Robert Gibbons

## Notice

This repository publishes distilled skills, indexes and rule quick references only. It contains no PDF, EPUB, OCR files, screenshots or full-book transcripts of the source book. Quotations that appear in the capability cards serve solely to attribute methodology and keep the material auditable.

All numeric criteria in the book (discount-factor thresholds, separating signal levels, auction bid coefficients, tournament prize spreads, etc.) are derivations from textbook worked examples without statistical backtesting; test them on your own setting and declare the convention you use. Nothing in this repository is investment advice.


## License

[MIT](./LICENSE)

