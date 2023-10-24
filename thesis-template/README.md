# About

LaTeX template for VUSec bachelor’s and master’s thesis reports.


## Editing

The main LaTeX file is `thesis.tex` and the contents of the thesis are neatly
arranged in separate LaTeX files under `sections/`. Start by providing
appropriate values for the cover page of the thesis in `thesis.tex` and populate
the contents of the appropriate sections. Pay special attention to the `\th*`
macros in `thesis.tex`. Please define your custom aliases and acronyms in
`aliases.sty`. Lastly, remove unwanted sections and references. 


## Compiling

The `Makefile` uses `latexmk` to simplify the build process. Simple type `make` to build the PDF, or use `make watch` to automatically build the PDF whenever the content changes.
