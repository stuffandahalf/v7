XSYSROOT=$(PWD)/../sysroot
XCFLAGS=-m32\ -std=c89\ -D_FILENAME=__FILE_NAME__\ -D__MODERN_HOST__=1\ -D__XSYSROOT__="\\\"$(XSYSROOT)\\\""
XLDFLAGS=-m32

XCC=$(XSYSROOT)/bin/ccom
XYACC=$(XSYSROOT)/bin/yacc

all: headers yacc-cp cpp-cp cc-cp

sysroot:
	mkdir -p $(XSYSROOT)

cc: yacc-cp
	cd ../src/cmd/pcc && $(MAKE) ccom \
		SYSROOT=$(XSYSROOT) \
		YACC=$(XYACC) \
		XCFLAGS=$(XCFLAGS) \
		XLDFLAGS=$(XLDFLAGS)

cc-cp: sysroot cc
	cd ../src/cmd/pcc && $(MAKE) cp \
		SYSROOT=$(XSYSROOT)

cpp: yacc-cp
	cd ../src/cmd/cpp && $(MAKE) cpp \
		SYSROOT=$(XSYSROOT) \
		YACC=$(XYACC) \
		XCFLAGS=$(XCFLAGS) \
		XLDFLAGS=$(XLDFLAGS)

cpp-cp: sysroot cpp
	cd ../src/cmd/cpp && $(MAKE) cp \
		SYSROOT=$(XSYSROOT)

yacc:
	cd ../src/cmd/yacc && $(MAKE) yacc \
		XCFLAGS=$(XCFLAGS) \
		XLDFLAGS=$(XLDFLAGS)

yacc-cp: sysroot yacc
	cd ../src/cmd/yacc && $(MAKE) cp \
		SYSROOT=$(XSYSROOT)

headers: sysroot
	mkdir -p $(XSYSROOT)/usr/include
	cp -r ../include/* $(XSYSROOT)/usr/include/

clean:
	rm -rf $(XSYSROOT)
	cd ../src/cmd/yacc && $(MAKE) clean
	cd ../src/cmd/cpp && $(MAKE) clean
	cd ../src/cmd/pcc && $(MAKE) clean

