SOURCE=runtime.tex
prefix=../
PDFS=presentation.pdf handout.pdf
notes=

all: clean $(SOURCE) $(PDFS)

%.pdf: $(SOURCE)
	@echo "Making: $@"
ifdef notes
	@sed 's@%%%withnotes%%%@@' $< >$(@:.pdf=.tex)
else
	@cp $< $(@:.pdf=.tex)
endif
	@sed "s@%%%$(@:.pdf=)%%%@@" $(@:.pdf=.tex) | pdflatex -halt-on-error -shell-escape --jobname $(@:.pdf=) -- >/dev/null
	@sed "s@%%%$(@:.pdf=)%%%@@" $(@:.pdf=.tex) | pdflatex -halt-on-error -shell-escape --jobname $(@:.pdf=) -- >/dev/null

.PHONY : clean
clean:
	rm -f *.vrb *.out *.aux *.nav *.snm *.toc *.log *.pyg *.tmp $(PDFS:.pdf=.tex)
