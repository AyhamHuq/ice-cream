# Creami formulation research: synthesis

Oct 25, 2026 · compiled from the three stage reports in this folder.

- `01-research-brief.md` (stage 1) consolidates `old/personal-findings.md` and `old/initial-analysis.md`.
- `02-site-science.md` (stage 2) mines the Ice Creamery info site.
- `03-repo-validation.md` (stage 3) checks stage 2 against jhermann's repo and runs the user's recipes through IceCreamCalc.

Citations below point to those files as `01 §x`, `02 §x` and `03 §x`; each stage report holds the primary `file:line` and URL evidence.

Evidence strength:

- **Strong:** reproduced from code or data, or two independent tools agree.
- **Moderate:** consistent empirical practice by one experienced author, or one tool.
- **Weak:** unsourced or AI-assisted statements.
- **Contested:** sources disagree.

Calculations marked "(my arithmetic)" were done for this synthesis with the site's coefficients. They were not run through a calculator.

---

## 1. What changed

1. **Your PAC ≈ 30 is right, and it is where the site's author works.** The site's formula reproduces your hand figure: 30.1 without salt, about 31 with salt (03 §3 #16). IceCreamCalc agrees, giving 30.6 (03 §5). The author's 122 rated Creami recipes cluster at PAC 30–33, with a median of 30.7 (03 §3 #10). Your experience that these pints "taste close to real ice cream" fits that practice. **Strong** for the arithmetic, **moderate** for the target.

2. **The "Scoopulator 35 vs site 30" conflict was a salt-coefficient difference, not different physics.** Scoopulator's "freezing-point depression" uses the same per-100 g scale as PAC. It values salt at about 10.7 per gram and uses higher inulin and polydextrose coefficients. With those, it reproduces both of its reported ranges (03 §5). **Moderate**: this is a fit to ranges, not to Scoopulator's documentation.

3. **The low-cal bases A–E are a different kind of recipe from anything the author makes.** Their PAC is about 13–20, against the author's 30–33 (03 §5). Both calculators predict them firmer than your current pints. IceCreamCalc flags A–D as crumbly, at 94–97 on its scale where above 90 means "add liquid post spin". That index is undocumented. The old plan to "trial A first" (`old/initial-analysis.md`) rested on Scoopulator's verdict that your current base would come out soft-serve. That verdict judges the pint at about −9 °C straight after the spin. The author's 30–33 band instead aims for pints that stay scoopable in the freezer. See §3.1. **Contested.**

4. **You already meet the calorie cap.** On site values every variant is 203–319 kcal per pint. The book base alone is about 225 kcal, and the book base plus 25 g NFDM is 314 (03 §5). The under-300 goal holds for the base. The 400–500 cap only binds once mix-ins are counted, so the cap conflict (01 §8.1) is about mix-in budget, not base design. **Strong.**

5. **Your erythritol dose is above every source's ceiling.** You use 9.0–9.5% of the mix. The site says below 8%, the manufacturer's optimum is 6.5–8%, and no author recipe exceeds 6.8% plain erythritol (03 §3 #25). The author pairs erythritol with xylitol at 3:2 ("SweEX"), which works out to about 4% erythritol. **Strong** that you are above the ceilings. The ceilings themselves are texture rules from the site and one manufacturer study.

6. **Your hot-water step conflicts with the site.** The site says: "Do not run your tubs under hot water before the first spin". It warns the frozen block can come loose and spin in the tub, which risks the machine. Instead it uses a spoon "scrape test" and a 5–15 minute rest on the counter. It allows cold tap water for 15–30 seconds only after the first spin, as do 17 of the author's recipes (02 §6, 03 §6). **Moderate** (author's practice and warning), and this is the most practical change in this report.

7. **The total-solids targets of 28–33% are not what the author's rated recipes reach.** Those recipes estimate at about 19–25% total solids, with a median of 22% (03 §7 Q6). Your book base is at 19.6%. **Moderate.**

8. **Swapping erythritol out moves the dose problem to xylitol.** Your current base has 40 g erythritol in a pint eaten in one sitting. Moving to SweEX at the same PAC means about 27 g erythritol plus 18 g xylitol in your 446 g mix (03 §1 #5). That is above the site's own unsourced suggestion of 5–10 g of xylitol per day (02 §3 Q7). Xylitol also has the same cardiovascular signal as erythritol (01 §7 Q10). The author's 680 g Deluxe tubs are not one serving, so their per-tub doses don't carry over to a whole pint eaten at once. **Moderate**, my inference from the stage data.

---

## 2. Answers by open question

| Q | Answer | Strength |
|---|---|---|
| **Q1** PAC target for a Creami | In practice about **30–33 per 100 g of mix**. That is the band of one experienced author across 122 recipes, and it matches your experience. The pint comes out soft after spinning and is meant to firm up in the freezer. The author advises a refreeze above PAC 25 (02 §3 Q1). The glossary's 20–25 / 24–28 are generic storage and churned-ice-cream rules of thumb. Scoopulator's −9 °C "standard scoop" model judges a different moment, right after the spin, and would push PAC to about 17–20. No source derives a target for the Creami's shaved block. | Moderate; contested on framing (§3.1) |
| **Q2** Crunch without a fat barrier | Still open. The author's practice is to freeze and chop wafers, use larger pieces, and fold mix-ins into pockets. Cantuccini and chopped frozen mint wafers survive the mix-in cycle. The wiki's coating advice is AI-assisted and unsourced (02 §3 Q2). | Weak |
| **Q3** Protein vs fat | Only qualitative. Cheesecake Light has 0.6% fat and 6.5 g protein per 100 g, and the author rates it top. The site gives no equivalence ratio (02 §3 Q3, 03 §7 Q3). | Weak |
| **Q4** Overrun vs fat | The site doesn't cover it. IceCreamCalc's frozen-water and serving-temperature outputs shift when overrun changes from 25% to 0%: 3–4 points of frozen water, about 1–2 °C. So overrun matters to the models, but nobody has measured it for the Creami (03 §5). | Open |
| **Q5** Stabilizers | The best-covered question; see 02 §6 for compositions, doses and synergies. The author's Salty Stability blend is 110 g inulin, 18 g GMS, 9 g CMC, 6 g guar, 5 g salt and 2 g xanthan (150 g batch). It has a pantry substitute: 1.5 g guar, 0.5 g xanthan and 0.5 g salt per 15 g dose, which is ⅔ of that for a 16 oz pint. That uses only ingredients you own. Guar with xanthan at 3:1 is the "cold" synergy; locust bean gum with xanthan needs heat. Your gum doses are in range (03 §7 Q5). | Moderate |
| **Q6** Total-solids target | The author's rated low-fat bases sit at about **20–25%**. The 28–33% boxes are unsourced and not supported by the author's practice. Total solids are computed as the sum of solids per ingredient; neither the site nor the repo prints them (03 §2). | Moderate |
| **Q7** Polyol ceiling | Per pint, using texture ceilings: erythritol below 8% of the mix. The site's other numbers are unsourced: xylitol 5–10 g per day, gut effects from glycerin starting around 14 g per day, sorbitol at most 10% (02 §3 Q7). No gut-tolerance figure exists for erythritol or allulose. | Weak |
| **Q8** Conversion procedure | No written procedure exists. One is assembled in §4 from the author's method, the glacier skill's audit steps and two worked conversions that reproduce exactly (03 §4). | Moderate (assembled, not validated) |
| **Q9** Fiber load | Inulin in A–D (8–15 g per pint) is within the author's per-tub range, 7–23 g once scaled to 16 oz. The author never uses polydextrose. The site gives 8–18 g per day for inulin, unsourced. Earlier work found trial data near about 10 g per day (01 §5.6). | Weak to moderate |
| **Q10** Cardiovascular signals | Nothing new. The site only relays one remark from Polar Ice Creamery. This needs the primary literature. | Open |
| **Q11** Monk fruit dosing | 0.25 g in a pint is 0.056–0.063% of the mix, inside the site's 0.05–0.1% range. In A–E that 0.25 g supplies about 80% of the sweetness, so potency per product is critical. A dilution stock gets around the 0.1 g scale; see §3.4. | Moderate |
| **Q12** Emulsifier | The author's low-fat bases carry about 0.26% GMS, through Salty Stability. A–E have none. No evidence on what it does at near-zero fat (03 §7 Q12). | Weak |
| **Q13** Temperature after the spin | Two repo readings: −9.6 °C for Milky Whey (PAC 32.4) after Ice Cream plus Respin, and about −7 °C for an older Fruit Kefir after Respin. That supports a −9 °C order of magnitude (03 §1 #9). The effect of your hot-water step is unmeasured. | Moderate |
| **Q14** Simple thickeners | No head-to-head test. The author combines waxy maize starch (10–15 g per tub) with inulin. | Open |
| **Q15** Program and respin | Author's practice: Lite Ice Cream (or Frozen Yogurt), scrape down, then Respin or Mix-in. Cold water only after the first spin. Refreeze if PAC is above 25. Don't Respin leftovers (02 §3 Q15). | Moderate |
| **Q16** Will A–D scoop as predicted? | Probably not as Scoopulator says. Both calculators predict them firmer than your current pints, and IceCreamCalc flags them crumbly. They sit 12–17 PAC points below anything the author makes. | Moderate |
| **Q17** Scoopulator targets on a Creami | Its 28–32% total solids and 12–14% MSNF are above nearly all the author's rated recipes. MSNF above about 11–12% also risks lactose sandiness (03 §7 Q8). Whether its 70–78% frozen-water band fits a shaved block is unanswered. | Moderate |
| **Q18** Inulin below 3% fat | Nothing beyond the author using up to 35 g per tub. One recipe note credits inulin for fixing iciness. | Weak |

---

## 3. Unresolved contradictions

### 3.1 Which moment to optimize, right after the spin or after freezer storage (central)

The two calculators and the author disagree because they judge different moments:

- **Scoopulator** judges the pint at about −9 °C straight from the machine. It calls your PAC-30 bases "soft serve" and A–E "standard scoop".
- **The author** targets PAC 30–33 so pints come out soft and leftovers stay scoopable after freezing. That is the "Scoopable" tag.

You eat a whole pint in one sitting (01 §7 Q7), so the moment right after the spin may be the one that counts for you. That would favour Scoopulator's framing. But your lived experience at PAC ~30 is good, and the low-PAC side carries a crumbly-spin risk. A probe thermometer plus a texture rating on two pints would settle it (§5, tests 1 and 3).

### 3.2 Coefficient conflicts that move the numbers

- **Salt:**
  - 5.9 in the sheet and glossary, where the sheet double-counts an explicit salt row;
  - 1070 dissolved / 585 undissolved in the docs table;
  - about 585 in IceCreamCalc;
  - about 1,000 in Scoopulator (03 §8 #1).
- **Inulin:** 0.09, 0.22 or 0.134, depending on the source.
- **Polydextrose:** blank, 1.0 or 0.40.

Together these swing A–D by 4–7 PAC points (03 §5). They barely affect your book base, which has neither fiber.

### 3.3 Other open conflicts

- **Erythritol recrystallization.** Untested. Your hypothesis is that recrystallization lowers effective PAC, which is why a PAC-30 base behaves. The site describes recrystallization only as hardening over weeks of storage. No calculator models it (02 §9 #6, 03 §5).
- **Total solids and MSNF targets.** The literature and box figures say 28–33% total solids and 7–11% or 12–14% MSNF. The author's practice is about 20–25% total solids and mostly under 7% MSNF.
- **IceCreamCalc's limits:**
  - Its kcal are not additive. Treat its energy figures as unreliable for polyol and fiber recipes.
  - Its texture indices are undocumented, and it has no monk fruit ingredient (03 §9).
- **Calorie cap.** 300 versus 400–500 kcal. Your decision; see §1 item 4.

### 3.4 Monk fruit with a 0.1 g scale

Weighing 0.25 g directly isn't reliable on a 0.1 g scale. A dilution stock gets around this (my inference): 1 g of extract mixed into 9 g of erythritol, then 2.5 g of the blend per pint. This applies the site's small-amounts trick for gums, which dilutes 10 g of gum into 90 g of filler, to sweeteners.

---

## 4. A conversion procedure, as far as the evidence supports

Assembled from the author's method (02 §7), the glacier skill's audit (03 §7 Q8) and the reproduced conversions (03 §4). Treat steps 5–6 targets as the author's empirical Creami values, not derived constants.

1. **Normalize to grams and scale to the tub.** A 16 oz pint is about ⅔ of the author's 680 ml Deluxe tub, so roughly 450 g of mix.
2. **Compute the composition.** Work out fat, MSNF, sugars by type, total solids, kcal and protein-to-energy.
   - PAC = Σ(g × PAC coefficient) / total g × 100, plus about 5.9 per 1% salt counted once.
   - POD = Σ(g × POD coefficient) / total g × 100.
   - Use the coefficient table in 02 §5, preferring the nutrition database. For the fibers, which conflict, give both values.
3. **Name each ingredient's job.**
   - Cream gives fat and mouthfeel.
   - Sugar gives PAC, sweetness and solids.
   - Corn syrup prevents crystallization and adds body.
   - Milk powder adds MSNF and binds water.
   - Egg yolk is the emulsifier.
   - Starch and gums bind water.
4. **Replace the fat.**
   - Swap cream for milk plus NFDM, keeping MSNF at or below about 11%.
   - Add stabilizer: Salty Stability, ICSv2, or guar plus xanthan.
   - Optionally add body with inulin, waxy maize starch or protein (whey, Greek yogurt).
   - Don't cut fat or solids without making them up (glacier skill).
5. **Replace the sugar by matching PAC first.** Aim for **PAC about 30–32**:
   - erythritol at or below about 6–8% of the mix;
   - plus a partner (allulose, xylitol or glycerin) to cover the rest of the PAC;
   - then top up sweetness with PAC-neutral sweeteners (monk fruit, stevia, sucralose). This order is the site's.
6. **Check the result** against these limits:

   | Check | Limit |
   |---|---|
   | PAC | 30–33 |
   | MSNF | ≤ 11% |
   | Total solids | about 20–25% |
   | Erythritol | < 8% |
   | Polyols per pint | erythritol, xylitol and glycerin all eaten at once |
   | Fiber per pint | — |
   | kcal per pint | — |
   | Carbs | usable carb on a "net of fiber" basis (the plain formula overstates it for fiber-heavy bases, 03 §1 #8) |

7. **Process like the author.**
   - Freeze 24 h.
   - Do the scrape test; rest on the counter if it is too hard. No hot water.
   - Spin on Lite Ice Cream, scrape down, then Respin or Mix-in.
   - Refreeze if it is too soft.
8. **Log and revise.** Record probe temperature, texture straight after the spin and texture after storage.

**Worked examples that reproduce exactly** (03 §3 #22):

| Conversion | PAC | Fat (g/100 g) | kcal/100 g |
|---|---|---|---|
| Jeni's Base → Jeni's Light | 21.5 → 28.2 | 13.3 → 7.2 | 214 → 124 |
| Salt & Straw Base → S&S Light | 26.7 → 31.8 | 14.0 → 6.9 | 228 → 121 |

In both, PAC rises as sugar is replaced by an erythritol/xylitol blend plus glycerin. Both use soy milk, so neither tests a lactose strategy.

**The procedure applied to your book base** (my arithmetic; a test candidate, not a recommendation):

- 400 g 2% milk, 15 g NFDM, 20 g Lakanto (as erythritol), about 31 g allulose, 5 g vanilla paste, a pinch of salt.
- The pantry substitute for Salty Stability scaled to 16 oz: 1.0 g guar, 0.35 g xanthan, 0.35 g salt.

| Measure | Value |
|---|---|
| PAC (without salt) | about 30.7 |
| Erythritol | about 4.2% |
| MSNF | about 10.7% |
| Total solids | about 24% |
| kcal | about 290 |

Sweetness should come out about 20% higher than the book base, and higher still because Lakanto's monk fruit isn't counted.

This keeps PAC in the author's band and halves the erythritol. It leans on allulose instead of xylitol (see §1 item 8). Allulose has no tolerance figure in any source. Run it through IceCreamCalc before making it.

---

## 5. Next experiments, in order of what they settle

1. **Probe-thermometer series on the book base** (Q13, Q15, §3.1). Take readings:
   - after 24 h in the freezer;
   - after your 60 s hot-water step, compared with the site's scrape test and counter rest;
   - after the spin;
   - after Respin.

   Rate texture at each stage.
2. **Erythritol partner test at equal PAC (about 31)** (Q1, Q7, recrystallization). Compare:
   - the book base;
   - 20 g erythritol plus about 31 g allulose;
   - optionally a SweEX version.

   Eat a half pint fresh and the rest after one week.
3. **Firmness check on the low-PAC designs** (Q16, §3.1). If you still want to try the low-cal fiber bases, make B as a half pint and record the post-spin temperature, crumbliness and whether a respin fixes it. B is the conservative fiber option.
4. **NFDM ladder: 0 g, 15 g and 25 g at about the same PAC** (Q6, Q17). Tests whether going from about 20% to 24% total solids helps, and whether 12.7% MSNF turns sandy.
5. **Measure overrun** (Q4). Weigh a level pint before spinning, then weigh a level pint's volume of the result.
6. **Read the Lakanto label and set up a monk fruit dilution stock** (Q11, §3.4) before using pure extract at all.
7. **Adapt the author's Cheesecake Light to US dairy** (§1, 03 §6). The author rates it 5 stars. It has 0.6% fat, 353 kcal per 16 oz and PAC 32. It is the closest known-good low-fat reference.

---

## 6. Housekeeping

- **IceCreamCalc account:** 14 recipes named `[research] …` (IDs 182133–182146) were created for these calculations and left in place. Nothing else was created or changed.
- **Key safety:** the key was never printed. A scan of `research/` and the session scratchpad found 0 files containing it, and `.env` stays git-ignored.
- **Scratch scripts:** the stage 3 scratch scripts, which re-implement the sheet formulas, are in the session scratchpad: `C:\Users\ayham\AppData\Local\Temp\claude\C--VS-Code-ice-cream\ecc378d4-e8a8-4395-bafd-501b876b8e15\scratchpad`
- **Bugs found in the upstream repo** (not fixed):
  - `scripts/icc-tool.py:160` calls a function that doesn't exist.
  - The spreadsheet counts explicit salt rows twice in PAC.
  - Several coefficients conflict between `nutrition-db.csv` and `docs/info/ingredients.md`.
  - There are 131 recipe folders, not 133. The 133 in the stage prompts came from a directory listing that also counted files.
