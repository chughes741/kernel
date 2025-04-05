.PHONY: all clean_boot

AS = $(HOME)/opt/cross/bin/i686-elf-as

all: boot/boot.o

boot/boot.o: boot/boot.s
	$(AS) $< -o $@

clean_boot:
	rm -f boot.o

