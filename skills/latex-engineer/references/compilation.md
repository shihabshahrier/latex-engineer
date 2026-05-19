# LaTeX Compilation Reference

## Installation Detection
Before compiling, verify LaTeX is available:
```bash
which latexmk || which pdflatex
```
If missing, instruct user:
- **macOS**: `brew install --cask mactex` (full) or `brew install --cask basictex` (minimal)
- **Ubuntu/Debian**: `sudo apt install texlive-full`
- **Fedora**: `sudo dnf install texlive-scheme-full`
- **Windows**: Install MiKTeX or TeX Live from https://tug.org/texlive/

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

## latexmkrc — pdflatex (default)
```perl
$pdf_mode = 1;
$pdflatex = 'pdflatex -interaction=nonstopmode -synctex=1 %O %S';
```

## latexmkrc — xelatex
```perl
$pdf_mode = 5;
$xelatex = 'xelatex -interaction=nonstopmode -synctex=1 %O %S';
```

## latexmkrc — lualatex
```perl
$pdf_mode = 4;
$lualatex = 'lualatex -interaction=nonstopmode -synctex=1 %O %S';
```

## XeLaTeX Compilation (manual)
```bash
xelatex -interaction=nonstopmode main.tex
biber main
xelatex -interaction=nonstopmode main.tex
xelatex -interaction=nonstopmode main.tex
```

## LuaLaTeX Compilation (manual)
```bash
lualatex -interaction=nonstopmode main.tex
biber main
lualatex -interaction=nonstopmode main.tex
lualatex -interaction=nonstopmode main.tex
```