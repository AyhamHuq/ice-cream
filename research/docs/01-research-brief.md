# Creami Formulation Science: Consolidated Research Brief (Stage 1 output)

Tag key: **[PF §x]** = `personal-findings.md` ("Creami Research Handoff", Oct 20, 2026, with a 21 Oct addition). **[IA §x]** = `initial-analysis.md` ("Creami low-calorie vanilla base: findings for expert review", Oct 21, 2026). "My arithmetic" means I computed it, and it is not in either source. Items marked FLAG are contradictions, gaps or contested evidence that I have deliberately not resolved.

---

## 1. Purpose

The user (Ayham Huq) has made 100+ Ninja Creami pints from four recipe books, and the pints already taste close to real ice cream [PF §intro, §Current setup]. What is missing is the formulation science. They want to build a base from first principles. It must stay under a 400–500 kcal per-pint ceiling and use traditional lactose-containing milk. Mix-in chunks must survive the Creami cycle intact [PF §intro]. The deepest aim is capability, not recipes. They want to read a conventional ice cream or gelato recipe, see which ingredient does which job, and work out what to substitute and what each substitution costs [PF §Goals]. A second, narrower exercise tried to design a cream-free vanilla base under 300 kcal per pint. It modeled versions A–E in the Scoopulator calculator and queued them for review by a professional [IA §Summary, §Goal and constraints].

---

## 2. Goals in priority order

**Handoff list [PF §Goals], as numbered:**
1. Good-tasting ice cream very similar to real ice cream.
2. Limit calories while using traditional milk: one pint, everything in, not above 400–500 kcal.
3. Real mix-in chunks that aren't pulverized.
4. Replicate real ice cream recipes, understand what I'm making, and know where to pivot. The handoff calls this "crucial" and says "Goal 4 is the priority. The others are outcomes; goal 4 is the capability." The user would rather be able to read a conventional recipe and work out substitutions than get more recipes. Openness to a dedicated machine is folded into this goal, with the preliminary belief that such machines need high fat, which "very likely conflicts with goal 2".

**Re-ordering in the Starting prompt [PF §Starting prompt]:**
1. Understand the science: read a conventional ice cream or gelato recipe, identify each ingredient's job, and work out substitutions and their cost. "I want a repeatable procedure, not more recipes."
2. Good-tasting ice cream very close to the real thing.
3. Whole pint, everything in, under 400–500 kcal, with traditional lactose-containing milk, not ultra-filtered.
4. Real mix-in chunks that survive the mix-in cycle.

So the old goal 4 becomes new 1, the old 1 becomes 2, the old 2 becomes 3, and the old 3 becomes 4. The prompt also tells the next session to start with Q1 (Creami vs churn PAC target) and Q8 (conversion procedure), "since those two unlock the rest." It asks for primary and academic sources first, with the Guelph ebook named, and says to flag thin or contested evidence rather than resolve it [PF §Starting prompt].

**IA's own goal [IA §Goal and constraints]:** a healthy, cream-free, plain-vanilla Creami base that is under 300 kcal for the whole pint (a base of roughly 380–430 g). It must be scoopable straight out of the machine, sweet enough for a strong sweet tooth, and able to carry a flavor later (e.g. gooey butter cake). "Healthy" here means low sugar and moderate saturated fat. This goal is narrower than the handoff's and sits partly in tension with it (see §8).

---

## 3. Hard constraints and setup

**Machine and pint size**
- Ninja Creami [PF §Current setup; IA §Summary]. The handoff says "Ninja Creami, no churn machine" in the starting prompt [PF §Starting prompt].
- Pint size is not stated in either doc. The handoff says "pint" and "multiple pints for batch prep". IA says "whole pint (a base of roughly 380 to 430 g)". FLAG: standard 16 oz vs Deluxe 24 oz is ambiguous. The 446 g mix in [PF] and 382–431 g mixes in [IA] suggest the 16 oz pint (my inference only). The Ice Creamery site and repo mark recipes Deluxe (24 oz) / Standard (16 oz).

**Workflow and programs [PF §Current setup]**
- Freeze 16+ hours.
- Hot water on the pint for 60 seconds.
- Spin on Lite Ice Cream, then Respin.
- Mix-ins go in on the mix-in cycle, not at serving.
- [IA §Cross-check] confirms Lite Ice Cream for sugar substitutes and a re-spin for crumbly results, from the Ninja guide and recipe blogs. It adds that Ninja's guide says the machine is built for pints frozen at a freezer setting between 9 °F and −7 °F (about −13 to −22 °C), and says nothing about the hot-water step. [PF] is the only source for hot water.

**Milk**
- Regular 1% or 2% lactose milk, already in use. The user wants the lactose [PF §Current setup, §Starting prompt].
- Ultra-filtered milk (Fairlife and similar) is excluded as a design choice: all of it is lactase-treated [PF §Ruled out].
- Nonfat dry milk is allowed and favored [PF §Established base; IA §Recipes].
- IA uses 2% milk, plus whole milk in C [IA §Recipes].

**Pantry and sweeteners**
- [PF]: monk fruit blend (Lakanto), erythritol-leaning. "Closest to real sugar in a Creami in my experience"; open to allulose or blends. Also xanthan gum, vanilla bean paste and salt. No store constraint [PF §Current setup].
- [IA §Goal and constraints]: Lakanto (monk fruit and erythritol blend), vegetable glycerin, xylitol, xanthan gum, guar gum, nonfat dry milk. Inulin, polydextrose and pure monk fruit extract are new to the user. IA introduced them [IA §Goal and constraints].

**Equipment [PF §Current setup]:** 0.1 g precision scale, immersion blender, multiple pints. IA notes that 0.25 g of monk fruit needs a 0.01 g scale or a diluted stock [IA §Calculator assumptions 4].

**Macro tracking and carb-seeking [PF]:** The user tracks macros closely and strength trains. They are "frequently short on carbohydrate", so carb-dense, low-fat ingredients are worth more to them. They want to hit a carb target, so the better-for-you snack category is built against them [PF §Current setup, §Ruled out]. IA does not mention carb-seeking. Its bases A–D push fiber and cut metabolizable carbohydrate (see §8).

**Calorie caps**
- [PF]: one pint, everything in, not above 400–500 kcal, mix-ins included [PF §Goals].
- [IA]: under 300 kcal per pint for a plain vanilla base [IA §Goal]. The mix-in flavor comes later and is not counted.

**Out of scope [PF §Ruled out]**
- "Add it at serving instead" is out of scope. Every mix-in goes through the mix-in cycle.
- Do not re-open pasteurization or UHT (§6).
- Category-level ingredient advice is not enough; label data is required.

---

## 4. The user's recipes

### 4a. Ingredients, grams per pint

