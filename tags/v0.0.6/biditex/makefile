TR=biditex
SRC=bidi.c biditex.c dict.c io.c util.c ignore.c
OBJ := $(patsubst %.c,%.o,$(SRC))
MAN=biditex.1
INSTPATH=/usr/local
TEXMF=/usr/share/texmf
BINPATH=$(INSTPATH)/bin/
MANPATH=$(INSTPATH)/share/man/man1/

LIBS = `fribidi-config --libs`
CC = gcc
CFLAGS = -O2 -Wall -g `fribidi-config --cflags`


all: $(TR)

$(TR) : $(OBJ)
	$(CC) -o $@ $^ $(LIBS)

.c.o:
	$(CC) -c $(CFLAGS) $<

clean:
	rm -f $(OBJ) $(TR) .depend

depend:
	$(CC) -M $(SRC) > .depend

install: $(TR)
	cp $(TR) $(BINPATH)
	cp ../docs/man/$(MAN) $(MANPATH)
	mkdir $(TEXMF)/tex/latex/biditex
	cp biditex.sty $(TEXMF)/tex/latex/biditex/
	mktexlsr

uninstall:
	rm -f "$(BINPATH)$(TR)"
	rm -f "$(MANPATH)$(MAN)"
	rm -fr $(TEXMF)/tex/latex/biditex
	mktexlsr


-include .depend
