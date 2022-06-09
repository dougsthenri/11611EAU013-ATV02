PROG = blinky

CC = arm-none-eabi-gcc
LD = arm-none-eabi-gcc
CP = arm-none-eabi-objcopy
CFLAGS = -g -mcpu=cortex-m4 -mthumb -O0 -Wall
LFLAGS = -nostdlib -T stm32f401xC-rom.ld

OBJS = startup.o \
       main.o

all: $(PROG).elf

$(PROG).elf: $(OBJS)
	$(LD) $(LFLAGS) $^ -o $@
	$(CP) $(PROG).elf -O binary $(PROG).bin

%.o: %.c
	$(CC) -c $(CFLAGS) $< -o $@
	
install: $(PROG).bin
	st-flash --reset --opt --flash=256k write $(PROG).bin 0x8000000

clean:
	rm -rf $(OBJS) $(PROG).elf
