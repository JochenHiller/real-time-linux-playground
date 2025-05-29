CXX=gcc
# CXX=clang
# TODO check with gcc13, gcc14, clang
# TODO check with -fsanitize=thread, use -g -O1
CXXFLAGS=-Wall -Wextra -Wpedantic -Werror -Wformat -Wformat=2 -fexceptions -O2
CXX_LINK_FLAGS=-lpthread

all:
	$(CXX) ${CXXFLAGS} cfs.c -o cfs   ${CXX_LINK_FLAGS} 
	$(CXX) ${CXXFLAGS} efd.c -o efd   ${CXX_LINK_FLAGS}
	$(CXX) ${CXXFLAGS} fifo.c -o fifo ${CXX_LINK_FLAGS}
	$(CXX) ${CXXFLAGS} lock.c -o lock ${CXX_LINK_FLAGS}
	$(CXX) ${CXXFLAGS} thread-affinity.c -o thread-affinity ${CXX_LINK_FLAGS}

.PHONY: all clean

clean:
	rm -fv cfs efd fifo lock thread-affinity
