# NeurIPS 2026 Paper Structure & LaTeX Guide

A comprehensive guide to formatting and structuring NeurIPS papers based on official templates and accepted paper examples.

---

## Table of Contents
1. [Quick Start](#quick-start)
2. [Document Class & Options](#document-class--options)
3. [Formatting Constraints](#formatting-constraints)
4. [Page Limits & Counting](#page-limits--counting)
5. [Paper Structure](#paper-structure)
6. [Detailed Formatting Rules](#detailed-formatting-rules)
7. [Citations & References](#citations--references)
8. [Figures & Tables](#figures--tables)
9. [Mandatory Checklist](#mandatory-checklist)
10. [PDF Requirements](#pdf-requirements)
11. [Common Patterns from Accepted Papers](#common-patterns-from-accepted-papers)

---

## Quick Start

### Minimal LaTeX Header
```latex
\documentclass{article}
\usepackage{neurips_2026}
\usepackage[utf8]{inputenc}
\usepackage[T1]{fontenc}
\usepackage{hyperref}
\usepackage{url}
\usepackage{booktabs}
\usepackage{amsfonts}
\usepackage{nicefrac}
\usepackage{microtype}
\usepackage{xcolor}

\title{Your Paper Title Here}
\author{Your Name \\ Affiliation}

\begin{document}
\maketitle
\begin{abstract} ... \end{abstract}
\section{Introduction}
...
\end{document}
```

### Key Checklist Before Submission
- [ ] Paper is exactly 9 pages or less (excluding references, appendix, checklist)
- [ ] Using `neurips_2026` package (not previous versions)
- [ ] All references, acknowledgments, and checklist are properly placed
- [ ] PDF uses only Type 1 or Embedded TrueType fonts
- [ ] Double-blind anonymity maintained (no author names in text)
- [ ] Mandatory checklist included at the end
- [ ] All figures/tables have captions

---

## Document Class & Options

### Basic Usage
```latex
\documentclass{article}
\usepackage{neurips_2026}  % Default option for main track submission
```

### Track Selection Options

| Option | Purpose |
|--------|---------|
| `(none)` or `default` | Main Track (double-blind reviewing) |
| `main` | Main Track (explicit) |
| `position` | Position Paper Track |
| `eandd` | Evaluations & Datasets Track |
| `eandd, nonanonymous` | E&D Track with single-blind review |
| `creativeai` | Creative AI Track |
| `sglblindworkshop` | Workshop with single-blind reviewing |
| `dblblindworkshop` | Workshop with double-blind reviewing |

### Additional Options for Submission Status

| Option | Purpose | Usage |
|--------|---------|-------|
| (none) | Submission version | Default - adds line numbers, anonymizes |
| `final` | Camera-ready version | Add AFTER acceptance: `\usepackage[main, final]{neurips_2026}` |
| `preprint` | arXiv/preprint version | For non-anonymous preprints before/after submission |
| `nonatbib` | No natbib package | Use if natbib conflicts with other packages |

### Option Passing Examples
```latex
% For submission (default)
\usepackage{neurips_2026}

% For camera-ready version after acceptance
\usepackage[main, final]{neurips_2026}

% For arXiv preprint
\usepackage[preprint]{neurips_2026}

% If natbib conflicts with another package
\usepackage[nonatbib]{neurips_2026}

% For workshop with custom natbib options
\PassOptionsToPackage{numbers, compress}{natbib}
\usepackage[dblblindworkshop]{neurips_2026}
```

---

## Formatting Constraints

### Page Layout & Margins
- **Text area**: 5.5 inches wide × 9 inches long (33 picas × 54 picas)
- **Left margin**: 1.5 inches (9 picas)
- **Paper size**: US Letter (8.5" × 11")
- **Top margin**: 1 inch from page top to start of content
- **Page numbering**: **REQUIRED** - All pages must be numbered

### Typography
- **Main font**: Times New Roman (10-point)
- **Vertical spacing (leading)**: 11 points
- **Paragraph spacing**: 0.5 line space (5.5 points) between paragraphs
- **Paragraph indentation**: None
- **Hyphenation**: Use `\-` command when LaTeX cannot properly hyphenate

### Special Spacing
```latex
\nicefrac{1}{2}   % For fractions like 1/2
\,em              % For small spacing in \paragraph headings
\medskip          % For medium vertical spacing
```

---

## Page Limits & Counting

### Main Content Limit
- **Maximum 9 pages** including all figures and tables
- Papers exceeding this limit **will not be reviewed**

### What DOES Count Toward Page Limit
- Abstract
- All main text (Introduction, Methods, Results, etc.)
- All figures and tables
- Figure/table captions

### What DOES NOT Count Toward Page Limit
- Acknowledgments section
- References section
- Mandatory checklist
- Technical appendices (supplementary material)
- Footnotes

**Critical**: The checklist and appendices can be unlimited in length.

---

## Paper Structure

### Standard Section Order

```
[Title]
[Authors & Affiliations]
[Abstract]
1. Introduction
2. [Problem Formulation / Related Work - depends on field]
3. [Methods / Technical Approach]
4. [Experiments / Results]
5. [Discussion / Conclusion]

[Acknowledgments] (only in camera-ready, not in submission)
[References]
[Mandatory NeurIPS Paper Checklist]
[Appendix: Technical appendices and supplementary material]
```

### Common Section Hierarchy from Accepted Papers
Based on examined papers, the typical structure includes:

```
1. Introduction
2. Related Works (or "Background and Related Works")
3. Preliminaries and Backgrounds (for theory-heavy papers)
4. [Main technical sections] (e.g., "Methods", "Problem Formulation", "Algorithm")
5. Experiments (or "Experimental Results")
6. Discussion (optional, sometimes merged with experiments)
[Conclusion section optional - sometimes last subsection]

[Acknowledgments]
[References]
[Checklist]
[Appendix sections]
```

---

## Detailed Formatting Rules

### Title
- **Size**: 17-point, bold
- **Case**: Initial caps/lower case (capitalize first word and proper nouns)
- **Alignment**: Centered between two horizontal rules
- **Rule above title**: 4-point thick
- **Rule below title**: 1-point thick
- **Spacing**: 1/4 inch (1.5-2 picas) above and below rules to title text
- **Example**: `Variational Regularized Unbalanced Optimal Transport: Single Network, Least Action`

### Authors & Affiliations
- **Anonymity note**: In submission (no `final` option), do NOT include author names or identifying information
- **For camera-ready** (with `final` option):
  - Author names in **boldface**
  - Each name centered above corresponding address
  - Lead author listed first (left-most)
  - Use `\And` to separate authors (LaTeX determines line breaks)
  - Use `\AND` to force line breaks between authors
  - Format: `Name \\ Department \\ Institution \\ Address \\ \texttt{email}`
- **Footnotes for authors**: Use for webpage/alternative address (NOT for funding acknowledgments)

### Abstract
- **Environment**: `\begin{abstract} ... \end{abstract}`
- **Heading**: Word "**Abstract**" must be centered, bold, 12-point
- **Content formatting**: 10-point type, 11-point line spacing
- **Indentation**: 1/2 inch (3 picas) on both left and right margins
- **Length**: Limited to **ONE paragraph** (no line breaks between paragraphs)
- **Spacing**: Two blank lines precede the abstract
- **No citations**: Typically should be self-contained without citations

### Section Headings

#### First-Level (Section)
```latex
\section{Introduction}
```
- **Size**: 12-point, bold
- **Case**: Lower case except first word and proper nouns
- **Alignment**: Flush left
- **Example**: `\section{Submission of papers to NeurIPS 2026}`

#### Second-Level (Subsection)
```latex
\subsection{Retrieval of style files}
```
- **Size**: 10-point, bold
- **Case**: Lower case except first word and proper nouns
- **Alignment**: Flush left

#### Third-Level (Subsubsection)
```latex
\subsubsection{Headings: third level}
```
- **Size**: 10-point, bold
- **Case**: Lower case except first word and proper nouns
- **Alignment**: Flush left

#### Inline Headings (Paragraph)
```latex
\paragraph{Paragraph heading}
```
- **Formatting**: Bold, flush left, inline with text
- **Spacing**: 1em space between heading and following text

### Footnotes
- **Usage**: Sparingly (minimize use)
- **Placement**: At bottom of page where they appear
- **Numbering**: Superscript number in text
- **Separator**: 2-inch (12-pica) horizontal rule above footnote
- **Punctuation**: Footnote marker appears **after** punctuation marks
- **Example**:
  ```latex
  Here is some text.\footnote{This is a footnote.}
  ```

### Acknowledgments
- **Environment**: `\begin{ack} ... \end{ack}` (auto-hides section in submission version)
- **Placement**: Before references section
- **Visibility in submission**: Automatically hidden when no `final` option is used
- **Visibility in camera-ready**: Only appears with `final` option
- **Heading**: Use unnumbered first-level heading: `\section*{Acknowledgments}`
- **REQUIRED DECLARATIONS** (mandatory in camera-ready version):
  - **Funding disclosure**: Declare all financial activities supporting the submitted work
  - **Competing interests**: Declare related financial activities outside the submitted work
  - Reference: https://neurips.cc/Conferences/2026/PaperInformation/FundingDisclosure
- **Note**: Do NOT include acknowledgments in anonymized submission (only in final paper)
- **Example**:
  ```latex
  \begin{ack}
    We thank [people] for [contributions]. 
    
    This work was supported by [funding source].
    
    Competing interests: [declaration if applicable].
  \end{ack}
  ```

---

## Citations & References

### Citation System
- **Default package**: `natbib` (automatically loaded)
- **Citation styles**: Either author-year OR numeric (must be consistent throughout)
- **Style flexibility**: Any reference style acceptable as long as internally consistent

### Citation Commands with natbib
```latex
\cite{key}        % Numeric or year citation
\citet{key}       % Text citation: "Author (Year)" or "Author [#]"
\citep{key}       % Parenthetical: "(Author, Year)" or "[#]"
```

### Double-Blind Review Compliance
- **For anonymous submissions**: Refer to your own work in **third person**
- **Correct**: "In the previous work of Jones et al. [4], ..."
- **Incorrect**: "In our previous work [4], ..."
- **Self-citations in supplementary material**: Anonymize as "A. Anonymous" if needed

### References Section
- **Heading**: `\section*{References}` (unnumbered first-level heading)
- **Font size**: Can be reduced to `\small` (9-point) for references
- **Placement**: After acknowledgments (not in submission), before checklist
- **Page counting**: Does NOT count toward 9-page limit
- **Numbering**: Any consistent style acceptable
- **Bibliography management**: Use natbib with preferred .bib file or manual formatting

### natbib Options
```latex
% If you need special natbib options, place BEFORE loading neurips_2026
\PassOptionsToPackage{numbers, compress}{natbib}
\usepackage{neurips_2026}

% To disable natbib if it conflicts with another package
\usepackage[nonatbib]{neurips_2026}
```

---

## Figures & Tables

### Figures

#### Basic Syntax
```latex
\begin{figure}
  \centering
  \includegraphics[width=0.8\linewidth]{myfile.pdf}
  \caption{Sample figure caption. Explain what the figure shows and add key take-away message.}
  \label{fig:my_figure}
\end{figure}
```

#### Formatting Rules
- **Placement**: Caption appears **AFTER** the figure (not before)
- **Centering**: All figures must be centered on the page
- **Caption format**: Lower case (except first word and proper nouns)
- **Caption message**: Explain what the figure shows + key take-away
- **Spacing**: One blank line BEFORE figure, one blank line AFTER caption
- **Numbering**: Consecutive (Figure 1, Figure 2, etc.)
- **Legibility**: Lines must be dark enough for reproduction in both color and B&W
- **Image specification**: Use `\includegraphics[width=X\linewidth]{file}`
  - Always specify width as multiple of linewidth
  - Don't use `\special` commands for positioning (can cause margin issues)
  - Prefer PDF format for vector graphics
- **Color**: Color figures allowed, but ensure legible in B&W printing

#### Acceptable Sizes
- Full width: `width=1.0\linewidth` or `width=\linewidth`
- Three-quarter width: `width=0.75\linewidth`
- Half width: `width=0.5\linewidth`
- One-third width: `width=0.33\linewidth`

### Tables

#### Basic Syntax
```latex
\begin{table}
  \caption{Sample table caption. Explain what the table shows and add key take-away.}
  \label{tab:my_table}
  \centering
  \begin{tabular}{lll}
    \toprule
    Column 1 & Column 2 & Column 3 \\
    \midrule
    Data 1 & Data 2 & Data 3 \\
    \bottomrule
  \end{tabular}
\end{table}
```

#### Formatting Rules
- **Placement**: Caption appears **BEFORE** the table (not after)
- **Centering**: All tables must be centered on the page
- **Caption format**: Lower case (except first word and proper nouns)
- **Spacing**: One blank line BEFORE caption, one line after caption, one line after table
- **Numbering**: Consecutive (Table 1, Table 2, etc.)
- **Professional appearance**: NEVER use vertical rules in tables
- **Recommended package**: `booktabs` for high-quality tables
  - `\toprule`: Top horizontal line
  - `\midrule`: Horizontal line in middle
  - `\bottomrule`: Bottom horizontal line
  - `\cmidrule(r){columns}`: Partial horizontal line with right trim

#### booktabs Package Usage
```latex
\usepackage{booktabs}

\begin{tabular}{lll}
  \toprule
  \multicolumn{2}{c}{Part} \\
  \cmidrule(r){1-2}
  Name & Description & Size \\
  \midrule
  Dendrite & Input terminal & 100 $\mu$m \\
  Axon & Output terminal & 10 $\mu$m \\
  \bottomrule
\end{tabular}
```

---

## Mathematics

### Display Math
- **Requirement**: Use LaTeX/AMSTeX commands, NOT bare TeX commands (e.g., `$$`)
- **Recommended**: Use `align*` environment instead of `$$..$$` or `\[...\]`
- **Reason**: Bare TeX display math doesn't create correct line numbers for submission

#### Proper Examples
```latex
% ✓ Correct
\begin{equation}
  E = mc^2
\end{equation}

\begin{align*}
  a &= b \\
  c &= d
\end{align*}

% ✗ Incorrect (don't use for submissions)
$$E = mc^2$$
\[E = mc^2\]
```

### Math Fonts
- **AMS fonts**: Use `\usepackage{amsfonts}` for blackboard bold symbols
  - `\mathbb{R}`, `\mathbb{N}`, `\mathbb{C}` for real, natural, complex numbers
  - AVOID `\bbold` package (uses bitmap fonts, not acceptable for PDF)
- **Fractions**: Use `\nicefrac{}{}` for inline fractions like 1/2

### Unnumbered Equations
- All unnumbered display math should use LaTeX environments with star variants
- Example: `align*` instead of `align`

---

## Mandatory Checklist

### Critical Information
- **Requirement**: MANDATORY - papers without checklist will be desk rejected
- **Placement**: After references, before technical appendices
- **Visibility**: Visible to reviewers, area chairs, senior area chairs, and ethics reviewers
- **Publication**: Checklist answers are an integral part of submission and will be published with the final paper
- **Page counting**: Does NOT count toward 9-page limit
- **Evaluation**: Reviewers will use checklist as one factor in evaluation (honest "No" answers with justification are acceptable)

### Instructions for Authors
1. Delete the instruction block at the beginning of `checklist.tex`
2. Keep the section heading "NeurIPS Paper Checklist"
3. Keep all checklist subsection headings and questions
4. Do NOT modify the questions themselves
5. Use ONLY the provided answer macros

### Answer Macros
```latex
\answerYes{}    % For affirmative answers
\answerNo{}     % For negative answers
\answerNA{}     % For not applicable answers
\justificationTODO{}  % Template for justification (replace with actual text)
```

### Checklist Questions Coverage

| Item | Focus Area |
|------|-----------|
| Claims | Do abstract/intro accurately reflect contributions? |
| Limitations | Does paper discuss work limitations? |
| Theory assumptions | Complete assumptions and proofs for theoretical results? |
| Experimental reproducibility | Full disclosure of info needed to reproduce experiments? |
| Code & data access | Are code and data publicly available with instructions? |
| Experimental details | All training/test details specified (splits, hyperparameters, optimizer)? |
| Statistical significance | Error bars or statistical significance tests reported? |
| Compute resources | Type/amount of compute needed for each experiment disclosed? |
| Code of ethics | Does research conform to NeurIPS Code of Ethics? |
| Broader impacts | Positive AND negative societal impacts discussed? |
| Safeguards | Are safeguards in place for high-risk models/datasets? |
| Asset licenses | Existing asset creators credited with licenses stated? |
| New assets | New datasets/code well documented with documentation provided? |
| Human subjects | Crowdsourcing experiments have full instructions and compensation details? |
| IRB approval | IRB approval obtained and disclosed (if applicable)? |
| LLM usage | Core methodology using LLMs as important component disclosed? |

**Total**: 16 mandatory checklist items

### Answer Guidelines
- **Yes is preferable but not required**: Answering "No" with proper justification is acceptable
- **Justification required**: Always provide 1-2 sentence justification, even for NA
- **Reference sections**: For "Yes" answers, point to paper section(s) where evidence appears
- **External evidence**: Supporting evidence can appear in main paper or supplemental material
- **Reviewers' perspective**: Checklist is one evaluation factor; honest "No" answers with justification are not grounds for rejection

---

## PDF Requirements

### PDF Generation
- **Method**: Use `pdflatex` to directly generate PDF (NOT dvi → ps → pdf)
- **Font embedding**: ALL fonts must be Type 1 or Embedded TrueType
  - Type 3 fonts NOT acceptable
  - Non-embedded TrueType fonts NOT acceptable
- **Paper size**: US Letter (8.5" × 11"), NOT A4

### Verifying Font Embedding

#### In Adobe Acrobat Reader
1. Select File → Document Properties → Fonts
2. Choose "Show All Fonts"
3. Verify all fonts are Type 1 or Embedded TrueType

#### Using Command Line
```bash
pdffonts your_paper.pdf
```
(Available on Linux; uses xpdf utilities)

### Common Font Issues & Solutions

| Problem | Solution |
|---------|----------|
| xfig "patterned" shapes use bitmap fonts | Use "solid" shapes instead |
| `\bbold` package uses bitmap fonts | Use `\usepackage{amsfonts}` with `\mathbb{}` |
| Math fonts not embedded | Ensure Type 1 fonts in preamble |

### Required Packages (All Included)
```latex
\usepackage[utf8]{inputenc}      % UTF-8 input
\usepackage[T1]{fontenc}         % 8-bit T1 fonts
\usepackage{hyperref}            % Hyperlinks
\usepackage{url}                 % URL typesetting
\usepackage{booktabs}            % Professional tables
\usepackage{amsfonts}            % Math symbols (not bbold!)
\usepackage{nicefrac}            % Compact fractions (1/2)
\usepackage{microtype}           % Microtypography
\usepackage{xcolor}              % Colors
```

### What NOT to Do
- ✗ Don't use `\special` commands for figure positioning
- ✗ Don't use bitmap fonts (like from `\bbold`)
- ✗ Don't modify width/length of text rectangle
- ✗ Don't change font sizes in style files
- ✗ Don't use A4 paper size
- ✗ Don't generate DVI → PS → PDF

---

## Appendix & Supplementary Materials

### Important Details
- **Page limit**: NO page limit for technical appendices and supplementary material
- **Content**: Additional results, figures, graphs, proofs, code, videos
- **File formats**: 
  - Upload as ZIP file for videos or code
  - **Do NOT** upload separate PDF file for appendix
  - Supplementary PDF can be appended to main paper if preferred
- **Inclusion in final submission**: Include before the full submission deadline
- **Nature of appendix**: Think of it as "optional reading" for reviewers
- **Critical note**: Paper must stand alone without appendix
  - Do NOT move critical experiments or results to appendix
  - Appendix should contain supporting/supplementary content only
  - Essential claims must be in main 9-page paper

### LaTeX Structure
```latex
\appendix

\section{Technical appendices and supplementary material}
Additional proofs, extended experiments, etc. go here.

% Or use \input to include separate file
\input{appendix.tex}
```

### Placement in Document
1. Main paper (9 pages max)
2. Acknowledgments (camera-ready only)
3. References
4. Mandatory Checklist
5. Appendix & Supplementary Materials (unlimited pages)

---

## Common Patterns from Accepted Papers

### Paper 1: Variational Regularized Unbalanced Optimal Transport (2025 NeurIPS)

**Structure**:
- Title with 2 horizontal rules
- Multiple authors with affiliations (numbered)
- Abstract (single paragraph)
- Introduction
- Related Works (Section 2)
- Preliminaries and Backgrounds (Section 3)
- Technical methods sections
- Figures with captions BELOW
- Mathematical equations properly formatted
- Detailed citations throughout

**Observations**:
- Clean use of `\textbf{}` for bold text in captions
- Comprehensive related works separating different research directions
- Formal preliminaries section before main contributions
- Large overview figure (Figure 1) summarizing approach
- Heavy mathematical notation, properly formatted

**Key Tips**:
- Use clear section headers to guide reader
- Put extensive background in preliminaries section
- Include overview figure early if your work is complex
- Use subsection headers to break up long sections

### Paper 2: Sinkhorn Distances (2013 NIPS)

**Structure**:
- Title with 2 horizontal rules
- Single author, clean affiliation
- Abstract
- Introduction with clear motivation
- Section 2: Reminders on Optimal Transport (background)
- Section 3: Technical contribution (Sinkhorn Distances)
- Formal definitions and theorems
- Proofs and properties clearly stated

**Observations**:
- Theorems and lemmas properly numbered and referenced
- Mathematical objects clearly defined before use
- Background section establishes notation
- Clear distinction between existing theory and contributions
- Formal mathematical presentation throughout

**Key Tips**:
- Define notation carefully early
- Use formal theorem/lemma environments with numbering
- Reference theorems/definitions by number
- Include proof sketches in main text when illuminating

### Paper 3: Optimal Flow Matching (2024 NeurIPS)

**Structure**:
- Title with 2 horizontal rules
- Multiple authors with date stamp (Nov 2024 - arxiv version)
- Abstract
- Introduction with contributions bullet points
- Section 2: Background and Related Works
- Section 2.1: Static Optimal Transport
- Section 2.2: Dynamic Optimal Transport
- Technical sections with figures
- Mathematical formulations and equations

**Observations**:
- Clear enumerated contributions in introduction
- Background section reviews necessary theory
- Subsections within main technical sections for organization
- Equations numbered for reference
- Code repository mentioned in abstract

**Key Tips**:
- Enumerate main contributions explicitly in introduction
- Organize technical content with subsections
- Reference equations by number
- Make code availability clear

### Paper 4: Low-Rank Optimal Transport (2024 NeurIPS)

**Structure**:
- Title with 2 horizontal rules
- Multiple authors with affiliations and superscript numbers
- Abstract
- Introduction with clear problem statement
- Related background sections with citations
- Section 2: Background (theory foundations)
- Section 3: Main algorithm/method
- Subsections for algorithm components
- Related constraints and formulations explained

**Observations**:
- Author affiliations use numbered superscripts for clarity
- Problem motivation clear in introduction
- Background section comprehensive but distinct from contributions
- Algorithm presented with clear sections
- Emphasis on problem setup before solution

**Key Tips**:
- Use superscript numbers for author affiliations when multiple
- Clearly state problem before jumping to solution
- Organize background logically with subsections
- Separate known results from novel contributions

---

## Style Consistency Checklist

### Formatting Consistency
- [ ] All headings follow case rules (lower case except first word + proper nouns)
- [ ] All figure captions lower case (except first word + proper nouns)
- [ ] All table captions lower case (except first word + proper nouns)
- [ ] Consistent citation style throughout (author-year OR numeric)
- [ ] All equations referenced with numbers when referenced in text
- [ ] Consistent use of bold, italics, and special formatting
- [ ] Spacing around section headings consistent
- [ ] Footnote numbering continuous throughout paper

### Content Structure
- [ ] Introduction clearly states contributions
- [ ] Related work properly organized into subsections
- [ ] All notation defined before use
- [ ] Theorems/lemmas properly stated with assumptions
- [ ] Experimental section includes all details for reproducibility
- [ ] Figures contribute to main message (not just filler)
- [ ] Tables properly formatted with horizontal lines only
- [ ] Paper can stand alone without appendix

### Technical Presentation
- [ ] Display math uses LaTeX environments (not $$)
- [ ] Math fonts properly imported (amsfonts, not bbold)
- [ ] Fractions use \nicefrac when inline
- [ ] All abbreviations defined on first use
- [ ] References to equations/figures/sections use \ref or explicit numbers
- [ ] Code snippets (if any) properly formatted and explained

### Compliance
- [ ] Double-blind anonymity maintained in submission version
- [ ] All identifying information removed (no author names in text)
- [ ] All pages are numbered
- [ ] Checklist included and properly filled
- [ ] No page limit exceeded (9 pages max for content)
- [ ] PDF uses only Type 1 or Embedded TrueType fonts
- [ ] US Letter paper size
- [ ] No modifications to neurips_2026.sty style file
- [ ] Funding and competing interests disclosed (camera-ready version only)

---

## Common Mistakes to Avoid

### LaTeX/Formatting
- ❌ Using `$$..$$` for display math (use LaTeX environments instead)
- ❌ Using `\bbold` for math symbols (use `amsfonts` with `\mathbb`)
- ❌ Modifying page margins or font sizes
- ❌ Using `\special` commands for figure positioning
- ❌ Creating vertical lines in tables
- ❌ Using A4 paper size instead of US Letter
- ❌ Not embedding fonts in PDF
- ❌ Forgetting to number pages

### Content Structure
- ❌ Anonymous submission includes author names or identifying info
- ❌ Missing mandatory checklist
- ❌ Abstract exceeds one paragraph
- ❌ Figure captions appear before figures
- ❌ Table captions appear after tables
- ❌ Exceeding 9-page limit (excluding references, appendix, checklist)
- ❌ Using first person ("we") in anonymous submission for self-citations

### Presentation
- ❌ Inconsistent citation style (mixing author-year and numeric)
- ❌ Headings with ALL CAPS or inconsistent capitalization
- ❌ Math notation defined after use
- ❌ Unmarked or unnumbered equations that are referenced
- ❌ Footnotes without horizontal separator line
- ❌ Figures not centered or with unclear captions
- ❌ Missing hyperlinks in PDF (using `\href` where appropriate)

### Reproducibility
- ❌ Insufficient experimental details for reproduction
- ❌ Missing hyperparameter specifications
- ❌ Unclear dataset descriptions or sources
- ❌ No code availability mentioned
- ❌ Missing error bars or statistical significance measures
- ❌ Unclear hardware/compute specifications

### Submission/Publication Compliance
- ❌ Missing mandatory checklist (automatic desk rejection)
- ❌ Incomplete checklist answers without justifications
- ❌ Missing funding and competing interests declaration (camera-ready)
- ❌ Including acknowledgments in anonymous submission
- ❌ Critical experiments relegated to appendix instead of main paper
- ❌ Uploading appendix as separate PDF instead of ZIP or inline

---

## Key Commands Reference

### Document Setup
```latex
\documentclass{article}
\usepackage{neurips_2026}
\usepackage[utf8]{inputenc}
\usepackage[T1]{fontenc}
\usepackage{hyperref}
\usepackage{url}
\usepackage{booktabs}
\usepackage{amsfonts}
\usepackage{nicefrac}
\usepackage{microtype}
\usepackage{xcolor}
```

### Text Formatting
```latex
\textbf{bold text}
\textit{italic text}
\texttt{typewriter/code}
\emph{emphasized text}
\textcolor{red}{colored text}
```

### Structural Elements
```latex
\section{Main heading}
\subsection{Subheading}
\subsubsection{Sub-subheading}
\paragraph{Inline heading}
\label{key}           % for cross-references
\ref{key}             % to reference labels
\cite{key}            % for citations
\footnote{text}       % for footnotes
```

### Math Elements
```latex
\mathbb{R}            % Blackboard bold (real numbers)
\nicefrac{1}{2}       % Inline fraction
\mathbf{vector}       % Bold math
\mathcal{class}       % Calligraphic
\approx, \leq, \geq   % Math symbols
```

### Figures and Tables
```latex
\begin{figure}
  \centering
  \includegraphics[width=\linewidth]{file}
  \caption{Caption text}
  \label{fig:key}
\end{figure}

\begin{table}
  \caption{Caption text}
  \label{tab:key}
  \centering
  \begin{tabular}{l|c|r}
    \toprule
    Left & Center & Right \\
    \midrule
    ... \\
    \bottomrule
  \end{tabular}
\end{table}
```

### Checklist Items
```latex
\answerYes{}
\answerNo{}
\answerNA{}
\justificationTODO{}  % Replace with actual justification
```

### Special Environments
```latex
\begin{abstract} ... \end{abstract}
\begin{itemize} \item ... \end{itemize}
\begin{enumerate} \item ... \end{enumerate}
\begin{verbatim} ... \end{verbatim}
\begin{ack} ... \end{ack}  % Acknowledgments (camera-ready only)
\begin{align*} ... \end{align*}  % Display math
```

---

## Resources

- **Official NeurIPS**: https://neurips.cc
- **Code Submission Policy**: https://neurips.cc/public/guides/CodeSubmissionPolicy
- **Funding Disclosure**: https://neurips.cc/Conferences/2026/PaperInformation/FundingDisclosure
- **Code of Ethics**: https://neurips.cc/public/EthicsGuidelines
- **natbib Documentation**: http://mirrors.ctan.org/macros/latex/contrib/natbib/natnotes.pdf
- **booktabs Documentation**: https://www.ctan.org/pkg/booktabs
- **Graphics Bundle**: http://mirrors.ctan.org/macros/latex/required/graphics/grfguide.pdf

---

## Version History

- **Created**: April 2026
- **Based on**: NeurIPS 2026 template, NeurIPS 2013-2025 accepted papers
- **Papers Analyzed**:
  - "Variational Regularized Unbalanced Optimal Transport" (2025 NeurIPS)
  - "Sinkhorn Distances: Lightspeed Computation of Optimal Transport" (2013 NIPS)
  - "Optimal Flow Matching: Learning Straight Trajectories in Just One Step" (2024 NeurIPS)
  - "Low-Rank Optimal Transport through Factor Relaxation with Latent Coupling" (2024 NeurIPS)
