# Stage 2: Ice Creamery site science

Scope: https://jhermann.github.io/ice-creamery/info/ plus linked site pages. Local copy is `C:\VS Code\ice-cream\jhermann\`. All paths below are relative to `jhermann/`. Live pages were fetched and compared with the local markdown.

Evidence tags used:
- **[SS]** site states, sourced
- **[SU]** site states, unsourced
- **[SD]** site derives, shows work
- **[AE]** author's experience
- **[INF]** inference by me

Citation form is `file:line`. `.fods` means `recipes/Ice-Cream-Recipes.fods`.

---

## 1. Summary

1. **The site's PAC formula is now known exactly, and it reproduces the user's hand figure.**
   - Formula in the author's sheet, `recipes/Ice-Cream-Recipes.fods:761`: `PAC = SUMPRODUCT(grams × ingredient_PAC) / total_grams × 100 + 5.9 × (salt g per 100 g mix)`.
   - Per-ingredient PAC is a per-gram coefficient on a sucrose = 1.0 scale (erythritol 2.8, glycerin 3.7, allulose 1.9, lactose 1.0, ethanol 7.4 per 100 vol%).
   - It is **not** MSNF × 0.545. Lactose and other sugars enter through the ingredient's "sugars" column divided by 100 (`.fods:1062`, `1182`, `2288`...).
   - The user's hand figure of 13,490 / 446 = 30.2 matches the site method. The site's sheet would also add about +1.2 for all salt in the mix, giving about 31 [INF].
2. **The site's targets conflict with each other, and its own Creami recipes ignore the 20–25 target.**
   - Glossary: PAC 20–25 at −18 °C; 24–28 for milk ice cream; 30–36 for sorbet (`docs/info/glossary.md:73,75`).
   - Tags page: "Scoopable" means PAC ≥ 30, "guaranteed freezer-stable" (`docs/tags.md:17`).
   - Tips and principles: PAC above 25 "typically need a refreeze" (`docs/info/tips+tricks.md:272`).
   - My scan of 122 recipe READMEs found a median PAC of 30.71. 103 are at or above 30, and 100 fall between 30 and 33.5. Only 19 are below 30.
   - Every Scoopable-tagged recipe has PAC ≥ 30, and every recipe with PAC ≥ 30 is tagged Scoopable.
   - So for the Creami the author works at about 30–33. The mechanism is: spin to soft-serve, refreeze, and the result stays scoopable. This is [AE]. No Creami-specific derivation is given (Q1).
3. **MSNF 7–11% is a gelato-practice target the author does not enforce.** Of 116 recipes with an MSNF value, 75 are below 7%, 33 are in range and 8 are above 11%. Many low-fat Creami recipes sit at 3–6% (`docs/info/glossary.md:56`, README stat lines).
4. **The site never computes total solids for its own recipes.**
   - TS appears only in the Polar Ice Creamery YouTube adaptations: zero-fat vanilla about 41%, Creami gelatos 38–47%.
   - It also appears in an unsourced "Targets for Creami Formulations" box on the web-resources page that says 28–33% (`docs/info/web-resources.md:136-142`).
   - These disagree by 8–13 points (Q6, Q17).
5. **Erythritol dose.**
   - The site's ceiling is "below 8% of total weight" (`docs/info/ingredients.md:151`), and the Jungbunzlauer-derived optimum is 6.5–8.0% (`:154,169`). Both are about crystallization and hardness, not gut tolerance.
   - The site's own recipes use a 3:2 erythritol/xylitol blend ("SweEX"), with about 4% erythritol plus about 2.6% xylitol of the mix.
   - The user's 40 g in 446 g is 9.0%, above the site's ceiling, with no xylitol companion.