| Ingredient (g) | Book base [PF §Current setup] | Original [IA] | Second [IA] | A Lean [IA] | B Light fiber [IA] | C Whole milk [IA] | D Max solids [IA] | E Own ingredients [IA] |
|---|---|---|---|---|---|---|---|---|
| 1% or 2% milk | 400 | 380 (2%) | 380 (2%) | 340 (2%) | 340 (2%) | – | 330 (2%) | 380 (2%) |
| Whole milk | – | – | – | – | – | 340 | – | – |
| Nonfat dry milk | – (a +25 g scenario is used in the PAC discussion) | – | 5 | 15 | 15 | 12 | 20 | 10 |
| Monk fruit blend (Lakanto) / erythritol | 40–45 (monk fruit blend) | 40 (erythritol) | 30 | 8 | 9 | 8 | 5 | 12 |
| Xylitol | – | – | 10 | – | – | – | – | 4 |
| Glycerin | – | – | 2.5 | – | – | – | – | 1.5 |
| Inulin | – | – | – | 15 | 8 | 12 | 15 | – |
| Polydextrose | – | – | – | 15 | 8 | 15 | 25 | – |
| Xanthan gum | 1 (¼ tsp) | 1 | 0.5 | 0.4 | 0.4 | 0.4 | 0.4 | 0.4 |
| Guar gum | – | – | 1.5 | 0.6 | 0.6 | 0.6 | 0.6 | 0.6 |
| Salt | a pinch | 1 | 1 | 0.5 | 0.5 | 0.5 | 0.5 | 0.5 |
| Vanilla bean paste | 5 | omitted | omitted | omitted | omitted | omitted | omitted | omitted |
| Pure monk fruit powder | – | – | – | 0.25 | 0.25 | 0.25 | 0.25 | 0.25 |

Notes:
- Vanilla is omitted from every IA version, controls included, because Scoopulator has no match for vanilla paste [IA §Recipes].
- Lakanto is entered as plain erythritol [IA §Recipes].
- IA's "Original" and "Second" are called "the user's own recipes" / "two controls" [IA §Recipes, §Goal]. FLAG: IA's Original (380 g milk, 1 g salt, no vanilla) is not identical to the handoff's book base (400 g milk, 5 g vanilla paste, a pinch of salt). The docs do not say whether Original is a simplified model of the book base. Second (xylitol, glycerin, guar, 5 g dry milk) appears only in IA.
- Mix totals stated: book base ≈ 446 g [PF §Current setup, PAC calc]. IA total weights are in 4b.

### 4b. Reported metrics

| Recipe | Weight g | kcal/pint | Firmness at −9 °C (% water frozen) | Sweetness | Total solids | MSNF | Fiber g | Protein g | Freezing-point depression / PAC | Method |
|---|---|---|---|---|---|---|---|---|---|---|
| Book base (400 g 2% milk, 40 g erythritol, ~3 g sugar from paste) | ≈446 | not stated | not stated | not stated | "maybe 20–25%" (rough estimate) | MSNF ≈36.5 g in the milk | not stated | not stated | **PAC ≈ 30** (13,490 / 446 × 100 by the unrounded calc) | Hand calculation, Ice Creamery PAC formula, lactose counted [PF §Current setup] |
| Fairlife-equivalent base (before regular 2% milk) | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | PAC ≈ 27 | Hand calc: regular 2% milk adds +2.2 PAC, +25 g NFDM adds +1.2, giving about 30 [PF §Current setup] |
| Original | 422 | 198 | 63% (soft serve) | 6.9% | 19.8% | 8.1% | 0 | 12.8 | "about 35" (controls, grouped) | Scoopulator [IA §Results, §Cross-check] |
| Second | 431 | 248 | 61% (soft serve) | 8.0% | 21.3% | 9.1% | 0 | 14.6 | "about 35" (controls, grouped) | Scoopulator |
| A Lean | 395 | 272 | 74.5% (standard) | 18.9% | 23.0% | 11.4% | 26.7 | 16.9 | 19.5–22 (A–E range) | Scoopulator |
| B Light fiber | 382 | 251 | 76.8% (standard) | 19.4% | 20.4% | 11.8% | 14.2 | 16.9 | 19.5–22 | Scoopulator |
| C Whole milk | 389 | 289 | 75.7% (standard) | 19.0% | 22.7% | 10.6% | 24.1 | 15.5 | 19.5–22 | Scoopulator |
| D Max solids | 397 | 294 | 72.3% (standard) | 18.7% | 25.5% | 12.3% | 35.7 | 18.3 | 19.5–22 | Scoopulator |
| E Own ingredients | 409 | 244 | 77.3% (standard) | 19.3% | 17.2% | 10.7% | 0 | 16.4 | 19.5–22 | Scoopulator |
| Calibration: Ninja's Vanilla Ice Cream (cream, whole milk, sugar; cream cheese and vanilla left out) | n/a | 1,006 | 76.9% (standard scoop) | n/a | 34.9% | n/a | n/a | n/a | 16.8 | Scoopulator [IA §Cross-check] |

Scoopulator targets stated in IA, for the "Low Fat Ice Cream" profile [IA §Results, §Assumptions 6]:

| Target | Value |
|---|---|
| kcal | under 300 |
| Firmness | 70 to 78% |
| Sweetness | 11 to 20% |
| Total solids | 28 to 32% |
| MSNF | 12 to 14% |
| Emulsifiers | 0.1 to 0.8% (every version shows 0%) |

Two cautions on the metrics:
- IA calls the freezing-point depression "score" without stating its units or formula (see §8).
- IA's hand check of A gives about 263 kcal against Scoopulator's 272. Inputs were approximate: milk ≈0.5 kcal/g, NFDM ≈3.6 kcal/g "from memory", inulin 1.5, polydextrose 1, erythritol 0.2 [IA §Assumptions 3]. Vanilla paste is missing, which is roughly 5–10 kcal (approximate) [IA §Assumptions 5].

### 4c. Scoopulator recipe URLs (reusable by later stages) [IA §Recipes]

The ingredient-ID mapping is my inference from the table rows, and IA does not state it: usdaff-746778 = 2% milk, usdaff-746782 = whole milk, usdaff-746775 = salt, usdafndds-2705585 = nonfat dry milk, usdafndds-2710266 = pure monk fruit powder. Every URL shares the prefix `https://scoopulator.app/calc?target=low-fat-ice-cream&serving=creami-spin&ingredients=`, followed by:

- Original: `usdaff-746778:380,erythritol:40,usdaff-746775:1,xanthan-gum:1`
- Second: `usdaff-746778:380,erythritol:30,usdaff-746775:1,usdafndds-2705585:5,xanthan-gum:0.5,guar-gum:1.5,xylitol:10,glycerin:2.5`
- A Lean: `usdaff-746778:340,usdafndds-2705585:15,inulin:15,polydextrose:15,erythritol:8,xanthan-gum:0.4,guar-gum:0.6,usdaff-746775:0.5,usdafndds-2710266:0.25`
- B Light fiber: `usdaff-746778:340,usdafndds-2705585:15,inulin:8,polydextrose:8,erythritol:9,xanthan-gum:0.4,guar-gum:0.6,usdaff-746775:0.5,usdafndds-2710266:0.25`
- C Whole milk: `usdaff-746782:340,usdafndds-2705585:12,inulin:12,polydextrose:15,erythritol:8,xanthan-gum:0.4,guar-gum:0.6,usdaff-746775:0.5,usdafndds-2710266:0.25`
- D Max solids: `usdaff-746778:330,usdafndds-2705585:20,inulin:15,polydextrose:25,erythritol:5,xanthan-gum:0.4,guar-gum:0.6,usdaff-746775:0.5,usdafndds-2710266:0.25`
- E Own ingredients: `usdaff-746778:380,usdafndds-2705585:10,erythritol:12,xylitol:4,glycerin:1.5,xanthan-gum:0.4,guar-gum:0.6,usdaff-746775:0.5,usdafndds-2710266:0.25`

IA states that A–E were each reopened to confirm the headline numbers. None of the recipes has been made [IA §Summary]. The only "Original" and "Second" status IA gives is "the user's two existing recipes," which are predicted soft-serve.

---

## 5. Established facts

