# LaTeX Templates Reference

## Resumes & CVs
- **ATS-Friendly**: Use standard fonts, avoid complex nested tables or multicolumns, use `\section` natively. Avoid `minipage` for critical text.
- **Academic CV**: Use `currvita` or `moderncv` (classic style).

## Papers & Publications
- **IEEE Conference/Journal**: `\documentclass[conference]{IEEEtran}` or `\documentclass[journal]{IEEEtran}`. Requires `cite`, `amsmath`.
- **ACM**: `\documentclass[sigconf]{acmart}`. Requires strict adherence to ACM formatting.
- **Springer LNCS**: `\documentclass{llncs}`.
- **Elsevier**: `\documentclass{elsarticle}`.
- **arXiv preprints**: Standard `article` class with `arxiv` style package.

## Thesis / Reports / Books
- **Class**: `book` or `report`.
- **Structure**: Include `\frontmatter`, `\mainmatter`, `\backmatter`.

## Beamer Presentations
- **Class**: `\documentclass{beamer}`
- **Structure**: Use `\begin{frame}`.

## Mathematical Notes & Lab Reports
- **Packages**: `amsmath`, `amssymb`, `geometry`, `graphicx`, `siunitx`.