# LaTeX Compilation Reference

## Engines
- **pdflatex**: Standard. Fails on complex Unicode.
- **xelatex**: Native Unicode and system fonts (`fontspec`).
- **lualatex**: Modern, Unicode, handles complex scripts (Bengali, Arabic, Chinese, Japanese) well. Recommended for multilingual.

## Bibliography
- **biber** + **biblatex**: Modern standard. `\usepackage[backend=biber,style=ieee]{biblatex}`
- **bibtex**: Legacy, still required by some venues.

## Compilation Workflow
1. `latexmk -pdf -interaction=nonstopmode main.tex` (Best practice)
2. Manual fallback:
   - `pdflatex main.tex`
   - `biber main`
   - `pdflatex main.tex`
   - `pdflatex main.tex`

## Error Recovery
- `! LaTeX Error: File \`styname.sty' not found.` -> Install package (`tlmgr install styname`) or fix name.
- `! Undefined control sequence.` -> Missing `\usepackage` or typo.
- `Underfull \hbox` -> Warning, can ignore.

## Makefile Example
```makefile
all:
	latexmk -pdf -interaction=nonstopmode main.tex
clean:
	latexmk -C
```

## latexmkrc Example
```perl
$pdf_mode = 1;
$pdflatex = 'pdflatex -interaction=nonstopmode -synctex=1 %O %S';
```