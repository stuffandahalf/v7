CFLAGS=-O $(XCFLAGS)
LDFLAGS=$(XLDFLAGS)

all: yacc yaccpar

cmp: all
	cmp yacc $(SYSROOT)/bin/yacc
	rm yacc *.o

cp:	all
	cp yacc $(SYSROOT)/bin/yacc
	cp yaccpar $(SYSROOT)/usr/lib/yaccpar
	$(MAKE) clean

yacc: y1.o y2.o y3.o y4.o
	$(CC) $(LDFLAGS) -s -o yacc y?.o

y1.o y2.o y3.o y4.o: dextern files

clean:
	rm -f *.o yacc
