CXX=gcc
CXXFLAGS=-Wall -Wextra -fsanitize=thread
CXX_LINK_FLAGS=-lpthread -fsanitize=thread

all:
	$(CXX) ${CXXFLAGS} cfs.c -o cfs   ${CXX_LINK_FLAGS} 
	$(CXX) ${CXXFLAGS} efd.c -o efd   ${CXX_LINK_FLAGS}
	$(CXX) ${CXXFLAGS} fifo.c -o fifo ${CXX_LINK_FLAGS}
	$(CXX) ${CXXFLAGS} lock.c -o lock ${CXX_LINK_FLAGS}
	$(CXX) ${CXXFLAGS} thread-affinity.c -o thread-affinity ${CXX_LINK_FLAGS}

.PHONY: all clean

clean:
	rm -fv cfs efd fifo lock thread-affinity
