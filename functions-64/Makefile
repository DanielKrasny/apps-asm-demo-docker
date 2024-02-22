TARGET=c-main
PLATFORM=$(shell arch)

ifneq ($(PLATFORM), x86_64)
DOCKERPREFIX=docker run --platform linux/amd64 -v "$(shell pwd):/run/apps/" danielkrasny/apps-asm:latest
endif

CFLAGS += $(shell $(DOCKERPREFIX) gcc -v 2>&1 | grep enable-default-pie > /dev/null && echo \-no\-pie)
CFLAGS += -g -std=c99
#CFLAGS += -m32

all: $(TARGET)

%.o: %.asm
	$(DOCKERPREFIX) nasm -g -f elf64 -Fdwarf $<

run:
	$(DOCKERPREFIX) ./$(TARGET)

clean:
	rm -rf $(TARGET) *.o

$(TARGET): asm-tool.o c-main.c
	$(DOCKERPREFIX) cc $(CFLAGS) asm-tool.o c-main.c -o $(TARGET)
