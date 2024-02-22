TARGET=c-main

ARCH=64
PLATFORM=$(shell arch)

ifeq ($(ARCH), 32)
CFLAGS += -m32
endif

ifneq ($(PLATFORM), x86_64)
DOCKERPREFIX=docker run --platform linux/amd64 -v "$(shell pwd):/run/apps/" danielkrasny/apps-asm:latest
endif

CFLAGS += $(shell $(DOCKERPREFIX) gcc -v 2>&1 | grep enable-default-pie > /dev/null && echo \-no\-pie)
CFLAGS += -g -std=c99

all: $(TARGET)

%.o: %.asm
	$(DOCKERPREFIX) nasm -g -f elf$(ARCH) -Fdwarf $<

run:
	$(DOCKERPREFIX) ./$(TARGET)

clean:
	rm -rf $(TARGET) *.o

$(TARGET): asm-module.o c-main.c
	$(DOCKERPREFIX) cc $(CFLAGS) asm-module.o c-main.c -o $(TARGET)
