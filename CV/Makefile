MAIN=cv_jungi

all: $(MAIN).pdf

$(MAIN).pdf: rev.tex
	pdflatex $(MAIN).tex
	bibtex conf.aux
	bibtex journal.aux
	#bibtex ur.aux
	#bibtex patent.aux
	pdflatex $(MAIN).tex
	pdflatex $(MAIN).tex

rev.tex: FORCE
	@printf '\\gdef\\therev{%s}\n\\gdef\\thedate{%s}\n' \
	   "$(shell git rev-parse --short HEAD)"            \
	   "$(shell git log -1 --format='%ci' HEAD)" > $@

clean:
	rm -f *.out *.log *.aux *.pdf *.bbl *.blg

.PHONY: clean FORCE

