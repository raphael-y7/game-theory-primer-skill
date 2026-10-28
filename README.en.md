<h1 align="center">A Primer in Game Theory Skill</h1>

<p align="center"><a href="README.md">中文</a> | English</p>

An AI skill pack for immediate use — it distills the game-modelling and equilibrium-solving methods from Robert Gibbons' *A Primer in Game Theory* into 19 capability cards that can be triggered individually or combined.

It is not a book summary, nor a reading response — it breaks the reusable methodology in the book into skill modules that can be triggered, executed and tested.

## What these skills solve

- You face a multi-party situation — a competitor cutting prices, management making promises, large holders against retail — and cannot say which class of game it is before jumping to conclusions; get the quadrant wrong and every downstream conclusion collapses
- Whether an industry price understanding, an output-restriction pact or a supplier reciprocity arrangement will hold is pure gut feel; you cannot compute the discount-factor threshold, nor tell whether it breaks down because punishment is not credible or because the other side never intended to comply
- You cannot separate credible threats, commitments and policy statements from cheap ones — "heads will roll if targets are missed", "no share sales for three years": will they still be optimal at the execution node?
- Buybacks, increases in holdings, dividends and equity issues: you cannot tell a real signal from cheap talk, what it costs a weak firm to mimic, or why separating signals always look "excessive"
- Block trades and market-making quotes collapse despite obvious room for mutual gain, and you cannot say whether that is a character problem or a structural loss under information rents
- Roadshows, guidance and analyst calls say a lot but carry little information — is that a integrity problem or a necessary consequence of the preference structure?

## What was distilled

19 capability cards, organized in the order "classify the game first, pick the tool by quadrant second, handle information and credibility last":

- **Classification and modelling foundations**: `game-type-classifier` (game type and equilibrium-concept selection), `normal-form-modeling` (the three elements of normal-form modelling), `extensive-form-modeling` (extensive form: five elements, information sets, sequential interaction)
- **Complete information, static: solving and pruning**: `iesda-procedure` (iterated elimination of strictly dominated strategies), `nash-equilibrium-solver` (first-order conditions, the underline method, mixed-strategy indifference), `mixed-strategy-reinterp` (what mixed strategies really mean: opponent uncertainty and purification)
- **Complete information, dynamic: credibility**: `backward-induction` (backward induction in games of complete and perfect information), `subgame-perfection-check` (subgame perfection and ruling out non-credible threats), `commitment-credibility` (commitment and threat credibility: first-mover advantage and time consistency)
- **Repeated games and incentive structures**: `repeated-game-cooperation` (sustainability of cooperation: trigger strategies and discount-factor thresholds), `incentive-schemes` (two incentive templates: tournaments and efficiency wages)
- **Incomplete information, static: types and mechanisms**: `bayesian-nash-solver` (Bayesian normal form and Bayesian Nash equilibrium), `double-auction-linear-eq` (linear equilibrium of the double auction and the loss from trade), `revelation-principle` (the revelation principle and compressing the mechanism search)
- **Incomplete information, dynamic: signals and reputation**: `pbe-verification` (perfect Bayesian equilibrium, requirements 1–4 item by item), `signaling-equilibrium` (separating / pooling / hybrid equilibria and four applications), `signal-refinement-checklist` (signal requirements 5/6 and the intuitive criterion), `reputation-mechanism` (KMRW reputation: feigned cooperation in finitely repeated games), `cheap-talk-info-transmission` (when cheap talk carries information: Crawford-Sobel partition equilibria)

## Two packaging modes: single and pack

The same 19 capability cards are compiled twice, at two granularities. The content is identical; the only difference is how many entries an agent can discover.

| | single (one entry) | pack (compact pack, multiple entries) |
|---|---|---|
| Discoverable entries | **1**: `game-theory-primer-skill` | **8**: one source router + 7 promoted standalone skills |
| Where the 19 cards live | All inside the entry's `references/capabilities/`, loaded 1–2 at a time by the router table | 7 high-frequency cards become standalone skills; the other 12 stay in the router's `references/` |
| Triggering | Only the entry description participates in matching; routing happens after entry | The 7 high-frequency capabilities are matched directly, one hop fewer |
| Upgrades | Replace 1 directory | Replace 8 directories |

