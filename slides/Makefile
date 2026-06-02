SLIDES = slides

all: $(SLIDES).pdf

$(SLIDES).pdf: $(SLIDES).tex
	latexmk -xelatex -interaction=nonstopmode -halt-on-error $(SLIDES).tex

clean:
	latexmk -C
	rm -f *.vrb *.nav *.snm

.PHONY: all clean
