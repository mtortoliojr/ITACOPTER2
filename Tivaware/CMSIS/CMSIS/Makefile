##
# Makefile to build DSP_Lib into libraries
# Taken from: https://github.com/mikeferguson/stm32/blob/9e27786de4e6df74dc735f3c5667fbe4874e59c5/libraries/CMSIS/Makefile
##

#ARCH        := M0l
ARCH        := M4lf
LIB         := Lib/libarm_cortex$(ARCH)_math.a
PART=TM4C123GH6PM

# Architectures to build for
#ARCHS       := M0b
ARCHS       := M4
#M0l_FLAGS   := -mthumb -mcpu=cortex-m0 -DARM_MATH_CM0
# M3l_FLAGS   := -mthumb -mcpu=cortex-m3 -DARM_MATH_CM3
#M4l_FLAGS   := -mthumb -mcpu=cortex-m4 -DARM_MATH_CM4
M4lf_FLAGS  := -mthumb -mcpu=cortex-m4 -mfloat-abi=hard -mfpu=fpv4-sp-d16 -DARM_MATH_CM4 -D__FPU_PRESENT -O
#M4lf_FLAGS  := -mthumb -mcpu=cortex-m4 -mfloat-abi=hard -mfpu=fpv4-sp-d16 -DARM_MATH_CM4 -DPART_${PART}

# Directories
DSPLIB      := DSP_Lib
DSPDIRS     := BasicMathFunctions          \
               CommonTables                \
               ComplexMathFunctions        \
               ControllerFunctions         \
               FastMathFunctions           \
               FilteringFunctions          \
               MatrixFunctions             \
               StatisticsFunctions         \
               SupportFunctions            \
               TransformFunctions

# Build Paths
BUILD_PATH  := Lib/build
BUILDDIRS   := $(BUILD_PATH)
BUILDDIRS   += $(foreach dir,$(DSPDIRS),$(BUILD_PATH)/$(DSPLIB)/$(dir))

# Targets to build
LIBS        := $(foreach tgt,$(ARCHS),Lib/libarm_cortex$(tgt)_math.a)
#SRCS        := $(wildcard $(DSPLIB)/*/*.c)
SRCS        := $(wildcard $(DSPLIB)/*/*.c)
OBJS        := $(patsubst %.c, %.o, $(SRCS))
OBJS        := $(foreach obj,$(OBJS),$(BUILD_PATH)/$(obj))

# Tools
CC          := /home/marcos/Embedded/gcc-arm-none-eabi-5_4-2016q3/bin/arm-none-eabi-gcc
CXX         := /home/marcos/Embedded/gcc-arm-none-eabi-5_4-2016q3/bin/arm-none-eabi-g++
LD          := /home/marcos/Embedded/gcc-arm-none-eabi-5_4-2016q3/bin/arm-none-eabi-ld
AR          := /home/marcos/Embedded/gcc-arm-none-eabi-5_4-2016q3/bin/arm-none-eabi-ar
AS          := /home/marcos/Embedded/gcc-arm-none-eabi-5_4-2016q3/bin/arm-none-eabi-gcc
CP          := /home/marcos/Embedded/gcc-arm-none-eabi-5_4-2016q3/bin/arm-none-eabi-objcopy
OD          := /home/marcos/Embedded/gcc-arm-none-eabi-5_4-2016q3/bin/arm-none-eabi-objdump
SIZE        := /home/marcos/Embedded/gcc-arm-none-eabi-5_4-2016q3/bin/-none-eabi-size

# Flags
INCLUDES    := -I./Include -I./../Device/ARM/ARMCM4/Include
#CFLAGS      := -c -fno-common -g3 -Os -ffunction-sections
CFLAGS      := -c -fno-common -g3 -O -ffunction-sections

CXXFLAGS    := $(CFLAGS) -fno-exceptions
CPFLAGS     := -Obinary -v
ODFLAGS     := -S -t
ARFLAGS     := 

#IPATH=../Device/ARM/ARMCM4/Include

all: $(BUILDDIRS) $(OBJS) $(LIB) $(BUILD_PATH)
clean:
	rm -rf $(BUILD_PATH)

$(BUILD_PATH)/%.o: %.c
	$(CC) $(CFLAGS) $(INCLUDES) $($(ARCH)_FLAGS) -o $@ $<

$(LIB): $(OBJS)
	$(AR) rcs $@ $?

$(BUILDDIRS):
	@mkdir -p $@
