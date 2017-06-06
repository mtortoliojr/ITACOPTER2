#******************************************************************************
#
# Makefile - Rules for building the FreeRTOS example.
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
ROOT=/home/lra/Embedded/ITACOPTER2/Tivaware

#
# Include the common make definitions.
#
include ${ROOT}/makedefs
include filespath

#
# Where to find source files that do not live in this directory.
#
VPATH=.
VPATH+=${FREE_RTOS_PATH}
VPATH+=${ROOT}/utils
VPATH+=drivers
VPATH+=tasks/AD
VPATH+=tasks/Status
VPATH+=tasks/PWM

#
# Where to find header files that do not live in the source directory.
#
IPATH=.
IPATH+=${ROOT}
IPATH+=${FREE_RTOS_PATH}
IPATH+=${CMSIS_PATH}

IPATH+=drivers
IPATH+=tasks/AD
IPATH+=tasks/Status
IPATH+=tasks/PWM


#
# The default rule, which causes the FreeRTOS example to be built.
#
all: ${COMPILER}
all: ${COMPILER}/freertos_ep2.axf

#
# The rule to clean out all the build products.
#
clean:
	@rm -rf ${COMPILER} ${wildcard *~}

#
# Flash the Tiva
#
burn:
	@lm4flash ${COMPILER}/freertos_ep2.bin

#
# The rule to create the target directory.
#
${COMPILER}:
	@mkdir -p ${COMPILER}

#
# Rules for building the FreeRTOS example.
#
${COMPILER}/freertos_ep2.axf: ${COMPILER}/startup_${COMPILER}.o
${COMPILER}/freertos_ep2.axf: ${COMPILER}/list.o
${COMPILER}/freertos_ep2.axf: ${COMPILER}/port.o
${COMPILER}/freertos_ep2.axf: ${COMPILER}/queue.o
${COMPILER}/freertos_ep2.axf: ${COMPILER}/timers.o
${COMPILER}/freertos_ep2.axf: ${COMPILER}/arm_matrix_example_f32.o
${COMPILER}/freertos_ep2.axf: ${COMPILER}/math_helper.o
${COMPILER}/freertos_ep2.axf: ${COMPILER}/pwm.o
${COMPILER}/freertos_ep2.axf: ${COMPILER}/buttons.o
${COMPILER}/freertos_ep2.axf: ${COMPILER}/freertos_ep2.o
${COMPILER}/freertos_ep2.axf: ${COMPILER}/heap_2.o
${COMPILER}/freertos_ep2.axf: ${COMPILER}/led_task.o
${COMPILER}/freertos_ep2.axf: ${COMPILER}/rgb.o
${COMPILER}/freertos_ep2.axf: ${COMPILER}/switch_task.o
${COMPILER}/freertos_ep2.axf: ${COMPILER}/tasks.o
${COMPILER}/freertos_ep2.axf: ${COMPILER}/uartstdio.o
${COMPILER}/freertos_ep2.axf: ${COMPILER}/ustdlib.o
${COMPILER}/freertos_ep2.axf: ${ROOT}/driverlib/${COMPILER}/libdriver.a
${COMPILER}/freertos_ep2.axf: ${CMSIS_PATH}/libarm_cortexM4lf_math.a
${COMPILER}/freertos_ep2.axf: freertos_ep2.ld
SCATTERgcc_freertos_ep2=freertos_ep2.ld
ENTRY_freertos_ep2=ResetISR
CFLAGSgcc=-DTARGET_IS_TM4C123_RB1

#
# Include the automatically generated dependency files.
#
ifneq (${MAKECMDGOALS},clean)
-include ${wildcard ${COMPILER}/*.d} __dummy__
endif
