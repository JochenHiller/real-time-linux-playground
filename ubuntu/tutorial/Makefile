CXX=gcc
CXX_LINK_FLAGS=-lpthread

all:
	$(CXX) cfs.c -o cfs   ${CXX_LINK_FLAGS} 
	$(CXX) efd.c -o efd   ${CXX_LINK_FLAGS}
	$(CXX) fifo.c -o fifo ${CXX_LINK_FLAGS}
	$(CXX) lock.c -o lock ${CXX_LINK_FLAGS}
	$(CXX) thread-affinity.c -o thread-affinity ${CXX_LINK_FLAGS}

.PHONY: all clean

clean:
	rm -fv cfs efd fifo lock thread-affinity
