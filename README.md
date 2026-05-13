# LaTeX Engineer Skill

An advanced AI-powered LaTeX engineering skill. Functions as a full LaTeX project operating system capable of generating complete projects, compiling PDFs, fixing errors, managing citations, supporting iterative editing, and maintaining large document structures.

## Usage
Invoke via standard commands:
- `/new resume`
- `/new ieee-paper`
- `/compile`
- `/fix-errors`
- `/add-citation {doi}`

## Installation

```bash
# All agents at once
bash install.sh
```

## Agent Support
- Claude Code
- opencode
- Codex
- Gemini CLI
- OpenClaw
- Cursor
- Windsurf
- Cline
- GitHub Copilot

## How it works
1. **Scaffold**: Generates proper folder structure, `main.tex`, and `Makefile`.
2. **Build**: Compiles using `latexmk` (pdflatex, xelatex, or lualatex).
3. **Debug**: Parses errors in `.log` to recover from missing packages.