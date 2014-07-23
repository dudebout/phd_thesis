all: full_cover_final.pdf cover.pdf

full_cover_final.png: full_cover.png
	convert -rotate 90 $< $@

%.pdf: %.png
	convert -format pdf $< $@

clean:
	rm *.pdf full_cover_final.png
