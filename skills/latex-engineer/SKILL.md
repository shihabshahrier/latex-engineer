---
name: latex-engineer
description: >
  Generate, compile, debug, and maintain production-ready LaTeX projects.
  Invoke via /latex-engineer or /new resume, /compile, etc.
  Produces complete compilable LaTeX structures, PDFs, and handles citations.
  Ideal for academia, research, resumes, technical reports.
license: MIT
compatibility: ">=1.0"
user-invocable: true
disable-model-invocation: false
argument-hint: 'command [args]'
when_to_use: >
  Use when user says build a resume, compile latex, fix tex errors, or any /new command related to tex.
model: sonnet
effort: high
---

# latex-engineer

Generate, compile, debug, and maintain production-ready LaTeX projects automatically. This is a full LaTeX project operating system.

## Prime Directive

Function as a complete LaTeX project operating system. Always prioritize successful compilation, academic correctness, professional formatting, and clean project structure.

## Invocation & Commands

| Command | Action |
|---------|--------|
| `/new {type}` | Generate a new project (e.g., `resume`, `ieee-paper`, `thesis`, `beamer`) |
| `/compile` | Compile current project to PDF |
| `/fix-errors` | Parse compiler logs and repair issues |
| `/optimize-ats` | Optimize resume for ATS compatibility. Load `references/ats-optimization.md`. |
| `/change-template {to}` | Switch document class/format |
| `/clean-build` | Remove auxiliary build files |

## Mode Detection

| Signal | Mode | Action |
|--------|------|--------|
| `/new ...` or "create a..." | **Scaffold** | Generate folder structure, main.tex, refs, Makefile. Load `references/templates.md`. |
| `/compile`, "build PDF" | **Compile** | Check LaTeX installed (`which latexmk`). Run compilation. If error, switch to Debug mode. Load `references/compilation.md`. |
| `/fix-errors`, "failed" | **Debug** | Parse .log files, identify missing packages or syntax errors. Fix and Recompile. |
| `/optimize-ats` | **Optimize** | Review format, maximize machine readability. Load `references/ats-optimization.md`. |
| "change format to..." | **Refactor** | Swap class files, adjust sections. |

## Phases

### Phase 1: Project Generation
Generate complete modular structure:
```text
project/
├── main.tex
├── references.bib
├── sections/
│   ├── abstract.tex
│   └── introduction.tex
├── figures/
├── tables/
├── styles/
├── Makefile
├── latexmkrc
└── README.md
```
*Load `references/templates.md` before generating.*

### Phase 2: Implementation & Editing
Write LaTeX files. Use proper semantic sections. For non-English/Unicode, default to `lualatex`. Support continuous iterative editing.

### Phase 3: Compilation Pipeline
1. Verify LaTeX installation: `which latexmk || which pdflatex`. If missing, instruct user to install TeX Live (`brew install --cask mactex` on macOS, `sudo apt install texlive-full` on Ubuntu).
2. Run compilation using `latexmk` or chosen engine.
3. If fails, read `.log`.
4. Fix errors (missing packages, bad syntax).
5. Run `biber` or `bibtex` if citations changed.
6. Produce final PDF.
*Load `references/compilation.md` before compiling.*

## Prohibited Actions
- Never leave syntax errors unresolved.
- Never use non-existent LaTeX packages.
- Never ignore compiler warnings about missing references or citations.
- Never write monolithic `main.tex` for large projects (split into `sections/`).

## Success Criteria
- Modular project structure generated.
- `main.tex` and all `sections/*.tex` follow semantic LaTeX.
- Bibliography correctly managed via `biblatex` and `biber`.
- Compilation succeeds with zero `!` errors in log.
- Final production-quality PDF produced.

## Token Efficiency Rules
- Skip explaining LaTeX internals unless asked.
- Provide direct, copyable file contents.

## Open-Weight Model Rules
- Substitute all placeholders in output.
- Always output clean, valid LaTeX.