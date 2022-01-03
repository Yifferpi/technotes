+++
title = "Latex"
tags = ["writing"]
+++

# Personal Latex cheat sheet

Mostly a summary of "Not so short Intro to LaTex"

## Commands and Rules
- empty line between two lines defines a new paragraph
- single new line is treated as a regular single whitespace
- multiple whitespaces are treated as a regular single whitespace
- whitespaces after commands are ignored
- to get whitespace after command add empty params `{}` and a whitespace
- commands take required params in `{}` and optional params in `[]`

### Comments
- comments are done with `%`
- `%` can also be used to split lines where no space is allowed
- for longer comment, use comment environment from `verbatim` package:
```
\begin{comment} 
... 
\end{comment}
```
### Layout
**Structure**

- every input file must start with `\documentclass{...}`
- after that, commands that influence style of entire doc or load packages
- when setup work is done: `\begin{document} ... \end{document`
- anything after end will be **ignored**
- `\pagestyle{[plain|headings|empty]}` for choice of header
- `\include{file}` to split input file. content will be on new page
- only check syntax: `\usepackage{syntonly} \syntaxonly`

**Packages:**

- primary source for info: Frank Mittelbach:The Latex Companion
- `texdoc <packagename>` command for looking at package documentation

| **Type** | **Description**   |
| -------- | ----------------- |
| `.tex`   | Tex Input File    |
| `.sty`   | Tex Macro Package: load this with `\usepackage` |
| `.dtx`   | documented TeX: main distribution format for latex style files |
| `.ins`   | installer for files contained in matching .dtx. run latex on the .ins to unpack the .dtx |
| `.cls`   | class file: defines what the document looks like. selected with `\documentclass` |
| `.fd`    | font description: telling latex about new fonts |

### Typesetting
- `\\` or `\newline` starts new line without starting new paragraph
- `\\*` additionally prohibits pagebreak
- `\newpage` starts a new pageA
- `\linebreak[n],\nolinebreak[n],\pagebreak[n],\nopagebreak[n]` suggests places
- `n` at a value below 4 leaves Latex the option to ignore the command
- `\newline, \newpage` makes a new page to really start a new line/page
- `\sloppy` lowers Latex linebreak requirements, `\fussy` raises it again
- `\hyphenation{FORTRAN Hy-phen-a-tion}` to make exceptions to hyphenation algo
- above: FORTRAN will not be hyphened, Hyphenation can be at all dashes
- `\mbox{text}` keeps words together on one line, `\fbox{text}` draws additional visible box
- ready made strings: `\today, \latex, \tex`
- dont use normal quotation marks: use backticks (one or two) to start and straight ticks to end
- dashes can be done with different length: 1 to 3
- start and end embedded math with `$`
- different language: start environment `\begin{german} ... \end{german}`, also `\textgerman{germanword}`
- package `polyglossia` for fonts and languages
- setting fonts: `\setmainfont{...}, \setsansfont{...}, \setmonofont{...}`
- latex inserts more whitespace after end of sentence. can be disabled with `\frenchspacing`
- backslash before space ensures space will not be enlarged, ~ does same and prohibits linebreak

- sectioning depends on document class, `\chapter` not always available
- normally `\section{}, \subsection{}, \paragraph{}, \subparagraph{}`
- `\part` does not affect numbering, `\appendix` takes no argument, `\tableofcontents` generates toc
- `*` after sectioncommand: heading does not show up in toc and has no numbering
- short title for toc: `\section[short name]{long name}`
- `\title, \author, \date` define and `\maketitle` generates the title(page)
- bookclass: `\frontmatter` makes roman page numbering, followed by `\mainmatter, \appendix, \backmatter`
- cross references: `\label{l}` for def (put label after!), `\ref{l}, \pageref{l}` for ref
- `\footnote{text}` to be put after word or sentence, makes footnote on current page
- emphasizing: `\underline{text}` or even better: `\emph{text}`, different per context

**Environments**

- `\begin{environment name} ... \end{environment name}`
- `itemize` for simple lists, ` ennumerate` for numbered, `description` for descriptions
- `\item` generates an item, sometimes optional params like `-` can be given
- other environments: `flushleft`, `flushright` and `center`
- `quote` for quotes, `quotation` for longer quotes (multiple paragraphs) and `verse` for poems
- there is also an `abstract` environment for scientific articles
- `verbatim` environment: directly printed with all linebreaks, no latex processing
- `verbatim` can be embedded with `\verb+text+` command where `+` can be any delimiter
- `tabular` environment for tables (see 2.11 in the book)
- graphics with `\usepackage{graphicx}`, then `\includegraphics[key=value..]{file}`
- `figure` and `table` are floating body environments: support optional placement specifier param
- float placing permissions: some of the letters `h, p, t, b, !`
- `\caption[short]{long captiontext}` defines a caption for the float
- reference using `\label` which must come AFTER the `\caption` command
- `\listoffigures` and `\listoftables` generate, analogous to ToC

## Resources

- [What is TeX?](https://www.texfaq.org/FAQ-texthings)
- [TeX packages](https://www.volkerschatz.com/tex/tpacks.html#kpathsea)
- [A not so short introduction to latex](https://mirror.foobar.to/CTAN/info/lshort/english/lshort.pdf)
- [MathSymbols](https://www.caam.rice.edu/~heinken/latex/symbols.pdf)

