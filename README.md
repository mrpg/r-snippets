# r\_snippets

The file `preload.R` contains some useful R snippets that [I](https://max.pm) have developed over time. This set of snippets makes serious use of R almost possible. This set of snippets is bound to be enhanced and amended over time. Feel free to just copy that file into your own R project. You can load it like this:

```r
source("preload.R")
```

These snippets default to [HC3 standard errors](https://doi.org/10.1016/0304-4076%2885%2990158-7). (Note: Stata defaults to HC1 standard errors, which are [not recommended](https://datacolada.org/99).)

## Example

See `example.R`.

This file also shows a feature of these snippets that is frequently missed: `save_to` saves your LaTeX regression table to a file. This means that within your paper, you can do

```tex
\input{output/table1.tex}
```

No more copy and pasting! Crucially, the file name is determined automatically from your list of models.

## Dependencies

### R

To use all the functions in `preload.R`, you need these R packages:

1. texreg, preferably as found [here](https://github.com/mrpg/texreg_fork)¹
2. lmtest
3. sandwich

¹ You can use `install.packages("remotes"); remotes::install_github("mrpg/texreg_fork")` to install that.

### LaTeX

When using `tt()`, include these LaTeX packages:

```tex
\usepackage{booktabs}
\usepackage{graphicx}
\usepackage{microtype}
\usepackage{siunitx}
\usepackage{threeparttable}
```

## License

**Code:** This R code is licensed under the [GNU General Public License v3.0](https://www.gnu.org/licenses/gpl-3.0.html) (GPL-3.0). See `LICENSE` for details. Note that there is **absolutely no warranty**.

**Why GPL?** Unfortunately, because `preload.R` uses GPL-licensed R packages (texreg, lmtest, and sandwich), the code must be GPL-licensed due to the copyleft requirement. This is a regrettable constraint imposed by dependencies stemming from an unfortunate norm within the R community to prefer the GPL over the LGPL.

**Data licensing recommendation:** While this code (and your code using it!) *must* be GPL, **you should license your data under [CC0 1.0](https://creativecommons.org/publicdomain/zero/1.0/)** (see `./LICENSE-DATA`). Data and code are separate works and can have different licenses. **Always put as much as possible under CC0, especially data.** This maximizes reusability and exceeds best practices for scientific reproducibility.

### How to License Your Data Under CC0

Follow the [Social Science Data Editors licensing guidance](https://social-science-data-editors.github.io/guidance/Guidance/Licensing_guidance.html). For repositories containing both code and data:

1. **Download CC0 license:** Download `LICENSE-DATA` from this repository or run `curl -o LICENSE-DATA https://creativecommons.org/publicdomain/zero/1.0/legalcode.txt` on your computer.

2. **Specify which files are dual-licensed** using glob patterns in `README.md`. Example:

```markdown
## License

All files in this repository are licensed under the [GNU General Public License v3.0](https://www.gnu.org/licenses/gpl-3.0.html) (GPL-3.0). See `LICENSE` for full legal text. Note that there is **absolutely no warranty**.

## Data files

The following files are **dual-licensed under GPL-3.0 AND CC0 1.0** (you may choose either license):

- `*.csv`
- `*.dta`
- `*.json`
- `*.RData`
- `*.rds`
- `*.tsv`
- `*.xlsx`

This dual-licensing means you can use these data files under the maximally permissive CC0 public domain dedication if you prefer. See `LICENSE` (GPL-3.0) and `LICENSE-DATA` (CC0) for full legal texts.
```

3. **Keep code under GPL** by maintaining separate `LICENSE` (GPL) and `LICENSE-DATA` (CC0) files.

This "globbing method" ensures maximum reusability: your data gets the most permissive license (CC0) while code respects GPL dependencies. See the [Greenelab example](https://github.com/greenelab/scihub-manuscript) for a complete implementation (with different licenses).
