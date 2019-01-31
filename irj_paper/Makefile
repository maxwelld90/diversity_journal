EXEC = xelatex
BIB = bibtex

.PHONY : all view

all : jir2018aspects.pdf clean view

jir2018aspects.pdf : jir2018aspects.tex *.tex figures/*
	$(EXEC) jir2018aspects.tex
	$(BIB) jir2018aspects
	$(EXEC) jir2018aspects
	$(EXEC) jir2018aspects

view :
	open jir2018aspects.pdf

clean :
	rm -f jir2018aspects.aux
	rm -f jir2018aspects.log
	rm -f jir2018aspects.blg
