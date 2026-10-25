# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository layout

The git repo root is the user's own repo. It contains two folders:

- `jhermann/` holds a copy of the forked upstream project `jhermann/ice-creamery` (Ninja Creami recipes + MkDocs site). All of the code, docs and commands below belong to it, and are run from inside `jhermann/`.
- `research/` is for the user's own research into that project (currently empty).

Because the project is a subfolder, its `.github/workflows/` is not at the git root and won't run on GitHub unless moved. Paths in this file are relative to `jhermann/`.

## Commands

```sh
python3 -mpip install -r ./requirements.txt   # deps (mkdocs plugins + pytest)
pytest                                        # all tests
pytest tests/test_utils.py                    # one file
pytest tests/test_utils.py::test_name         # one test
pylint --fail-under=8.0 $(git ls-files '*.py')  # CI lint gate (Python 3.10)
./linkdocs.sh && mkdocs serve 2>&1 | grep -v 'INFO.*absolute link'   # local site
MKDOCS_EXPORTER_PDF=true mkdocs build        # also render site/.well-known/site.pdf
```

`linkdocs.sh`, `refresh-recent.sh` and `scripts/*.sh` are bash scripts using GNU tools (`find -xtype`, `date --iso`); run them from WSL/Git Bash. `linkdocs.sh` must run before `mkdocs serve/build` (CI does this too).

## Architecture

**Recipe pipeline.** Recipes are authored as sheets in LibreOffice Calc (template: `recipes/Ice-Cream-Recipes.fods`; one sheet per recipe, duplicated from the template sheet). A sheet is exported via *Save a Copy → Text CSV* as `Ice-Cream-Recipes.csv`, and `scripts/ice-cream-recipe.py` converts it to `recipes/<Name>/README.md`, using `scripts/nutrition-db.csv` for macro/ingredient metadata. The converter depends on the exact row structure of the template sheet (`tests/test_recipe_template_sheet.py` guards this), so changing the template means changing the script. Each recipe folder also holds the CSV and its images.

**Docs site.** MkDocs Material, configured in `mkdocs.yml`; content root is `docs/`, but recipes live in `recipes/`. `linkdocs.sh` bridges them: it creates `docs/<Letter>/<Name>.md` symlinks (and image symlinks) to each `recipes/<Name>/README.md`. `Toppings` and `Piña Colada Cocktail (Deluxe)` are special-cased: their README is copied and concatenated with `recipe-*.md` parts instead of symlinked. Broken symlinks are cleaned on each run, so don't hand-edit files under `docs/<Letter>/`.

**Macros.** `macros.py` (mkdocs-macros plugin) loads `scripts/ice-cream-recipe.py` as a module via importlib (hyphenated filename, so it can't be imported normally) and calls `parse_info_docs('ingredients', '### ')` on import, so the converter script doubles as a library for the site build. Tests load scripts the same way through the `load_script_module` fixture in `tests/conftest.py`.

**Other scripts.** `scripts/recipe.py` lists/searches/opens recipe sheets in LibreOffice (config via `--create-config`); `icc-tool.py` converts recipe CSVs to icecreamcalc JSON; `_utils.py` has shared helpers; `refresh-recent.sh` regenerates `docs/changed.md` from the last 2 months of git history. `scripts/update-all-md.sh` references a `wiki/` dir that is not in this repo.

**Licensing.** Content in `assets/`, `docs/`, `recipes/` is CC BY-NC 4.0; code is under the repo `LICENSE`.

## Conventions

Detailed rules live in `.github/instructions/` (also surfaced via `.github/copilot-instructions.md`); read the relevant file before editing that file type:

- **Python** (`python-style`, `python-tests`, `secure-development`): max 110-char lines, 4 spaces, double quotes, grouped imports, break before binary operators, trailing commas in multi-line collections, pytest only with shared fixtures in `tests/conftest.py`.
- **Markdown** (`markdown-style`) and **recipe/video content** (`content-creator`, applies to `recipes/*/README.md`, `docs/contributed/*.md`, `docs/youtube/*/*.md`): fixed recipe section structure (metadata, H1 title, stats table, description, ingredients in grams with imperial in parentheses, directions, nutrition facts); Creami recipes carry a Deluxe (24oz) / Standard (16oz) marker in the title.
- **Ice cream science** (`expert-glacier` instructions and `.github/skills/expert-glacier`): PAC/POD/solids reasoning for recipe formulation.
