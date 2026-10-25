# Creami Research Handoff

Oct 20, 2026 · @Ayham Huq

Four recipe books are exhausted and the pints already taste close to real ice cream. What's missing is the formulation science: how to build a base from first principles, under a 400–500 calorie per-pint ceiling, using traditional lactose-containing milk, with mix-in chunks that survive the cycle intact.

## Current setup

Ninja Creami, roughly 100+ pints made from four of Eli Mack's (@FitnessProductFinder) recipe books: Fan Favorites, Keto, Lactose Free, and No Protein Powder Needed. 243 recipe pages across them, 148 distinct flavors once duplicates are merged. Equipment includes a 0.1g precision scale, an immersion blender, and multiple pints for batch prep.

The standard base in those books, which is what I've been running:

| Component | Amount |
| --- | --- |
| Liquid | 400g regular 1% or 2% milk (the books call for Fairlife ultra-filtered or a flavored protein shake) |
| Sweetener | 40–45g monk fruit blend (Lakanto) |
| Flavor | 5g vanilla bean paste |
| Salt | a pinch |
| Stabilizer | 1g (¼ tsp) xanthan gum |

Freeze 16+ hours, hot water on the pint for 60 seconds, spin on Lite Ice Cream, then Respin. Mix-ins go in on the mix-in cycle, not at serving.

What I'm changing and why:

- **Already on regular 1% or 2% milk, not Fairlife.** I want the lactose. Every ultra-filtered milk on the market is lactose-free by design, so there's no drop-in replacement.
- **Sweetener is erythritol-leaning right now** (monk fruit blends are usually erythritol-bulked). It's the closest to real sugar in a Creami in my experience, but I'm open to allulose or blends.
- **I track macros closely** and strength train. I'm frequently short on carbohydrate, so carb-dense and low-fat ingredients are worth more to me than they would be to most people.
- No store constraint — any grocery or online source is fine.

**Baseline PAC of the current base, computed.** Using the Ice Creamery formula and counting lactose: 400g of 2% milk gives about 36.5g MSNF (non-fat portion × 0.093), so about 19.9g lactose at PAC 100; 40g erythritol at PAC 280; roughly 3g of sugar from the vanilla paste. That totals 13,490 over a 446g mix, so **PAC ≈ 30** — above the 20–25 storage band and at the top of the 24–28 milk ice cream band.

