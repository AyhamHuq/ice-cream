# Stage 3: Repo validation and three-method comparison

Paths are relative to `C:\VS Code\ice-cream\jhermann\` unless absolute. `.fods` = `recipes/Ice-Cream-Recipes.fods`. Evidence tags: [code] [data] [computed] [API] [inference] [web].

Scratchpad: `C:\Users\ayham\AppData\Local\Temp\claude\C--VS-Code-ice-cream\ecc378d4-e8a8-4395-bafd-501b876b8e15\scratchpad`. It holds `recompute.py`, `usercalc.py`, `final_tables.py`, `recipes_def.py`, `run_create.py`, `api\calc_*.json` and `api\ingredients_full.json`. I did not run the repo's scripts. They need `attrdict` and `yaml`, and Python is not on PATH. I re-implemented the sheet formulas in Python 3.12 and validated them against the recipe CSVs (section 4). Nothing under `C:\VS Code\ice-cream\` was written.

---

## 1. Summary

1. **The site formula is confirmed, with one defect.** PAC = Σ(g × FPDF) / total g × 100 + 5.9 × (salt g per 100 g mix) (`.fods:761`). The explicit "Salt" ingredient row also carries FPDF 5.9 per gram (`.fods:9465`). Explicit salt is therefore counted twice, at about 11.8 per 1% of mix instead of 5.9. This is visible in about 40 printed PAC values. My re-implementation reproduces printed PAC within ±0.4 for 99 of 102 recipe CSVs (mean +0.04, SD 0.08). MSNF% is within 0.1 for 100 of 101 and kcal/100 g within 0.1 for 101 of 101 [computed].
2. **The user's base lands in the author's window.** Book base: PAC 30.10 without salt, 31.1 with salt counted once, 31.5 as the sheet would print it. The hand figure 13,490/446 = 30.2 reproduces. IceCreamCalc (ICC) gives PAC se 30.6 and PACtot 31.0 [API]. Adding 25 g NFDM gives +1.1 (PF said +1.2). The Fairlife-equivalent baseline is 27.9 (PF said "≈27").
3. **Conflict 8.2 (Scoopulator ~35 vs site ~30) is largely resolved.** ICC "PAC se" ÷ 10 equals the site's no-salt PAC. Scoopulator's "FPD" is the same per-100-g-of-mix quantity with the ingredients-table coefficients (inulin 0.22, polydextrose 1.0) and salt at about 10.7 per gram, including salt from milk and NFDM. That reproduces the controls (34.6, 35.4 vs "about 35") and A–E (18.6–20.8 vs "19.5–22") [inference, computed]. With the nutrition-db coefficients (inulin 0.09, polydextrose blank), A–D come out at 10.5–13.2 and do not match. The "35 vs 30" gap is therefore a salt-term difference, not different physics.
4. **A–E sit far below the author's practice.** Their PAC is about 13–20, against the author's cluster of 30–33 (n = 122) and against Jeni's Base at 21.5. ICC puts their 75%-frozen-water serving temperature at −6.3 to −7.4 °C, against −13 °C for Original and Second. ICC's "Crumbly" score is 94–97 for A–D (above 90 means "add liquid post spin"). The controls and book base (PAC 31–35) are where the author's rated recipes live.
5. **Erythritol dose.** The user's pints are 9.0% (book base) and 9.5% (Original). The author's maximum is 6.8% (Ultimate FroYo, plain erythritol). SweEX-based recipes are at most 4.4% erythritol and 7.7% total polyols. For the book base, 45 g SweEX (27 g erythritol + 18 g xylitol) holds PAC at 31 and cuts erythritol to 6.0% [computed].
6. **Total solids.** The author's own rated bases are at about 19–25% TS (macro-TS median 22%, p90 28.5%; this is a lower bound, about 1–2 points low). ICC gives Vanil-Low 20.9% and Milky Whey 24.9%. The "28–33%" Creami box and Scoopulator's 28–32% target are not supported by the author's practice. The user's pints are 17.1–25.6% (book base 19.6%).
7. **Calories.** All nine user pints are 203–319 kcal on site-db values (198–294 with Scoopulator-style fibre kcal). Even the book base + 25 g NFDM is 314 kcal, well under 400–500. Scoopulator's kcal are reproduced to within 2 kcal by milk 50 kcal/100 g, erythritol 0.2, inulin 2.0, polydextrose 1.0 kcal/g and zero for gums. ICC's Energy/100g is unreliable for polyol/fibre recipes (details in section 5).
8. **The usable-carb formula is misleading for A–D.** It returns 33–46 g, against 24–28 g of real sugars, because fibre kcal count as carb. IA's fibre designs keep the lactose carbs (23.9–28.4 g, about the same as the book base's 22.4 g) and only remove erythritol.
9. **Measured anchors in the repo (Q13).** Milky Whey (PAC 32.4) probed at −9.6 °C after Ice Cream + respin (photo `recipes/Milky Whey (Deluxe)/Milky-Whey_2025-09-18_7.jpg`). An older Fruit Kefir went from almost −18 to −7 °C after respin (`recipes/Fruit Kefir (Deluxe)/README.md:47`). This supports Scoopulator's −9 °C preset, but it does not test the user's hot-water step.
10. **Hot water.** The site calls hot water before the first spin a machine-damage risk: the frozen block can come loose and spin in the tub (`docs/info/tips+tricks.md:36,295-298`). 17 recipes use only cold running water after the first spin.
11. **Closest recipes (section 6).** Cheesecake Light, Buttermilk Vanilla, Buttermilk Stracciatella, Milky Whey, Pomegranate Light, Vanil-Low, Speyside Vanilla and Lazy Skyr. Cheesecake Light is the best match: 0.6% fat, 353 kcal per 16 oz.
12. **API.** 14 `[research]` recipes were created and calculated. No errors and no 429s. Smart Balance was not run (no chart is linked). No key value appears in any scratchpad file.

---

## 2. How the repo actually computes stats

**The converter computes none of PAC, MSNF, kcal or P/E.** The sheet computes them and the script passes them through.

- `scripts/ice-cream-recipe.py:682-706` (`handle_top_row`) copies sheet rows that have a value in column 2 into bullets such as `**label:** value`. The nutrition table is just the CSV rows (classes `NutrientItem` 456-495 and `NutrientFacts` 498-581).
- **What Python does compute:**
  - unit conversion (`ImperialUnitTransform` 309-413);
  - the PREPPED expansion text (442-452; data 57-74);
  - tags (`add_default_tags` 146-182).
- **Tags in detail:**
  - Light is `kcal <= 75.0`, read by regex `100g; X kcal;` or the table row (lines 49, 154-158).
  - Scoopable is `PAC >= 30.0`, read by regex `FPDF / .?PAC.+:.?.? ([.0-9]+)` (lines 50, 159-161).
  - DEFAULT_TAGS (75-86) are matched as words in the rendered text. Low-Fat, Low-Sugar and Hi-Protein come from the sheet's flag cells. Low-Cal and Low-Salt are not in the list, so they are never emitted as tags.
  - CALCULATED_TAGS (120-132) are reset on every run.
- `write_nutrition_db` (612-643) exports sheet ingredient rows to `scripts/nutrition-db.csv`, but only rows where `kcal` is non-empty (`has_macro_row_data`, 304-306). This is why the Salt row (no kcal) is absent from the db.
- `macros.py` loads the module and calls `parse_info_docs`.
- `scripts/icc-tool.py:160` calls `recipe_lib.parse_recipe_csv`, which does not exist anywhere in the repo (grep). The tool is stale/broken. Its ingredient-import template hard-codes `pac: 1.0, pod: 1.0`.
- `tests/` has no PAC/MSNF/kcal tests. They cover unit conversion, template sheet names and `_utils`.

**The spreadsheet (single sheet "Template") holds everything.**

- **Ingredient database.**
  - Rows 21 to about 316, columns A–P: name, amount, unit, step #, kcal, fat, carbs, sugar, protein, salt, FPDF, MSNF, comment, 0Carb[%], Counts?, ID (`.fods:949`).
  - Counts? = `IFS(step>3 → ""; unit g → 1; unit ml → 1; else "")`.
  - Mix-ins (step 4+) and toppings are excluded from every total. Drops, pinches and pieces are excluded because their unit is not g or ml.
- **Totals and stats.**
  - Row 6 totals are SUMPRODUCT(amount, column, Counts?). B6 is the total counted grams.
  - Row 4 is per 100 g. J4 = J6/B6×B4 (`.fods:682`, J6 at 746), which is salt per 100 g from all rows, including salt inside milk and premixes.
  - PAC: `.fods:761`.
  - P/E = `I4*4/E4` (`:772`).
  - Hi-Protein is `B9>0.2` (`:786`).
  - Tags: LOW-CAL `E4>40` excluded, so ≤40; LOW-FAT ≤3 g; Low-Sugar ≤5 g; Low-Salt ≤0.12 g (`:776-789`).
  - MSNF g = Σ g×L/100 (`:798`); the % is B10/B6.
  - Net carbs = G6 − Σ g×N/100 (`:815`). N is a per-ingredient "0Carb[%]", for example erythritol 100, xylitol 100, glycerin 50, inulin 89.
- **Per-ingredient FPDF column.**
  - Most rows use `=H/100`, the sugar column (e.g. milk `.fods:7520`).
  - Polyols, sweetener blends, fibre and honey-type rows are typed constants.
  - Liqueurs use `H/100 + 1/0.7875 × 0.074 × vol%` (`:1221`); egg/coconut liqueurs use 1/0.789.
  - Generic "Brandy or Vodka 40 vol%" is the constant 2.96 (= 7.4×0.4).
  - Cocoa, chocolate and oils are negative.
  - Salt row: salt = 100, FPDF = 5.9 (`.fods:9462, 9465`).
- **MSNF conventions per ingredient.**
  - Fluid milk and cream: (100−fat)×0.093 (`:7523`).
  - Buttermilk: 9−fat (`:2291`).
  - Cottage cheese: fat/0.2−fat (`:3706`).
  - SMP and whey: 95−fat (`:7857`), so SMP = 94.03, not the glossary's 97%.
  - Cream cheese: fat/0.7−fat (`:4042`).
  - Yoghurt: (carbs+protein+salt)×1.11 (`:5594`).
  - Quark: 12−fat or 21−fat.
  - Skyr: 100−82−fat.
  - Evaporated milk: ×0.093×2 or 2.55.
- **Not computed anywhere:** POD, total solids, overrun. Printed per-recipe stats are PAC, P/E, MSNF, net carbs and tags.

**Where the code differs from what the site says.**

- Salt is counted twice when it is an ingredient row (the glossary says "add the salt percentage", once).
- The glossary says SMP is 97% MSNF; the sheet uses 95−fat.
- The glossary says lactose is 54.5% of MSNF; the sheet uses the sugar column.
- The docs say Light is "<75"; the code is `<=75`.

---

## 3. Claim-by-claim verdicts (02 §10)

| # | Claim (short) | Verdict | Evidence |
|---|---|---|---|
| 1 | PAC formula at `.fods:761` | **Partly** | Formula correct. J4 covers salt from all rows (`:682,746`). But the Salt row has FPDF 5.9 (`:9465`), so explicit salt counts twice. Avocado pure: printed 30.40, mine 30.40 with double count, 28.48 single. About 40 recipes with Salt rows match only with the double count (e.g. Margarita Sorbet 30.69 vs 30.74 double / 28.13 single). [computed] |
| 2 | db `fpdf` values (erythritol 2.80 … ICSv2 1.32) | **Confirmed** | `nutrition-db.csv`: Allulose 1.90 (l.6), Dextrose 1.90 (92), Erythritol 2.80 (101), Glycerin 3.70 (111), ICSv2 1.32 (131), Lactose 0.95 (152), SMP 0.51 (179), SweEX 2.56 (246), Trehalose 1.00 (259), Xylitol 2.20 (280). [data] |
| 3 | fpdf = sugar/100; alcohol rows = sugar/100 + 0.074×vol% | **Partly** | 118 of 187 rows with fpdf equal sugar/100 (±0.006). 69 are overrides: polyols, honey/syrups, dried fruit (raisins 0.10 vs sugar 68), cocoa/chocolate (negative), inulin, maltodextrin, ICS blends, spirits. The 1/0.7875 factor sits on g-unit liqueur rows (`.fods:1221`), not "volume units". Generic vodka is a constant 2.96. [computed] |
| 4 | No plain salt row in db; salt via the 5.9 term | **Partly** | No Salt row in the db (exporter drops kcal-less rows, `ice-cream-recipe.py:304-306`). The sheet has a Salt row with FPDF 5.9 (`.fods:9462-9465`), so salt enters via both K and the 5.9×J4 term. The 1070 table value is docs-only (commit 4be64ea touched only `docs/info/ingredients.md`). |
| 5 | MSNF conventions: milk (100−fat)×0.093; buttermilk 9−fat; cottage fat/0.2−fat | **Confirmed** | `.fods:7523, 2291, 3706`. Extra conventions listed in section 2. |
| 6 | MSNF% = Σ g×msnf/100 ÷ total | **Confirmed** | `.fods:798`; Vanil-Low CSV 44.1 g / 680 g = 6.5% (mine 6.49%). |
| 7 | P/E = protein×4/kcal; Hi-Protein >20% | **Confirmed** | `.fods:772, 786`. Vanil-Low: printed 29.99%, mine 29.99%. |
| 8 | Auto-tags in script and sheet | **Confirmed** | `ice-cream-recipe.py:49-50, 157, 160`; `.fods:776-789`. Caveats: `<=75` in code vs "<75" in docs; Low-Cal and Low-Salt are never emitted as tags (DEFAULT_TAGS 75-86); the skill file says "below 3 g/5 g" (strict) where the sheet is ≤. |
| 9 | Scoopable ⇔ PAC ≥ 30 | **Partly** | 102 Scoopable READMEs, all PAC ≥ 30. 104 READMEs have PAC ≥ 30 and two are untagged: Forget-Me-Nut Swirl (47.58; explicit `excluded_tags: Scoopable`) and Almond Milk Mix (229.5; a dry mix). Folder count is 131, not 130/133. [computed] |
| 10 | Distribution: median 30.71 of 122; 103 ≥30; 19 below | **Confirmed** | Exact 19-recipe list reproduced. 100 recipes fall in 30–33.5. Median 30.71 excluding Almond Milk Mix (30.72 including). [computed] |
| 11 | MSNF: 75 <7, 33 in 7–11, 8 >11 of 116 | **Confirmed** | [computed] |
| 12 | 24 Light READMEs <75 kcal; hand list stale | **Confirmed** | Max 74.4 (Banana • Slim); no ≤75 recipe is untagged. `docs/tags.md:28-39` vs READMEs: CocoaLow 61.4 vs 70.0; Lean Coffee 66.6 vs 61.4; Lemon Sorbet 28.0 vs 45.0; Cherry Ice Cream 67.6 vs 80.2 (not Light); Blueberry Buttermilk 72.1 vs 75.7 (not Light); Vanil-Low 69.1 vs 68.5 (`recipes/README.md:28` says 59.9). |
| 13 | ICSv2 composition, dose, FPDF 1.42/1.32 | **Confirmed** | PREPPED `ice-cream-recipe.py:58-65` = README (218 g, 30 g dose). (100×2.8+100×0.09)/218 = 1.326. With salt 1.7 g/100 g: +5.9×0.017 = 0.100 → 1.43 (README 1.42). Implied salt coefficient 5.9. |
| 14 | Salty Stability composition; FPDF 0.26/0.06 | **Confirmed** | PREPPED `:66-73`. 110×0.09/150 = 0.066; with 3.5 g/100 g salt +0.207 → 0.27 vs README 0.26 (rounding). |
| 15 | Vanil-Low PAC reproduced (31.29 by hand) | **Confirmed** | Mine 31.25 vs printed 31.24. Σ(g×K) = 202.7 gives 29.81; salt 1.656 g gives +1.44. Stage 2's 31.29 used 1.7 g salt. |
| 16 | Book base ≈30.1 without salt, ≈31 with | **Confirmed** | 30.10 / 31.09 (salt once) / 31.49 (sheet, with a 0.3 g pinch row). [computed] |
| 17 | Salt 1070/585 in docs only | **Confirmed** | `git show 4be64ea`: 590 → "1070 / undissolved 585" in `docs/info/ingredients.md:36` only. `.fods:761` and `glossary.md:71` unchanged. Scoopulator's learn page also says salt is "over 1,000%" [web]. ICC uses about 585 (see section 5). |
| 18 | Polydextrose blank, inulin 0.09, maltodextrin 1.29 in db | **Confirmed** | `nutrition-db.csv` lines 208, 135, 163. ICC: inulin 0.134, polydextrose 0.40, maltodextrin 18 DE 0.325 [API]. |
| 19 | Missing db rows | **Confirmed** | None of Lakanto, pure monk fruit, US 1%/2%/skim milk, NFDM (only Vita2You SMP), instant pudding, LBG, US low-fat cream cheese is in the db. Rheinnatur 2.46 exists (line 184). |
| 20 | SweEX 40–45 g (6–6.6%) in all Light/low-fat dairy | **Partly** | In 29 Light/low-cal (≤85 kcal) SweEX recipes: 20–50 g (2.9–7.3% of mix), erythritol 1.8–4.4%. Across all 82 SweEX recipes: median 5.1% (p10 3.7%, p90 6.6%). 40–45 g is the mode, not the rule. [computed] |
| 21 | Inulin per tub: 31 / 22.3 / 25 / 35 / 11 g | **Confirmed** | Cheesecake Light 31.0, Locarb Vanilla 22.3, S&S Light 25, Jeni's Light 35 (+35 g isomalt), Vanil-Low 11.0. [computed] |
| 22 | Jeni's / S&S stats in §7 | **Confirmed** | Jeni's Base 21.46 / 13.3 fat / 213.8 kcal; Jeni's Light 28.18 / 7.2 / 123.5; S&S Base 26.73 / 14.0 / 228.1; S&S Light 31.82 / 6.9 / 120.7. |
| 23 | Zero-fat vanilla composition computed from ingredients | **Partly** | Table (`docs/youtube/PolarIceCreamery/Vanilla-Zero-Fat.md:12-16`) is the video's. Fat 0.5% and sugar 8.7% match the page's nutrition table. My TS ≈ 266 g/682 g = 39% vs stated 41%. Overrun ≈30% cannot be derived. |
| 24 | Starry Night / Radler / Speyside remarks | **Confirmed (caveat)** | `Starry Night/README.md:39` "was too soft, adapted recipe accordingly": the printed 29.59 is the adapted recipe. Radler `:38` very soft, needs 1–2 h refreeze (30.07). Speyside `:34` "a bit icy" (32.74). |
| 25 | Erythritol <8% everywhere | **Confirmed** | Max 6.8% plain erythritol (Ultimate FroYo, 44 g/652 g); SweEX-derived ≤4.4%; ery+xyl max 7.7% (Winter Wonderland). The ICS premix itself is 46%. |
| 26 | No TS line in any recipe README | **Confirmed** | Zero "total solids" hits in `recipes/`; the 'solids' hits are MSNF labels and changelog text. TS tables exist only in `docs/youtube` and `docs/contributed`. |
| 27 | Glossary lactose-via-MSNF not implemented | **Confirmed** | Lactose enters through `H/100` (`.fods:7520`). MSNF is used only for the MSNF%. |
| 28 | Ingredients table values | **Confirmed** | `docs/info/ingredients.md:36-66`. Also lactose POD 16–40, polydextrose POD 10, inulin POD 10. |
| 29 | Only "20..30" and "(ok=12%; hi=20%)" | **Confirmed** | 123 READMEs print "20..30"; 118 print the P/E text. No other strings. |
| 30 | ICC with Vanil-Low: ~31.2 or ~35? | **Resolved** | ICC PAC se 305.07 (÷10 = 30.5), PACtot 32.2 [API]. It reproduces ~31, not 35. The ~35 came from Scoopulator on sugar-free controls (section 5). |

Tally: 23 Confirmed, 6 Partly (1, 3, 4, 9, 20, 23), 1 Resolved (30), 0 Untestable.

---

## 4. Reproduction of the author's recipes

All numbers come from `Ice-Cream-Recipes.csv` in each recipe folder, recomputed with the sheet formulas. "d" is mine minus printed.

| Recipe | PAC printed / mine (d) | MSNF% printed / mine | kcal/100 g printed / mine | Total kcal printed / mine | Net carbs / P/E |
|---|---|---|---|---|---|
| Vanil-Low | 31.24 / 31.25 (+0.01) | 6.5 / 6.49 | 68.5 / 68.54 | 466.0 / 466.0 | 16.1 = 16.1; 29.99% = 29.99% |
| Cheesecake Light | 32.14 / 32.27 (+0.13) | 9.3 / 9.27 | 77.1 / 77.06 | 529.4 / 529.4 | 34.2 = 34.2; 33.98% = 33.98% |
| Jeni's Light | 28.18 / 28.15 (−0.03) | 4.0 / 3.95 | 123.5 / 123.47 | 847.6 / 847.6 | – |
| S&S Light | 31.82 / 31.83 (+0.01) | 6.0 / 5.98 | 120.7 / 120.70 | 834.6 / 834.6 | – |
| Buttermilk Vanilla | 30.85 / 30.84 (−0.01) | 9.7 / 9.75 | 95.5 / 95.54 | 640.1 / 640.1 | 38.5 = 38.5; 22.14% = 22.14% |
| Jeni's Base | 21.46 / 21.52 (+0.06) | 6.5 / 6.49 | 213.8 / 213.80 | 1466.7 / 1466.7 | – |
| S&S Base | 26.73 / 26.78 (+0.05) | 7.2 / 7.20 | 228.1 / 228.06 | 1565.6 / 1565.6 | – |

Across all recipes:

- **PAC:** 102 CSVs have a printed PAC. 70 are within ±0.05 and 99 within ±0.4 (mean +0.04, median +0.01, SD 0.08).
- **MSNF%:** 101 recipes, 100 within 0.1 (max |d| 0.33).
- **kcal/100 g:** 101 recipes, all within 0.05.
- **Systematic offset:** a small positive PAC offset of about +0.1 remains in a few recipes (e.g. Cheesecake Light +0.13). I could not trace it; it is probably DB values updated after the CSV export.
- **Outliers:**
  - Topfenpalatschinken (printed 32.01, mine 21.15) is an old-format CSV with step-0 rows and manual Counts? values. Its PAC is not reproducible.
  - Apple Strudel (30.29, mine 27.75) has Counts?=1 typed onto mix-in rows. Excluding step 4 gives 30.04 (−0.25).

---

## 5. The user's recipes across three methods

**Modeling assumptions.**

- Pint = 16 oz. The site's tub is the 24 oz Deluxe; ×⅔ gives 16 oz.
- **2% milk (assumed, USDA-style):** 50 kcal, fat 2.0, protein 3.4, lactose 4.9, salt 0.11, FPDF 0.049 (site sugar/100 rule), MSNF 9.11 ((100−2)×0.093), TS 10.8. Scoopulator's kcal and protein back-calculate to about 49.5–50 kcal and 3.37 g protein.
- **Whole milk (assumed):** 61 kcal, fat 3.25, protein 3.2, lactose 4.8, MSNF 9.0, TS 12.1.
- **NFDM:** site SMP row (`074ed6d`): 358 kcal, FPDF 0.51, MSNF 94.03.
- **Lakanto = erythritol:** 24 kcal/100 g, FPDF 2.8 (site precedent).
- **Pure monk fruit:** PAC-neutral. POD taken as 240× sucrose, so 0.25 g = 60 g sucrose-equivalent (IA, brief).
- **Other rows:** xylitol 2.2 / 238 kcal; glycerin 3.7 / 400 kcal; xanthan 320 kcal and guar 180 kcal (site rows).
- **Book base salt:** "pinch" = 0.3 g (446.3 g total).
- **Salt in the "sheet" PAC columns:** the Salt ingredient row (K = 5.9) is counted as the sheet counts it, plus milk/NFDM salt through J4.
- **Coefficient sets** (both reported for inulin/polydextrose):
  - "db": inulin 0.09, polydextrose 0 (blank).
  - "table": inulin 0.22, polydextrose 1.0 (`docs/info/ingredients.md`).
  - For ICC the library values are 0.134 and 0.40.
- **Fibre kcal:** db gives inulin 210 and polydextrose 191 kcal/100 g (the polydextrose row looks misentered, carbs 4.7). "alt kcal" = inulin 2.0, polydextrose 1.0, erythritol 0.2, gums 0 (this reproduces Scoopulator).
- **Site net-carb column:** polydextrose carbs are only 4.7 in the db row, so it is nearly absent; the true net-of-fibre figure for D would be about +2 g higher.

**Main table.**

PAC columns are per 100 g of mix. ICC PAC and POD are ÷10 (ICC works per kg). "Sheet" includes salt as the sheet counts it. "Scoop-style" uses table coefficients with salt at 10.7 per g of all salt.

| Recipe | Site PAC no-salt (db / table) | Site PAC sheet (db / table) | Scoop-style (table, 1070 salt) | ICC PAC se / PACtot | ICC POD / TS % / MSNF % | ICC serving °C / FW@−9 / kcal pint | Scoopulator FPD / %frozen −9 / TS / MSNF / kcal | Ery % mix | Usable carb g | Fibre g |
|---|---|---|---|---|---|---|---|---|---|---|
| Book base | 30.10 | 31.49 | 31.90 | 30.6 / 31.0 | 7.7 / 19.6 / 7.9 | −12.8 / 66.0 / 219 | n/a | 9.0 | 24.5 | 0 |
| Book base + 25 g NFDM | 31.21 | 32.84 | 33.48 | 31.8 / 32.2 | 7.8 / 23.8 / 12.6 | −14.6 / 61.5 / 256* | n/a | 8.5 | 37.6 | 0 |
| Original | 30.95 | 34.35 | 34.57 | 30.9 / 32.3 | 7.3 / 19.7 / 7.9 | −13.3 / 64.7 / 213 | ~35 / 63 / 19.8 / 8.1 / 198 | 9.5 | 20.6 | 0 |
| Second | 31.69 | 35.08 | 35.36 | 31.8 / 33.1 | 8.3 / 21.3 / 8.9 | −14.1 / 62.8 / 226* | ~35 / 61 / 21.3 / 9.1 / 248 | 7.0 (+2.3 xyl) | 31.3 | 0 |
| A Lean | 12.17 / 16.47 | 14.69 / 18.99 | 19.68 | 13.9 / 14.6 | 5.1† / 23.0 / 11.3 | −6.6 / 81.0 / 272 | 19.5–22 / 74.5 / 23.0 / 11.4 / 272 | 2.0 | 39.5 | 27.0 |
| B Light fibre | 13.16 / 15.53 | 15.65 / 18.02 | 18.64 | 14.1 / 14.9 | 5.1† / 20.4 / 11.7 | −6.5 / 81.2 / 242 | 19.5–22 / 76.8 / 20.4 / 11.8 / 251 | 2.4 | 32.6 | 14.4 |
| C Whole milk | 11.81 / 16.07 | 14.31 / 18.57 | 19.23 | 13.5 / 14.3 | 5.0† / 22.8 / 10.6 | −6.3 / 81.6 / 291 | 19.5–22 / 75.7 / 22.7 / 10.6 / 289 | 2.1 | 36.9 | 24.3 |
| D Max solids | 10.52 / 17.31 | 13.20 / 19.99 | 20.83 | 13.2 / 14.0 | 4.9† / 25.6 / 12.2 | −6.7 / 80.7 / 310 | 19.5–22 / 72.3 / 25.5 / 12.3 / 294 | 1.3 | 46.3 | 36.1 |
| E Own ingr. | 17.51 | 19.71 | 20.19 | 17.5 / 18.2 | 6.0† / 17.1 / 10.6 | −7.4 / 78.9 / 204* | 19.5–22 / 77.3 / 17.2 / 10.7 / 244 | 2.9 (+1.0 xyl) | 27.8 | 0 |

\* The ICC kcal here differ from the site and Scoopulator by 11–20%. ICC Energy/100g is not additive over library kcal. +25 g NFDM adds only +37 kcal, 1.5 kcal/g versus 3.6 real. Milky Whey is 570 kcal in ICC vs 703 in its README. I treat ICC kcal as unreliable.

† ICC POD includes the Stevia proxy for monk fruit (30× instead of 240×). Adding the missing 52 g sucrose-equivalent gives A 18.4, matching the site-method POD with monk fruit (A 18.4, B 18.9, C 18.5, D 18.1, E 19.0, vs Scoopulator "sweetness" 18.9, 19.4, 19.0, 18.7, 19.3). Without monk fruit the site POD is only 2.9–4.3, so all of IA's sweetness for A–E comes from 0.25 g of monk fruit.

**Other site-method values.**

All are per pint, with site-db kcal; "alt" is the Scoopulator-style fibre kcal.

| Recipe | kcal db / alt (per 100 g) | Fat g (%) | Protein g | P/E % | MSNF % | TS % | POD no-monk | Usable carb alt | Sugars g | Site net carb g | Polyols g |
|---|---|---|---|---|---|---|---|---|---|---|---|
| Book base | 225 / 220 (50.4) | 8.0 (1.8) | 13.7 | 24.4 | 8.2 | 19.6 | 8.0 | 23.3 | 22.4 | 23.2 | 40 |
| +25 NFDM | 314 / 309 (66.7) | 8.2 (1.7) | 22.4 | 28.6 | 12.7 | 23.6 | 8.0 | 36.4 | 35.0 | 35.9 | 40 |
| Original | 203 / 198 (48.1) | 7.6 (1.8) | 13.0 | 25.6 | 8.2 | 19.7 | 7.8 | 19.4 | 18.6 | 19.4 | 40 |
| Second | 253 / 248 (58.8) | 7.7 (1.8) | 14.8 | 23.4 | 9.1 | 21.2 | 8.7 | 29.9 | 21.1 | 24.0 | 42.5 |
| A | 288 / 270 (73.0) | 6.9 (1.8) | 16.9 | 23.4 | 11.4 | 22.7 | 3.2 | 35.1 | 26.0 | 27.0 | 8 |
| B | 260 / 249 (68.2) | 6.9 (1.8) | 16.9 | 25.9 | 11.8 | 20.2 | 3.2 | 29.9 | 25.2 | 26.1 | 9 |
| C | 308 / 291 (79.4) | 11.2 (2.9) | 15.1 | 19.6 | 10.8 | 22.7 | 3.1 | 32.5 | 23.9 | 24.9 | 8 |
| D | 319 / 293 (80.5) | 6.8 (1.7) | 18.3 | 22.9 | 12.3 | 25.2 | 2.9 | 39.6 | 28.4 | 29.5 | 5 |
| E | 247 / 244 (60.2) | 7.7 (1.9) | 16.5 | 26.7 | 10.8 | 17.1 | 4.3 | 27.1 | 23.7 | 25.2 | 17.5 |

- **Usable carb** is the user's formula `(kcal − fat×9 − protein×4)/4`. The table's "Usable carb" column in the main table uses db kcal; the "alt" column here uses fibre at Scoopulator kcal.
- **Fibre dose per pint:** A 15 g inulin + 15 g polydextrose, B 8 + 8, C 12 + 15, D 15 + 25.
- **Gums:** total gums are 0.25% of mix in A–E. Book base xanthan alone is 0.22% (ICC lists 0.05–0.2% as typical). Second carries 0.46% gums, near the skill's 0.5% cap.

**Calibration (same engines).**

| | Site | ICC PAC se / PACtot / POD / TS / MSNF / serving °C | Note |
|---|---|---|---|
| Vanil-Low | 31.25 (printed 31.24) | 30.5 / 32.2 / 7.6 / 20.9 / 3.7 / −13.1 | ICC MSNF 3.7% vs site 6.5%: ICC treats soy milk and cottage cheese differently |
| Jeni's Base (conventional) | 21.52 (printed 21.46) | 18.9 / 20.0 / 15.4 / 38.4 / 6.4 / −10.7 | FW@−9 70.8% |
| Milky Whey (real, probed) | 32.36 | 29.4 / 30.4 / 6.4 / 24.9 / 9.2 / −13.7 | FW@−9.6 °C ≈ 65.6% (interpolated) |

- Scoopulator's calibration pint (1,006 kcal, TS 34.9%, FPD 16.8) has no quantities in the brief, so I did not run it in ICC.
- A cream/whole-milk/sugar mix that fits 1,006 kcal and 34.9% TS (172 g cream 36%, 243 g milk, 67 g sugar) gives a site-style PAC of about 17–18 [inference].
- That is consistent with Scoopulator's 16.8 on the same per-mix scale. The composition itself is my inference.

**Analysis: do the three scales agree?**

- **ICC "PAC se" ÷ 10 is the site's per-100-g PAC without salt.**
  - Book base 30.6 vs 30.1. Original 30.9 vs 31.0. Second 31.8 vs 31.7. E 17.5 vs 17.5.
  - A–D differ only through the fibre coefficients: ICC 13.2–14.1 sits between the db (10.5–13.2) and table (15.5–17.3) values.
  - ICC's salt term (PACtot − PAC se) corresponds to about 5.85 per 1% of weight (the "585 undissolved" value).
- **Scoopulator's FPD is the same per-mix quantity.** Residuals from the reported values, controls at ~35, A–E inside 19.5–22:

  | Scale | Max deviation | Mean deviation |
  |---|---|---|
  | Scoop-style (table coefficients + salt 10.7) | 0.9 | 0.3 |
  | Site sheet, table coefficients | 1.5 | 0.5 |
  | Site sheet, db coefficients | 6.3 | 3.0 |
  | ICC PAC se ÷ 10 | 6.3 | 4.7 |
  | ICC PACtot ÷ 10 | 5.5 | 3.7 |
  | ICC PAC per water ÷ 10 | 5.3 | 2.3 |

  The reported A–E range cannot rank individual recipes, so this is a range fit, not a regression. The better fit comes from using the table's inulin and polydextrose coefficients and the 1070 salt value (the same value Scoopulator's learn page states) [inference].
- **Scoopulator's kcal, TS, MSNF and protein are reproduced.**
  - kcal within 2 for all seven (alt column).
  - TS within 0.3, MSNF within 0.2, protein within 0.4.
  - Fibre within 0.4 g, except D where mine is 36.1 vs its 35.7.
  - Erythritol POD back-calculates to about 65 (site: 75), so its controls' sweetness reads lower than the site POD.
- **Firmness at −9 °C.**
  - Controls agree within 2 points (ICC 62.8–64.7 vs Scoopulator 61–63).
  - ICC is 4–9 points higher for A–E (78.9–81.6 vs 72.3–77.3). The rank correlation (Spearman) is about 0.61. Both separate controls from A–E.
- **ICC frozen water depends on overrun, which is undocumented.**
  - Original with overrun 0 vs the inherited 25%: FW@−9 goes 64.7 → 68.1%; serving temp goes −13.3 → −11.4 °C.
  - A with overrun 0: 81.0 → 85.3%; serving temp −6.6 → −5.6 °C.
  - Treat ICC serving temp as sensitive to this setting.
- **Direction of the A–E error.** Lower PAC means harder at a given temperature. A–E are predicted to be firm and to need warm-up or respin, not soft.
- **Hypothesis from 8.2 (erythritol recrystallisation reduces effective PAC).** None of the three tools models recrystallisation. The calculators agree on PAC, so the hypothesis is untested by this evidence.

---

## 6. Closest jhermann recipes

Criteria: dairy milk or cultured-dairy base, fat ≤ ~4%, erythritol-family sweetener, ≤ ~110 kcal/100 g. Scaling is ×⅔ (Deluxe → 16 oz); 16 oz weights computed from the CSVs. All are rated by the author unless noted.

| Recipe | 16 oz g / kcal | /100 g kcal / fat / protein | PAC / MSNF % / TS est. | Sweetener | Stabiliser | Program notes |
|---|---|---|---|---|---|---|
| **Cheesecake Light** | 458 / 353 | 77.1 / 0.6 / 6.5 | 32.1 / 9.3 / ~23 | SweEX 40 g (4%) | inulin 20 + Salty Stability 15 (31 g inulin in all) | Light Ice Cream → scrape → mix-in or respin; 5 stars (`README.md:31`) |
| Buttermilk Vanilla | 447 / 427 | 95.5 / 4.1 / 5.3 | 30.9 / 9.7 / ~23 | SweEX 45 g | waxy maize starch 10 g | Light Ice Cream, scrape, respin; tip: 2% Fairlife, no cream, ~525 kcal per Deluxe |
| Buttermilk Stracciatella | 457 / 437 | 95.8 / 2.1 / 6.9 | 31.3 / 12.1 / ~24 | SweEX 35 g | Salty Stability 10 g + SMP 15 g | Sorbet program, scrape, mix-in; includes mix-in chocolate |
| Milky Whey | 455 / 468 | 102.9 / 4.3 / 4.7 | 32.4 / 9.5 / ~24 | SweEX 35 g | inulin 15 + waxy maize 10 + guar 1.5 | Ice Cream → scrape → respin; probed −9.6 °C after spin |
| Pomegranate Light | 448 / 319 | 71.2 / 0.9 / 4.1 | 30.6 / 8.0 / ~22 | SweEX 45 g | Salty Stability 10 g | Light Ice Cream, cold-water, mix-in |
| Vanil-Low | 453 / 311 | 68.5 / 1.9 / 5.1 | 31.2 / 6.5 / ~19 | SweEX 45 g | Salty Stability 15 g | Frozen Yogurt, cold-water, Ice Cream; 5 stars |
| Speyside Vanilla | 463 / 476 | 102.7 / 4.1 / 4.5 | 32.7 / 8.8 / ~19 | SweEX 15 g + tablets + 45 g whisky | inulin 15 + waxy maize 15 | "creamy but a bit icy"; low SweEX, PAC from spirit |
| Lazy Skyr | 457 / 395 | 86.5 / 0.6 / 7.6 | 32.6 / 13.9 / ~23 | SweEX 30 g | Salty Stability 10 g | FroYo, scrape, respin or mix-in |

**What the user would change to adopt each:**

- **Common to all:**
  - Swap erythritol-only for SweEX 3:2, or accept the PAC change (section 5).
  - Replace the author's UK/EU milk rows (buttermilk 1%, quark) with US equivalents; the quark is not stocked in the US, and the site suggests low-fat cream cheese.
  - Add Salty Stability or ICSv2 (a 15 g/10 g dose per Deluxe/16 oz), or the 3-ingredient substitute (`recipes/Salty Stability/README.md`).
- **Cheesecake Light.** Replace buttermilk with 1% milk (1.0% fat vs 0.5%) and quark with a low-fat cream cheese or Greek yogurt. Remove the glycerin and vodka if not needed. Fat will rise slightly.
- **Vanil-Low.** Replace soy milk (480 g) with 2% milk; MSNF goes from 6.5% to about 9–10%. Replace cottage cheese 100 g with milk or Greek yogurt. Soy lowers lactose, so PAC will rise by about 1 point from lactose (milk sugar 4.9 vs soy 0.7).
- **Milky Whey.** Replace whole milk with 2% milk; kcal drops about 9% and fat 4.3 → ~3.3%.
- **Buttermilk Vanilla / Speyside.** 1% buttermilk is a US dairy-case item (cultured); regular 2% milk can substitute but will not give the tang.
- **Program/respin notes.**
  - The user's flow (hot water 60 s → Lite Ice Cream → Respin) differs from every recipe here.
  - 17 READMEs prescribe cold running water for 15–30 s after the first spin, never before.
  - Light Ice Cream + scrape + respin or mix-in is the common pattern; Frozen Yogurt and Sorbet programs also appear.
- All of these use 4–5% SweEX, not 9% erythritol.

---

## 7. Open questions Q1–Q18

**Q1 (Creami PAC target).** New evidence: the author's rated Creami recipes cluster at 30–33 (n = 122, median 30.71). Milky Whey (PAC 32.4) was probed at −9.6 °C after spin and an older Fruit Kefir at −7 °C after respin. ICC models Milky Whey at about 65.6% frozen water at −9.6 °C, below Scoopulator's 70–78% "standard scoop" band. The expert-glacier skill gives yet other ranges (gelato 22–26, American 18–23 firm / 24–28 soft, "home machines ~22–25", sorbet/low-fat 26–32; `SKILL.md:76-97`). The repo's evidence is empirical (author's practice), not derived. PAC alone does not determine iciness (Speyside, 32.7, "a bit icy").

**Q2 (crunch).** Nothing new beyond stage 2. Repo practice: freeze and chop wafers; add mix-ins manually with a chopstick (Milky Whey README); fold into pockets.

**Q3 (protein vs fat).** Cheesecake Light (fat 0.6%, protein 6.5 g/100 g, P/E 34%) is the author's top-rated low-fat dairy base; Lazy Skyr 0.6% fat, 7.6 g. No equivalence ratio. ICC's own "Creaminess" index scores the user's bases 10–16 and Vanil-Low 13 (0–20 = "not creamy/sorbet"; Jeni's Base 60); the formula is undocumented.

**Q4 (overrun).** The repo has only Polar's stated overruns (0% for Creami gelatos; 30% for zero-fat vanilla) and no measurement. ICC changes frozen-water% and serving temperature when overrun is set to 0 (+3.4 points FW@−9, serving temp +1.9 °C), so overrun is a live model input but its mechanism is undocumented.

**Q5 (stabilisers).** Exact ICSv2 and Salty Stability compositions confirmed (`ice-cream-recipe.py:58-73`). Salty Stability appears in 58 READMEs and ICSv2 in 23. Emulsifier-tagged recipes: 71 of 131, including 30 of 59 Low-Fat. The author's doses: a 15 g dose gives GMS 0.26% and gums about 0.2%. Waxy maize starch 10–15 g is the other recurring body agent. The user's gum doses (0.25% total in A–E) are within the skill's 0.1–0.4% (`SKILL.md:63`).

**Q6 (TS target).** The author's recipes have no TS printed. Macro-estimated TS: median 22%, p90 28.5%, only 13 of 99 recipes ≥ 28%. So the "28–33%" box is not the author's practice. ICC: Vanil-Low 20.9%, Milky Whey 24.9%, Jeni's Base 38.4%. User pints: 17.1–25.6%.

**Q7 (polyol ceiling).** The skill says keep polyols ≤ 6–8% (`SKILL.md:68`), citing cooling effect and tolerance. Doses per pint: book base 40 g erythritol (9.0%), Second 30 g + 10 g xylitol + 2.5 g glycerin, A–E 5–17.5 g polyols. No tolerance number is new.

**Q8 (conversion procedure).** No written procedure in the repo. `SKILL.md:29-38` is a generic 8-step audit (normalise → composition → PAC/POD → compare → smallest change). It does not address lactose-containing low-fat bases, erythritol recrystallisation or fibre. The only relevant items are "do not fix hardness by adding sugar alone" (`:103`), "do not reduce fat or solids without compensating" (`:104`) and the sandy/lactose warning in `trouble-shooting.md:104-120` (too much SMP). The author's conversions (Jeni's → Light: PAC 21.5 → 28.2; S&S → Light: 26.7 → 31.8) are reproduced exactly, so they are usable as worked examples. ICC's library note on SMP says watch MSNF above about 11–12% for lactose sandiness; D (12.3%) and the +25 g NFDM scenario (12.7%) are above it.

**Q9 (fibre load).** Per pint: A 15 g inulin + 15 g polydextrose (27 g fibre), B 14.4, C 24.3, D 36.1. The author's inulin per Deluxe tub is 11–35 g (×⅔ = 7–23 g per 16 oz), so A–D inulin (8–15 g) is within the author's range. The author uses no polydextrose.

**Q10 (CV signals).** Nothing new.

**Q11 (monk fruit).** ICC has no monk fruit ingredient (library has Stevia, POD 30); the site has no pure-extract row. At 240× the 0.25 g dose is 15.2 POD points of a 395 g pint, which is what Scoopulator shows. This is 80% of A–E's sweetness. 0.25/395 = 0.063%, inside the site's 0.05–0.1% range. The 0.1 g scale problem is unchanged.

**Q12 (emulsifier).** ICC's emulsifier field is 0.38% for Vanil-Low (GMS-bearing Salty Stability). The author's best low-fat dairy bases carry about 0.26% GMS. A–E have none. No data on bases without emulsifier.

**Q13 (post-spin temperature).** Two measurements exist (above): −9.6 °C after processing (Milky Whey) and about −7 °C (Fruit Kefir, older version). This supports a −9 °C order of magnitude for the end state. The hot-water step is not measured anywhere. The −18.6 °C freezer reading in `Milky-Whey_2025-09-18_6.jpg` is blurry and could read −10.6, so I do not rely on it.

**Q14 (simple thickeners vs inulin/polydextrose).** The repo uses both: waxy maize starch (Buttermilk Vanilla, Milky Whey, Speyside) alongside inulin. No head-to-head comparison.

**Q15 (program/respin).** The repo's pattern is Light Ice Cream or Frozen Yogurt, cold water after the first spin, then respin or mix-in. 17 READMEs use cold running water for 15–30 s after. The site warns against hot water before the first spin (`tips+tricks.md:36,295-298`).

**Q16 (will A–D scoop as predicted).** Calculators disagree on firmness (ICC 81% frozen at −9, Scoopulator 72–77%); both say firmer than the controls. ICC's Crumbly score for A–D is 94–97 (controls 58, E 76). Relative to the author's practice at PAC 30–33, A–E are about 12–17 PAC points lower, so expect firmer.

**Q17 (do Scoopulator's solids/MSNF/firmness targets apply?).** Computed: author's rated recipes have TS about 19–25% and MSNF 6.5–12%; the Scoopulator 28–32% TS and 12–14% MSNF targets are above nearly all of them. Whether the 70–78% frozen band applies to a shaved block is not answerable from the repo (Milky Whey at −9.6 °C is about 65.6% frozen per ICC).

**Q18 (inulin as bulking agent below 3% fat).** Nothing new beyond the author's inulin usage (up to 35 g per Deluxe). Speyside's "a bit icy, hopefully fixed now by adding inulin" is the only direct remark.

---

## 8. Contradictions register

1. **Salt coefficient.** Sheet 5.9 applied to explicit salt rows twice (`.fods:761, 9465`); glossary says 5.9 added once (`glossary.md:71`); docs table 1070 / 585 (`ingredients.md:36`, commit 4be64ea); ICC about 585 [API]; Scoopulator "over 1,000%" [web].
2. **Inulin PAC.** db 0.09 (`nutrition-db.csv:135`); table 0.22; ICC 0.134; Scoopulator fit suggests about 0.22.
3. **Polydextrose.** db blank (carbs 4.7, kcal 191, `:208`); table PAC 100; ICC 0.40, 200 kcal; text "1 kcal/g"; Scoopulator 1.0 kcal/g.
4. **Maltodextrin.** db 1.29; table 0.34; ICC 0.325.
5. **Erythritol kcal.** Site 24/100 g; Scoopulator about 20; ICC library 240 (while its Energy calc is non-additive).
6. **Spirits PAC.** Site 2.96 per g for "40 vol%" (vol% treated as wt%); db also has a "by volume" row of 2.34; ICC 2.47 per g (33.4% by weight). The site over-credits spirits by about 20% per gram.
7. **SMP MSNF.** Glossary 97%; sheet 95−fat = 94.03; ICC 97%.
8. **PAC targets.** Glossary 20–25 / 24–28 / 30–36; printed "20..30"; Scoopable ≥30; skill 22–26 gelato, 18–28 American, 26–32 sorbet/low-fat; actual recipes 30–33; the user's A–E 13–20.
9. **Light/Low-fat thresholds.** "<75" (faq/principles), "at most 75" (`tags.md:15`), code `<=75`; Low-Fat "below 3 g" (skill) vs sheet ≤3; Low-Cal ≤40 (sheet) vs "<85" (recipe-guide).
10. **Stale numbers.** `docs/tags.md:28-39` list differs from READMEs (section 3, #12); `recipes/README.md:28` says Vanil-Low 59.9.
11. **Tools.** `scripts/icc-tool.py:160` calls a function that does not exist; the repo's tests do not cover the stat formulas.
12. **Folder count.** 131 recipe folders (CLAUDE.md and stage 2 say 133).
13. **Scoopulator vs site vs ICC.** Controls: site no-salt 31.0, site sheet 34.3–35.1, ICC 30.9–31.8, Scoopulator ~35. Resolved as a salt/coefficient difference (section 5). A–D: site-db 10.5–13.2, table 15.5–17.3, ICC 13.2–14.1, Scoopulator 19.5–22.
14. **Erythritol POD.** Site 75; Scoopulator about 65 (back-calculated); ICC 70.
15. **Fairlife baseline.** PF "≈27" vs 27.9 by site coefficients.
16. **User workflow vs site.** Hot water 60 s before the first spin vs site's prohibition and damage warning; the site's own recipes use cold water only after the first spin.
17. **Milk in the db.** No US 1%/2% rows; the site's nearest are 1.5% German and 2% Fairlife/Natrel (ultrafiltered, which the user excludes).
18. **Starry Night.** "Too soft" remark applies to an earlier version; the printed PAC 29.59 is for the adapted recipe.
19. **Stage 2's "SweEX 40–45 g in all Light recipes"** is the mode, not the range (20–50 g).
20. **Erythritol "<8%"** (site) vs the user's 9.0–9.5%; no author recipe exceeds 6.8% plain erythritol.

---

## 9. API log

- **Smoke tests:** `GET /recipes/test` → 200 `{"message":"Recipes API is working"}`. `GET /recipes` (with key) → 200, count 0 before my writes.
- **Ingredient cache:** `GET /ingredients?detail=full` → 200, 397 ingredients, cached in `api\ingredients_full.json` (no key in it).
- **Writes:** only `POST /recipes` ×14 (all returned a recipeId); then `GET /recipes/{id}/calculated` ×14. No PUT, DELETE, ingredient writes or balance calls. No 429s or other errors. Smart Balance not run (no recipe has a chart: `hasChart=false`).
- **Duplicate check:** the list was empty before the first create; `run_create.py` checks externalId before creating.
- **Substitutions (library id):**
  - 2% milk → "Milk2%" (49); whole milk → "Whole milk US" (58, 3.2% fat);
  - NFDM → "Skim milk powder" (52);
  - Lakanto → Erythritol (160);
  - Xylitol (180); Glycerin (9123); Inulin (132); Polydextrose (137); Xanthan (156); Guar (146); Salt (138);
  - vanilla bean paste (17417);
  - **pure monk fruit extract → Stevia (175), 0.25 g (no monk fruit in the library; POD 30 vs 240, so ICC sweetness for A–E is understated by about 52 g sucrose-equivalent);**
  - Vanil-Low: soy milk (139), cottage cheese (9148), brandy (17453), SweEX → erythritol 27 g + xylitol 18 g, Salty Stability → inulin 11 + GMS (17413) 1.8 + CMC (142) 0.9 + guar 0.6 + salt 0.5 + xanthan 0.2, vanilla bean powder → "Vanilla powder" (17418), whey+casein → "Whey Protein Powder" (9204);
  - Jeni's Base: whole milk (56) 295, "Cream 33" (30) 225 (for 32%), sugar (176) 95, Karo light corn syrup (9137) 20, "Cream cheese" (31, 34% fat vs the site's 23%), corn starch (143) 10, salt 1;
  - Milky Whey: whole milk 550, glycerin 15, brandy 10, erythritol 21 + xylitol 14, inulin 15, Whey Protein Powder 15, corn starch (for waxy maize) 10, guar 1.5, salt 1, "Cream 33" 30.
- **Assumptions:**
  - Overrun inherited (−1): effective `Overrun` = 25% (global default) in 12 recipes. Two variants set `overrun: 0` (Original, A).
  - `evaporation` 0 (Evaporation 0.00 g).
  - Serving temp depends on the account's frozen-water settings, which are not readable through the API. I read their effect from the returned fields: Ice cream 75%, Gelato 69%, Extraction 55%; temperatures in °C.
  - ICC PAC/POD are per kg (×10 vs per 100 g); I divided by 10.
- **`[research]` recipes created (id, externalId):**
  - 182133 `research-book-base`
  - 182134 `research-book-base-plus25nfdm`
  - 182135 `research-original`
  - 182136 `research-second`
  - 182137 `research-a-lean`
  - 182138 `research-b-light-fiber`
  - 182139 `research-c-whole-milk`
  - 182140 `research-d-max-solids`
  - 182141 `research-e-own-ingredients`
  - 182142 `research-vanil-low`
  - 182143 `research-jenis-base`
  - 182144 `research-original-overrun0`
  - 182145 `research-a-lean-overrun0`
  - 182146 `research-milky-whey`
  - All names start `[research] `. All are left in the account.
- **Secret hygiene:** `grep -rlF` for the key value across the scratchpad returns 0 files. The only `icc_` pattern hits are my own file names (`icc_results.json`, `icc_table.py`) and identifiers, not keys. I deleted the downloaded API reference page (it contained placeholder `icc_your_key` strings). The key was never printed or written; the scripts read it from `.env` at runtime.

---

## 10. Limits and suggested next steps

**Limits.**

- The 2% and whole-milk rows, the NFDM kcal and the fibre kcal are assumptions (section 5). The Lakanto composition is assumed to be pure erythritol. The monk fruit potency of 240× is IA's.
- 108 of 131 recipe CSVs parse; the other recipe CSVs have different layouts, and two parsed ones are outliers.
- Macro-TS is a lower bound by about 1–2 points.
- ICC's energy is non-additive and its FW changes with overrun, with no documentation. The "Crumbly", "Creaminess" and "Body" indices are ICC-internal and unvalidated.
- The Ninja calibration pint's quantities are unknown, so it was not run. The Scoopulator reconstruction is a fit to ranges, not a check against its source.
- Nothing here models erythritol recrystallisation, protein effects on freezing, or the Creami's shaving process.

**Empirical tests that would settle what modeling cannot.**

1. **Probe temperature** right after each step (spin, respin) for the book base and one A–E variant, with and without the hot-water step.
2. **PAC sweep:** the book base at PAC ≈ 31 versus a SweEX version (45 g, 6% erythritol) at the same PAC, for iciness and hardness after a week in the freezer. This tests the recrystallisation hypothesis directly.
3. **A vs B (half pint)** at PAC 14–19 to see whether the firmness prediction (ICC) or the Scoopulator band holds.
4. **TS ladder:** 20% vs 25% TS at the same PAC (NFDM 0 vs 25 g) to test whether the author's 19–25% TS is enough for the user's base.
5. **Weigh the pint before and after spinning** to measure actual overrun (an input both calculators use).
6. **Check the Lakanto label** and a monk fruit dilution protocol before relying on the 0.25 g dose.
