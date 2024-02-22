TARGET=c-main

PLATFORM=$(shell arch)

ifneq ($(PLATFORM), x86_64)
DOCKERPREFIX=docker run --platform linux/amd64 -v "$(shell pwd):/run/apps/" danielkrasny/apps-asm:latest
endif

#CFLAGS += $(shell gcc -v 2>&1 | grep enable-default-pie > /dev/null && echo \-no\-pie)
CFLAGS += -g -std=c99
#CFLAGS += -m32

all: $(TARGET)

run:
	$(DOCKERPREFIX) ./$(TARGET)

clean:
	rm -rf $(TARGET) *.o

$(TARGET): c-module.c c-main.c
	$(DOCKERPREFIX) cc $(CFLAGS) c-module.c c-main.c -o $(TARGET)
