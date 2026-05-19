# ATS Optimization Reference

ATS (Applicant Tracking System) parsers extract text from PDFs. LaTeX resumes must produce clean, parseable output.

## Layout Rules
- **No tables for layout.** ATS parsers read tables cell-by-cell in unpredictable order. Use `\textbf` + `\hfill` for side-by-side elements.
- **No multi-column layouts.** Avoid `multicol`, `paracol`, or manual column layouts. Single-column only.
- **No `minipage` for critical content.** Text inside minipages may be skipped or reordered.
- **No text boxes or `tikz` decorations** around content areas.
- **Simple margins.** Use `geometry` package, 0.5in–1in margins.

## Heading Rules
- Use standard `\section*{}` headings with conventional names:
  - `Experience` (not "Professional Background")
  - `Education` (not "Academic History")
  - `Skills` (not "Core Competencies")
  - `Projects` (not "Portfolio")
  - `Certifications`
- ATS searches for these exact headings to categorize content.

## Font Rules
- Use standard PDF fonts: Computer Modern (default), Times, Helvetica, Palatino.
- Avoid custom/decorative fonts. If using `fontspec`, stick to system serif/sans-serif.
- Minimum 10pt font size.

## Content Rules
- **No icons or symbols** for contact info. Use plain text: `email@example.com | +1-555-000-0000 | City, State`.
- **No images or graphics** in content areas.
- **Use `itemize`** for bullet points, not manual dashes or custom symbols.
- **Spell out acronyms** at first use: "Machine Learning (ML)".
- **Include keywords** from job description naturally in bullet points.

## File Rules
- Output as PDF (not DVI or PS).
- Filename: `FirstLast_Resume.pdf` (no spaces, no special characters).
- Single page for <10 years experience, two pages max.

## Packages to Avoid
- `fancyhdr` with complex headers (simple page numbers OK)
- `tikz` for layout elements
- `tcolorbox` around content
- `fontawesome` / `fontawesome5` (icons not parsed)
- `tabularx` / `longtable` for layout (OK for actual data tables)

## Packages Safe to Use
- `geometry` — margins
- `enumitem` — list formatting
- `hyperref` — clickable links (ATS reads `href` URLs)
- `titlesec` — section heading styling (keep simple)
- `xcolor` — subtle color OK, but ensure sufficient contrast

## Verification
After compilation, test parsability:
1. Open PDF, Select All (Cmd+A / Ctrl+A), paste into plain text editor.
2. If all content appears in correct order — ATS will parse it.
3. If text is garbled, reordered, or missing — fix layout.