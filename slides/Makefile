SLIDES = slides slides_precision

all: $(addsuffix .pdf,$(SLIDES))

%.pdf: %.tex
	latexmk -xelatex -interaction=nonstopmode -halt-on-error $<

clean:
	latexmk -C
	rm -f *.vrb *.nav *.snm

.PHONY: all clean
