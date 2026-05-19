# LaTeX Templates Reference

## Resumes & CVs

### ATS-Friendly Resume
- Use standard fonts, avoid complex nested tables or multicolumns, use `\section` natively.
- Avoid `minipage` for critical text. Use simple `\textbf`, `\hfill`, `itemize`.
- See `references/ats-optimization.md` for full ATS rules.

```latex
\documentclass[11pt,a4paper]{article}
\usepackage[margin=0.75in]{geometry}
\usepackage{enumitem}
\usepackage{hyperref}
\pagestyle{empty}

\begin{document}

\begin{center}
  {\LARGE\textbf{First Last}} \\[4pt]
  email@example.com \quad | \quad +1-555-000-0000 \quad | \quad City, State
\end{center}

\section*{Experience}
\textbf{Job Title} \hfill Company Name \\
\textit{Start -- End} \hfill City, State
\begin{itemize}[nosep,leftmargin=*]
  \item Accomplished X by doing Y, resulting in Z.
\end{itemize}

\section*{Education}
\textbf{Degree} \hfill University \\
\textit{Year} \hfill City, State

\section*{Skills}
Skill1, Skill2, Skill3

\end{document}
```

### Academic CV
- Use `moderncv` (classic style) or `currvita`.

```latex
\documentclass[11pt,a4paper]{moderncv}
\moderncvstyle{classic}
\moderncvcolor{blue}
\usepackage[margin=0.75in]{geometry}

\name{First}{Last}
\email{email@example.com}
\phone{+1-555-000-0000}

\begin{document}
\makecvtitle

\section{Education}
\cventry{Year}{Degree}{University}{City}{}{}

\section{Publications}
\cvlistitem{Author et al. Title. Journal, Year.}

\end{document}
```

## Papers & Publications

### IEEE Conference/Journal
```latex
\documentclass[conference]{IEEEtran}
\usepackage{cite}
\usepackage{amsmath,amssymb,amsfonts}
\usepackage{graphicx}

\title{Paper Title}
\author{\IEEEauthorblockN{Author Name}
\IEEEauthorblockA{University \\ email@example.com}}

\begin{document}
\maketitle
\begin{abstract}
Abstract text here.
\end{abstract}

\section{Introduction}
Introduction text.

\bibliographystyle{IEEEtran}
\bibliography{references}
\end{document}
```

### ACM (sigconf)
```latex
\documentclass[sigconf]{acmart}
\title{Paper Title}
\author{Author Name}
\affiliation{\institution{University}}
\email{email@example.com}

\begin{document}
\maketitle
\section{Introduction}
Introduction text.
\bibliographystyle{ACM-Reference-Format}
\bibliography{references}
\end{document}
```

### Springer LNCS
```latex
\documentclass{llncs}
\begin{document}
\title{Paper Title}
\author{Author Name}
\institute{University}
\maketitle
\begin{abstract}
Abstract text.
\end{abstract}
\section{Introduction}
Introduction text.
\bibliographystyle{splncs04}
\bibliography{references}
\end{document}
```

### Elsevier
```latex
\documentclass{elsarticle}
\usepackage{lineno}
\journal{Journal Name}
\begin{document}
\begin{frontmatter}
\title{Paper Title}
\author{Author Name}
\address{University}
\begin{abstract}
Abstract text.
\end{abstract}
\end{frontmatter}
\section{Introduction}
Introduction text.
\bibliographystyle{elsarticle-num}
\bibliography{references}
\end{document}
```

## Thesis / Reports / Books
```latex
\documentclass[12pt,a4paper]{report}
\usepackage[margin=1in]{geometry}
\usepackage{graphicx}
\usepackage[backend=biber,style=ieee]{biblatex}
\addbibresource{references.bib}

\title{Thesis Title}
\author{Author Name}
\date{\today}

\begin{document}
\maketitle
\tableofcontents

\chapter{Introduction}
Introduction text.

\printbibliography
\end{document}
```

For `book` class, use `\frontmatter`, `\mainmatter`, `\backmatter`.

## Beamer Presentations
```latex
\documentclass{beamer}
\usetheme{Madrid}
\title{Presentation Title}
\author{Author Name}
\date{\today}

\begin{document}
\begin{frame}
\titlepage
\end{frame}

\begin{frame}{Outline}
\tableofcontents
\end{frame}

\section{Topic}
\begin{frame}{Slide Title}
\begin{itemize}
  \item Point one
  \item Point two
\end{itemize}
\end{frame}
\end{document}
```

## Mathematical Notes & Lab Reports
```latex
\documentclass[11pt]{article}
\usepackage{amsmath,amssymb}
\usepackage{geometry}
\usepackage{graphicx}
\usepackage{siunitx}

\title{Lab Report Title}
\author{Author Name}
\date{\today}

\begin{document}
\maketitle
\section{Objective}
Objective text.
\section{Results}
\begin{equation}
  F = ma
\end{equation}
\end{document}
```