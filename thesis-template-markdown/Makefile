# constants for defining the author, title, etc.
FILENAME = thesis
TITLE = Diplomaterv sablon Markdown leírónyelven
AUTHOR = Szárnyas Gábor
ADVISOR = Konzulens Elemér
UNIVERSITY = Budapesti Műszaki és Gazdaságtudományi Egyetem
DEPARTMENT = Méréstechnika és Információs Rendszerek Tanszék
RESEARCH_GROUP = Hibatűrő Rendszerek Kutatócsoport
THESIS_TYPE = Diplomaterv
DOCUMENT_LANG = magyar
BEFORE_FILE = guideline.md
SOURCE_FILES = abstract.md chapter1.md chapter2.md chapter3.md chapter4.md summary.md acknowledgements.md bibliography.md
APPENDIX_FILE = appendix.md

# variables for the PDF/HTML compiler
ARGS = \
	$(SOURCE_FILES) \
	--from=markdown \
	--variable=lang:"$(DOCUMENT_LANG)" \
	--variable=title:"$(TITLE)" \
	--variable=author:"$(AUTHOR)" \
	--variable=advisor:"$(ADVISOR)" \
	--variable=university:"$(UNIVERSITY)" \
	--variable=department:"$(DEPARTMENT)" \
	--variable=research-group:"$(RESEARCH_GROUP)" \
	--variable=thesis-type:"$(THESIS_TYPE)" \
	--variable=lof \
	--variable=lot \
	--standalone \
	--table-of-contents \
	--bibliography=bibliography.bib \

LATEX_ARGS = \
	$(ARGS) \
	--include-before-body=$(BEFORE_FILE).tex \
	--include-after-body=$(APPENDIX_FILE).tex \
	--template=template.latex \
	--variable=documentclass:report \
	--variable=fontsize:11pt \
	--variable=papersize:a4paper \
	--variable=sides:oneside \
	--variable=numbersections \
	--natbib \
	--variable=biblio-files:"bibliography" \
	--variable=biblio-style:"plain" \

HTML_ARGS = \
	--mathjax \
	--filter pandoc-citeproc \
	--csl=ieee.csl \

# rules

## rules for compiling the document

pdf: latex build-latex


latex: compile-guideline-tex compile-appendix-tex
	pandoc \
		$(LATEX_ARGS) \
		--to=latex \
		--output=$(FILENAME).tex \

html: compile-guideline-html compile-appendix-html
	pandoc \
		$(FILES) \
		$(ARGS) \
		$(HTML_ARGS) \
		--include-before-body=$(BEFORE_FILE).html \
		--include-after-body=$(APPENDIX_FILE).html \
		--to=html \
		--output=$(FILENAME).html \
		--css=buttondown.css \

mobi: compile-guideline-mobi compile-appendix-mobi
	pandoc \
		$(FILES) \
		$(ARGS) \
		--include-before-body=$(BEFORE_FILE).mobi \
		--include-after-body=$(APPENDIX_FILE).mobi \
		--output=$(FILENAME).mobi \
		--css=buttondown.css \
		--mimetex \

build-latex:
	pdflatex $(FILENAME).tex
	bibtex $(FILENAME).aux
	pdflatex $(FILENAME).tex
	pdflatex $(FILENAME).tex

## rules for compiling the guideline

compile-guideline-tex:
	pandoc \
		$(BEFORE_FILE) \
		--from=markdown \
		--to=latex \
		--variable=documentclass:report \
		--output=$(BEFORE_FILE).tex \

compile-guideline-html:
	pandoc \
		$(BEFORE_FILE) \
		--from=markdown \
		--to=html \
		--output=$(BEFORE_FILE).html \

compile-guideline-mobi:
	pandoc \
		$(BEFORE_FILE) \
		--from=markdown \
		--output=$(BEFORE_FILE).mobi \


## rules for compiling the appendix

compile-appendix-tex:
	pandoc \
		$(APPENDIX_FILE) \
		--from=markdown \
		--to=latex \
		--variable=documentclass:report \
		--output=$(APPENDIX_FILE).tex \

compile-appendix-html:
	pandoc \
		$(APPENDIX_FILE) \
		$(HTML_ARGS) \
		--from=markdown \
		--to=html \
		--output=$(APPENDIX_FILE).html \

compile-appendix-mobi:
	pandoc \
		$(APPENDIX_FILE) \
		$(HTML_ARGS) \
		--from=markdown \
		--output=$(APPENDIX_FILE).mobi \

## misc rules

open:
	gnome-open \
		$(FILENAME).pdf \

clean:
	rm -f *.tex *.aux *.dvi *.log *.pdf *.html *.mobi *.out
