# hack: machine specific
SDRAW := "/cygdrive/c/Program Files (x86)/LibreOffice 4/program/sdraw.exe"

#ODG_FILES := $(wildcard */*.odg)
#EPS_FROM_ODG := $(subst odg,eps,$(ODG_FILES))
#PNG_FROM_ODG := $(subst odg,png,$(ODG_FILES))
#all :: $(PNG_FROM_ODG)

PNGFILES := $(shell find -name "*.png")
PNGDIRS := $(sort $(dir $(PNGFILES)))
PWD := $(shell pwd)
PNGOPTJ := -j 4

all ::

# twoMassSpringCouplingFig1.png was generated using the rule below, but
# I don't know how to crop the file without using external tools (and can't
# figure out how to do it with libreoffice draw)
# 
# by default the libreoffice draw inserted equations are tiny

%.eps : %.odg
	$(SDRAW) --headless --convert-to eps $^ 

%.png : %.odg
	$(SDRAW) --headless --convert-to png $^

pngoptimize : 
	$(foreach dir,$(PNGDIRS),make -C $(dir) -k $(PNGOPTJ) -f $(PWD)/make.pngopt;)
