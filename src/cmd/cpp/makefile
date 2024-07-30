CFLAGS=-O -s $(XCFLAGS)
LDFLAGS=-O -s $(XLDFLAGS)

all:	cpp

cp:	cpp
	mkdir -p $(SYSROOT)/lib
	cp cpp $(SYSROOT)/lib
	$(MAKE) clean

cmp:	cpp
	cmp cpp /lib/cpp
	$(MAKE) clean
cpp: cpp.o cpy.o
	$(CC) $(LDFLAGS) cpp.o cpy.o -o cpp
cpp.o: cpp.c
	$(CC) $(CFLAGS) -c -Dunix=1 -Dpdp11=1 cpp.c
cpy.c: cpy.y
	YACC_PARSER=$(SYSROOT)/usr/lib/yaccpar $(YACC) cpy.y
	mv y.tab.c cpy.c
cpy.o: cpy.c yylex.c

clean:
	rm -f *.o cpy.c cpp
