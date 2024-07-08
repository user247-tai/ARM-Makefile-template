# ARM-Makefile-template
This is an ARM Makefile template using ARM GCC toolchain (can generate ELF file)

make build:

    Create output dir then compile the main.c and startup_ARMCM0.s into main.o and startup_ARMCM0.o and store in output dir
    
    Link .o files into a elf file, also generate a map file
    
make clean:

    Delete output dir
