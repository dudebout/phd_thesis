TEXMFHOME := texmf
export TEXMFHOME

PACKAGES := $(wildcard *.sty)
FIGURES := $(wildcard figures/*.tikz)
SOURCES := presentation.tex content.tex $(FIGURES) $(PACKAGES)

latex := pdflatex -halt-on-error

.PHONY: all
all: presentation.pdf handout.pdf

%.pdf: %.tex $(SOURCES)
	$(latex) $<

.PHONY: clean
clean:
	rm -f *.pdf *.aux *.log *.nav *.out *.snm *.toc
