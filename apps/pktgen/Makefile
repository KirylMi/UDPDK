#
# Created by leoll2 on 10/07/20.
# Copyright (c) 2020 Leonardo Lai. All rights reserved.
#

# all source are stored in SRCS-y
SRCS= main.c

CFLAGS = -O3 $(shell pkg-config --cflags libdpdk)
LDFLAGS_SHARED = $(shell pkg-config --libs libdpdk)
LDFLAGS_STATIC = $(shell pkg-config --static --libs libdpdk)
LDFLAGS = $(shell pkg-config --libs libdpdk)

LIBS+= -L${UDPDK_PATH}/udpdk -Wl,--whole-archive,-ludpdk,--no-whole-archive

CFLAGS += $(WERROR_FLAGS) -O3

TARGET="pktgen"
all:
	cc  ${CFLAGS} -I${ROOTDIR}/udpdk -o ${TARGET} ${SRCS} ${LIBS} ${LDFLAGS_SHARED}

.PHONY: clean
clean:
	rm -f *.o ${TARGET}

## binary name
#APP = l2fwd
#
## all source are stored in SRCS-y
#SRCS-y := main.c
#
#PKGCONF ?= pkg-config
#
## Build using pkg-config variables if possible
#ifneq ($(shell $(PKGCONF) --exists libdpdk && echo 0),0)
#$(error "no installation of DPDK found")
#endif
#
#all: shared
#.PHONY: shared static
#shared: build/$(APP)-shared
#        ln -sf $(APP)-shared build/$(APP)
#static: build/$(APP)-static
#        ln -sf $(APP)-static build/$(APP)
#
#PC_FILE := $(shell $(PKGCONF) --path libdpdk 2>/dev/null)
#CFLAGS += -O3 $(shell $(PKGCONF) --cflags libdpdk)
## Add flag to allow experimental API as l2fwd uses rte_ethdev_set_ptype API
#CFLAGS += -DALLOW_EXPERIMENTAL_API
#LDFLAGS_SHARED = $(shell $(PKGCONF) --libs libdpdk)
#LDFLAGS_STATIC = $(shell $(PKGCONF) --static --libs libdpdk)
#
#ifeq ($(MAKECMDGOALS),static)
## check for broken pkg-config
#ifeq ($(shell echo $(LDFLAGS_STATIC) | grep 'whole-archive.*l:lib.*no-whole-archive'),)
#$(warning "pkg-config output list does not contain drivers between 'whole-archive'/'no-whole-archive' flags.")
#$(error "Cannot generate statically-linked binaries with this version of pkg-config")
#endif
#endif
#
#build/$(APP)-shared: $(SRCS-y) Makefile $(PC_FILE) | build
#        $(CC) $(CFLAGS) $(SRCS-y) -o $@ $(LDFLAGS) $(LDFLAGS_SHARED)
#
#build/$(APP)-static: $(SRCS-y) Makefile $(PC_FILE) | build
#        $(CC) $(CFLAGS) $(SRCS-y) -o $@ $(LDFLAGS) $(LDFLAGS_STATIC)
#
#build:
#        @mkdir -p $@
#
#.PHONY: clean
#clean:
#        rm -f build/$(APP) build/$(APP)-static build/$(APP)-shared
#        test -d build && rmdir -p build || true






#ROOTDIR=../..
#DEPSDIR=${ROOTDIR}/deps
#
#ifeq ($(RTE_TARGET),)
#$(error "Please define RTE_TARGET environment variable")
#endif
#
#ifeq ($(UDPDK_PATH),)
#	UDPDK_PATH=${ROOTDIR}
#endif
#
## all source are stored in SRCS-y
#SRCS= main.c
#
#LIBS+= -L${UDPDK_PATH}/udpdk -Wl,--whole-archive,-ludpdk,--no-whole-archive
#LIBS+= -L${DEPSDIR}/dpdk/${RTE_TARGET}/lib -Wl,--whole-archive,-ldpdk,--no-whole-archive
#LIBS+= -Wl,--no-whole-archive -lrt -lm -ldl -lcrypto -pthread -lnuma
#
#CFLAGS += $(WERROR_FLAGS) -O3
#
#TARGET="pktgen"
#all:
#	cc $(CFLAGS) -I${ROOTDIR}/udpdk -I${DEPSDIR}/dpdk/${RTE_TARGET}/include -o ${TARGET} ${SRCS} ${LIBS}
#
#.PHONY: clean
#clean:
#	rm -f *.o ${TARGET}
