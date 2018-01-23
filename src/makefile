# Lispy -- lisp style interpreter
#
GIT_VERSION := $(shell git describe --tags --abbrev=4)

IDIR=../include
CC=cc
CPPFLAGS = -DLISPY_VERSION=\"$(GIT_VERSION)\" -I$(IDIR)
CFLAGS = -std=c99 -ggdb -Wall -Wextra
LIBS=-lm -ledit 

ODIR=obj

_DEPS = mpc.h
DEPS = $(patsubst %,$(IDIR)/%,$(_DEPS))

_OBJ = lispy.o mpc.o 
OBJ = $(patsubst %,$(ODIR)/%,$(_OBJ))


$(ODIR)/%.o: %.c $(DEPS)
	$(CC) -c -o $@ $< $(CFLAGS) $(CPPFLAGS)

lispy: $(OBJ)
	$(CC) -o $@ $^ $(CFLAGS) $(CPPFLAGS) $(LIBS)

.PHONY: install clean

install:
	install lispy /usr/local/bin
	install prelude.lspy /usr/local/include/stdlib.lspy

clean:
	rm -f $(ODIR)/*.o *~ core $(IDIR)/*~ 
