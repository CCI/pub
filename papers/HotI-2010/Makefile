################################################################################
# Clean Files
################################################################################
CLEANFILES = cci.aux cci.bbl cci.blg cci.brf cci.log\
             cci.out cci.toc cci.lof cci.lot cci.nlo\
             cci.ist cci.nls cci.ilg cci.ist cci.glg\
			 cci.gls cci.glo

################################################################################
# Phony Targets
################################################################################
.PHONY: all clean

################################################################################
# All Target
################################################################################
all: cci.pdf

################################################################################
# cci Target
################################################################################
cci.pdf: Makefile\
              IEEEtran.cls\
              cci.tex
	pdflatex  cci
	pdflatex  cci
	pdflatex  cci
	pdflatex  cci
	rm -f $(CLEANFILES)
	@echo The following PDF files are above v1.3 and may cause compatibility issues:
	find . | egrep -e ".pdf$$" >.files
	file -f .files | grep -v 1.2 | grep -v 1.3 | grep -v cci.pdf; rm -f .files

################################################################################
# Clean Target
################################################################################
clean:
	rm -f $(CLEANFILES)

################################################################################
# Cleanall Target 
################################################################################
cleanall: clean
	rm -f cci.pdf

################################################################################
# Backup Target 
################################################################################
backup: cleanall
	tar -C .. -cjf "../$(shell basename "$$PWD")\
	 $(shell date +%Y-%m-%d\ %H-%M-%S).tar.bz2" "$(shell basename "$$PWD")"

################################################################################
# Export Target 
################################################################################
export: cleanall
	tar -C .. --exclude .git      --exclude .DS_Store
	 -cjf "../$(shell basename "$$PWD")\
	 $(shell date +%Y-%m-%d\ %H-%M-%S).tar.bz2" "$(shell basename "$$PWD")"
