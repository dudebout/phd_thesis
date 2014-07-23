TEXMFHOME = texmf

CONTENT := $(wildcard *.tex) $(wildcard content/*.tex)
PACKAGES := $(wildcard *.sty)
FIGURES := $(wildcard figures/*.tikz)

COVER = ../cover/cover.pdf

latex = pdflatex -halt-on-error

.PHONY: all
all: thesis.pdf online.pdf printed.pdf

thesis.pdf: $(CONTENT) $(FIGURES) $(PACKAGES)
	$(latex) thesis
	bibtex thesis
	$(latex) thesis
	$(latex) thesis
	makeglossaries thesis
	$(latex) thesis
	$(latex) thesis
	$(latex) thesis

$(COVER):
	$(MAKE) -C ../cover cover.pdf

blank.pdf: thesis.pdf
	gs -q -dNOPAUSE -dBATCH -dFirstPage=2 -dLastPage=2 -sDEVICE=pdfwrite -sOutputFile=blank.pdf thesis.pdf

online.pdf: thesis.pdf blank.pdf $(COVER)
	gs -q -dNOPAUSE -dBATCH -dAutoRotatePages=/None -sDEVICE=pdfwrite -sOutputFile=$@ $(COVER) blank.pdf thesis.pdf

printed.pdf: thesis.pdf printed.tex
	$(latex) printed

.PHONY: clean
clean:
	rm -f *.pdf *.aux *.log *.nav *.out *.snm *.toc *.acn *.acr *.alg *.bbl *.blg *.ist
