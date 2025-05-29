CC=gcc
# CC=clang
# TODO check with gcc13, gcc14, clang
# TODO check with thread sanitizer
CFLAGS_BASE=-Wall -Wextra -Wpedantic -Werror -Wformat -Wformat=2 -fexceptions
CFLAGS=${CFLAGS_BASE} -O2
CFLAGS_TSAN=${CFLAGS_BASE} -fsanitize=thread -g -O1
C_LINK_FLAGS=-lpthread

all:
	$(CC) ${CFLAGS} cfs.c -o cfs   ${C_LINK_FLAGS} 
	$(CC) ${CFLAGS} efd.c -o efd   ${C_LINK_FLAGS}
	$(CC) ${CFLAGS} fifo.c -o fifo ${C_LINK_FLAGS}
	$(CC) ${CFLAGS} lock.c -o lock ${C_LINK_FLAGS}
	$(CC) ${CFLAGS} thread-affinity.c -o thread-affinity ${C_LINK_FLAGS}

tsan:
	$(CC) ${CFLAGS_TSAN} cfs.c -o cfs_tsan   ${C_LINK_FLAGS} 
	$(CC) ${CFLAGS_TSAN} efd.c -o efd_tsan   ${C_LINK_FLAGS}
	$(CC) ${CFLAGS_TSAN} fifo.c -o fifo_tsan ${C_LINK_FLAGS}
	$(CC) ${CFLAGS_TSAN} lock.c -o lock_tsan ${C_LINK_FLAGS}
	$(CC) ${CFLAGS_TSAN} thread-affinity.c -o thread-affinity_tsan ${C_LINK_FLAGS}

.PHONY: all clean

clean:
	rm -fv cfs efd fifo lock thread-affinity
	rm -fv cfs_tsan efd_tsan fifo_tsan lock_tsan thread-affinity_tsan