Quantifying the lactose consequence: switching from Fairlife to regular 2% roughly doubles lactose over 400g and adds about +2.2 PAC on its own. Adding 25g of nonfat milk powder adds roughly 13g more lactose, about +1.2 PAC. So the two changes together move the base from about 27 to about 30 — real, but small next to the sweetener, which supplies some 83% of the total. (Assumes lactose PAC = 100 on molar grounds; the site's per-ingredient dataset would give the exact coefficient.)

The tension this exposes: nominal PAC 30 should spin soft, yet erythritol is the sweetener that behaves best here. If erythritol recrystallizes as the literature says, effective PAC drops well below 30, which would explain both the good behavior and the need for the hot-water-and-respin routine. That is directly testable.

## Goals

1. **Good-tasting ice cream that's very similar to real ice cream.**
2. **Limit calories while using traditional milk.** One pint, everything in, should not exceed 400–500 calories.
3. **Real mix-in chunks that aren't pulverized.**
4. **Replicate real ice cream recipes, understand what I'm making, and know where to pivot.** This one is crucial. I'm willing to keep making my current batches, but I really want to understand the science. I'm also open to a dedicated ice cream machine if it's genuinely worth it — though my preliminary reading says those need high fat, which very likely conflicts with goal 2.

Goal 4 is the priority. The others are outcomes; goal 4 is the capability. I'd rather come away able to read a conventional ice cream recipe, understand which ingredient is doing which job, and work out what to substitute, than be handed another set of recipes to follow.

## Established — base and texture

**Total solids and freezing point depression are the two master variables.** Free water is what freezes into detectable crystals, so anything that binds water or displaces it improves texture. Conventional ice cream runs 10–16% milkfat and 36–40% total solids. My base is roughly 2% fat and maybe 20–25% total solids, so it's far below standard on both.

**That's why ultra-filtered milk works.** Fairlife is 13g protein and 6g sugar per cup against regular milk's 8g and 12g — more protein, less water. The books specify it for texture, not for macros.

**Nonfat dry milk powder is the highest-leverage single addition I've found.** 30g is 109 cal, 16g carb, 11g protein, 0.2g fat. It raises protein, total solids, lactose and carbohydrate at once, at almost no fat cost. It reproduces most of what ultra-filtration does while keeping the lactose. It also toasts — see the technique note below.

**Freeze-dried fruit powder behaves as a stabilizer.** USDA ARS work found it absorbs liquid from the ice cream rather than letting it melt, reduces ice crystal formation, and was presented as a raw-fruit alternative to xanthan gum and sodium alginate. Strawberry was most effective. This also means freeze-dried fruit pulls free water out of a base rather than adding any — the opposite of fresh fruit.

**The Creami generates little overrun.** A churn machine whips air in during freezing; the Creami shaves a frozen block. Low fat therefore penalizes me less than it would in a conventional machine, but it also means conventional recipes assume air incorporation I will not get. This matters for interpreting any book formula.

**Cold suppresses sweetness and aroma perception.** This is the documented reason fat-based inclusions read as waxy and bland in ice cream — the mouth is cold. The practical consequence is that a base should taste slightly too sweet and too salty at room temperature.

Techniques identified but not yet tested: toasting milk powder in a dry pan until deep golden (described in pastry writing as dried, concentrated brown butter, and nonfat); steeping and straining aromatics in warmed milk; cooking a starch or custard base instead of relying on xanthan alone.

## Established — sweeteners

Professional gelato practice uses two values that are deliberately decoupled, both indexed to sucrose = 100. This is the framework that handles a sugar substitution, and it's the thing none of the ice cream books cover.

| Sweetener | PAC (anti-freeze power) | POD (sweetness) | Browns? |
| --- | --- | --- | --- |
| Sucrose | 100 | 100 | Yes |
| Allulose | \~190 | \~70 | Yes, faster than sugar |
| Erythritol | \~280 | \~60–70 | No |

Erythritol's PAC of 280 falls straight out of molecular weight — 122 against sucrose's 342, so about 2.8× the molecules per gram and about 2.8× the freezing point depression. An erythritol manufacturer's technical report on light protein ice cream confirms that 2.8× figure independently.

**The paradox, and its resolution.** On paper erythritol should produce the softest pint of the three. In practice it's reported as the hardest. The same manufacturer report explains why: erythritol crystallises after freezing more readily than sugar, which significantly hardens the texture during deep-freeze storage. Once it drops out of solution it stops acting as a dissolved solute, so its effective PAC collapses well below 280. Its nominal number is not what you have after a day in the freezer.

**Why my preference for erythritol may still be right, for a machine-specific reason.** A churn machine wants maximum PAC so the product is scoopable at −18°C. A Creami wants the opposite — a block solid enough for the blade to shave, since a base that isn't frozen solid through spins to soup. Gelato guidance treats erythritol at 100–120g per 1000g as *too soft*. And erythritol's other defect, grittiness from recrystallization, is the one thing a Creami blade destroys by design. Creami-specific vendor guidance disagrees and ranks erythritol as most likely to freeze hard, recommending a 10–15 minute counter thaw and a respin — which is already the standard workflow, so the effect may be real but masked.

**Where the technical sources converge: blend them.** The manufacturer report found allulose alone gave poor texture, but allulose combined with erythritol improved both texture and scoopability. Creami vendor guidance says pair erythritol with allulose or a starch stabilizer. Eli's own affiliate page says he prefers allulose/erythritol blends with monk fruit. Three sources with different incentives, same conclusion.

Other settled points: both sweeteners are roughly 60–70% as sweet as sucrose, so a 1:1 swap by weight under-sweetens. Erythritol is recommended at 6.5–8.0% of the recipe by weight. Removing sugar without replacing its freezing point depression produces, in the report's words, "a very hard and icy texture." And because erythritol does not brown at all, any caramel or butterscotch note has to come from allulose or from toasted milk solids.

**Lactose counts toward anti-freeze power.** Lactose makes up 54.5% of MSNF and contributes to freezing point depression; the PAC method is specifically recommended when lactose levels vary or run high enough to make the product too soft. This has a direct consequence I had not accounted for: switching to regular milk and adding nonfat milk powder both raise lactose, so both push PAC upward on their own, independent of the sweetener.

## Established — mix-ins

Food science sorts inclusions by **failure mode**, not by food type. A UW–Madison food science deck gives five behavioral classes, each with a characteristic way it goes wrong in a frozen dessert:

| Class | Examples | How it fails | Fix |
| --- | --- | --- | --- |
| Fat-based | Chips, flakes, barks, coatings | Waxy, low flavor — the mouth is cold | Lower melt point, more flavor, more sugar so it dissolves on the tongue |
| Hygroscopic | Toffee, fudge | Sticky, loses piece identity | Fat or confectionery coating; larger pieces |
| Low water activity | Crisp rice, pretzels, cookies | Loses crispness | Fat or chocolate coating; **larger pieces**; keep cold and dry |
| Textural | Fudge, chewy caramel | Hardens over time | More fat, lower melt point, glycerin or invert sugar |
| Variegate | Sauces, ribbons | Sinks | Colder draw temperature |

**This explains the coconut oil trick.** Eli's chips-plus-coconut-oil shell is textbook, not folklore: cutting chocolate with oil lowers its melt point so it dissolves on the tongue instead of reading waxy. It's the industry's own prescribed fix for fat-based inclusions.

**Moisture migration into dry, unprotected inclusions is treated as unavoidable.** Tharp and Young's industry column states it plainly; commercial ice cream sandwich wafers go soggy within days of manufacture and the trade accepts it. The commercial countermeasure is a water-resistant layer on the contact surface — chocolate or a fat film.

**Quantified example of the barrier working.** A patent on confectionery color bleed (US6110515) records that uncoated sugar-shelled candies — M&M's-type — bleed color within five minutes in water and turn the dessert colored and soggy, which is why manufacturers add them shortly before serving rather than packaging them in advance. A cocoa butter coating of 25–200 µm, roughly 1–8% of the piece's weight, showed essentially no bleed for over 28 weeks in ice cream at −25°C.

**The core conflict with goal 3.** Durable crunch requires a fat barrier. Fat costs calories against goal 2 and wrecks the carb-to-fat ratio I care about. The two best partial answers found so far: Grape-Nuts, which at 4.5% of calories from fat is the slowest-softening item in the low-water-activity class because it's a dense baked nugget rather than a puff; and soy protein crisps, which deliver crunch at 3.6% of calories from fat because they're protein rather than starch, though they carry almost no carbohydrate.

**And a direct contradiction of my own habit.** The recommended fix for crisp loss includes *larger* piece sizes. The mix-in cycle pulverizes, which maximizes distribution through the pint but also maximizes surface area exposed to moisture. Crushing and crunch retention pull against each other, which is exactly the tension in goal 3.

## Open questions

Roughly in order of how much they'd change what I do.

1. **What is the correct PAC target for a Creami, as opposed to a churn machine?** This is the biggest gap. PAC/POD would let me compute any substitution instead of guessing, but every published target assumes a product that must be scoopable straight from the freezer. A Creami needs the opposite: a block hard enough for the blade to shave cleanly. Gelato aims at 220–280. Partially answered as of 21 Oct — the Ice Creamery site publishes 20–25 per 100g of mix for storage at −18°C (below 15 is "quite hard") and 24–28 for milk ice cream. That reconciles with the gelato figure of 220–280, which is the same number on a per-1000g basis, so my guess that a Creami wants materially lower PAC looks wrong. Still open: that target is framed as "easily scoopable," which is a churn-machine requirement a Creami doesn't have, so it may be inherited from gelato practice rather than derived for a shaved block. Worth confirming empirically.
2. **Can durable crunch be achieved without a fat barrier?** Everything found so far says the barrier has to be fat or chocolate, which fights goals 2 and 3 simultaneously. Worth investigating: whether any non-fat barrier works (confectioner's glaze, shellac, protein or sugar-glass coatings); how fast inclusions actually soften at −18°C versus the −25°C used in the commercial literature; and whether dense low-porosity items can be ranked by how slowly they soften.
3. **How much does protein substitute for fat, mechanically?** My base is protein-heavy and fat-poor, which is an unusual formulation space. Microparticulated whey protein was commercialized as a fat replacer decades ago, so there should be real literature on what protein does and does not replace. This bears directly on whether goals 1 and 2 are actually in tension or only appear to be.
4. **Does the Creami's lack of overrun change the fat requirement?** Part of fat's contribution to mouthfeel in conventional ice cream works through stabilizing the air phase. A Creami incorporates little air. If fat's role is partly air-dependent, a low-fat base may be penalized less here than the textbooks imply — which would reframe the whole calorie-versus-quality trade.
5. **Stabilizer and bulking agents beyond xanthan.** Guar, locust bean, tara, carrageenan, inulin, and especially trehalose, which gelato guidance mentions as a way to add body and anti-freeze power without adding sweetness. Two concrete leads now: the ICSv2 blend (erythritol, CMC/Tylose, tara gum, xanthan, inulin, salt), and "synergistic interaction gels" — thickener combinations such as locust bean gum with xanthan that reportedly build gel networks able to mimic missing fat. The second is the most promising thing found so far for reconciling goals 1 and 2.
6. **What total solids target should a low-fat Creami base hit, and how do I compute it from a recipe?** Partially answered: MSNF of 7–11% is the published range, and PAC has an explicit formula — sum each sweetener's grams multiplied by its coefficient, divide by total mix weight, multiply by 100. Still open: a total solids target as distinct from MSNF, and what shifts when fat is near zero.
7. **Polyol tolerance ceiling.** A pint is eaten in one sitting, so 40–45g of erythritol or allulose is a single large dose. What's the practical limit before GI effects, and does it differ between the two?
8. **A systematic procedure for converting a conventional recipe.** Goal 4 restated as a research question: given a published ice cream formula — Jeni's, a Ben & Jerry's clone, a gelato base — what is the step-by-step method for converting it to a low-fat, lactose-containing, non-sugar Creami base while knowing what each substitution costs? Principles are useful; a repeatable procedure is what I actually want.

## The dedicated machine question

My premise — that churn machines need high fat and that conflicts with the calorie ceiling — is half right, and the half that's wrong points somewhere useful.

**Where it's right.** Under FDA 21 CFR 135.110, anything labeled ice cream must contain at least 10% milkfat, and American premium products run higher. So conventional ice cream formulations do assume fat I can't afford under a 400–500 calorie pint.

**Where it's wrong.** Ice cream is not the only churned tradition. Gelato typically runs 4–8% fat and has no US standard of identity constraining it. More to the point, gelato also runs *low* overrun — it's churned slowly and incorporates little air. So gelato achieves good texture at roughly half the fat **without** relying on whipped-in air. The lever it uses instead is sugar and solids balancing, which is precisely what PAC/POD is for.

That reframes the whole question. The relevant body of practice for a low-fat, high-flavor frozen dessert is **gelato formulation, not ice cream formulation** — and gelato's core technique transfers to the machine I already own, because it's about what goes in the mix, not about how it's frozen.

**What a dedicated machine would actually add:** overrun. Air is volume with no calories, and a Creami incorporates almost none. Under a calorie cap, more volume per calorie is worth something. But gelato demonstrates that low fat plus low air can still be good, so this looks like a secondary benefit rather than the thing standing between me and goal 1.

**What a dedicated machine would not fix:** the fat requirement itself. Churning doesn't reduce the fat a formula needs. It changes how the mix is frozen, not what the mix has to contain.

**Working conclusion, to be tested rather than assumed:** a dedicated machine looks like a poor buy for these constraints, and the higher-leverage move is to adopt gelato balancing theory on the Creami. I'd like this challenged properly — specifically whether overrun turns out to matter more than the gelato comparison suggests, and whether any machine category (soft-serve, frozen yogurt, a compressor gelato machine) is genuinely built for low-fat formulations.

## Ruled out and corrected

Things already checked, so they don't get researched again. Several of these are corrections to claims made confidently and then withdrawn.

- **Lactose avoidance does not reduce lactase production.** Intestinal lactase appears to be constitutive; withdrawing lactose from the diet does not reduce its expression, and the post-weaning decline is genetically determined. What *is* adaptable is the colonic microbiome, which adjusts to regular lactose. So keeping lactose is defensible on microbiome and preference grounds, not on enzyme-preservation grounds.
- **No lactose-containing ultra-filtered milk exists.** Fairlife, Darigold FIT, Organic Valley Protein Plus and Pioneer Pastures all list lactase enzyme in the ingredients. The whole category is lactose-free by design. The substitute is regular milk plus nonfat dry milk powder.
- **Pasteurization method is not a meaningful factor in a frozen dessert.** I was told UHT milk would leave a cooked note and should be avoided; that was withdrawn. Fairlife is itself UHT, cold suppresses the relevant volatiles, and traditional custard bases are deliberately heated past 170°F anyway. Not worth re-opening.
- **"Add it at serving instead" is out of scope.** Every mix-in goes through the mix-in cycle. Any solution that depends on adding inclusions at serving time doesn't answer the question.
- **Freeze-dried fruit is not a crunch ingredient through the mix-in cycle.** It rehydrates. It's still a good mix-in, but as a flavor and water-binding agent, not for texture.
- **Meringue cookies dissolve into the base; angel food cake becomes mush.** Both were suggested and withdrawn.
- **Swapping sweetener for real sucrose makes pints firmer, not softer.** Counterintuitive, but it follows from molecular weight: sucrose has the lowest anti-freeze power of the three options.
- **Category-level ingredient research is not good enough; SKUs differ materially.** Great Value grahams beat Nabisco by roughly 5% on carb per calorie. More dramatically, HallPass candy's label shows 29g carbohydrate per 43g bag, but subtracting fat and protein calories leaves only about 9g of metabolizable carbohydrate — and 45% of its calories are fat. Any ingredient recommendation needs actual label data.
- **The better-for-you snack category is built against a carb-seeking goal.** HallPass, Catalina Crunch and similar products exist specifically to replace metabolizable carbohydrate with fiber and polyols. For someone trying to *hit* a carb target, mainstream products are strictly better.

One tool worth carrying forward: **usable carb = (calories − fat×9 − protein×4) ÷ 4.** It's an approximation, but it exposes polyol- and fiber-inflated labels immediately. The theoretical ceiling for carbohydrate per 100 calories is 25g.

## Sources already consulted

| Source | What it gave |
| --- | --- |
| [Ice Cream Technology eBook — H. Douglas Goff, U. Guelph](https://books.lib.uoguelph.ca/icecreamtechnologyebook/front-matter/introduction/) | Free, Creative Commons, by a professor who co-authors the standard academic text. Identified but not yet worked through — should be the backbone of the research |
| [Inclusions in Ice Cream — Liz Miller, UW–Madison](https://foodsci.wisc.edu/wp-content/uploads/2024/10/Liz-Miller-Inclusions-in-Ice-Cream.pdf) | The five inclusion failure modes and their fixes. Most useful single source on goal 3 |
| [Tharp & Young on ice cream — Dairy Foods](https://dairyfoods.com/articles/83213-tharp-young-on-ice-cream) | Moisture migration into dry inclusions is unavoidable; fat and chocolate coatings as the commercial barrier |
| [Minimizing added sugars in ice cream — Dairy Foods](https://dairyfoods.com/articles/93602-how-to-minimize-added-sugars-in-ice-cream) | Sugar's structural role; allulose depresses freezing point substantially enough that formulators offset it |
| [Erythritol in light protein ice cream — Jungbunzlauer](https://www.jungbunzlauer.com/wp-content/uploads/2026/03/06-JBL-AR-ERYLITE%C2%AE-Erythritol-in-light-protein-ice-cream-2021-012.pdf) | The 2.8× freezing point figure, the recrystallization problem, 6.5–8.0% dosing, and that allulose+erythritol beats either alone. **Manufacturer source** |
| [Erythritol vs allulose PAC/POD — gelato balancing](https://freegelatobalancing.app/blog/erythritol-allulose) | The PAC/POD numbers and how gelato balancing works. **Sells software** |
| [Ninja Creami sweetener guide](https://simplydesserts.us/ninja-creami/sweetener-guide/) | Machine-specific sweetener behavior; disagrees with my own experience on erythritol. **Vendor source** |
| [Freeze-dried fruit powder in ice cream — USDA ARS summary](https://www.foodanddrinktechnology.com/news/32475/lower-melting-rate-for-ice-cream-with-freeze-dried-fruit-powder/) | Fruit powder absorbs liquid, reduces ice crystals, works as a stabilizer alternative |
| [Lactose digestion and lactase expression — PMC](https://pmc.ncbi.nlm.nih.gov/articles/PMC6669050) | Intestinal lactase is constitutive; withdrawing lactose doesn't reduce it. The microbiome is what adapts |
| [Patent US6110515 — confectionery color bleed](https://patents.justia.com/patent/6110515) | Quantified barrier performance: cocoa butter at 1–8% of weight, no bleed 28+ weeks at −25°C |
| [Allulose browning — Splenda](https://www.splenda.com/blog/everything-you-need-to-know-about-allulose/) | Allulose browns like sugar and faster; erythritol doesn't. **Sells allulose** |
| [Gelato vs ice cream — fat and overrun](https://www.healthline.com/nutrition/gelato-vs-ice-cream) | FDA 21 CFR 135.110 sets 10% minimum milkfat for ice cream; gelato is 4–8% with low overrun and no US standard |
| [Jeni's base formula — Saveur](https://www.saveur.com/article/Recipes/Jenis-Ice-Cream-Base/) | Eggless architecture: cornstarch slurry for body, cream cheese for richness, corn syrup for softness |

Added 21 Oct: **[jhermann's Ice Creamery](https://jhermann.github.io/ice-creamery/info/faq/)** — a Creami-specific MkDocs site by Jürgen Hermann (CC-BY-NC). The most directly useful resource found so far. It publishes the metrics the recipes are balanced on (PAC/FPDF with targets, MSNF 7–11%, a protein-to-energy ratio), a [per-ingredient PAC and MSNF dataset](https://jhermann.github.io/ice-creamery/info/nutrition/), a [glossary](https://jhermann.github.io/ice-creamery/info/glossary/) with the PAC formula and target ranges, a named stabilizer blend, a detailed sweetener comparison covering sucrose, dextrose, trehalose, allulose, erythritol and xylitol blends, and a "Light" recipe category under 75 kcal per 100g — which lands inside my calorie ceiling. It is a practical recipe site rather than a formulation text: it states the metrics without deriving them and lists stabilizers without explaining their mechanisms, so it complements Goff rather than replacing him. Self-published by an experienced hobbyist, not peer-reviewed; its coefficients and targets appear drawn from standard gelato literature.

**Four of the five non-academic technical sources have a commercial interest** — an erythritol maker, an allulose seller, a software vendor and a product vendor. I'd weight them on the physics they agree on (molecular weight drives anti-freeze power; erythritol recrystallizes) and discount their rankings and recommendations.

Books identified but not yet read: Goff & Hartel, *Ice Cream*, 7th ed. (Springer, 2013) — the academic standard; Dana Cree, *Hello, My Name Is Ice Cream* — formulation for a home cook; Stella Parks, *BraveTart* — reverse-engineering American desserts; Jeni Britton Bauer, *Jeni's Splendid Ice Creams at Home*; *The Flavor Bible* and *The Flavor Matrix* for pairing. Not yet consulted: r/ninjacreami, which is where the machine-specific knowledge actually lives since no book covers the Creami.

## Starting prompt

```markdown
I've made 100+ pints in a Ninja Creami working through four recipe books, and they
already taste close to real ice cream. I'm done following recipes — I want the
formulation science so I can build and debug bases myself.

My goals, in priority order:

1. Understand the science well enough to read a conventional ice cream or gelato
   recipe, identify which ingredient does which job, and work out what to
   substitute and what that substitution costs. This is the main thing. I want a
   repeatable procedure, not more recipes.
2. Good-tasting ice cream very close to the real thing.
3. A whole pint, everything in, under 400-500 calories, using traditional
   lactose-containing milk rather than ultra-filtered.
4. Real mix-in chunks that survive the mix-in cycle without turning to mush.

Constraints: Ninja Creami, no churn machine. 0.1g scale, immersion blender.
Sweetener is erythritol/monk fruit, open to allulose or blends. I track macros
closely and am often short on carbohydrate, so low-fat carb-dense ingredients are
worth more to me than they would be to most people. I want to keep the lactose.

I'm attaching a handoff document covering what's already established, what's been
ruled out, and a numbered list of open questions. Read it first and don't
re-derive what's in it.

Start with open question 1 (the correct PAC target for a Creami as opposed to a
churn machine) and question 8 (a systematic procedure for converting a
conventional recipe), since those two unlock the rest. Prioritize primary and
academic sources — the Guelph ice cream technology ebook is free and linked in the
doc. Several sources I've already used have commercial interests, which the doc
flags.

Where the evidence is thin or contested, say so rather than resolving it for me.
```

Export this doc to Markdown or PDF and attach it to the new chat, or share the link if the new session can read it. The prompt assumes the doc is available — without it, the new chat will re-derive several things that are already settled, including at least two claims that were tested and withdrawn.
