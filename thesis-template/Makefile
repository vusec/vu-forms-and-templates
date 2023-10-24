
MAIN:=thesis
SRCS:=$(wildcard */*.tex)
DEPS:=$(wildcard *.sty)

LMK:=latexmk
OTYPE:=-pdf
TEX:=-pdflatex
# TeX options for a regular compile, fix, and repeat process.
REG_OPTS:="pdflatex -shell-escape"
# TeX options for a continuous/incremental compilation, where regardless of
#  errors LaTeX will try to produce a PDF.
INC_OPTS:="pdflatex -interaction=nonstopmode -shell-escape"
BIB:=-bibtex

ERROR_MSG=Error: cannot find '$(LMK)' in path; try 'pdflatex $(MAIN).tex'

lmk_check =								\
	@which $(LMK) > /dev/null ||		\
		(echo "$(ERROR_MSG)" >& 2 &&	\
			exit 1)

default: $(MAIN).pdf

$(MAIN).pdf: $(MAIN).tex $(SRCS) $(DEPS)
	$(call lmk_check)
	@$(LMK) $(OTYPE) $(TEX)=$(REG_OPTS) $(BIB) $<


.PHONY: watch mostlyclean clean

# Automatically rebuild latex files whenever changes are made.
watch: $(MAIN).tex
	$(call lmk_check)
	@$(LMK) -pvc $(OTYPE) $(TEX)=$(INC_OPTS) $(BIB) $<

# Clean up all intermediate files.
mostlyclean:
	@$(LMK) -c
	@rm -rf auto/

clean: mostlyclean
	@rm -f *.dvi *.ps *~ $(MAIN).pdf paper-thesis-fmt.zip


# Bundle files into an archive.
paper-thesis-fmt.zip: $(MAIN).pdf
	@zip -r $@ . -x "*.git*" -x "*.DS_Store"
