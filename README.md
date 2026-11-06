# SlideMage citation format: APA 7

Author-year citations and a reference list after APA 7 (7th edition), through biblatex-apa. A SlideMage *citation format package* (`docs/CITATION_PACKAGE.md` in
[SlideMage](https://github.com/SlideMage/SlideMage)), key `apa`. It contains one TeX file and no program.

![The reference list on a SlideMage slide](preview.png)

## What it looks like

In the text: `(Fama et al., 1993)`, `(OECD, 2023; Shetty & Manley, 2005)`, and `Kahneman (2011)` for `\textcite`.

In the list, the way APA 7 wants it, for example:

> Fama, E. F., French, K. R., Roll, R., & Ross, S. A. (1993). Common risk factors in the returns on stocks and bonds. *Journal of Financial Economics*, *33*(1), 3-56. https://doi.org/10.1016/0304-405X(93)90023-5
>
> Thaler, R. H. (2005). The end of behavioral finance. In D. Hirshleifer & S. H. Teoh (Eds.), *Advances in behavioral finance, Volume II* (pp. 1-12). Princeton University Press.

It uses biblatex-apa (`style=apa`), which implements the 7th edition. Needs biblatex-apa in the TeX installation (MiKTeX installs missing packages on demand;
with TeX Live: `tlmgr install biblatex-apa`),
biber and lualatex, which SlideMage uses anyway.

## Install

In SlideMage 0.13.0 or later: **Settings → Extensions → Citation formats → Add from GitHub…** and type

    SlideMage/slidemage-citation-apa

or download `apa-<version>.smcite` and its `.sha256` from the latest release and use **Add from file…**.

## Choose it

In a template (between `\input{SlideMage_setup}` and `\input{SlideMage_base}`), or in a deck (before
`\SMUseBibliography`):

```latex
\renewcommand{\SMCitationFormat}{apa}
```

Then cite and list as always:

```latex
\parencite{fama1993}  \textcite{kahneman2011}  \footnote{\fullcite{fama1993}}
\printbibliography[heading=none]
```

A list on a slide is set in the theme's bibliography fonts, which are body size; for more than a few entries put
`\setbeamerfont{bibliography entry author}{size=\small}` (and the same for `title`, `location`, `note`) before
`\printbibliography`, or split the list over frames with `\begin{frame}[allowframebreaks]`.

## Notes

- Titles of articles, books and chapters are set in sentence case by biblatex-apa itself; proper nouns and
  acronyms in a title that must keep their capitals need braces in the `.bib` file (`title = {The {OECD} ...}`).
- A publisher or institution name containing "and" needs double braces (`publisher = {{Farrar, Straus and Giroux}}`),
  otherwise biblatex reads it as two names.
- biblatex-apa expects `@online` for web pages and `@report` for reports and working papers.
- A project's own copy of `SlideMage_citation_apa.tex` wins over the installed one, which freezes a version.

## Licence

The TeX file is LPPL-1.3c-or-later; see `LICENSE`.
