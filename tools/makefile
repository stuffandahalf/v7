XSYSROOT=$(PWD)/../sysroot
XCFLAGS="-m32 -std=c89"
XLDFLAGS="-m32"

XCC=$(XSYSROOT)/bin/ccom
XYACC=$(XSYSROOT)/bin/yacc

all: yacc-cp cc-cp

sysroot:
	mkdir -p $(XSYSROOT)
	mkdir -p $(XSYSROOT)/bin
	#mkdir -p $(XSYSROOT)/lib
	mkdir -p $(XSYSROOT)/usr/lib

cc: yacc-cp
	cd ../src/cmd/pcc && $(MAKE) ccom SYSROOT=$(XSYSROOT) YACC=$(XYACC) XCFLAGS=$(XCFLAGS) XLDFLAGS=$(XLDFLAGS)

cc-cp: cc
	cd ../src/cmd/pcc && $(MAKE) cp SYSROOT=$(XSYSROOT)

yacc:
	cd ../src/cmd/yacc && $(MAKE) yacc XCFLAGS=$(XCFLAGS) XLDFLAGS=$(XLDFLAGS)

yacc-cp: sysroot yacc
	cd ../src/cmd/yacc && $(MAKE) cp SYSROOT=$(XSYSROOT)

clean:
	rm -rf $(XSYSROOT)
	cd ../src/cmd/yacc && $(MAKE) clean

