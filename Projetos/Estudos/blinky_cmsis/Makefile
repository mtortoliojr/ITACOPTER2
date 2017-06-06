#******************************************************************************
#
# Makefile - Rules for building the blinky example.
#
# Copyright (c) 2012-2017 Texas Instruments Incorporated.  All rights reserved.
# Software License Agreement
# 
# Texas Instruments (TI) is supplying this software for use solely and
# exclusively on TI's microcontroller products. The software is owned by
# TI and/or its suppliers, and is protected under applicable copyright
# laws. You may not combine this software with "viral" open-source
# software in order to form a larger program.
# 
# THIS SOFTWARE IS PROVIDED "AS IS" AND WITH ALL FAULTS.
# NO WARRANTIES, WHETHER EXPRESS, IMPLIED OR STATUTORY, INCLUDING, BUT
# NOT LIMITED TO, IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR
# A PARTICULAR PURPOSE APPLY TO THIS SOFTWARE. TI SHALL NOT, UNDER ANY
# CIRCUMSTANCES, BE LIABLE FOR SPECIAL, INCIDENTAL, OR CONSEQUENTIAL
# DAMAGES, FOR ANY REASON WHATSOEVER.
# 
# This is part of revision 2.1.4.178 of the EK-TM4C123GXL Firmware Package.
#
#******************************************************************************

#
# Defines the part type that this project uses.
#
PART=TM4C123GH6PM

#
# The base directory for TivaWare.
#
ROOT=../../../Tivaware

#
# Include the common make definitions.
#
include ${ROOT}/makedefs

#
# Where to find header files that do not live in the source directory.
#
IPATH=../../../Tivaware
IPATH+=../../../Tivaware/CMSIS/CMSIS/Lib/GCC
IPATH+=../../../Tivaware/CMSIS/CMSIS/Include
IPATH+=../../../Tivaware/CMSIS/Device/ARM/ARMCM4/Include
IPATH+=../../../Tivaware/CMSIS/Device/ARM/ARMCM4/Source
IPATH+=../../../Tivaware/CMSIS/CMSIS/DSP_Lib/BasicMathFunctions
IPATH+=../../../Tivaware/CMSIS/CMSIS/DSP_Lib/MatrixFunctions
IPATH+=../../../Tivaware/CMSIS/CMSIS/DSP_Lib/SupportFunctions
IPATH+=../../../Tivaware/CMSIS/CMSIS/DSP_Lib/CommonTables
IPATH+=../../../Tivaware/CMSIS/CMSIS/DSP_Lib/ControllerFunctions
IPATH+=../../../Tivaware/CMSIS/CMSIS/DSP_Lib/Examples/Common
IPATH+=../../../Tivaware/CMSIS/CMSIS/DSP_Lib/Examples/Common/Source
IPATH+=../../../Tivaware/CMSIS/CMSIS/DSP_Lib/Examples/Common/Include

VPATH=../../../Tivaware
VPATH+=../../../Tivaware/CMSIS/CMSIS/Lib/GCC
VPATH+=../../../Tivaware/CMSIS/CMSIS/Include
VPATH+=../../../Tivaware/CMSIS/Device/ARM/ARMCM4/Include
VPATH+=../../../Tivaware/CMSIS/Device/ARM/ARMCM4/Source
VPATH+=../../../Tivaware/CMSIS/CMSIS/DSP_Lib/BasicMathFunctions
VPATH+=../../../Tivaware/CMSIS/CMSIS/DSP_Lib/MatrixFunctions
VPATH+=../../../Tivaware/CMSIS/CMSIS/DSP_Lib/SupportFunctions
VPATH+=../../../Tivaware/CMSIS/CMSIS/DSP_Lib/CommonTables
VPATH+=../../../Tivaware/CMSIS/CMSIS/DSP_Lib/ControllerFunctions

#
# The default rule, which causes the blinky example to be built.
#
all: ${COMPILER}
all: ${COMPILER}/blinky.axf

#
# The rule to clean out all the build products.
#
clean:
	@rm -rf ${COMPILER} ${wildcard *~}


#
# Flash the Tiva
#
burn:
	@lm4flash ${COMPILER}/blinky.bin

#
# The rule to create the target directory.
#
${COMPILER}:
	@mkdir -p ${COMPILER}

#
# Rules for building the blinky example.
#
${COMPILER}/blinky.axf: ${COMPILER}/blinky.o
${COMPILER}/blinky.axf: ${COMPILER}/startup_${COMPILER}.o
${COMPILER}/blinky.axf: ${ROOT}/driverlib/${COMPILER}/libdriver.a
${COMPILER}/blinky.axf: ${ROOT}/CMSIS/CMSIS/Lib/GCC/libarm_cortexM4lf_math.a	
${COMPILER}/blinky.axf: blinky.ld
SCATTERgcc_blinky=blinky.ld
ENTRY_blinky=ResetISR
CFLAGSgcc=-DTARGET_IS_TM4C123_RB1

#
# Include the automatically generated dependency files.
#
ifneq (${MAKECMDGOALS},clean)
-include ${wildcard ${COMPILER}/*.d} __dummy__
endif
