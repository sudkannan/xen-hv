TOPLEVEL=../..
XEN_ROOT=$(TOPLEVEL)/../..
include $(TOPLEVEL)/common.make

OBJS = eventchn
INTF = $(foreach obj, $(OBJS),$(obj).cmi)
LIBS = eventchn.cma eventchn.cmxa

all: $(INTF) $(LIBS) $(PROGRAMS)

bins: $(PROGRAMS)

libs: $(LIBS)

eventchn_OBJS = $(OBJS)
eventchn_C_OBJS = eventchn_stubs

OCAML_LIBRARY = eventchn

.PHONY: install
install: $(LIBS) META
	mkdir -p $(OCAMLDESTDIR)
	ocamlfind remove -destdir $(OCAMLDESTDIR) eventchn
	ocamlfind install -destdir $(OCAMLDESTDIR) -ldconf ignore eventchn META $(INTF) $(LIBS) *.a *.so *.cmx

.PHONY: uninstall
uninstall:
	ocamlfind remove -destdir $(OCAMLDESTDIR) eventchn

include $(TOPLEVEL)/Makefile.rules