6. **Fiber doses.** The site says "typically 10–20 g in a 680 g mix" for inulin (`ingredients.md:199`). Its own Light recipes use about 22–35 g of inulin per 680 g (Cheesecake Light about 31 g, S&S Light about 25 g plus gum-blend inulin, Jeni's Light 35 g plus 35 g isomalt). The site gives no per-pint polyol or fiber tolerance number for erythritol (Q7, Q9).
7. **The author's own conventional-to-light conversions (the best Q8 evidence).**
   - Jeni's Base → Jeni's Light: PAC 21.5 → 28.2, fat 13.3 → 7.2 g/100 g, 214 → 124 kcal/100 g.
   - Salt & Straw Base → S&S Light: PAC 26.7 → 31.8, fat 14.0 → 6.9, 228 → 121 kcal/100 g.
   - The recipe is rebuilt in a spreadsheet, and the PAC rises as sugar is replaced (see §7).
8. **Gaps.** The site does not cover:
   - pint temperature after spinning (Q13);
   - overrun versus fat for the Creami (Q4, only Polar's 0% overrun for Creami gelatos);
   - a quantified protein-for-fat equivalence (Q3);
   - a head-to-head of simple thickeners versus inulin or polydextrose (Q14);
   - cardiovascular evidence for polyols (Q10, only an unsourced one-line relay of Polar's remark).
9. **Internal inconsistencies worth knowing.**
   - Salt PAC: table says 1070 dissolved and 585 undissolved (`ingredients.md:36`, changed 2026-08-07 in commit 4be64ea). The sheet and glossary still use 5.9 (`glossary.md:71`, `.fods:761`).
   - The stabilizer ICSv2 is "tara" in the FAQ and principles pages but "guar" in the actual recipe (changed June 2025).
   - GMS:CMC ratio is 2:1 in the ingredients page and Salty Stability, but 30% GMS to 60% CMC in the Polar section.
   - Inulin PAC is 22 in the ingredients table but 0.09 in the nutrition table.
   - Polydextrose is "1 kcal/g" in the text but 191 kcal/100 g in nutrition.
   - Xylitol GI is 12 in the table but 7 in the nutrition note.
10. **Mix-ins.** Direct site evidence for crunch survival is thin: frozen chopped mint-chocolate wafers, cantuccini and freeze-dried strawberry slices survive. The author says white-chocolate flake "crunch... should probably be added manually" (Starry Night).

---

## 2. Coverage log

Live and local matched for every page unless noted.

| Page | Live URL | Local file | Note |
|---|---|---|---|
| Overview | /info/ | `docs/info/index.md` | Local read in full (78 lines). Not separately fetched live. Links to the author's GitHub wiki. |
| FAQ | /info/faq/ | `docs/info/faq.md` | Fetched live. Identical on tara/guar: FAQ says tara (lines 11, 19). |
| Glossary | /info/glossary/ | `docs/info/glossary.md` | Fetched live. PAC and MSNF text identical. |
| Principles | /info/principles/ | `docs/info/principles.md` | Fetched live. Identical. |
| Ingredients | /info/ingredients/ | `docs/info/ingredients.md` (1213 lines, read in full) + `docs/assets/*.inc.md` | Live table identical. Only the last 581 characters of the live page were not read. Macro `{{ 'alcohol' \| ingredient }}` in `booze2vg.inc.md` renders as plain text with no extra numbers. |
| Nutrition | /info/nutrition/ | `docs/info/nutrition.md` (380 lines, read in full) | Live rows match. The page defines no units for PAC or MSNF. |
| Recipe guide | (not fetched live) | `docs/info/recipe-guide.md` | Local only. Static list of 28 recipes "under 85 kcal". |
| Tips and tricks | /info/tips%2Btricks/ | `docs/info/tips+tricks.md` | Fetched live. Identical. |
| Plating | (not fetched live) | `docs/info/plating.md` | Local only. No science content. |
| Polar Ice Creamery | (not fetched live) | `docs/info/polar-ice-creamery.md` | Local only. Transcript digests. |
| Web resources | (not fetched live) | `docs/info/web-resources.md` | Local only. Contains the "Targets for Creami Formulations" box. |
| Recently changed | /info/recently_changed/ | `docs/info/recently_changed.md` | Page says "last 3 months" but the latest entry is 2025-12-22. Footer says "Last updated 2026-08-07". Dated, low value. |
| Tags | /tags/ | `docs/tags.md` | The live page is macro-rendered per-tag lists, which the local file lacks. See the Light-category subsection in §6. |
| Recipes | (not fetched live) | `recipes/*/README.md` (all 133 folders scanned for stats); read in full: Vanil-Low, Buttermilk Vanilla, ICSv2, Salty Stability, Vanilla Paste, Locarb Vanilla, Cheesecake Light, Lazy Skyr, Jeni's Base, Jeni's Light, S&S Base, S&S Light, DC's Blank Slate, Creamia | These show the rendered stat lines. |
| Contributed and YouTube | (not fetched live) | `docs/youtube/*`, `docs/contributed/*` | Composition tables (fat, sugar, TS, overrun). |
| Spreadsheet | n/a | `recipes/Ice-Cream-Recipes.fods` | Source of the PAC, MSNF, Protein/Energy and tag formulas (grep'd). |

**Extra sources opened (beyond the strict brief).** The info index links the author's GitHub wiki, so I opened five wiki pages for Q2, Q8 and Q9:
- "The Hunt for the Ultimate Inclusions"
- "How to Achieve Good Results, Consistently"
- "Using Fiber in Ice Cream"
- "Example for Modifying a Recipe Using an AI Chat"
- "Ninja Creami Ingredient Swapping Guide"

I also opened "Professional Guide to Ice Cream Stabilization", "Reddit Ninja Creami Recipe Tips" and "Beginner's Guide to Scoopable Ice Cream".

Caveat on the wiki:
- The pages appear AI-assisted. Several lines are self-contradictory (guar/xanthan swap ratios, "erythritol raises effective freezing point"), and no sources are given.
- Treat them as [SU], lower confidence.

The Jungbunzlauer erythritol PDF could not be retrieved (the fetch returned the corporate homepage). The 6.5–8% and 3:2 figures are therefore verified only through the site's summary.

---

## 3. Findings map by open question

**Q1. PAC target for Creami vs churned: PARTLY ANSWERED.**
- The site gives no Creami-specific derivation. The general rule is written as "double the serving temp" (milk ice cream, "i.e. −12°C", 24–28) and "factor 2.5" (sorbet, 30–36) (`docs/info/glossary.md:73-75`) [SU].
- Soft enough means "about 65% of water molecules frozen at serving temperature (e.g. −11°C)" (`glossary.md:73`) [SU]. Storage at −18 °C with PAC 20–25 is "easily scoopable", and below 15 is "quite hard" (`:73`) [SU].
- The Creami targets are different and empirical. Every recipe prints "target 20..30" (e.g. `recipes/Vanil-Low (Deluxe)/README.md:122`).
- The Scoopable tag is PAC ≥ 30 "guaranteed freezer-stable" (`docs/tags.md:17`; `scripts/ice-cream-recipe.py:50` `TAG_SCOOPABLE_PAC_LIMIT = 30.0`) [AE].
- PAC above 25 "typically benefit from a refreeze after processing" (`principles.md:48`; `tips+tricks.md:272`) [AE]. "Spin a base during the day and enjoy it late at night... leftovers remain scoopable permanently" (`tips+tricks.md:272-274`).
- Recipe distribution: median 30.71, 100 of 122 between 30 and 33.5, one outlier at 47.6 (Forget-Me-Nut Swirl) [SD from READMEs].
- The only low-PAC Creami recipes are the author's untested or draft conversions of conventional bases: Jeni's Base 21.5 (Draft), DC's Blank Slate 24.1 ("untested"), S&S Base 26.7 (Draft), and Creamia 22.5 (a soft-serve style).
- Author observations at PAC about 30:
  - Starry Night (29.6): "was too soft, adapted recipe accordingly" (`recipes/Starry Night (Deluxe)/README.md:39`).
  - Radler Zäpfle (30.07): "very soft... needs 1-2h refreezing" (`recipes/Radler Zäpfle (Deluxe)/README.md:38`).
  - Speyside Vanilla (32.7): "creamy but a bit icy, hopefully fixed now by adding inulin" (`recipes/Speyside Vanilla (Deluxe)/README.md:34`).
- Implication [INF]: PAC 30 describes a soft pint that must be refrozen. PAC alone does not prevent iciness (Speyside), and solids and stabilizers matter.

**Q2. Durable crunch without a fat barrier: PARTLY ANSWERED (thin).**
- Cantuccini "will *not* totally disappear" in mix-in mode (`ingredients.md:1094`) [AE].
- Frozen, chopped mint chocolate wafers "do not disintegrate into the base" and become "chewy bits of mint that do not fully freeze" (`ingredients.md:1100-1105`) [AE]. The recipes say "freeze for more integrity, and chop them when frozen" (`recipes/Vanil-Low (Deluxe)/README.md:90`).
- Crumbled freeze-dried strawberry slices give "a nice crunch from the mix-in" (`recipes/Strawberry Ice Cream (Deluxe)/README.md:38-42`) [AE]. "Fruity chew" in Locarb Vanilla (`recipes/Locarb Vanilla (Deluxe)/README.md:41`).
- White-chocolate flakes: "the mix-ins are a nice crunch, and should probably be added manually" (`recipes/Starry Night (Deluxe)/README.md:39`) [AE]. This implies the mix-in cycle degrades crunch.
- Technique: make a hole to the bottom, add partial amounts, "fold the ice cream over, building pockets of mix-ins" (e.g. `Vanil-Low README.md:108`).
- Mix-in mode: 30 s down at 450 rpm, 35 s up at 450 rpm (`tips+tricks.md:234`).
- Beso de Ángel leaves headroom: the base is "600g on purpose, to leave room for plenty of mix-ins" (`recipes/Beso de Ángel (Deluxe)/README.md:34`).
- Wiki (AI-assisted, [SU]): even Mix-In mode reduces cookies and cereal "to dust"; sugar enamel, chocolate or cocoa-butter lipid coating, brittle and toffee resist moisture; keep inclusions to about 15–20% of pint volume; add 0.5–1 tbsp glycerin per pint so no re-spin is needed.
- Nothing quantifies retention time.

**Q3. How much protein substitutes for fat: PARTLY ANSWERED (qualitative).**
- Polar's zero-fat vanilla "swaps fat for protein and special fillers": fat 0.5%, protein 7.9 g/100 g, TS about 41% (`docs/youtube/PolarIceCreamery/Vanilla-Zero-Fat.md:14-20,63`) [AE/transcript].
- Whey makes ice cream "creamier, soft-serve-like", casein "thicker, denser", soy isolate is a fat replacer (`ingredients.md:947-952`, `1054`) [SU].
- Cheesecake Light has 0.6% fat and 6.5 g protein/100 g, and is rated top marks (`recipes/Cheesecake Light (Deluxe)/README.md`) [AE].
- Wiki: "Keep at least a small fat phase" [SU].
- No equivalence ratio is given.

**Q4. Does low Creami overrun change the fat requirement: NOT COVERED directly.**
- Polar: home machines "typically yield lower overrun" (`polar-ice-creamery.md:109`).
- Creami gelatos are tabulated at 0% overrun (Pistachio, Salted Caramel) and 0–5% (Hazelnut) (`docs/youtube/PolarIceCreamery/Pistachio-Gelato.md:15`; `Stunning-Hazelnut-Gelato.md:15`).
- Gelato fat: "6-12%" (`polar-ice-creamery.md:249`).
- No fat-versus-overrun argument is made.

**Q5. Stabilizers and bulking agents beyond xanthan: ANSWERED (broadest coverage).** Details in §6.

**Q6. Total-solids target and how to compute it: PARTLY ANSWERED.**
- Glossary: "a good traditional ice cream contains 12% fat, 7-11% MSNF (11 for high fat), 15% sugar, 0.3% stabilizer and emulsifier, and 38.3% total solids" (`glossary.md:56`) [SU].
- Creami block: total solids 28–33% of mix weight; total sugars (sugar equivalents) about 11.5–12.5%; fat about 2.5%, "can be lowered toward 0%" if compensated by inulin, SMP, protein or sweeteners (`web-resources.md:136-142`) [SU, source unnamed].
- Polar TS values: 36–47% for Creami gelatos and bases; zero-fat vanilla about 41%.
- The author's recipe pages show no TS figure, only MSNF.

**Q7. Polyol tolerance ceiling per pint: PARTLY ANSWERED.**
- Erythritol: below 8% of total weight (texture) (`ingredients.md:151`); "Dosage: 6.5–8% of an ice cream base" (`:154`).
- Sorbitol: "max. 10% of a recipe" (`:322`) [SU]. Maltitol: "over 20-30g" laxative (`:245`) [SU]. Isomalt: "50g per day" suggested ceiling (`:217`) [SU].
- Xylitol: "no daily intake limits defined, but... 5-10g over a day is recommended" (`:414-415`) [SU].
- Glycerin: "adverse GI effects... start at ~14g/day in a 70kg adult" (`:387`) [SU]. Wiki: a polyol-free-carb comparison is not given.
- Allulose: no tolerance figure. Only "GRAS in 2025... EFSA evaluating" (`:144`).
- No erythritol-specific gut ceiling. Polar calls erythritol "relatively tolerant" (`polar-ice-creamery.md:76`).

**Q8. Systematic conversion procedure: PARTLY ANSWERED.** No written step-by-step procedure, but worked examples exist. See §7.

**Q9. Fiber load (inulin/polydextrose) per pint: PARTLY ANSWERED.**
- Inulin: "Typically 10-20g in a 680g mix is enough"; "Fat can be reduced by 50% with 5% native inulin — i.e. up to 35g in a Deluxe tub" (`ingredients.md:199`) [SU, citing Ice Cream Science blog]. "RDA is 8-18g (tested for up to 24 weeks)"; side effects "gas, bloating, diarrhea, constipation, and cramps" (`:201`) [SU].
- Polydextrose: EU labelling "above 15g"; "no limits set" (`:281`) [SU]. Resistant dextrin: with inulin "may offer... less gas" (`:309-310`) [SU].
- Wiki "Using Fiber in Ice Cream": inulin 2.5–4% of mix, total fiber 4–6% (AI-assisted, [SU]).
- Actual recipe inulin per 680 g tub (computed from READMEs [SD]):
  - Cheesecake Light: 20 g + 11 g in Salty Stability = 31 g (4.5%).
  - Locarb Vanilla: 15 + 7.3 = 22.3 g.
  - S&S Light: 25 g.
  - Jeni's Light: 35 g plus 35 g isomalt.
  - Vanil-Low: 11 g (all from the stabilizer mix).

**Q10. Erythritol/xylitol cardiovascular signals: PARTLY ANSWERED (relay only).**
- Polar (2024): "recently there have been some fears that [erythritol] may contribute to blood clots and future heart disease" (`polar-ice-creamery.md:85`).
- The site's ingredients page has no CV discussion. Xylitol is flagged only as dangerous for dogs (`docs/youtube/PolarIceCreamery/Chocolate-Protein.md:24-26`).
- No study is cited.

**Q11. Monk fruit potency and dosing: PARTLY ANSWERED.**
- Mogroside V is "150 to 250 times sweeter than sucrose"; "typically comprises only 0.05% to 0.1% of an ice cream base... negligible freezing point depression" (`ingredients.md:265-270`) [SU].
- "Monk fruit Sweetener" sold 1:1 is "mostly erythritol or allulose" (`:252-259`) [SU].
- Worked ratio: 100 g sugar replaced by 50 g allulose + 50 g inulin + 0.35 g monk fruit powder (80% pure) (`tips+tricks.md:110-111`) [SD, no derivation shown].
- Back-calculation [INF]: that 0.35 g of 80% powder supplies about 60 g sucrose-equivalent sweetness, about 170× the product or about 214× on a pure basis.
- For the user's 0.25 g pure extract the same ratio gives about 53 g sucrose-equivalent, and 150–250× gives 37–62 g.
- 0.25 g in 446 g is 0.056%, inside the site's 0.05–0.1% range [INF].
- No Lakanto row. The closest is "Monk Fruit / Erythritol Sweetener [Rheinnatur]", 88 g erythritol per 100 g, PAC 2.46, 31 kcal (`nutrition.md:248`).

**Q12. Emulsifier gap: ANSWERED (qualitatively).**
- Egg yolk "is a natural source of... lecithin" (`ingredients.md:794`). The author limits eggs: "if you use too many egg yolks, you're tasting egg" (`polar-ice-creamery.md:278`).
- Lecithin is "essential" for recipes with nut butter or unusual fat (`tips+tricks.md:74`); egg-free dose 0.15–0.5% (`ingredients.md:843`). GMS 0.1–0.5% of mix, with CMC (`:815-817`).
- The ICSv2 recipe has no emulsifier; Salty Stability does (GMS 18 g per 150 g mix = 1.8 g in a 15 g dose, about 0.26% of a Deluxe base) (`recipes/Salty Stability/README.md`). The low-cal recipes use Salty Stability, so they are not at 0%.
- The site says an emulsifier matters mostly with fat; no data on near-zero-fat bases.

**Q13. Pint temperature right after spinning: NOT COVERED.**
- Related only: do not process bases outside −12 to −20 °C (`tips+tricks.md:32`); "Frozen Yogurt... induces the most heat" (`:222`); Respin can "induce heat for softer consistency" (`:225`).
- Polar: a churned target serving temperature "e.g. −7°C" (`polar-ice-creamery.md:256`).
- The "Targets for Creami Formulations" box says aim for 13–14 °C serving temperature (sign dropped, presumably −13/−14), and that a modeled temperature warmer than about −13 °C means too icy (`web-resources.md:139-142`) [SU].
- No source for the −9 °C figure in the brief.

**Q14. Simple thickeners vs inulin/polydextrose: PARTLY ANSWERED.**
- Instant starch (E1422/E1442/instant pudding) as a cold-base starch (`recipes/Jeni's Light (Deluxe)/README.md:38-42`); waxy maize 10 g in Buttermilk Vanilla.
- Starch dosing: tapioca "1.5—3%" (`ingredients.md:706`); green banana powder 15–30 g per liter (`:1200`).
- Protein/dairy as texture: SMP "very effective at binding free water" (`:945`); casein/Greek yogurt/skyr give "a more authentic ice cream consistency" (`:962-967`).
- No head-to-head comparison.

**Q15. Program choice and re-spin: ANSWERED (author's practice).**
- Lite Ice Cream "optimized for lower-fat bases... Often used for milk alternatives and protein shakes". Ice Cream "Needs normal ratios of sugar and fat". Frozen Yogurt: 5 min, "safest... but induces the most heat". Sorbet: for fruity or dairy-free bases. Respin: "timed like Mix-in, but at about 2.5 times the speed, to integrate crumbly spins or induce heat" (`tips+tricks.md:217-225`; speed table `:227-239`, from Dream Scoops and an IngoCoffee video).
- Typical low-fat sequence: Lite Ice Cream (or FroYo) → scrape down → Respin or Mix-in; if icy walls, 15–30 s of 20–25 °C tap water then Mix-in (soft bases) or Respin (`tips+tricks.md:262-264`).
- "Do not process left-overs... using the Respin mode" unless the recipe is anti-freeze-rich (`:44-46`).

**Q16. Will modeled low-cal bases scoop as predicted: PARTLY ANSWERED.**
- Direct site evidence: low-fat recipes at PAC 30–32 rated well (Cheesecake Light 5 stars, PAC 32.1, 0.6% fat, 77 kcal/100 g).
- The author's caveats are in Q1.
- The site predicts nothing numeric about hardness (no hardness model).

**Q17. Calculator solids/MSNF targets and the 70–78% frozen band: PARTLY ANSWERED.**
- The site's MSNF is 7–11%; the box says TS 28–33%. The site claims about 65% frozen water at serving temperature (`glossary.md:73`), not 70–78%.
- The "12–14% MSNF" figure from another calculator is not on the site.

**Q18. Inulin as bulking agent below 3% fat: PARTLY ANSWERED.**
- "[Inulin] improves mouthfeel, stability, acceptability of low-fat ice creams, and forms a gel-like network that binds water" (`ingredients.md:191`) [SU, cites Ice Cream Science].
- Skim milk "trade-offs... should be compensated, e.g. by adding inulin" (`:1002-1004`).
- Inulin is near zero PAC (0.09 in nutrition, 22 in the table), so it adds solids without softening.

---

## 4. Numeric parameters table

| Parameter | Value / range | Applies to | Source (page, file:line) | Tag |
|---|---|---|---|---|
| PAC formula (sheet) | `Σ(g × ing_PAC) / total_g × 100 + 5.9 × salt_g_per_100g_mix` | every recipe stat line | `recipes/Ice-Cream-Recipes.fods:761` | [SD] |
| PAC formula (glossary) | `sum(weight[g] * specific FPDF) / total weight * 100`, over all sweeteners in 100 g mix; salt's PAC 5.9 should be added | recipe stat | `docs/info/glossary.md:70-71` | [SU] |
| PAC definition | "PAC is the same as FPDF but includes lactose, which constitutes 54.5% of MSNF"; SMP "contains 97% MSNF, so 53% of lactose" | PAC vs FPDF | `glossary.md:61` | [SU] |
| PAC target | 20–25 at −18 °C easily scoopable; <15 quite hard | ordinary ice cream | `glossary.md:73` | [SU] |
| PAC target | 24–28 ("double the serving temp, i.e. −12°C"); sorbet 30–36 ("factor 2.5") | milk ice cream; sorbet | `glossary.md:75` | [SU] |
| PAC target, printed per recipe | 20..30 | every recipe | e.g. `recipes/Vanil-Low (Deluxe)/README.md:122` | [AE] |
| Scoopable tag | PAC ≥ 30 | recipes | `docs/tags.md:17`; `scripts/ice-cream-recipe.py:50` | [SD] |
| Refreeze rule | PAC > 25 typically needs refreeze | spun Creami pints | `principles.md:48`; `tips+tricks.md:272` | [AE] |
| Frozen water at serve | ≈ 65% at −11 °C | "soft enough" | `glossary.md:73` | [SU] |
| Operating range | −12 to −20 °C | frozen pints | `tips+tricks.md:32` | [SU] |
| Freeze time | 24 h min (less only if a scrape test OK or pre-chilled) | pints | `tips+tricks.md:30` | [AE] |
| MSNF target | 7–11% | printed per recipe | `glossary.md:56`; `faq.md:48`; recipes | [SU] |
| MSNF from milk | non-fat part × 0.093 | milk | `glossary.md:58` | [SU] |
| Traditional ice cream composition | 12% fat, 7–11% MSNF, 15% sugar, 0.3% stabilizer+emulsifier, 38.3% TS | "good traditional ice cream" | `glossary.md:56` | [SU] |
| Creami formulation box | TS 28–33%, sugars 11.5–12.5%, serve temp 13–14 (neg.), fat ≈ 2.5% (→ 0 if compensated) | Creami | `web-resources.md:136-142` | [SU] |
| Protein/Energy | ok = 12%, hi = 20%; formula `protein_g × 4 / kcal` | recipes | `.fods:772`; e.g. Vanil-Low 5.1 × 4 / 68.5 = 29.8% (page 29.99%) | [SD] |
| Tag thresholds | LOW-CAL ≤ 40 kcal/100 g; LOW-FAT ≤ 3 g fat/100 g; Low-Sugar ≤ 5 g; Hi-Protein > 20% energy from protein; Low-Salt ≤ 0.12 | auto-tags | `.fods:776-789` | [SD] |
| Light | < 75 kcal/100 g (tag text says "at most 75") | recipes | `faq.md:58`; `principles.md:43`; `tags.md:15,26`; `scripts/ice-cream-recipe.py:49` | [SU] |
| "Low-cal" in Recipe Guide | < 85 kcal/100 g | static list | `recipe-guide.md:26` | [SU] |
| Erythritol limit | < 8% of total weight; 6.5–8.0% (JBL); blend ≥ 40% xylitol; stabilizer ≥ 0.05% | static freezer | `ingredients.md:151-154,169` | [SS, primary unread] |
| Erythritol vs sucrose | max about ⅓ the amount (Polar) | substitution | `polar-ice-creamery.md:84` | [SS] |
| SweEX | erythritol:xylitol 3:2; PAC 256; POD ≈ 85; GI < 7; swap 133% allulose | blend | `ingredients.md:171-180` | [SD] |
| Glycerin dose | 5–15 g per 680 g; GI effects from ≈ 14 g/day | tub | `ingredients.md:387` | [SU] |
| Inulin dose | 10–20 g per 680 g; ≤ 35 g (5%) | tub | `ingredients.md:199` | [SU] |
| Trehalose dose | 2%–8% | any | `ingredients.md:368` | [SU] |
| Monk fruit dose | 0.05–0.1% of base | base | `ingredients.md:269` | [SU] |
| Alcohol rule | ≤ 200 g of 40% per kg base (≈ 8 vol% total); ~4 g pure ethanol (0.6%) typical | tub | `ingredients.md:1134-1139`; `tags.md:20` | [SU] |
| Alcohol→VG | 10 g booze (40%) → 8 g VG | non-boozy | `assets/booze2vg.inc.md:6` | [SD] |
| Hardening factors (negative PAC) | cocoa 21% −160; cocoa 11% −130; vegetable fat −90; cocoa butter −90; cocoa paste −160; hazelnut paste −90 | in "per-100 PAC" units | `ingredients.md:78-86` | [SU] |
| Tub scaling | Deluxe 680 ml / 24 oz; others ⅔ | scaling | `principles.md:10`; `tips+tricks.md:12` | [SU] |
| Gum doses | xanthan 0.1–0.3% (≤ 0.25% recommended); guar 0.1–0.3%; LBG 0.15–0.75%; tara 0.05–0.15%; CMC with GMS 0.2–0.5% each | mix | `ingredients.md:436-447,605,626,721,727` | [SU] |
| Gum synergies | guar/tara : xanthan 4TG:1XG or 3GG:1XG; CMC:guar:xanthan 4:3:1 at 0.3–0.5%; guar:LBG 3:2 (ingredients) vs 2LBG:1GG (LBG entry); LBG:XG 7:3 | blends | `ingredients.md:436-438,634,744` | [SU] |
| Emulsifier doses | GMS 0.1–0.5%, GMS:CMC 2:1; lecithin 0.15–0.5% (egg-free); E473 0.2–0.3% (≤ 0.5%) | mix | `ingredients.md:815-817,843,863` | [SU] |
| Sugar content context | American 13–20%, gelato 15–23% sugar; gelato fat 6–12% vs ice cream 10–24% | churned | `polar-ice-creamery.md:45,249` | [SS] |

---

## 5. Per-ingredient coefficient table

All values are per 100 g. In the nutrition table the PAC column is on a sucrose = 1.0 scale. In the ingredients table the same quantity is ×100.

| Ingredient | PAC (nutrition / ingredients table) | POD | kcal | MSNF | Source line | Notes |
|---|---|---|---|---|---|---|
| Milk 1.5% (Weihenstephan) | 0.05 | – | 47 | 9.16 | `nutrition.md:229` | sugar 4.9, protein 3.5. No US skim, 1% or 2% rows. |
| Milk 3.5% | 0.05 | – | 64 | 8.97 | `:235` | – |
| Milk 2% hi-protein (Fairlife / Natrel) | 0.03 / 0.04 | – | 50 / 64 | 9.13 / 9.11 | `:233-234` | ultrafiltered. Fairlife zero-fat 33 kcal, 0.03, 9.30 (`:241`). |
| Skim milk | none | – | – | – | – | text only (`ingredients.md:995-1006`) |
| Buttermilk 1% | 0.04 | – | 35 | 8.50 | `:55` | – |
| SMP / NFDM (Vita2You) | 0.51 | – | 358 | 94.03 | `:240` | sugar 50.5. Glossary 97% MSNF (`glossary.md:61`). |
| Full-fat milk powder | 0.35 | – | 482 | 69.0 | `:239` | – |
| Erythritol | 2.80 (280) | ≈ 75 (70–80) | 24 | – | `:138`; `ingredients.md:40` | Polar says PAC 290–320 (`polar-ice-creamery.md:81`). |
| Allulose | 1.90 (190) | 70 | 40 | – | `:16`; `ingredients.md:42` | 133% allulose replaces SweEX. |
| Xylitol | 2.20 (220) | 100 | 238 | – | `:371`; `ingredients.md:41` | GI 12 in table, 7 in nutrition note. |
| SweEX (E:X 3:2) | 2.56 | ≈ 85 | 109.6 | – | `:328` | – |
| Vegetable glycerin | 3.70 (370) | 60 | 400 | – | `:151`; `ingredients.md:38` | Net carbs counted at 50% (`ingredients.md:407`). |
| Sucrose | 1.00 | 100 | 387 | – | `:324` | – |
| Dextrose | 1.90 | 70 | 350 | – | `:129` | – |
| Trehalose | 1.00 | 45 | 355 | – | `:344` | GI 38. |
| Lactose | 0.95 | 16–40 | 380 | 95 | `:207`; table PAC 100 | – |
| Inulin (Vit4ever) | 0.09 nutrition vs 22 table | 8–10 | 210 | – | `:184`; `ingredients.md:65` | Conflict between pages. 2 kcal/g in text (`:193`). |
| Polydextrose | blank nutrition vs 100 table | 10 | 191 listed vs "1 kcal/g" text | – | `:278`; `ingredients.md:52,277` | Nutrition row looks misentered (carbs 4.7). |
| Monk fruit, pure | none (negligible) | 150–250× sucrose | 0 | – | `ingredients.md:265-270` | No row. |
| Monk fruit / erythritol blend (Rheinnatur) | 2.46 | – | 31 | – | `:248` | 88 g erythritol/100 g. |
| Stevia / sucralose (liquid) | ~0 | stevia 200–400×; sucralose 600× | – | – | `ingredients.md:326,336` | No row; "no influence on PAC" (`:330,340`). |
| Xanthan | blank | – | 320 | – | `:370` | – |
| Guar | blank | – | 180 | – | `:161` | – |
| LBG | none | – | – | – | – | no row. |
| Tara | blank | – | 185 | – | `:333` | – |
| CMC | blank | – | 175 | – | `:64` | – |
| Salt | 5.9 per 1% (sheet) vs 10.7 dissolved / 5.85 undissolved (table) | – | – | – | `ingredients.md:36`; `glossary.md:71`; `.fods:761` | Conflict. |
| Vanilla bean paste | 0.55 | – | 239 | – | `:346` | sugar 55. |
| Vanilla bean powder | blank | – | 288 | – | `:350` | – |
| Vanilla extract (alcohol) | 2.22 | – | 300 | – | `:351` | – |
| Egg yolk | blank | – | 321 | blank | `:136` | fat 27, protein 16. |
| Whey protein (vanilla) | 0.05 | – | 392 | 89.2 | `:366` | protein 78. |
| Casein | 0.03 | – | 356 | – | `:66` | protein 82. |
| Soy protein isolate | blank | – | 372 | 93.0 | `:315` | – |
| Instant pudding mix | none | – | – | – | – | text only ("instant pudding" as modified starch, `Jeni's Light README.md:40`) |
| Waxy maize starch (E1442) | blank | – | 391 | – | `:363` | – |
| Greek yogurt 9% / 0% | 0.04 / 0.05 | – | 113 / 54 | 7.91 / 15.57 | `:159-160` | – |
| Skyr | 0.04 | – | 65 | 17.8 | `:300` | – |
| Cream cheese 23% (Exquisa) | 0.03 | – | 238 | 9.64 | `:110` | US full-fat cream cheese = 2:1 with milk (`ingredients.md:924-925`). No low-fat US row. |
| Cottage cheese 4% | 0.01 | – | 91 | 16.0 | `:103` | – |
| Quark 0.6% | 0.04 | – | 70 | 11.4 | `:341` | – |
| ICSv2 | 1.32 (1.42 with salt) | – | 107.2 | – | `:177`; `recipes/Ice Cream Stabilizer (ICS)/README.md:59-63` | – |
| Salty Stability | 0.06 (0.26 with salt) | – | 267.5 | – | `:294`; `recipes/Salty Stability/README.md` | – |
| Maltodextrin 18 DE | 0.34 table vs 1.29 nutrition | 21 / 15 | 383 | – | `:221`; `ingredients.md:64` | Conflict. |
| Ethanol 40 vol% | 2.96 | – | 280 | – | `:352-353` | Sheet: sugar/100 + 0.074 × vol%. |

Notes on how the sheet builds the PAC column:
- Most rows are `sugars_g / 100` (`.fods:1062,1182`...). Fruit rows therefore use PAC 1.0 for all their sugars (bananas 0.16 for 16 g sugar), which understates fructose and glucose (1.9) [INF].
- Alcohol rows add `0.074 × vol%` (`.fods:1221`).
- Missing PAC means 0 in the sum.

---

## 6. Stabilizers, sweeteners, Creami workflow, Light category, mix-ins

### Stabilizers

**ICSv2 (current).** `recipes/Ice Cream Stabilizer (ICS)/README.md:44-51`:
- 100 g erythritol, 100 g inulin, 10 g CMC (GoodBake), 3.5 g guar, 3.5 g salt, 1 g xanthan. Total 218 g.
- Dose is 30 g for a Deluxe tub (about 2.0 g gums, 0.29% of mix) and 20 g for the 16 oz tub (`:37-38`).
- "The salt is added... for a FPDF boost" (`:32-33`).
- Changelog: v2 added inulin 2024-10-29; tara → guar 2025-06-16 (`:66-67`).
- The FAQ, principles page and ingredients page still say tara (`faq.md:11,19`; `principles.md:30`). Older "ICS" nutrition row: erythritol / CMC / tara / XG (`nutrition.md:176`).

**Salty Stability** (`recipes/Salty Stability/README.md`; scripts `PREPPED`): 110 g inulin, 18 g GMS, 9 g CMC, 6 g guar, 5 g salt, 2 g xanthan.
- Dose 15 g per Deluxe tub, 10 g per 16 oz tub. A 15 g dose is 11.0 g inulin, 1.8 g GMS, 0.9 g CMC, 0.6 g guar, 0.5 g salt, 0.2 g xanthan.
- Substitute: 1.5 g guar + 0.5 g xanthan + 0.5 g salt per 15 g (`tips+tricks.md:75`).
- Recommended: heat at least 200 ml milk to 50–80 °C and blend the mix in (activates GMS, hydrates gums).

**Hydration, synergies, doses.** See §4. Additional details:
- Xanthan and guar at 1:3 act as "cold" synergistic gel; xanthan with LBG needs heat (`ingredients.md:754-762`) [SS: Food Manufacturing Africa Q1 2020].
- Relative viscosity at 0.2% (estimates): xanthan about 32 mPa·s, tara 2.4–4.3, guar 3.5, LBG 3.2, CMC 1.6, gum arabic 1.1 (`:453-460`) [SD from published intrinsic viscosities].
- Hydration temperatures: guar soak or 80 °C, LBG 90 °C, tara 80 °C, CMC cold (`:603,631,718,563`).
- Small-amount trick: dilute 10 g gum into 90 g inulin or filler (`assets/small-amounts.inc.md`).
- Polar's own blend recommendation for the Creami zero-fat vanilla: "Polar 4:4:2 blend" at 2.5 g per 680 g (`Vanilla-Zero-Fat.md:34`), plus lecithin 1.3 g.
- Under-belly blends (0.15% dose): LBG:guar:λ-carrageenan 4:2:1; CMC:guar:λC 2:1:1 for sorbet (`ingredients.md:442-447`).
- Conflict on ratios: GMS:CMC is 2:1 in the ingredients page (`:816`) and Salty Stability, but Polar states "60% CMC to 30% GMS" (`polar-ice-creamery.md:207`).

**Fat and bulking agents.**
- Inulin: see Q9 and Q18.
- Polydextrose: PAC 100, "five times higher PAC" than inulin (`:283-284`).
- Resistant dextrin: low PAC (<20), POD about 10, GI 25–48, "replace or accompany inulin" (`:294-310`).
- Maltodextrin: increases solids, low PAC (`:290-292`).
- MCC: "creamy mouthfeel in low-fat products, but without the typical GI issues" (`:646`).
- Psyllium: up to 0.9% of base (`:678`). Tapioca 1.5–3% (`:706`). Gelatin 0.15–0.3% (`:589`).

### Sweeteners

**Site rankings (FAQ).**
- Table sugar and dextrose "probably 'best'" (`faq.md:27`).
- Trehalose is next "natural" (same PAC and calories, half as sweet, much lower GI) (`faq.md:30`).
- Then allulose ("try allulose first (in the US/CA market, maybe combined with monk fruit)"), then a monk fruit/erythritol combo ("erythritol should be combined with another bulky sweetener to prevent crystallization"), then SweEX (`faq.md:32-35`).
- All these options have "a POD of 70..100, and a PAC from 190 to 280" (`faq.md:35`).

**Recommended blends.**
- Erythritol:xylitol 3:2 (SweEX), from Jungbunzlauer (`ingredients.md:169-175`).
- Allulose is "recommended only in combination with other sweeteners like erythritol" (`principles.md:24`); alone "a poorer texture (slight graininess)" (`ingredients.md:137-138`) [AE].
- 100 g sugar → 50 g allulose + 50 g inulin + 0.35 g monk fruit powder (`tips+tricks.md:110-111`).
- 55% isomalt + 45% fructose (PAC 107, POD 104, GI about 10); 50% fructose + 50% inulin for allulose (`:105-106`).
- Replacement ratios to preserve PAC/POD are in `tips+tricks.md:95-106`, including erythritol → 40% honey + 60% glycerin.

**Dose and crystallization.**
- Erythritol "strong tendency to crystallize in long-term frozen state (weeks), leading to a hard texture" (`ingredients.md:151`). Polar: it "recrystallizes once subjected to freezing temperatures... borderline inedible" and creates an "ultra cold effect" (`polar-ice-creamery.md:80-82`). Polar advises against erythritol for ice cream (`:86`).
- This confirms the user's recrystallization premise. The site does not quantify how much effective PAC is lost to recrystallization. The site's PAC table treats erythritol's 280 as constant, which supports the user's hypothesis that real behavior departs from the model [INF].

**Health notes.**
- Glycerin and net carbs: count 50% (`ingredients.md:407`).
- Xylitol: count 35–40% of weight as net carbs (`:412`).
- Allulose: GI 0, "does not count as added sugar" (`:133`).

**Dial in sweetness.** Fix bulky-sweetener PAC first, then top up with PAC-neutral ultra-sweeteners (drops) (`ingredients.md:108-122`).

### Creami workflow

- **Program choice:** see Q15.
- **Freeze:** 24 h with lid on, flat surface (`tips+tricks.md:30,42`). Freezer −12 to −20 °C (`:32`). Wiki suggests 48 h if gritty (AI-assisted).
- **Scrape test, always** (`:250-256`): judge hardness with a spoon; if it resists, let it sit 5–15 min on counter or in fridge. "Do not soften (thaw) your frozen tubs without checking" (`:34`); "no premature thawing... hot water" before the first spin (`:36,295-298`).
- **Icy walls after the spin:** 20–25 °C tap water for 15–30 s, then Mix-in (soft bases) or Respin (`:262-264`). The user's "hot water 60 s" differs from the site: the site prohibits hot water before the first spin and recommends cold water only after (`:36,262,295-298`).
- **Hump:** "Do not skip flattening the hump" (`:38`).
- **Leftovers:** do not Respin them; use the original mode (`:44`). "Always flatten left-overs you intend to process again" (`:42`).
- **Base prep:** immersion blender, then let blend run 1–2 min for gum hydration; age in fridge a few hours or overnight (`Vanil-Low README.md:100-107`).
- **Scaling:** Deluxe 24 oz (680 ml) is the author's unit. Other models use ⅔ (`principles.md:10`; `tips+tricks.md:12`). The user's 16 oz pint corresponds to the ⅔ scaling (about 450 g).
- **Overrun:** see Q4.
- **Troubleshooting phrases:** crumbly → Respin; crumbly zero-fat vanilla → "add a splash of milk and Re-spin" (`Vanilla-Zero-Fat.md:49`); icy → more inulin (Speyside).

### Light category

- **Definition:** < 75 kcal/100 g (`faq.md:58`; `principles.md:43`; `tags.md:15`). The auto-tag is `TAG_LIGHT_KCAL_LIMIT = 75.0` (`scripts/ice-cream-recipe.py:49`).
- **Live tag page:** 24 recipes are tagged Light, with the same count in my local scan: Banana • Slim, Berry Punch, CocoaLow, Dirty Peach Bourbon, Epic Spoons of Nom, Espresso Martini Light, GaMe On, Grapple Sorbet, Just Fruit, Lean Coffee, Lemon Sorbet, Margarita Sorbet, Milkshake, Plum Sherbet, Pomegranate Light, Radler Zäpfle, Rosehip & Hibiscus, Shregg, Soda Pop Sorbet, Strawberry Sangria, Strawberry Sherbet • Vegan, Vanil-Low, Vegan Vanilla, Winter Apple.
- **Stale list:** the "Light Recipes" list at the bottom of the tags page is a 12-item hand list (NotebookLM-produced, `tags.md:24-54`) with kcal values that differ from the READMEs (e.g. CocoaLow 61.4 vs 70.0; Vanil-Low 69.1 vs 68.5). It also includes Cherry Ice Cream and Blueberry Buttermilk, which are not Light-tagged in the READMEs. `recipes/README.md` quotes yet another figure (Vanil-Low 59.9).
- **Dairy Light recipes' typical stats (README stat lines):**
  - Vanil-Low: 68.5 kcal, fat 1.9, protein 5.1, PAC 31.24, MSNF 6.5%.
  - Cheesecake Light (77 kcal; not Light-tagged): PAC 32.14, MSNF 9.3%, fat 0.6.
  - Epic Spoons of Nom: 67.7 kcal.
  - Pomegranate Light (71.2) and Lean Coffee (61.4) are other dairy Light recipes.
- **Not tagged Light despite being low-cal:** Vanilla Protein (83.1), Cheesecake Light (77), Crème Caramel (75.9), Lazy Skyr (86.5).

### Mix-ins

See Q2. Also, the Toppings recipe page (not read) is linked for processed toppings (`ingredients.md:1087`). The wiki page on inclusions is AI-assisted and unsourced.

---

## 7. The site's recipe-design / conversion method

There is no formal procedure. The author's method, assembled from the pages:

1. **Spreadsheet-first design.** Recipes are built in LibreOffice (`principles.md:7`); the spreadsheet computes macros, PAC, MSNF and protein/energy (`recipes/README.md`, `.fods`). A Python script exports to markdown.
2. **Scale to the tub.** Base is about 600–690 g in a 680 ml (24 oz) Deluxe tub (`principles.md:10`; "Fill to MAX" lines in recipes). Conventional bases are rescaled to about 600–690 g (DC's Blank Slate "scaled to ~625g").
3. **Fix the freezing-point budget first, then sweetness.** Pick bulky sweetener and PAC ingredients to hit PAC about 30–32 (the author's empirical Creami target), then dial sweetness with PAC-neutral drops (`ingredients.md:108-122`).
4. **Replace sugar with PAC-matched sweetener plus bulk.** Use the table of replacement ratios (`tips+tricks.md:92-111`), e.g. sucrose + corn syrup → SweEX + glycerin + inulin.
5. **Reduce fat by swapping dairy for lower-fat dairy or soy, and add solids and stabilizer.** Add SMP and protein powder for MSNF, inulin for body, ICSv2 or Salty Stability for gums (and GMS).
6. **Add alcohol or glycerin for FPD** (about 4 g pure ethanol is typical; 8 g VG replaces 10 g booze).
7. **Check the stat line:** PAC target 20..30 (practically ≥ 30), MSNF 7–11%, protein/energy.
8. **Test, rate and revise.** The README rating field and changelog lines record revisions (e.g. "Jun 4, 2025: Added almond butter").

**Worked conversions** (all from READMEs, [SD]):

| | Original | Converted |
|---|---|---|
| Jeni's | Jeni's Base: 295 g milk 3.5%, 225 ml cream 32%, 95 g sugar, 20 ml corn syrup, 40 g cream cheese, 10 g starch. 214 kcal, fat 13.3, PAC 21.5 (`recipes/Jeni Britton's Base (Deluxe)/README.md`) | Jeni's Light: 400 ml soy milk 1.6%, 100 ml cream, 50 g cream cheese, 40 g SweEX, 35 g inulin, 35 g isomalt, 15 g VG, 10 g starch, 0.75 g xanthan. 123.5 kcal, fat 7.2, PAC 28.2. "Energy is reduced from almost 1500kcal to about 850kcal, fat roughly halved" (`recipes/Jeni's Light (Deluxe)/README.md:29`) |
| Salt & Straw | S&S Base: 275 g cream 32%, 200 g milk 3.5%, 30 g corn syrup, 75 g sugar, 15 g SMP, 0.75 g xanthan, VG 10. 228 kcal, fat 14.0, PAC 26.7 | S&S Light: 375 ml soy milk, 125 g cream, 45 g SweEX, 18 g VG, 25 g inulin, 10 g SMP, 10 g whey/casein. 120.7 kcal, fat 6.9, PAC 31.8. "Targeted for less fat (8%) and sugar (2%) with 3.4% net carbs" (`recipes/S&S Light (Deluxe)/README.md:26`) |
| Dana Cree's Blank Slate | kept with sugar, PAC 24.1, "untested" | – |
| Cremia | sugar replaced by trehalose + xylitol (35 g + 30 g); fat reduced to 12% | – |
| Polar zero-fat vanilla | skim milk 415 g, SMP 65 g, whey 20 g, allulose 100 g, maltodextrin 26 g, inulin 20 g, stabilizer 2.5 g, lecithin 1.3 g (cooked to 85 °C, aged) | scaled to 680 g Deluxe tub from a video transcript |
| AI-assisted modification (wiki) | prompt: "Keep the recipe balanced, with a PAC target of about 30" | the AI rebuilt the recipe (replace amaretto and mix-ins, keep macros) |

What the conversions show [INF]:
- As fat falls, PAC rises: the author compensates the lost fat and sugar solids with inulin and SMP/protein and adds VG and SweEX.
- Sugar (PAC 1.0) → SweEX (2.56) at 44% mass plus VG (3.7) is how the PAC gets maintained or raised while kcal falls.
- The author does not run a "known costs" accounting step (e.g. sweetness, solids) in the text.

**Roles the site assigns:** cream = fat, mouthfeel; sugar = sweetness, FPD, solids; corn syrup = anti-crystallization, body (`tips+tricks.md:119-138` DIY glucose syrup); SMP = free-water binding, MSNF; egg yolk = lecithin (skipped); starch/stabilizers = water binding.

Gaps for Q8:
- The site shows no general algorithm for converting to low-fat lactose-containing bases.
- It gives no check for sweetness (POD) in the stat line.
- Its conversions lean on soy milk, glycerin, isomalt and polyols, not on a lactose strategy.

---

## 8. States vs derives vs experience

**Well-founded or sourced:**
- Basic coefficients: sucrose 100, dextrose 190, erythritol 280, ethanol 740, glycerin 370, with the Ice Cream Science blog cited under the table (`ingredients.md:69-71`).
- Erythritol: 3:2 polyol blend and 6.5–8% from the Jungbunzlauer 2015 study (primary not retrievable).
- Xanthan/guar 1:3 synergy cites an industry article (`ingredients.md:764`).
- Gum viscosity table is derived from published intrinsic viscosity (shows work).
- Mode speed table is sourced to Dream Scoops and a video.

**Derived by the author (shows work in the sheet):**
- PAC, MSNF and protein/energy formulas (fods).
- Polyol PACs are computed from sugar columns; alcohol uses 0.074/vol%.
- SweEX PAC 256 = 0.6 × 280 + 0.4 × 220 [INF; matches].

**Unsourced assertions presented as fact:**
- PAC target ranges (20–25, 24–28, 30–36) and the "double the serving temp" rule: standard gelato-practice rules of thumb, no source.
- MSNF 7–11%.
- Inulin and glycerin tolerance numbers.
- "Targets for Creami Formulations" box.
- Monk fruit potency.

**Author's practice (empirical):**
- PAC about 30 as the Creami target, the refreeze advice, program choice, mix-in handling, and all ratings.

The site is an experienced hobbyist's working method, not a derivation from first principles. Its numbers are consistent within one author's spreadsheet. The Creami-specific calibration (PAC about 30–33) is not explained.

---

## 9. Conflicts with the user's established facts or stage 1 numbers

1. **Hand PAC ≈ 30 is confirmed as the site's formula.** The site would add its salt term, giving about 31 [INF]. The user's "lactose at PAC 100" and "erythritol 280" match the site's tables (`ingredients.md:40,51`; `nutrition.md:138`).
2. **Lactose and MSNF.** The site's prose says lactose is 54.5% of MSNF (`glossary.md:61`), but the sheet counts lactose via the ingredient's sugar column. For milk the two agree within about 2% (sugar 4.9 vs 9.16 × 0.545 = 5.0).
3. **The other calculator's "~35" and the site's "~30".** They are not shown to be the same scale. The site's PAC excludes protein, fibers (inulin 0.09 in the sheet), and uses 5.9 for salt. Whether the other tool's FPD score uses a different basis cannot be determined from the site. Not resolved.
4. **MSNF 7–11% (site) vs 12–14% (other calculator's low-fat profile).** The site's number is the gelato-literature figure; its own recipes typically fall at 3–8%. The site gives no reason for 12–14%.
5. **Erythritol dose.** The user's 9.0% exceeds the site's "below 8%" and the 6.5–8.0% optimum. The site's own use of a 3:2 blend gives about 4% erythritol (the crystallization inhibitor is built in). The user's "manufacturer 6.5–8.0%" claim matches the site's quote of the Jungbunzlauer study.
6. **The user's "erythritol recrystallizes so effective PAC drops" hypothesis.** The site supports recrystallization (hardening) but states the opposite sign for scoopability: the site's erythritol warning is that recrystallization makes ice cream hard over weeks (`ingredients.md:151`; Polar `:80`). The site does not say a nominally soft PAC-30 base behaves better because of recrystallization. This explains hardening, not the user's observation of good behavior [INF].
7. **Hot water.** The user's workflow of 60 s hot water before spinning conflicts with the site: "Do not run your tubs under hot water before the first spin" and "No Premature Thawing" (`tips+tricks.md:36,295-298`). The site allows only cold tap water after the first spin, 15–30 s.
8. **Lakanto/monk fruit modeling.** The site models blends by their bulking sweetener (Rheinnatur 88% erythritol, PAC 2.46) and treats monk fruit extract itself as PAC-neutral. This supports modeling Lakanto as essentially erythritol.
9. **Pint size.** The site's unit is the 24 oz Deluxe; its ⅔ scaling gives 16 oz. The user's 380–446 g mixes match.

---

## 10. Claims for stage 3 to verify

1. `recipes/Ice-Cream-Recipes.fods` computes PAC as `SUMPRODUCT(grams × ingredient_PAC × include)/total_weight × 100 + 5.9 × salt_g_per_100g_mix` (line 761).
2. The converter/csv carries `fpdf` per ingredient in `scripts/nutrition-db.csv` on a per-gram sucrose = 1 basis: erythritol 2.80, glycerin 3.70, allulose 1.90, xylitol 2.20, dextrose 1.90, lactose 0.95, SMP 0.51, trehalose 1.00, SweEX 2.56, ICSv2 1.32.
3. For ordinary sugar-bearing rows the db's `fpdf` equals `sugar/100` (e.g. milk 1.5% sugar 4.9 → 0.05; banana sugar 16 → 0.16). Alcohol rows equal `sugar/100 + 0.074 × vol%` (× density factor 1/0.7875 for volume units).
4. `nutrition-db.csv` does not list a plain table-salt row; salt enters via the `5.9 × salt%` term (the ingredients table's 1070 value is documentation only).
5. MSNF per ingredient uses `(100 − fat) × 0.093` for fluid milk (milk 1.5% → 9.16), `9 − fat` for buttermilk (1% buttermilk fat 0.5 → 8.5), and `fat/0.2 − fat` for cottage-type cheese rows (4.3% fat → 17.2).
6. MSNF% printed in the recipe = `Σ(g × msnf)/100 ÷ total weight` (`.fods:798`), e.g. Vanil-Low 44.1 g / 680 g = 6.5%.
7. Protein/Energy = `protein_g × 4 / kcal` (`.fods:772`); Hi-Protein tag when > 0.2.
8. Auto-tags in `scripts/ice-cream-recipe.py`: Light when kcal/100 g < 75 (`TAG_LIGHT_KCAL_LIMIT = 75.0`, line 49); Scoopable when PAC ≥ 30 (line 50). Sheet tags LOW-CAL ≤ 40 kcal, LOW-FAT ≤ 3 g fat, Low-Sugar ≤ 5 g, Low-Salt ≤ 0.12 g (`.fods:776-789`).
9. In `recipes/*/README.md`: every recipe tagged Scoopable has printed PAC ≥ 30, and every recipe with PAC ≥ 30 is tagged Scoopable (my scan found no exceptions among 130 tagged files).
10. Distribution: of 122 recipes with a PAC stat, median 30.71; 103 are ≥ 30; 19 are < 30 (Jeni's Base 21.46, FroYo Apricot 22.13, Creamia 22.50, DC's Blank Slate 24.12, PB+J FroYo 26.24, Salt & Straw Base 26.73, Dark Temptation 26.81, ChiaChoco 26.90, Sweet Potato Pie 27.39, Plum Sherbet 27.82, Banoffee 28.09, Jeni's Light 28.18, PB Swirl 28.85, German Cheesecake 29.01, Ube Coconut 29.38, Umamiso 29.42, Orange & Peach 29.47, Starry Night 29.59, Soda Pop Sorbet 29.79).
11. Of 116 recipes with an MSNF% stat, 75 are < 7%, 33 are 7–11%, 8 are > 11%.
12. All 24 Light-tagged READMEs have < 75 kcal/100 g (Banana • Slim 74.4, Dirty Peach Bourbon 74.2, Plum Sherbet 74.3 are the closest), while the hand-written Light list in `docs/tags.md:28-39` has different kcal values (stale).
13. The ICSv2 README states 100 g erythritol, 100 g inulin, 10 g CMC, 3.5 g guar, 3.5 g salt, 1 g xanthan (218 g), dose 30 g per Deluxe tub, and its FPDF line is 1.42 with salt and 1.32 without. Check: `scripts/ice-cream-recipe.py` `PREPPED['ICSv2']` matches. Salt term implied: (1.42 − 1.32) / (3.5/218) ≈ 6.2, consistent with 5.9 within rounding.
14. Salty Stability = 110 g inulin, 18 g GMS, 9 g CMC, 6 g guar, 5 g salt, 2 g xanthan (150 g), dose 15 g; FPDF 0.26 with salt, 0.06 without.
15. The sheet reproduces Vanil-Low's PAC 31.24 from its ingredient list to within 0.1 (my hand computation 31.29: Σ coefficients 202.7 / 680 + 5.9 × 1.7/680).
16. By the same method the user's base (400 g milk 1%, 40 g erythritol-type, 5 g vanilla paste, 1 g xanthan, pinch salt; 446 g) gives about 30.1 without the salt term and about 31 with it, if milk sugar is 4.9 g/100 g.
17. The ingredient table in `docs/info/ingredients.md:34-66` lists salt 1070 (dissolved, 585 undissolved) while `.fods:761` and `glossary.md:71` use 5.9 (commit 4be64ea changed only the docs).
18. Polydextrose has no `fpdf` in `nutrition-db.csv` but PAC 100 in the ingredients table; inulin `fpdf` is 0.09 (not 0.22); maltodextrin `fpdf` 1.29 (not 0.34).
19. `nutrition-db.csv` has no rows for: Lakanto, pure monk fruit extract, plain 1%/2%/skim US milk, nonfat dry milk beyond the Vita2You SMP row, instant pudding mix, LBG, US low-fat cream cheese. It does have Rheinnatur monk fruit/erythritol (fpdf 2.46).
20. The author's sweetener usage: in all Light and low-fat dairy recipes, SweEX is 40–45 g per 680 g (6–6.6% of mix), i.e. erythritol about 3.6–4.0% and xylitol about 2.4–2.7%.
21. Inulin per 680 g tub in the recipes: Cheesecake Light 20 g + 11 g (via Salty Stability) = 31 g; Locarb Vanilla 15 + 7.3 = 22.3; S&S Light 25; Jeni's Light 35 (+ 35 g isomalt); Vanil-Low 11.
22. The Jeni's Light, S&S Light, Jeni's Base and S&S Base stats quoted in §7 are accurate (PAC, fat, kcal).
23. `Vanilla-Zero-Fat.md` composition (fat 0.5%, sugar 8.7%, TS ≈ 41%, overrun ≈ 30%) is computed from the ingredient list: check TS from nutrition rows (SMP 65 g, skim milk 415 g, etc.).
24. Starry Night, Radler Zäpfle and Speyside Vanilla READMEs contain the "too soft", "very soft... refreeze" and "a bit icy" remarks with PAC 29.6, 30.07 and 32.74 respectively.
25. Erythritol share of mix in the Light recipes is below 8% everywhere (check against `nutrition-db.csv` erythritol rows, SweEX 3:2 expansion).
26. Does any recipe README contain a total-solids (TS) line? My scan says none. Verify via grep for "solids".
27. The glossary's claim "PAC includes lactose, 54.5% of MSNF" is not what the sheet implements (it uses sugar columns).
28. The ingredients table gives sucrose 100, dextrose 190, erythritol 280, allulose 190, xylitol 220, glycerin 370, inulin 22, polydextrose 100, trehalose 100, lactose 100, ethanol 740, salt 1070 (`docs/info/ingredients.md:34-66`).
29. Check whether any recipe README prints a PAC "target" other than "20..30" and "(ok=12%; hi=20%)" for protein/energy.
30. An ice-cream calculator API (if used by stage 3) should be tested with Vanil-Low's ingredient list to see whether its freezing-point score reproduces about 31.2 or lands near 35 as in stage 1's other calculator.

---

## 11. Outside links worth following later

Opened for this report (wiki, same author): see §2. Not crawled:
- https://jhermann.github.io/ice-creamery/info/ingredients/#... cited blog posts: Ice Cream Science, "Why is corn syrup used in ice cream?" and "Why is inulin used in ice cream?" (https://www.icecreamscience.com/blog/corn-syrup-used-ice-cream; https://www.icecreamscience.com/blog/why-is-inulin-used-in-ice-cream). Likely the source of the PAC table and the inulin dose.
- Jungbunzlauer 2015 study "Erythritol makes a difference" PDF (URL in `docs/info/ingredients.md:158`). Primary source for the 6.5–8% and 3:2 numbers; the PDF did not load here.
- Polar Ice Creamery videos listed at `docs/info/web-resources.md:45-64`: Ice Cream Science playlist; "Zero fat luxury ice creams - Possible?" (https://www.youtube.com/watch?v=6qXUJV6vVhM); "Untold Secrets of High Protein, Zero Sugar Ice Cream" (https://www.youtube.com/watch?v=KZ7blzvnryY); Ultimate Ice Cream Stabilizer videos; the Sugars series.
- Underbelly (https://under-belly.org/category/ice-cream/): source of the stabilizer blend ratios in `ingredients.md:442-447`.
- Calculators listed at `web-resources.md:117-134`: Scoopulator, Dream Scoops, Calculate Ice Cream, IceCreamCalc, Scoop Science, Ice Cream Science spreadsheet, Will It Creami (creamiguide.com). The "Targets for Creami Formulations" box has no named source; Scoop Science or Scoopulator is a guess [INF].
- Food Manufacturing Africa Q1 2020, "Texture control, stabilisation and xanthan gum" (https://savannah.co.za/wp-content/uploads/2020/03/FMA-Q1_JB-March20.pdf), source of the xanthan/guar 1:3 synergy.
- Glycerin and blood sugar article (https://gpinzone.blogspot.com/2014/03/lost-article-on-insulin-response-to.html), source of glycerin GI claims.
- Dream Scoops Creami review and IngoCoffee video (mode timing table source), `tips+tricks.md:243`.
- Ninja owner's guides (NC30x, NC50x) at `web-resources.md:71-108`: the only candidate for official program/temperature facts (Q13, Q15).
- AFCD (Australian Food Composition Database), used for the YouTube adaptations' nutrition (https://afcd.foodstandards.gov.au/).
- Author's wiki pages not opened: "Beginner's Guide to Ice Cream Stabilizers", "Creamy Vegan Ice Cream", "Techniques for Creating Swirls", "Ninja Creami Quickstart", "CREAMi DELUXE NC501 Safety and Operation Guide".
- Frozen Dessert Spreadsheet of Doom (Google Sheets, `web-resources.md:32`) and the r/ninjacreami wiki (https://www.reddit.com/r/ninjacreami/wiki/index/).
