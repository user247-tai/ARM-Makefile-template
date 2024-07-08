PRO_DIR := .
PRO_NAME := main

INC_DIR := $(PRO_DIR)/inc
SRC_DIR := $(PRO_DIR)/src
LINK_FILE := $(PRO_DIR)/linker/STM32F030_mini_board.ld
OUTPUT_PATH := $(PRO_DIR)/output

COMPILER_DIR := D:/ARMCompiler/arm-gnu-toolchain-13.3.rel1-mingw-w64-i686-arm-none-eabi
PREFIX_GCC_COMPILER := arm-none-eabi

CC := $(COMPILER_DIR)/bin/$(PREFIX_GCC_COMPILER)-gcc
AS := $(COMPILER_DIR)/bin/$(PREFIX_GCC_COMPILER)-as
LD := $(COMPILER_DIR)/bin/$(PREFIX_GCC_COMPILER)-ld

FILE_TO_LINK := $(OUTPUT_PATH)/main.o $(OUTPUT_PATH)/startup_ARMCM0.o

CC_OPT := -march=armv6-m -mcpu=cortex-m0 -c -O0 -g -mthumb -I$(INC_DIR)
AS_OPT := -march=armv6-m -mcpu=cortex-m0 -c -mthumb
LD_OPT := -T $(LINK_FILE) -Map $(OUTPUT_PATH)/$(PRO_NAME).map $(FILE_TO_LINK)


$(OUTPUT_PATH)/main.o: $(SRC_DIR)/main.c create_dir
	$(CC) $(CC_OPT) $(SRC_DIR)/main.c -o $(OUTPUT_PATH)/main.o

$(OUTPUT_PATH)/startup_ARMCM0.o: $(SRC_DIR)/startup_ARMCM0.S create_dir
	$(AS) $(AS_OPT) $(SRC_DIR)/startup_ARMCM0.s -o $(OUTPUT_PATH)/startup_ARMCM0.o

create_dir:
	@mkdir $(PRO_DIR)/output

build: $(FILE_TO_LINK) $(LINK_FILE) 
	$(LD) $(LD_OPT) -o $(OUTPUT_PATH)/$(PRO_NAME).elf

clean:
	@rm -r $(PRO_DIR)/output

