.PHONY: all clean run iso check

all: run

include boot/Makefile
include kernel/Makefile

LD = $(HOME)/opt/cross/bin/i686-elf-g++
LDFLAGS = -ffreestanding -O2 -nostdlib -lgcc

os.bin: boot/boot.o kernel/kernel.o
	$(LD) -T linker.ld -o $@ $(LDFLAGS) $^

run: os.bin
	qemu-system-i386 -kernel $<

os.iso: os.bin grub.cfg
	mkdir -p iso/boot/grub
	cp os.bin iso/boot/os.bin
	cp grub.cfg iso/boot/grub/grub.cfg
	grub-mkrescue -o $@ iso

iso: os.iso
	qemu-system-i386 -cdrom $<

check:
	@grub-file --is-x86-multiboot os.bin && echo "os.bin is multiboot-compliant!" || (echo "Error: os.bin is NOT multiboot-compliant." && exit 1)

clean:
	$(MAKE) -C boot clean_boot
	$(MAKE) -C kernel clean_kernel
	rm -f os.img