The 7 cards promoted to standalone skills in the pack:

- `game-type-classifier` — game type and equilibrium-concept selection
- `nash-equilibrium-solver` — Nash equilibrium solving procedure
- `backward-induction` — backward induction and spotting non-credible threats
- `subgame-perfection-check` — subgame perfection and ruling out non-credible threats
- `repeated-game-cooperation` — sustainability of cooperation and discount-factor thresholds
- `pbe-verification` — verifying requirements 1–4 of perfect Bayesian equilibrium
- `signaling-equilibrium` — separating / pooling / hybrid equilibrium determination

### Which one to install

Pick by the way you work, and **install only one**:

| How you work | Recommended | Why |
|---|---|---|
| You use DSH / Codex / Claude Code with a skills directory and want a clean list | single | Takes 1 slot, loses no capabilities |
| Your daily questions concentrate on "what game is this / how do I solve the equilibrium / is that threat credible / will the understanding hold / is this announcement a signal" | pack | Those are exactly the 7 promoted standalone skills, matched directly |
| You distribute to several agents or teammates who pick what they need | pack | They can install only the standalone skills they want |
| You want to install once and maintain one directory | single | Upgrades replace a single directory |

> Both builds come from the same bundle and carry identical capabilities. **Installing both will double-trigger**, so pick one.

## Examples

### Example 1: how long can an industry price understanding last?

**User question**

"These two oligopolists have held prices steady for years and nobody has cut first. How much longer can this understanding last?"

**How the skill reasons**

- `game-type-classifier`: pass the two questions first — are the payoff functions common knowledge (complete / incomplete), and do actions have an order that later movers can observe (static / dynamic)? Pricing simultaneously every period with repeated interaction lands in "complete-information repeated game", not a one-shot pricing game
- `repeated-game-cooperation`: write out the stage game and the profit triple (collusive πm/2, deviation πd, stage Nash πc), then apply the trigger-strategy condition (πm/2)/(1−δ) ≥ πd + δπc/(1−δ). Under Cournot structure this solves to δ ≥ 9/17
- The same card then checks punishment strength: 9/17 is only the threshold for "revert permanently to the stage Nash output". The book also shows Abreu's carrot-and-stick strategy sustaining the monopoly output at δ = 1/2
- `subgame-perfection-check`: verify the punishment is still optimal at the execution node and would not be undone by renegotiation

**Sample answer**

> Classify it first: this is a complete-information repeated game, not a one-shot pricing game. Using the Cournot triple from the book, the threshold for cooperation to be self-sustaining under a trigger strategy is δ ≥ 9/17 ≈ 0.53. But δ is an exogenous parameter in the book — it never tells you how to convert real-world patience into δ. Order frequency, cash reserves and reputation value can only serve as proxies; what value you assign is your call and must be written into the judgement, because there is no standard answer here. And 9/17 is not the only answer: with a harsher credible punishment (the carrot-and-stick strategy in the book), δ = 1/2 also sustains collusion. So "δ below 9/17 means a price war" is a wrong inference — check punishment strength before concluding the understanding cannot hold. Finally run the renegotiation test: if the punishment phase hurts both sides and can be renegotiated afterwards, the threat itself gets overturned. Give the conclusion in three tiers: δ clearly above the threshold with credible punishment → the understanding is sustainable; borderline → look at who has the strongest deviation incentive (the side with the largest πd − x is the weakest link); clearly below → short-sighted competition is the norm.

### Example 2: is a buyback a real signal, and is an equity issue bad news?

**User question**

"One company with plenty of cash announced a large buyback; another with heavy debt announced an equity issue. Is the buyback a credible signal? Is the equity issue bad news?"

**How the skill reasons**

- `signaling-equilibrium`: build the five elements of the signaling game (sender / receiver / types and prior / signal set / action set and payoffs), then ask the key question — **what does it cost a weak firm to mimic this?** A cancellation buyback with a premium and a long lock-up costs real cash and burns future financial flexibility, so mimicking is expensive for a weak firm; a mere "buyback intention / increase plan" is close to cheap talk
- Single-crossing check: the cost must be type-dependent (the low type pays more for the same signal), otherwise separation is impossible and only pooling or hybrid equilibria remain
- Separation must distort: the separating signal level is pinned by the low type's no-mimicry constraint and therefore sits above the complete-information optimum — so a signal that looks "just right" is actually suspicious
- The Myers-Majluf branch of `signaling-equilibrium`: equity is priced at average quality, so the high-profit type gives up a share that subsidises the low-profit type; good firms therefore avoid equity and turn to debt or internal funds
- `signal-refinement-checklist`: signaling games usually have multiple equilibria; use signal requirements 5/6 and the intuitive criterion to eliminate candidates that rest on arbitrary off-path beliefs

