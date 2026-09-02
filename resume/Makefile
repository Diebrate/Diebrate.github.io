# Resume / CV build
#
#   make            -> build the main resume (resume_special.tex)
#   make all        -> build every resume_*.tex variant
#   make publish    -> build the main resume and copy it to the website's PDF path
#   make watch      -> rebuild continuously while editing
#   make clean      -> remove build artifacts
#
# Requires a TeX distribution (MacTeX / TeX Live) providing latexmk + pdflatex.

MAIN      := resume_special
BUILD     := build
SITE_PDF  := ../assets/pdf/resume_KZhang.pdf

SOURCES   := $(wildcard *.tex) $(wildcard sections*/*.tex) $(wildcard global/*.tex)
VARIANTS  := $(basename $(wildcard resume*.tex))

LATEXMK   := latexmk -pdf -interaction=nonstopmode -halt-on-error -outdir=$(BUILD)

.PHONY: default all publish watch clean $(VARIANTS)

default: $(BUILD)/$(MAIN).pdf

$(BUILD)/%.pdf: %.tex $(SOURCES)
	$(LATEXMK) $<

all: $(addprefix $(BUILD)/,$(addsuffix .pdf,$(VARIANTS)))

# `make resume_quant`, `make resume_ds`, ...
$(VARIANTS): %: $(BUILD)/%.pdf

publish: $(BUILD)/$(MAIN).pdf
	@mkdir -p $(dir $(SITE_PDF))
	cp $(BUILD)/$(MAIN).pdf $(SITE_PDF)
	@echo "Published $(BUILD)/$(MAIN).pdf -> $(SITE_PDF)"

watch:
	$(LATEXMK) -pvc $(MAIN).tex

clean:
	latexmk -C -outdir=$(BUILD) $(wildcard resume*.tex)
	rm -rf $(BUILD)
