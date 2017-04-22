# Lispy -- lisp style interpreter

VERSION = 0.15

IDIR=../include
CC=cc
CPPFLAGS = -DLISPY_VERSION=\"$(VERSION)\" -I$(IDIR)
CFLAGS = -std=c99 -Wall -Wextra -Og
LIBS=-lm -ledit 

ODIR=obj

_DEPS = mpc.h
DEPS = $(patsubst %,$(IDIR)/%,$(_DEPS))

_OBJ = lispy.o mpc.o 
OBJ = $(patsubst %,$(ODIR)/%,$(_OBJ))


$(ODIR)/%.o: %.c $(DEPS)
	$(CC) -c -o $@ $< $(CFLAGS) $(CPPFLAGS)

lispy: $(OBJ)
	$(CC) -o $@ $^ $(CFLAGS) $(LIBS)

.PHONY: clean

clean:
	rm -f $(ODIR)/*.o *~ core $(IDIR)/*~ 
