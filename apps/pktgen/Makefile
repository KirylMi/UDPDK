#
# Created by leoll2 on 10/07/20.
# Copyright (c) 2020 Leonardo Lai. All rights reserved.
#

# all source are stored in SRCS
SRCS= main.c

CFLAGS = -O3 $(shell pkg-config --cflags libdpdk)
LDFLAGS_SHARED = $(shell pkg-config --libs libdpdk)
LIBS = -Wl,--whole-archive,-ludpdk,--no-whole-archive

TARGET="pktgen"
all:
	cc  ${CFLAGS} -o ${TARGET} ${SRCS} ${LIBS} ${LDFLAGS_SHARED}

.PHONY: clean
clean:
	rm -f *.o ${TARGET}