**Sample answer**

> The order of judgement is not "buyback = good news" but "what does it cost a weak firm to mimic this buyback". If it is only a sentence of intent with no amount commitment and no lock-up, the mimicking cost is near zero, so in equilibrium it is a pooling signal and the market cannot separate types with it. The book gives no threshold for "how large a buyback becomes credible" — you have to define that magnitude yourself from the company's cash flow, financing capacity and lock-up terms, and state it; do not treat some percentage as if it came from the book. Note also that separation must distort: a signal that actually separates has to be "excessive", above the current optimum, to form a barrier the low type will not cross — so "the buyback is too large" cannot be read directly as irrationality. On the equity issue, the Myers-Majluf logic applies: equity is priced at average quality, the high-profit type gives up shares that subsidise the low-profit type, so good firms turn to debt or internal funds, and the negative reaction to an equity issue is an equilibrium property, not a market failure. Finally, one announcement often supports several equilibria — run the refinement checklist to remove versions that rely on arbitrary beliefs such as "the market must read a non-buyback as a bad firm", and what survives is the conditional main scenario.

## How these skills were generated

These skills were produced with the **[cangjie-skill](https://github.com/kangarooking/cangjie-skill)** RIA-TV++ pipeline, in six stages:

1. **Whole-book comprehension (Adler analysis)** — apply Mortimer Adler's analytical reading method to the book: structure, interpretation, criticism, application
2. **Parallel extraction** — several specialized extractors (frameworks, principles, cases, counter-examples, terminology) mine candidate methodology units from the source text
3. **Triple verification** — every candidate must pass three checks: at least two independent in-book supports (cross-domain), the ability to answer questions the book never explicitly addresses (predictive power), and not being common sense (distinctiveness)
4. **RIA++ construction** — structure each unit along R (quotation) / I (restatement in own words) / A1 (in-book case) / A2 (future trigger scenario) / E (executable steps) / B (boundaries and blind spots)
5. **Zettelkasten linking** — map dependencies, contrasts and combinations between cards, producing the capability index and routing table
6. **Trigger and output testing** — write trigger blind tests (including decoy questions: fire when they should, stay silent when they should not) and output evaluation scenarios for every card; failing cards go back for rework and are re-verified afterwards

The nature of this book also shapes the distillation: it is a 1992 graduate textbook with a very clear boundary — it covers only the four classes of complete / incomplete information × static / dynamic games, and it requires the payoff functions to be writable. Every card therefore states in its B section when it must not be used, and the A2 section of each card carries an investment-scenario mapping (added at compile time, not part of the original book).

## Testing and verification

This repository publishes the test material from the generation process alongside the skills: `evals/test-prompts.json` holds 24 trigger, decoy, routing and boundary cases, `evals/blindtest-A.md` and `evals/blindtest-B.md` are the two blind-test records, `evals/skill-list-for-blindtest.md` is the list that gives the blind tester only card names and descriptions, `evals/output-evals/` holds the 9 output-evaluation tasks, and `evals/test-results.md` is the item-by-item scoring log.

- **Trigger precision**: 7 promoted cards tested independently, 7 / 7 hit
- **Decoy tests**: 3 / 3 passed (zero tolerance) — a pure data lookup triggers nothing, and a multi-opponent scenario is classified first instead of jumping to a single-point tool
- **Routing reachability**: 12 router cards, 12 / 12 hit the target card
- **Output evaluation**: 9 representative tasks (including boundary and missing-input scenarios) all passed; 1 of them was a task-design flaw corrected by the evaluator and recorded, not a formula error in a card
- **Planned 24 + 9 = 33 cases, 33 completed.** A gap worth stating plainly: the 12 router cards were verified by "blind-test reachability + formula checking" rather than a full output-evaluation task each (a cost trade-off); all 7 promoted cards were fully evaluated
- **Blind-test environment**: independent blind-test sub-agent in a clean context, host ZCode (GLM-5.3-Flash family), dated 2026-10-28; the material is published as-is, including the recorded gap

## Repository layout

```text
game-theory-primer-skill/
├── README.md                      ← Chinese version
├── README.en.md                   ← you are reading this
├── LICENSE                        ← MIT
├── BOOK_OVERVIEW.md               ← whole-book comprehension (Adler four-step, stage 0 output)
├── verified.md                    ← triple-verification conclusions for the 19 units
├── single/                        ← single-entry build
│   └── game-theory-primer-skill/
│       ├── SKILL.md               ← entry: triggers + routing table + loading rules
│       ├── BUILD_MANIFEST.json    ← build manifest and file hashes
│       └── references/
│           ├── overview.md        ← whole-book overview
│           ├── capability-index.md  ← full intent and keyword index
│           ├── cheatsheet.md      ← decision-rule quick reference
│           ├── glossary.md        ← glossary
│           └── capabilities/      ← 19 capability cards
├── pack/                          ← multi-entry build (compact pack)
│   ├── BUILD_MANIFEST.json
│   ├── capability-destinations.json
│   ├── gibbons-game-theory-router/
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
└── evals/                          ← trigger blind tests and output evaluation records
    ├── test-results.md             ← item-by-item scoring and the stated gap
    ├── test-prompts.json           ← 24 trigger / decoy / routing / boundary cases
    ├── blindtest-A.md              ← group A blind test (triggers + decoys)
    ├── blindtest-B.md              ← group B blind test (routing)
    ├── skill-list-for-blindtest.md ← blind-test material: names and descriptions only
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

## Usage

Clone the repository first:

```bash
git clone https://github.com/raphael-y7/game-theory-primer-skill.git
```

### Install single (recommended first try)

```bash
# macOS / Linux
cp -r game-theory-primer-skill/single/game-theory-primer-skill ~/.agents/skills/
```

```powershell
# Windows
Copy-Item -Recurse .\game-theory-primer-skill\single\game-theory-primer-skill "$env:USERPROFILE\.agents\skills\"
```

### Install pack

Copy only the directories that contain a `SKILL.md`; do not copy the two JSON files under `pack/` into your skills directory:

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

> `~/.agents/skills` is the DSH skills directory; with another agent, use its own skills directory (for example `~/.claude/skills` for Claude Code).

### How to verify the install

Ask: "Will these two oligopolists' price understanding hold, and how do I compute the discount-factor threshold?" If the agent enters the repeated-game threshold flow (stage-game triple, δ threshold, punishment-strength check) instead of giving generic industry commentary, the install works. With the single build it reads the entry first and then routes to a card; with the pack build the matching capability is hit directly.

## Sources

- *A Primer in Game Theory* by Robert Gibbons, translated by Gao Feng, checked by Wei Yugen
- Original edition 1992 (Prentice Hall / Harvester Wheatsheaf); Chinese translation March 1999, China Social Sciences Press (Contemporary Economics Textbook Translation Series)
- Distilled from the whole book, producing 19 capability cards
- The models and applications in the book come mostly from Western economics literature around 1990 (financial applications of signaling such as Myers-Majluf 1984), and there is not a single A-share case. The investment-scenario mapping in each card's A2 section was added at compile time, and every place where A-share institutional differences matter is marked separately inside the card

## Notice

This repository publishes distilled skills, indexes and rule quick references only. It contains no PDF, EPUB, OCR files, screenshots or full-book transcripts of the source book. Quotations that appear in the capability cards serve solely to attribute methodology and keep the material auditable.

All numeric criteria in the book (the 9/17 discount-factor threshold, the 1/4 threshold in the prisoner's dilemma, bid shading in auctions, the tournament prize spread, the 1/4 trade band in the double auction, etc.) are model solutions under specific functional forms — change the linear-demand, uniform-distribution or risk-neutral assumptions and the numbers no longer carry over automatically, and the book offers no statistical backtesting. Recompute them for your own setting and declare the assumptions you use. Nothing in this repository is investment advice.

## License

[MIT](https://opensource.org/licenses/MIT)