### 5.1 Base and texture [PF §Established base and texture]
- **Master variables.** Total solids and freezing point depression. Free water forms detectable crystals, so anything that binds or displaces water helps.
- **Conventional vs this base.** Conventional ice cream runs 10–16% milkfat and 36–40% total solids. The user's base is roughly 2% fat and "maybe 20–25%" total solids.
- **Why ultra-filtered milk works.** Fairlife is 13 g protein and 6 g sugar per cup, against regular milk's 8 g and 12 g. It has more protein and less water. The books specify it for texture, not macros.
- **Nonfat dry milk is the highest-leverage single addition found.** 30 g is 109 cal, 16 g carb, 11 g protein, 0.2 g fat. It raises protein, total solids, lactose and carbohydrate at almost no fat cost.
- **Freeze-dried fruit powder acts as a stabilizer.** USDA ARS work found it absorbs liquid, reduces ice crystals and is presented as an alternative to xanthan and sodium alginate. Strawberry was most effective. It pulls free water out of a base, the opposite of fresh fruit.
- **The Creami generates little overrun** because it shaves a frozen block. Low fat therefore penalizes it less than a churn machine, but book formulas assume air incorporation it won't get. This is the handoff's reading; whether the machine truly incorporates so little air is not measured (see Q4).
- **Cold suppresses sweetness and aroma.** The base should taste slightly too sweet and too salty at room temperature.
- **Untested techniques:** toasting milk powder in a dry pan to deep golden (described as dried, concentrated, nonfat brown butter); steeping and straining aromatics in warmed milk; cooking a starch or custard base instead of relying on xanthan alone.
- **Baseline PAC arithmetic (user's method) [PF §Current setup].**
  - Ice Creamery formula, lactose counted: 400 g 2% milk gives about 36.5 g MSNF (non-fat portion × 0.093), so about 19.9 g lactose at PAC 100.
  - 40 g erythritol at PAC 280.
  - About 3 g sugar from the vanilla paste.
  - Total 13,490 over 446 g, so PAC ≈ 30. That is above the 20–25 storage band and at the top of the 24–28 milk ice cream band.
  - Sweetener supplies about 83% of the total.
  - Fairlife to regular 2%: roughly doubles lactose over 400 g and adds about +2.2 PAC. Adding 25 g NFDM adds about 13 g lactose and about +1.2 PAC. Together the base goes from about 27 to about 30.
  - Assumes lactose PAC = 100 on molar grounds; the site's per-ingredient dataset would give the exact coefficient.
- **PAC formula (Ice Creamery) [PF §Open questions Q6]:** sum each sweetener's grams × its coefficient, divide by total mix weight, multiply by 100.
- **Lactose and PAC [PF §Established sweeteners].** Lactose is 54.5% of MSNF and contributes to freezing point depression. The PAC method is specifically recommended when lactose levels vary or run high enough to make the product too soft. Regular milk and NFDM both raise lactose and so push PAC up independently of the sweetener.
- **Overall hypothesis [PF §Current setup], testable:** nominal PAC 30 should spin soft, yet erythritol behaves best. If erythritol recrystallizes, effective PAC is well below 30. That would explain the good behavior and the need for hot water plus respin.

### 5.2 Sweeteners [PF §Established sweeteners]

| Sweetener | PAC (anti-freeze) | POD (sweetness) | Browns? |
|---|---|---|---|
| Sucrose | 100 | 100 | Yes |
| Allulose | ~190 | ~70 | Yes, faster than sugar |
| Erythritol | ~280 | ~60–70 | No |

- PAC and POD are deliberately decoupled, both indexed to sucrose = 100. This is the framework for substitution that none of the ice cream books cover.
- Erythritol's 280 follows from molecular weight (122 vs sucrose 342, so about 2.8× molecules per gram). The Jungbunzlauer report (manufacturer source) confirms 2.8× independently.
- **Paradox.** On paper erythritol should be the softest, but in practice it is reported hardest. The same manufacturer report says erythritol crystallises after freezing more readily than sugar and hardens texture in deep-freeze storage. Once out of solution it stops acting as a solute, so effective PAC falls well below 280.
- **Creami-specific reasoning for liking erythritol.** A churn machine wants maximum PAC for scoopability at −18 °C. A Creami wants a solid block for the blade to shave, since a base not frozen solid spins to soup. Gelato guidance treats erythritol at 100–120 g per 1000 g as too soft. Erythritol's grittiness is something the Creami blade destroys by design. Creami vendor guidance (Simply Desserts, a vendor source) disagrees: it ranks erythritol as most likely to freeze hard and recommends a 10–15 minute counter thaw plus a respin. That is already the user's workflow, so the effect may be real but masked.
- **Blends converge.** The manufacturer report found allulose alone gave poor texture, and allulose plus erythritol improved texture and scoopability. Creami vendor guidance says pair erythritol with allulose or a starch stabilizer. Eli's affiliate page prefers allulose/erythritol blends with monk fruit. The handoff counts these as three sources with different incentives and one conclusion.
- **Other settled points.** Both sweeteners are roughly 60–70% as sweet as sucrose, so a 1:1 swap by weight under-sweetens. Erythritol is recommended at 6.5–8.0% of recipe weight (manufacturer). Removing sugar without replacing its freezing point depression gives, in the report's words, "a very hard and icy texture." Erythritol does not brown, so any caramel or butterscotch note must come from allulose or toasted milk solids.
- **Dairy Foods source.** Allulose depresses freezing point enough that formulators offset it [PF §Sources].
- **Monk fruit [IA §Assumptions 4].**
  - Scoopulator's pure monk fruit powder behaves like about 240× sugar by weight. 0.25 g adds about 15 sweetness points to a 395 g pint, roughly 60 g sugar-equivalent.
  - Suppliers list extracts standardized to 40–50% mogroside V at 200–300× sugar (ChemPoint, a supplier). A retail powder at 1% mogroside V claims only about 4× (GnG, a retailer).
  - The dose must be re-derived from the label.
- **Lakanto [IA §Assumptions 5].** Lists only erythritol and monk fruit extract and is sold as 1:1 for sugar. Entered as plain erythritol, so real sweetness is probably a little higher than modeled. [PF §Current setup] similarly notes monk fruit blends are usually erythritol-bulked.
- **Sweetness model result [IA §Calculator results].** In Scoopulator's model, cutting erythritol from 30–40 g to 5–9 g and taking sweetness from 0.25 g monk fruit extract is how the sweetness target is met without a soft pint.

### 5.3 Lactose [PF]
- Lactose counts toward PAC (above).
- **Lactase and lactose avoidance** are covered under "Ruled out" (§6). Keeping lactose is defensible on microbiome and preference grounds, not enzyme-preservation grounds.

### 5.4 Mix-ins [PF §Established mix-ins]

Food science sorts inclusions by failure mode. These are the five classes from the UW–Madison deck (Liz Miller):

| Class | Examples | How it fails | Fix |
|---|---|---|---|
| Fat-based | Chips, flakes, barks, coatings | Waxy, low flavor: the mouth is cold | Lower melt point, more flavor, more sugar so it dissolves on the tongue |
| Hygroscopic | Toffee, fudge | Sticky, loses piece identity | Fat or confectionery coating; larger pieces |
| Low water activity | Crisp rice, pretzels, cookies | Loses crispness | Fat or chocolate coating; **larger pieces**; keep cold and dry |
| Textural | Fudge, chewy caramel | Hardens over time | More fat, lower melt point, glycerin or invert sugar |
| Variegate | Sauces, ribbons | Sinks | Colder draw temperature |

- **Coconut oil trick.** Eli's chips-plus-coconut-oil shell is textbook: oil lowers chocolate's melt point so it dissolves on the tongue rather than reading waxy.
- **Moisture migration into dry, unprotected inclusions is unavoidable** (Tharp & Young, Dairy Foods). Ice cream sandwich wafers go soggy within days and the trade accepts it. The commercial countermeasure is a water-resistant chocolate or fat film.
- **Quantified barrier [US6110515, patent].** Uncoated sugar-shelled candies bleed color within five minutes in water. A cocoa butter coating of 25–200 µm (roughly 1–8% of piece weight) showed essentially no bleed for over 28 weeks in ice cream at −25 °C.
- **Core conflict with the crunch goal.** Durable crunch needs a fat barrier. Fat costs calories and wrecks the carb-to-fat ratio. Best partial answers so far:
  - Grape-Nuts, at 4.5% of calories from fat, is the slowest-softening item in the low-water-activity class because it is a dense baked nugget.
  - Soy protein crisps give crunch at 3.6% of calories from fat but carry almost no carbohydrate.
- **Direct contradiction of habit.** The fix for crisp loss includes larger pieces. The mix-in cycle pulverizes, which spreads pieces through the pint but maximizes surface area exposed to moisture.
- **Freeze-dried fruit as a mix-in** is a flavor and water-binding agent, not a crunch ingredient (it rehydrates).
- **Evidence limits.** All mix-in barrier data are at −25 °C (commercial) while the user stores at about −18 °C (see Q2).

### 5.5 Dedicated machine conclusion [PF §The dedicated machine question]
- **Premise half right.** FDA 21 CFR 135.110 requires at least 10% milkfat for anything labeled ice cream, and premium products run higher, so conventional ice cream formulations assume fat the user can't afford under the cap.
- **Half wrong.** Gelato typically runs 4–8% fat, has no US standard of identity, and also runs low overrun (slow churn, little air). Gelato gets good texture at about half the fat without relying on air. Its lever is sugar and solids balancing, which is what PAC/POD is for. So the relevant body of practice is gelato formulation, and it transfers to the Creami because it concerns what goes in the mix.
- **A dedicated machine would add** overrun, meaning air as volume with no calories. This is judged a secondary benefit.
- **It would not fix** the fat requirement, because churning changes how the mix is frozen, not what the mix must contain.
- **Working conclusion, to be tested:** a dedicated machine looks like a poor buy for these constraints. The higher-leverage move is gelato balancing theory on the Creami. The user wants this challenged (see Q4). It asks specifically whether overrun matters more than the gelato comparison suggests, and whether any machine category (soft-serve, frozen yogurt, compressor gelato machine) is built for low-fat formulations.

### 5.6 Inulin and polydextrose [IA §Inulin and polydextrose]
- **Rationale.** Both are soluble fibers that add body and solids at 1 to 1.5 kcal per gram and lower the freezing point less than sugars do. That is why A–D use them. IA asserts the freezing-point point without a cited source here. Precedent is rated strong for inulin and moderate for polydextrose. The main concern is digestive tolerance at pint-sized doses.

| | Inulin | Polydextrose |
|---|---|---|
| What it is | Fructan fiber from chicory or agave; thickens, adds body, mimics some fat | Glucose polymer; bulking agent, no sweetness |
| Ice cream use | Studied at 2–8%. Around 4% worked best in several studies; 6–8% lowered flavor scores in a vegan ice cream (Narala 2022; reduced-fat study; inulin and erythritol study) | Frozen-confection patent US 6,896,923 prefers 1–10% by weight (excerpt only; the PDF would not open). Used with sorbitol and sucralose or stevia in a low-fat, sugar-free ice cream study (Egyptian J Dairy Sci) |
| Calories | 1.5 kcal/g suggested for labeling; modeled range 0–2.5 (Roberfroid 1999) | 1 kcal/g; FDA allows it on labels |
| Tolerance | News report of a challenge study: most healthy people tolerate up to 10 g/day of native inulin, and the inulin was supplied by an inulin maker (commercial-interest flag). Placebo-controlled trial: 5 and 7.5 g agave inulin still raised bloating and gas slightly. A FODMAP | Mean laxative threshold about 90 g/day or 50 g in one dose (EFSA). At 20 g/day, a mild laxative effect with few other complaints (J Nutr 2013) |
| Per pint, A / B / C / D | 15 / 8 / 12 / 15 g (3.8 / 2.1 / 3.1 / 3.8% of the mix) | 15 / 8 / 15 / 25 g (3.8 / 2.1 / 3.9 / 6.3%) |

- A, C and D exceed the roughly 10 g/day inulin level. D's 25 g polydextrose exceeds the 20 g/day dose that gave a mild laxative effect. A whole pint of A also delivers 8 g erythritol. No study tested the three together, and EFSA notes laxative effects should be weighed in combination with other compounds that act the same way. B is the conservative choice and a half pint halves every figure.
- In the studies IA saw, inulin replaced part of fat in mixes of roughly 2–10% fat. A–E are under 3% fat, so inulin here works mainly as a bulking agent, which IA labels an extrapolation.
- **Cross-check precedent [IA §Cross-check].** No home Creami recipe found uses inulin or polydextrose, so A–D are untested modeled formulas. Commercial light ice creams and food-science studies do use both. Home recipes use sugar-free pudding mix, protein powder and Greek yogurt, then re-spin. Halo Top lists prebiotic fiber, and the Ochsner dietitian roundup says other light ice creams list inulin or chicory root fiber.

### 5.7 Calculator calibration and assumptions [IA §Calculator assumptions to verify, §Cross-check]
1. **Serving temperature.** Scoopulator's Creami Spin preset assumes −9 °C right after processing. IA found no source for that figure. Ninja's guide says only that the machine is built for pints frozen at 9 °F to −7 °F (about −13 to −22 °C). The calibration run (Ninja's own vanilla landing in the standard-scoop band at 76.9%) supports the preset for conventional recipes. A probe thermometer reading right after a spin would settle it.
2. **Program and re-spin** are not modeled.
3. **Calories** are Scoopulator's totals; its per-ingredient values were not displayed (hand check gives 263 vs 272 for A).
4. **Monk fruit potency** (see 5.2).
5. **Lakanto and vanilla** (see 5.2).
6. **Targets.** The Low Fat Ice Cream profile asks for 28–32% total solids and 0.1–0.8% emulsifiers; no version meets either. The controls already fall short on solids (19.8% and 21.3%).
- **Evidence cautions [IA §Cross-check].** The Creami evidence is a handful of recipe blogs and one manufacturer guide, not controlled tests. IA set aside several scraped or machine-written Creami tip pages that repeat each other without a named source.
- **Cross-check numbers [IA §Cross-check].**
  - Live Simply base: 238 kcal per pint from 240 g 2% milk, 50 g nonfat Greek yogurt, 7 g sugar-free pudding mix and 15 g protein powder (plus 8 g peanut butter powder in the full recipe). Lite Ice Cream program, with a re-spin and 10–20 g milk for a crumbly first spin.
  - Slimming Eats: pudding-mix-based low-calorie base; warns that very watery low-calorie milks can turn icy.
  - Ninja guide: official lite recipes (fat-free half-and-half with a stevia sugar blend; coconut cream with 3 tbsp monk fruit/erythritol blend; cream and milk with 2 tbsp of that blend plus agave). They use more sweetener and more fat than A–D.
  - Halo Top: 280 kcal per pint; per half cup 3 g fiber, 5 g sugar alcohol, 5 g protein; reviewers call it icier, slightly grainy and harder than regular ice cream. About 12 g fiber per pint (IA's own arithmetic, 4 × 3 g) against 14–36 g in A–D (IA says "14 to 36"; table shows B 14.2 up to D 35.7, with E and controls at 0).

---

## 6. Ruled out / corrected [PF §Ruled out and corrected]

1. Lactose avoidance does not reduce lactase production; the enzyme is constitutive and the post-weaning decline is genetic. Only the colonic microbiome adapts, so keeping lactose is defensible on microbiome and preference grounds, not enzyme preservation.
2. No lactose-containing ultra-filtered milk exists. Fairlife, Darigold FIT, Organic Valley Protein Plus and Pioneer Pastures all list lactase. The substitute is regular milk plus nonfat dry milk powder.
3. Pasteurization method (UHT) is not a meaningful factor in a frozen dessert. The "cooked note" claim was withdrawn: Fairlife is itself UHT, cold suppresses the volatiles, and custard bases are heated past 170 °F anyway.
4. "Add it at serving instead" is out of scope. Every mix-in goes through the mix-in cycle.
5. Freeze-dried fruit is not a crunch ingredient through the mix-in cycle (it rehydrates). It is still a good flavor and water-binding mix-in.
6. Meringue cookies dissolve into the base and angel food cake becomes mush. Both suggestions were withdrawn.
7. Swapping to real sucrose makes pints firmer, not softer, because sucrose has the lowest anti-freeze power of the three options (molecular weight).
8. Category-level ingredient research is not good enough; SKUs differ. Great Value grahams beat Nabisco by roughly 5% on carb per calorie. HallPass candy's label shows 29 g carbohydrate per 43 g bag, but subtracting fat and protein calories leaves about 9 g metabolizable carbohydrate, and 45% of its calories are fat. Any ingredient recommendation needs actual label data.
9. The better-for-you snack category is built against a carb-seeking goal (HallPass, Catalina Crunch and similar replace metabolizable carbohydrate with fiber and polyols), so mainstream products are strictly better for someone who wants carbs.

**Tool to carry forward [PF §Ruled out]:** usable carb = (calories − fat×9 − protein×4) ÷ 4. It is an approximation that exposes polyol- and fiber-inflated labels. The theoretical ceiling is 25 g carbohydrate per 100 calories. Observation (my own, not in the sources): fiber and polyol calories (e.g. 1–1.5 kcal/g) would be counted as usable carb by this formula, so it overstates usable carb for IA's fiber-heavy bases.

---

## 7. Open questions, merged and deduplicated

### From the handoff [PF §Open questions], original numbering

**Q1. Correct PAC target for a Creami, as opposed to a churn machine?** Status: **partially answered (21 Oct).**
- Known: the Ice Creamery site publishes 20–25 per 100 g of mix for storage at −18 °C (below 15 is "quite hard") and 24–28 for milk ice cream. That reconciles with the gelato 220–280, the same number per 1000 g, so the user's guess that a Creami wants materially lower PAC "looks wrong."
- Still open: the target is framed as "easily scoopable," a churn-machine requirement the Creami doesn't have, so it may be inherited from gelato practice rather than derived for a shaved block.
- Closes with: an empirical test on the user's own pints (PAC vs spin quality), plus the Goff text on hardness and draw temperature. Cross-ref Q13 (the −9 °C assumption) and the erythritol recrystallization hypothesis. IA's firmness target also rests on "standard scoop" logic (see §8).

**Q2. Durable crunch without a fat barrier?** Status: **open.**
- Known: the barrier has to be fat or chocolate (§5.4).
- Closes with: evidence on non-fat barriers (confectioner's glaze, shellac, protein or sugar-glass coatings); softening rates at −18 °C vs the −25 °C commercial data; a ranking of dense low-porosity items by softening speed.

**Q3. How much does protein substitute for fat, mechanically?** Status: **open.**
- Known: microparticulated whey protein was commercialized as a fat replacer decades ago. Bears on whether goals 1 and 2 truly conflict.
- Closes with: dairy-science literature (Goff & Hartel) on what protein does and does not replace.

**Q4. Does the Creami's lack of overrun change the fat requirement?** Status: **open.**
- Known: part of fat's mouthfeel role works through stabilizing the air phase, and a Creami incorporates little air. Also bears on the dedicated-machine challenge.
- Closes with: Goff on fat/air structure, and any measured Creami overrun. Also whether overrun matters more than the gelato comparison suggests.

**Q5. Stabilizers and bulking agents beyond xanthan?** Status: **open, with two leads.**
- Known: candidates are guar, locust bean, tara, carrageenan, inulin and trehalose (body and anti-freeze without sweetness).
- Leads: the ICSv2 blend (erythritol, CMC/Tylose, tara gum, xanthan, inulin, salt), and "synergistic interaction gels" such as locust bean gum with xanthan, which could mimic missing fat. The handoff calls the second "the most promising thing found so far" for reconciling goals 1 and 2.
- Merge with IA (Q14 and Q9): IA adds guar, inulin and polydextrose to this space.
- Closes with: mechanism and dose data for each stabilizer; Ice Creamery's named stabilizer blend.

**Q6. Total solids target for a low-fat Creami base, and how to compute it?** Status: **partially answered.**
- Known: MSNF of 7–11% is the published range. PAC has an explicit formula (§5.1).
- Still open: a total solids target distinct from MSNF, and what shifts when fat is near zero.
- Cross-ref: IA's Scoopulator profile asks for 28–32% total solids and 12–14% MSNF, which disagrees with the 7–11% MSNF range (see §8).

**Q7. Polyol tolerance ceiling.** Status: **open.**
- Known: a pint is eaten in one sitting, so 40–45 g of erythritol or allulose is one large dose. Whether the limit differs between the two is unknown.
- Merge with IA Q9 (fiber load) and Q10 (erythritol/xylitol CV signals): IA treats this as stacked doses of GI-active ingredients (polydextrose, inulin, erythritol) and cites EFSA on combination effects.
- Closes with: published GI dose-response data for erythritol, allulose, xylitol, plus an individual self-test.

**Q8. A systematic procedure for converting a conventional recipe.** Status: **open**, and the highest-value question.
- Wanted: a step-by-step method for converting a published formula (Jeni's, a Ben & Jerry's clone, a gelato base) to a low-fat, lactose-containing, non-sugar Creami base, knowing what each substitution costs.
- Closes with: Goff and Hartel on ingredient roles; the Ice Creamery metrics; a worked example. Jeni's eggless architecture (cornstarch slurry for body, cream cheese for richness, corn syrup for softness, from Saveur) is a candidate test case.

### New from IA [IA §Open questions for the reviewing professional; §Calculator assumptions]

**Q9. Fiber load and tolerance per pint.** Status: **partially answered / open.**
- Known: A–D carry 8–15 g inulin and 8–25 g polydextrose per pint (§5.6). A, C, D exceed the roughly 10 g/day inulin tolerance level, and D exceeds the 20 g/day polydextrose dose that was mildly laxative. IA does not know the person's digestive history. A half pint halves every figure.
- Merge with PF Q7 (polyol tolerance).
- Closes with: professional/dietitian input; stacked-dose GI data; a graded personal trial (B first).

**Q10. Erythritol and xylitol cardiovascular signals; how much weight?** Status: **open (contested).**
- Known: Cleveland Clinic linked higher blood erythritol to heart attack and stroke in a large cohort, and a small trial of healthy volunteers found 30 g erythritol made platelets more reactive. A 2024 study reported similar signals for xylitol (NIH summary). A 2023 Frontiers commentary cautions about what the original findings can show. IA did not raise this earlier in the conversation, when its xylitol answers covered only digestion and dogs.
- A–D hold 5–9 g erythritol and no xylitol; the controls hold 30–40 g. E has 12 g erythritol and 4 g xylitol, and IA's text does not discuss E on this question.
- Note: the handoff's preferred sweetener is erythritol at 40–45 g, and it does not discuss CV risk (see §8).
- Closes with: primary literature on dose and causality, plus the reviewing professional.

**Q11. Monk fruit potency and dosing practicality.** Status: **open.**
- Known: Scoopulator behaves as ~240× sugar. Supplier extracts run 200–300× (40–50% mogroside V), a retail 1% product only ~4×. The dose depends on the product label. 0.25 g needs a 0.01 g scale (the user has 0.1 g) or a diluted stock. IA asks whether a ready-made blend would be better.
- Closes with: label data for an actual product and a dilution protocol. Note the user's scale is 0.1 g [PF], so 0.25 g cannot be weighed directly.

**Q12. Emulsifier gap.** Status: **open.**
- Known: Scoopulator shows 0% emulsifier in all versions against a 0.1–0.8% target. A test version with a 17 g pasteurized egg yolk reached 310 kcal, just over the 300 cap.
- Cross-ref Q5 (ICSv2 includes CMC; stabilizer/emulsifier roles may differ).
- Closes with: what emulsifiers do in a shaved-block product and whether lecithin (or yolk) is worth the kcal.

**Q13. Does Scoopulator's −9 °C Creami preset hold?** Status: **partially answered.**
- Known: no source found for −9 °C. Ninja's guide gives the freezer range only. Ninja's vanilla lands in the standard-scoop band, which supports the preset for conventional recipes. Unconfirmed for A–E.
- Closes with: a probe thermometer reading right after a spin.

**Q14. Do simpler thickeners (sugar-free pudding mix, protein powder, Greek yogurt) beat inulin/polydextrose?** Status: **open.**
- Known: home recipes use them (Live Simply 238 kcal pint; Slimming Eats). No home recipe found uses inulin or polydextrose.
- Cross-ref Q5 (stabilizer options) and Q3 (what protein replaces).
- Closes with: side-by-side trials or a calculator comparison.

**Q15. Program and re-spin not modeled.** Status: **open.**
- Known: Scoopulator ignores which Creami program is used or whether a re-spin follows. The user's workflow is hot water, Lite Ice Cream, Respin. Ninja recommends Lite Ice Cream for sugar substitutes and re-spin for crumbly results.
- Closes with: before/after temperature or texture readings for each step.

**Q16. Will A–D scoop as predicted (texture trial)?** Status: **open (no version made).**
- Known: proposed trial is A first, B second (or B if fiber is a worry), as a half pint, with temperature recorded after the spin.
- Related: Slimming Eats warns that very watery low-calorie milks can turn icy, and solids of 17–26% may fall into that warning.

**Q17. Do the Scoopulator solids/MSNF targets (28–32% TS, 12–14% MSNF) and 70–78% frozen-water firmness apply to a Creami shaved block?** Status: **open (not asked by IA directly).** This is my consolidation of IA §Assumptions 1 and 6 with PF Q1 and Q6. Closes with the Goff text and the Ice Creamery targets.

**Q18. Does inulin work mainly as a bulking agent below 3% fat?** Status: **open.** IA labels it an extrapolation from studies at ~2–10% fat.

---

## 8. Conflicts and tensions between the two docs (flagged, not resolved)

**8.1 Calorie cap: 400–500 kcal (PF) vs under 300 kcal (IA).**
- PF: whole pint, everything in (mix-ins included), 400–500 kcal [PF §Goals]. IA: base only, under 300 kcal, flavor added later [IA §Goal]. IA's recipes land at 198–294 kcal.
- Matters because the 100–200 kcal difference could pay for cream, fat or protein that IA excluded, and IA's design trades solids for calories. PF's own Ice Creamery "Light" category is under 75 kcal per 100 g, which gives roughly under 337 kcal for a 450 g pint (my arithmetic, using the 446 g mix).
- Settled by: the user's decision on whether the base-only cap or the all-in cap governs, and a mix-in kcal estimate.

**8.2 PAC ≈ 30 (PF) vs Scoopulator's "freezing-point depression" scores (IA): same scale?**
- PF: PAC ≈ 30 for the book base, by the Ice Creamery formula (sum of grams × coefficient / mix weight × 100), with targets 20–25 (storage at −18 °C) and 24–28 (milk ice cream), and below 15 "quite hard." IA: controls score "about 35," Ninja's vanilla 16.8, A–E 19.5–22 on "freezing-point depression," feeding a % frozen-water firmness model at −9 °C. IA does not state units, formula, or whether lactose is counted.
- Matters because the numbers are suspiciously similar for the controls (30 vs ~35, with different milk weights and no vanilla) but not for the reference: Ninja's vanilla (34.9% solids, 1,006 kcal, a cream recipe) scores 16.8, below the Ice Creamery 24–28 milk ice cream band. In IA, a score of 35 predicts soft-serve, which matches PF's "nominal PAC 30 should spin soft." But PF's pints are made, taste good, and are served after hot water and respin, while IA predicts the same recipe class comes out soft-serve. PF's hypothesis (erythritol recrystallization) would make Scoopulator over-credit erythritol, but neither doc tests it.
- Settled by: recomputing every recipe with the Ice Creamery coefficients and comparing to Scoopulator's scores (Stage 3); getting Scoopulator's method documentation; and an empirical test.

**8.3 Erythritol as preferred (PF) vs cutting it to 5–9 g and the CV flag (IA).**
- PF: erythritol-leaning, 40–45 g, "closest to real sugar in a Creami," with the Creami-specific argument that a hard block is desirable. PF does not mention cardiovascular risk. IA: cuts erythritol from 30–40 g to 5–9 g in A–D (E: 12 g plus 4 g xylitol), citing CV signals, and replaces it with inulin/polydextrose/monk fruit. The cuts in IA are driven partly by the firmness model, not only by safety.
- Also a three-way dose gap on erythritol (my arithmetic): 40 g in 446 g is about 9.0%, vs the manufacturer's recommended 6.5–8.0% and the gelato "too soft" band of 100–120 g per 1000 g (10–12%). IA's A–D are about 1.3–2.4% (5–9 g over 382–397 g) and the controls are 7.0% (Second) and 9.5% (Original).
- Settled by: the CV literature (Q10), the Ice Creamery sweetener comparison, and a trial.

**8.4 Overrun assumptions.**
- PF: the Creami makes little overrun and conventional recipes assume air it won't get; this is central to the fat and dedicated-machine arguments (Q4). IA: never mentions overrun, and its Scoopulator "Creami spin" model's overrun assumption is unknown; its kcal are per weight so unaffected, but firmness and sweetness percentages could be.
- Settled by: Scoopulator documentation of the Creami preset, and a measured pint volume or weight.

**8.5 Sweetener modeling.**
- Both docs treat Lakanto as plain erythritol (PF's PAC calc uses 40 g erythritol; IA enters erythritol). IA states the real sweetness is probably higher. PF's POD table gives erythritol ~60–70 and treats monk fruit as a bulking blend. IA's design depends on pure monk fruit extract at 0.25 g with a potency (~240×) that conflicts with retail powders (~4× at 1% mogroside V).
- Settled by: the Lakanto label (erythritol vs monk extract proportions) and the Ice Creamery coefficients.

**8.6 Pint size.** Neither doc states standard 16 oz vs Deluxe 24 oz. PF's 446 g mix and IA's 382–431 g mixes are internally consistent with a 16 oz pint (inference only). Settled by asking the user.

**8.7 Cream-free (IA) vs the handoff's openness.**
- PF never excludes cream. It cites cream cheese and cream in Jeni's, and a 400–500 kcal cap could accommodate some fat. IA excludes cream outright and has under 3% fat, with moderate saturated fat as a health preference. PF's base (400 g 1–2% milk) is itself near-zero cream.
- Matters because IA's emulsifier gap and the Ninja guide's higher-fat recipes (more sweetener and more fat) suggest cream is a tradeoff, not a given. A 17 g yolk already takes IA's base to 310 kcal.
- Settled by: the user's stance on cream and a test case in the 300–500 kcal range.

**8.8 Carb-seeking (PF) vs fiber-forward design (IA).**
- PF: the user is often short on carbs and wants low-fat, carb-dense ingredients. The better-for-you category (fiber and polyol replacement) is "built against" that goal. IA's A–D cut metabolizable carbohydrate by swapping erythritol for 14–36 g fiber (inulin and polydextrose), which is exactly the replacement pattern PF warns against. IA never mentions carb-seeking.
- Settled by: the user's priority (macros vs satiety/low sugar) and a usable-carb check on each IA recipe.

**8.9 MSNF and solids targets.** PF: MSNF 7–11% (Ice Creamery); conventional ice cream 36–40% total solids; user's base maybe 20–25%. IA: Scoopulator target 28–32% total solids and 12–14% MSNF. IA's Original (8.1%) is within PF's range but under Scoopulator's; C (10.6%) and A (11.4%) are within PF's range but below IA's. Nobody states which is right for a Creami (links to Q6 and Q17). Settled by: the Goff text and the Ice Creamery glossary.

**8.10 Model vs lived experience.** IA's model puts E (lowest solids at 17.2%, zero fiber) at the best firmness (77.3%), while IA itself worries that solids of 17–26% may come out icy (Slimming Eats). Separately, PF reports good pints from a base the model calls soft-serve. Settled by trials and a temperature measurement.

**8.11 Which book?** IA says the user "read a book on ice cream formulation (freezing-point depression, PAC; POD)" and asked whether its claims match real food science [IA §Goal and constraints]. PF says Goff & Hartel, Dana Cree, BraveTart and others are "identified but not yet read." The two may be consistent (a different book) but the title is not given in either.

**8.12 Stabilizers.** PF explores locust bean/tara/CMC/trehalose and "synergistic interaction gels"; IA adds guar (0.6–1.5 g) plus inulin/polydextrose and never mentions LBG, tara, CMC or trehalose. The overlap is only xanthan and inulin. Settled by the stabilizer research in Q5.

**8.13 Hot water step.** PF only. IA's cross-check sources mention only Lite Ice Cream and a re-spin. Not necessarily a conflict, but IA's model cannot represent it.

---

## 9. Sources already consulted

### From the handoff [PF §Sources]
| Source | What it gave | Flag / status |
|---|---|---|
| Ice Cream Technology eBook, H. Douglas Goff, U. Guelph | Free, CC, by a professor who co-authors the standard academic text | **Identified, NOT yet worked through. Should be the backbone.** |
| Inclusions in Ice Cream, Liz Miller, UW-Madison | Five failure modes and fixes | Exhausted for Q2/mix-in classes |
| Tharp & Young, Dairy Foods | Moisture migration unavoidable; fat and chocolate coatings | Exhausted |
| Minimizing added sugars in ice cream, Dairy Foods | Sugar's structural role; allulose offset | Exhausted |
| Jungbunzlauer, Erythritol in light protein ice cream (2021 report) | 2.8× freezing point, recrystallization, 6.5–8.0% dosing, allulose+erythritol beats either | **Manufacturer source (erythritol maker)** |
| freegelatobalancing.app, Erythritol vs allulose PAC/POD | PAC/POD numbers, gelato balancing | **Sells software** |
| Simply Desserts Ninja Creami sweetener guide | Machine-specific sweetener behavior; disagrees with the user on erythritol | **Vendor source** |
| USDA ARS summary via Food & Drink Technology | Freeze-dried fruit powder as stabilizer | Exhausted |
| PMC6669050, lactose digestion and lactase expression | Lactase constitutive | Exhausted |
| Patent US6110515, confectionery color bleed | Barrier quantification | Exhausted |
| Splenda, allulose browning | Browns like sugar, faster | **Sells allulose** |
| Healthline, gelato vs ice cream | 21 CFR 135.110, gelato 4–8% fat | Exhausted |
| Saveur, Jeni's base formula | Eggless architecture | Exhausted (candidate worked example for Q8) |
| **jhermann Ice Creamery** (https://jhermann.github.io/ice-creamery/info/faq/), added 21 Oct | PAC/FPDF targets, MSNF 7–11%, protein-to-energy ratio, per-ingredient PAC/MSNF dataset (nutrition page), glossary (PAC formula, ranges), named stabilizer blend, sweetener comparison (sucrose, dextrose, trehalose, allulose, erythritol, xylitol blends), "Light" category under 75 kcal/100 g | Self-published hobbyist, CC-BY-NC, not peer-reviewed; coefficients/targets appear drawn from standard gelato literature; states metrics without deriving them. **Only partially mined: Stage 2 should go deeper.** |

The handoff's own flag: four of the five non-academic technical sources have a commercial interest (an erythritol maker, an allulose seller, a software vendor, a product vendor). The handoff says to weight them on the physics they agree on (molecular weight drives anti-freeze power; erythritol recrystallizes) and discount their rankings and recommendations. Eli Mack's affiliate page is also a commercial source.

**Identified but not yet read [PF]:** Goff & Hartel, *Ice Cream* 7th ed.; Dana Cree, *Hello, My Name Is Ice Cream*; Stella Parks, *BraveTart*; Jeni Britton Bauer, *Jeni's Splendid Ice Creams at Home*; *The Flavor Bible*; *The Flavor Matrix*. **Not yet consulted:** r/ninjacreami, where Creami-specific knowledge lives.

### From the initial analysis [IA §Sources]
- **Opened in full:** Scoopulator pages, the Healthline Halo Top review, and the Ninja CREAMi inspiration guide.
- **Read only as search-result excerpts (abstract or page text):** all other pages. The US 6,896,923 patent PDF would not open.
- **Calculator, recipes, products:** Scoopulator; Live Simply; Slimming Eats; Ninja guide (opened); Halo Top/Healthline (opened); Ochsner dietitian roundup; Lakanto listing (Instacart/Natural Grocers).
- **Inulin:** Narala 2022 (DOAJ); reduced-fat ice cream inulin study (SUJST); the I3L light-fat/reduced-sugar formulation study; Roberfroid 1999; Fox News report on an inulin challenge study (inulin supplied by an inulin maker); agave inulin tolerance trial (RSC 2014).
- **Polydextrose:** US 6,896,923 (excerpt only); Egyptian J Dairy Sci low-fat sugar-free ice cream; EFSA re-evaluation (PMC7792022); J Nutr 2013 (PubMed 23427334); FDA guidance on non-digestible carbohydrates.
- **Monk fruit and sweetener safety:** ChemPoint (supplier); GnG organic monk fruit powder (retailer); Cleveland Clinic erythritol release 2024; NIH xylitol summary 2024; Frontiers 2023 commentary on erythritol and CV risk.

**Already exhausted or not worth redoing:** the PF sources above except Goff and the Ice Creamery site; the IA excerpt-only sources are only thinly read, so a primary read (especially the EFSA, J Nutr 2013, Cleveland Clinic and Roberfroid papers) is still valid for Q9/Q10, but the Scoopulator calibration runs, the Ninja guide and the Halo Top review need no repeat.

---

## 10. Research agenda for the next two stages

### Stage 2: website https://jhermann.github.io/ice-creamery/info/
Pages: faq, glossary, principles, ingredients, nutrition, recipe-guide, tips+tricks, plating, polar-ice-creamery, web-resources.

Extract, tagged with the question each serves:

1. **PAC/FPDF targets and the exact formula** (Q1, Q6, Q8): the target ranges per product type (the 20–25 storage band, 24–28 milk ice cream, below 15 "quite hard"); whether targets are for Creami vs churned; how lactose and MSNF coefficients are applied; the "per 100 g of mix" basis.
2. **Per-ingredient PAC / POD / MSNF coefficients** (Q1, Q6, Q8, and for recomputing §4 recipes): 1%, 2% and whole milk; nonfat dry milk; erythritol; xylitol; allulose; glycerin; inulin; polydextrose; monk fruit (blend vs pure); xanthan; guar; salt; vanilla paste; trehalose; lactose itself (confirm the PF assumption PAC = 100).
3. **Total-solids targets** and what the site says about near-zero-fat bases (Q6, Q17); MSNF 7–11% justification (conflict 8.9).
4. **Stabilizer guidance** (Q5, Q12, Q14): the ICSv2 blend composition and dose; other named blends; any mechanisms, LBG/xanthan synergy, tara, CMC, guar doses; any emulsifier or egg-yolk guidance.
5. **Sweetener comparison** (Q7, Q10, conflict 8.3, 8.5): the site's ranking and notes on erythritol recrystallization, hardness, dose limits and GI effects; blends of allulose/erythritol/xylitol; whether it recommends erythritol at the user's 9% dose.
6. **Creami program, re-spin and temperature guidance** (Q13, Q15): Lite Ice Cream vs Ice Cream choice, hot-water or counter-thaw advice, freeze time and temperature, re-spin recommendations; any measured output temperatures.
7. **The "Light" category definition** (under 75 kcal per 100 g) and its stats; what PAC/MSNF/total solids the site's Light recipes hit (conflict 8.1).
8. **Mix-in guidance** (Q2, Q3-adjacent): how the site handles mix-in cycle, crunch retention, coatings.
9. **Anything on Creami vs churn PAC targets** (Q1, Q4): overrun statements, and any derivation of the shaved-block requirement.
10. **Protein-to-energy ratio** metric and protein as a fat replacer (Q3).
11. **Citations the site gives** (which gelato texts underlie its numbers), so the primary sources can be traced.

### Stage 3: the jhermann repo
Contents per the orchestrator: 133 recipes with stats tables, a nutrition DB CSV (`scripts/nutrition-db.csv`), the recipe-converter code that computes stats (`scripts/ice-cream-recipe.py`), the "expert-glacier" skill, and the IceCreamCalc REST API.

**Claims and numbers to verify:**
- The Ice Creamery PAC formula and coefficient values used by the code, against PF's hand calculation (13,490 / 446 → ≈30; lactose 19.9 g at PAC 100; erythritol 280; allulose ~190) and the +2.2 / +1.2 PAC shifts.
- Whether the code counts lactose via MSNF × (a fraction) and which fraction (PF used non-fat portion × 0.093 and 54.5% lactose of MSNF).
- The code's treatment of inulin, polydextrose, glycerin, guar, xylitol, monk fruit, and whether those coefficients exist.
- Targets coded in the stats (PAC bands, MSNF 7–11%, "Light" threshold).

**Recompute (hand PAC per the Ice Creamery formula, with MSNF, total solids, fat, kcal, protein ratio):**
- The book base (400 g milk, 40–45 g blend, 5 g vanilla paste, 1 g xanthan).
- Original, Second, and A–E from §4a.
- Also the Fairlife-equivalent baseline (the "27") and the +25 g NFDM scenario.

**Comparisons to make:**
- Ice Creamery method vs Scoopulator (the freezing-point depression scores and firmness percentages in §4b) vs IceCreamCalc REST API, for every §4a recipe. Specifically test whether the Scoopulator scores (controls about 35; Ninja vanilla 16.8; A–E 19.5–22) correlate with Ice Creamery PAC, and whether the scales are comparable (conflict 8.2).
- Where Ninja's vanilla (cream, whole milk, sugar) sits on the Ice Creamery PAC scale.
- kcal and fiber checks against the nutrition DB (IA's hand check of A: ~263 vs 272).
- Usable-carb check on each IA recipe (conflict 8.8).
- Erythritol % of mix across recipes (conflict 8.3).

**Likely analog recipes to locate in the repo's 133 recipes** (names unverified; the orchestrator suggests these categories): Light-category recipes (<75 kcal/100 g), erythritol-sweetened recipes, dairy-based (milk plus NFDM) recipes, and vanilla/buttermilk bases. For each, compare PAC, MSNF, total solids and kcal against A–E, and note which stabilizer blend and program/re-spin the recipe specifies. Also check the `expert-glacier` skill for any formal conversion procedure (Q8) and any treatment of lactose, erythritol recrystallization and fiber (Q5, Q9).

---

## Notes for the orchestrator (ambiguities not resolved by the two docs)

1. **Authorship and voice of IA.** It is signed @Ayham Huq but written as an AI-assisted report ("I introduced both," "the user's two existing recipes"). Whether Original and Second are real recipes the user makes, and how they relate to the book base, is not stated.
2. **Pint size** (16 oz vs 24 oz Deluxe) is never given.
3. **Scoopulator ingredient IDs** (usdaff-/usdafndds-) are not mapped in IA; my mapping in §4c is inferred from the table.
4. **Scoopulator "freezing-point depression" units and method** are undocumented, so §8.2 cannot be settled from the docs. IA also doesn't say whether Scoopulator counts lactose or assumes overrun.
5. **Which "book on ice cream formulation"** IA's user read (IA §Goal) vs PF's "not yet read" list.
6. **PF's MSNF coefficient.** It says "non-fat portion × 0.093" to get about 36.5 g MSNF from 400 g of 2% milk, but does not show how the non-fat portion is derived. Treat 36.5 g as the stated figure, not a derivation.
7. **PF carries a 21 Oct addition** (the Ice Creamery site) inside a doc dated Oct 20. The Q1 and Q6 status notes ("partially answered as of 21 Oct") are from that update.
8. **The Ice Creamery site** was consulted only at the level the handoff summarizes (faq, nutrition, glossary pages named). Which of its other pages were read is not stated.
9. **IA does not say whether any of the A–E, Original or Second recipes has been compared against an actual pint**, only that none of A–E has been made.
10. **I did not read the repo or website**, per instructions. The repo and stage descriptions (133 recipes, file names, the API) come from the orchestrator's brief, not from the two docs.