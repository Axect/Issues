# Madgraph

## 1. Install Delphes

```sh
Mg5_aMC> install Delphes
```

### Error case `rpc/types.h` 

* Edit `/opt/madgraph/Delphes/Makefile`
    1. `CXXFLAGS += $(ROOTCFLAGS) -Wno-write-strings -D_FILE_OFFSET_BITS=64 -DDROP_CGAL -I. -Iexternal -Iexternal/tcl -I/usr/include/tirpc`
    2. `DELPHES_LIBS = $(shell $(RC) --libs) -lEG $(SYSLIBS) -ltirpc`

## 2. Install Pythia8

* Should check `rsync` is installed : `yay -S rsync`
