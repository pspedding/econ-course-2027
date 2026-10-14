# 📚 Resources

Supplementary materials to use alongside this course. Everything here is freely available online or in the shared Dropbox folder.

---

## Textbook

**Wooldridge, J.M. — Introductory Econometrics: A Modern Approach**

The primary reference for the modules. Chapter and page references may vary across editions; check examples against your copy. If you have access, look in the shared Dropbox folder under `ECMT5001 - Principles of Econometrics/`.

| Edition | Notes |
|---|---|
| 8th ed. | Current publisher edition; do not assume it is the unit’s prescribed text |
| 7th ed. | Reference edition used in these self-study notes; check your unit outline for prescribed texts |
| 5th–6th ed. | Useful for self-study, but chapter, example and page details can differ |

---

## R Resources

This course uses R for applied examples. The `wooldridge` R package gives you all 115 textbook datasets ready to load in one line.

### Install the package

```r
install.packages("wooldridge")
library(wooldridge)
```

### Key R resources

#### 1. Introductory Econometrics Examples (vignette)
**<https://justinmshea.github.io/wooldridge/articles/Introductory-Econometrics-Examples.html>**

The official package vignette. Reproduces worked examples from Chapters 2–18 of Wooldridge using R. Covers simple OLS through IV/2SLS and time series. **Start here** if you are new to R and want to see the textbook examples in code.

- Ch 2: Simple regression — log wage equation (`wage1`)
- Ch 3–4: Multiple regression, inference (`gpa1`, `hprice1`)
- Ch 8: Heteroskedasticity (`hprice1`, `smoke`)
- Ch 10–12: Time series (`intdef`, `barium`)
- Ch 15: IV/2SLS (`mroz`, `card`)

#### 2. r-econometrics.com — Wooldridge Chapter Reproductions
**<https://www.r-econometrics.com/reproduction/wooldridge/wooldridgeintro/>**

Chapter-by-chapter R reproductions of every main-text example in Wooldridge (2013, 5th ed.), with additional commentary. Covers Ch 2–19. Useful as a second reference if the vignette examples are unclear.

#### 3. wooldridge Package Reference Manual (CRAN)
**<https://cloud.r-project.org/web/packages/wooldridge/refman/wooldridge.html>**

Full documentation for all 115 datasets: variable names, descriptions, sources, and page references to the textbook. Use this to look up a dataset before loading it.

#### 4. Heiss — *Using R for Introductory Econometrics* (2nd ed., 2020)
**<http://www.urfie.net/>**

A free companion textbook that mirrors Wooldridge chapter-by-chapter and teaches R alongside the econometrics. Recommended if you want a more structured R introduction than the vignette alone provides.

---

## Datasets

All 115 Wooldridge datasets are available in two ways:

1. **Via the R package** — `data(wage1)`, `data(hprice1)`, etc.
2. **Dropbox folder** — raw files in `ECMT5001 - Principles of Econometrics/` (CSV and Stata `.dta` formats)

Key datasets by module:

| Module | Dataset(s) | Topic |
|---|---|---|
| M01 | `wage1`, `gpa1` | Summary stats, distributions |
| M02 | `wage1`, `ceosal1` | Simple OLS, log-wage |
| M03 | `gpa1`, `hprice1` | Multiple regression |
| M04 | `gpa2`, `meap93` | t-tests, F-tests |
| M05 | `hprice1`, `wage1`, `cps78_85` | Log models, dummies |
| M06 | `hprice1`, `smoke` | Heteroskedasticity tests, WLS |
| M07 | `lawsch85`, `wage2` | Proxy variables, measurement error |
| M08 | `intdef`, `fertil3` | Time series, FDL models |
| M09 | `barium`, `nyse` | Serial correlation, Cochrane-Orcutt |
| M10 | `mroz`, `card` | IV, 2SLS, DiD |

---

## Publisher and package links

| Resource | Link |
|---|---|
| USYD ECMT5001 unit page | <https://www.sydney.edu.au/units/ECMT5001> |
| Cengage Book Companion Site | <https://www.cengage.com/cgi-wadsworth/course_products_wp.pl?fid=M20b&product_isbn_issn=9781111531041> |
| CRAN wooldridge package | <https://cran.r-project.org/web/packages/wooldridge/> |
| Package source (GitHub) | <https://github.com/JustinMShea/wooldridge> |

!!! note "Cengage materials"
    The Cengage companion site requires institutional access for instructor materials (solutions, test banks). Link to the public-facing companion only; do not reproduce Cengage-owned content.

---

## USYD ECMT5001

This self-study course is intended to support USYD **ECMT5001 Principles of Econometrics**. The week-by-week mapping below is an indicative study plan, not a verified Semester 1 2027 unit outline; check the official outline when available.

| Course Module | ECMT5001 Lectures | Wooldridge Chapters |
|---|---|---|
| M01 | Wk 1 — Probability & Stats Review | Appendix B–C |
| M02 | Wk 2 — Simple Regression | Ch 2 |
| M03 | Wk 3 — Multiple Regression | Ch 3–4 |
| M04 | Wk 4 — Inference | Ch 4–5 |
| M05 | Wk 5 — Functional Forms | Ch 6–7 |
| M06 | Wk 6 — Heteroskedasticity | Ch 8 |
| M07 | Wk 7 — Specification | Ch 9 |
| M08 | Wk 8 — Time Series | Ch 10–11 |
| M09 | Wk 9 — Serial Correlation | Ch 12 |
| M10 | Wk 10 — IV & DiD | Ch 15 |
