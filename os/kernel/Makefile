.PHONY: all clean_kernel

CXX = $(HOME)/opt/cross/bin/i686-elf-g++
CXXFLAGS = -ffreestanding -O2 -Wall -Wextra -fno-exceptions -fno-rtti

all: kernel/kernel.elf

kernel/kernel.o: kernel/kernel.cpp
	$(CXX) $(CXXFLAGS) -c $< -o $@

clean_kernel:
	rm -f *.o

