CC=gcc
# CC=clang
# TODO check with gcc13, gcc14, clang
# TODO check with thread sanitizer
CFLAGS=-Wall -Wextra -Wpedantic -Werror -Wformat -Wformat=2 -fexceptions -O2
CFLAGS_TSAN=-fsanitize=thread -g -O1
C_LINK_FLAGS=-lpthread

all:
	$(CC) ${CFLAGS} cfs.c -o cfs   ${C_LINK_FLAGS} 
	$(CC) ${CFLAGS} efd.c -o efd   ${C_LINK_FLAGS}
	$(CC) ${CFLAGS} fifo.c -o fifo ${C_LINK_FLAGS}
	$(CC) ${CFLAGS} lock.c -o lock ${C_LINK_FLAGS}
	$(CC) ${CFLAGS} thread-affinity.c -o thread-affinity ${C_LINK_FLAGS}

tsan:
	$(CC) ${CFLAGS} ${CFLAGS_TSAN} cfs.c -o cfs   ${C_LINK_FLAGS} 
	$(CC) ${CFLAGS} ${CFLAGS_TSAN} efd.c -o efd   ${C_LINK_FLAGS}
	$(CC) ${CFLAGS} ${CFLAGS_TSAN} fifo.c -o fifo ${C_LINK_FLAGS}
	$(CC) ${CFLAGS} ${CFLAGS_TSAN} lock.c -o lock ${C_LINK_FLAGS}
	$(CC) ${CFLAGS} ${CFLAGS_TSAN} thread-affinity.c -o thread-affinity ${C_LINK_FLAGS}

.PHONY: all clean

clean:
	rm -fv cfs efd fifo lock thread-affinity
