LATEX             = pdflatex
BIBTEX            = bibtex

MAIN              = master
BIB               = bib/kilder.bib
TEXFILES          = $(wildcard *.tex) $(wildcard sections/*/*.tex)\
										$(wildcard setup/*.tex) $(wildcard sections/*/*/*.tex)\
										$(wildcard sections/*/*/*/*.tex)
IMAGES            = $(wildcard images/*)
EPSPDFFILES       = $(patsubst %.eps, %.pdf, $(wildcard images/*.eps))
FIGPDFFILES       = $(patsubst %.fig, %.pdf, $(wildcard images/*.fig))
DOTPDFFILES       = $(patsubst %.dot, %.pdf, $(wildcard images/*.dot))
BILAG             = $(wildcard bilag/*/*.tex)

all : pdf

pdf : $(MAIN).pdf 

force : 
	touch $(MAIN).tex
	make

$(MAIN).pdf : $(TEXFILES) $(IMAGES) $(FIGPDFFILES) $(DOTPDFFILES)\
 	$(EPSPDFFILES) $(BILAG) $(BIB)

	$(LATEX) ${MAIN}
	if egrep -c "No file.*\.bbl|Citation.*undefined" $(MAIN).log;then\
		echo "** Running BibTeX **";\
		$(BIBTEX) $(MAIN).aux;\
		else echo "** No need to run BibTeX **";\
		fi
	@while ( grep "Rerun to get cross-references" 	\
		${MAIN}.log > /dev/null ); do		\
		echo '** Re-running LaTeX **';		\
		$(LATEX) ${MAIN};				\
		done

clean :
	rm -f *.aux
	rm -f *.log
	rm -f *.bbl
	rm -f *.out
	rm -f *.bak
	rm -f *.blg
	rm -f *.toc
	rm -f *.lox
	rm -f images/*.bak

# EPS-FILES
%.pdf : %.eps
	epstopdf $*.eps

# XFIG
%.pdf : %.fig
	fig2dev -L pdf $*.fig > $*.pdf

# DOT
%.pdf : %.dot
	dot $< -Tpdf -o $@
