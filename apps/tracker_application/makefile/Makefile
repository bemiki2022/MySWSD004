# --- The Clear BSD License ---
# Copyright Semtech Corporation 2021. All rights reserved.
#
# Redistribution and use in source and binary forms, with or without
# modification, are permitted (subject to the limitations in the disclaimer
# below) provided that the following conditions are met:
#     * Redistributions of source code must retain the above copyright
#       notice, this list of conditions and the following disclaimer.
#     * Redistributions in binary form must reproduce the above copyright
#       notice, this list of conditions and the following disclaimer in the
#       documentation and/or other materials provided with the distribution.
#     * Neither the name of the Semtech corporation nor the
#       names of its contributors may be used to endorse or promote products
#       derived from this software without specific prior written permission.
#
# NO EXPRESS OR IMPLIED LICENSES TO ANY PARTY'S PATENT RIGHTS ARE GRANTED BY
# THIS LICENSE. THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND
# CONTRIBUTORS "AS IS" AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT
# NOT LIMITED TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A
# PARTICULAR PURPOSE ARE DISCLAIMED. IN NO EVENT SHALL SEMTECH CORPORATION BE
# LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR
# CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF
# SUBSTITUTE GOODS OR SERVICES; LOSS OF USE, DATA, OR PROFITS; OR BUSINESS
# INTERRUPTION) HOWEVER CAUSED AND ON ANY THEORY OF LIABILITY, WHETHER IN
# CONTRACT, STRICT LIABILITY, OR TORT (INCLUDING NEGLIGENCE OR OTHERWISE)
# ARISING IN ANY WAY OUT OF THE USE OF THIS SOFTWARE, EVEN IF ADVISED OF THE
# POSSIBILITY OF SUCH DAMAGE.

######################################
# target
######################################
TOP_DIR = ../../..

APP ?= tracker_application_autonomous

APP_TRACE ?= yes
MODEM_TRACE ?= no
MCU_BOARD = LR1110TRK1XKS
RADIO_BOARD = LR1110TRK1XKS
MIDDLEWARE_TRACE ?= no
USE_LR11XX_CRC_SPI ?= yes
CRYPTO = LR11XX_WITH_CREDENTIALS
LBM_STORE_AND_FORWARD = yes
MIDDLEWARE = yes
LBM_GEOLOCATION = yes
LBM_ALMANAC = yes
REGION = ALL


TOOLCHAIN_MAKEFILE = $(TOP_DIR)/toolchain/gcc/toolchain.mk
PROJECTS_COMMON_MAKEFILE = $(TOP_DIR)/apps/common/apps_modem_common.mk
PLATFORM_BOARD_MAKEFILE = $(TOP_DIR)/board/LR1110TRK1xKS/lr1110_trk1xks.mk


######################################
# building variables
######################################
# debug build?
DEBUG ?= no
# optimization
OPT ?= -Os

#######################################
# paths
#######################################

# Build path
BUILD_DIR = ./build

######################################
# source
######################################

# C sources

C_SOURCES +=  \
../main_$(APP).c \
$(TOP_DIR)/apps/tracker_application/tracker_utility/tracker_utility.c \
${TOP_DIR}/apps/tracker_application/middleware/ble/app_debug.c \
${TOP_DIR}/apps/tracker_application/middleware/ble/app_entry.c \
${TOP_DIR}/apps/tracker_application/middleware/ble/hw_timerserver.c \
${TOP_DIR}/apps/tracker_application/middleware/ble/stm32_lpm_if.c \
${TOP_DIR}/apps/tracker_application/middleware/ble/target/hw_ipcc.c \
${TOP_DIR}/apps/tracker_application/middleware/ble/app/app_ble.c \
${TOP_DIR}/apps/tracker_application/middleware/ble/app/ble_thread.c \
${TOP_DIR}/apps/tracker_application/middleware/ble/app/p2p_server_app.c \
${TOP_DIR}/apps/tracker_application/middleware/ble/lpm/tiny_lpm/stm32_lpm.c \
${TOP_DIR}/apps/tracker_application/middleware/ble/sequencer/stm32_seq.c \
${TOP_DIR}/apps/tracker_application/middleware/ble/STM32_WPAN/interface/patterns/ble_thread/tl/tl_mbox.c \
${TOP_DIR}/apps/tracker_application/middleware/ble/STM32_WPAN/interface/patterns/ble_thread/tl/hci_tl.c \
${TOP_DIR}/apps/tracker_application/middleware/ble/STM32_WPAN/interface/patterns/ble_thread/tl/hci_tl_if.c \
${TOP_DIR}/apps/tracker_application/middleware/ble/STM32_WPAN/interface/patterns/ble_thread/shci/shci.c \
${TOP_DIR}/apps/tracker_application/middleware/ble/STM32_WPAN/interface/patterns/ble_thread/shci/shci_tl.c \
${TOP_DIR}/apps/tracker_application/middleware/ble/STM32_WPAN/interface/patterns/ble_thread/shci/shci_tl_if.c \
${TOP_DIR}/apps/tracker_application/middleware/ble/STM32_WPAN/utilities/dbg_trace.c \
${TOP_DIR}/apps/tracker_application/middleware/ble/STM32_WPAN/utilities/otp.c \
${TOP_DIR}/apps/tracker_application/middleware/ble/STM32_WPAN/utilities/stm_list.c \
${TOP_DIR}/apps/tracker_application/middleware/ble/STM32_WPAN/utilities/stm_queue.c \
${TOP_DIR}/apps/tracker_application/middleware/ble/STM32_WPAN/ble/core/template/osal.c \
${TOP_DIR}/apps/tracker_application/middleware/ble/STM32_WPAN/ble/svc/Src/svc_ctl.c \
${TOP_DIR}/apps/tracker_application/middleware/ble/STM32_WPAN/ble/svc/Src/p2p_stm.c \
${TOP_DIR}/apps/tracker_application/middleware/ble/STM32_WPAN/ble/core/auto/ble_gap_aci.c \
${TOP_DIR}/apps/tracker_application/middleware/ble/STM32_WPAN/ble/core/auto/ble_gatt_aci.c \
${TOP_DIR}/apps/tracker_application/middleware/ble/STM32_WPAN/ble/core/auto/ble_hal_aci.c \
${TOP_DIR}/apps/tracker_application/middleware/ble/STM32_WPAN/ble/core/auto/ble_hci_le.c \
${TOP_DIR}/apps/tracker_application/middleware/ble/STM32_WPAN/ble/core/auto/ble_l2cap_aci.c \

# C includes
C_INCLUDES += \
-I$(TOP_DIR)/apps/tracker_application \
-I$(TOP_DIR)/apps/tracker_application/tracker_utility \
-I$(TOP_DIR)/apps/tracker_application/middleware/ble \
-I$(TOP_DIR)/apps/tracker_application/middleware/ble/app \
-I${TOP_DIR}/apps/tracker_application/middleware/ble/lpm/tiny_lpm \
-I${TOP_DIR}/apps/tracker_application/middleware/ble/sequencer \
-I${TOP_DIR}/apps/tracker_application/middleware/ble/STM32_WPAN \
-I${TOP_DIR}/apps/tracker_application/middleware/ble/STM32_WPAN/interface/patterns/ble_thread \
-I${TOP_DIR}/apps/tracker_application/middleware/ble/STM32_WPAN/interface/patterns/ble_thread/tl \
-I${TOP_DIR}/apps/tracker_application/middleware/ble/STM32_WPAN/interface/patterns/ble_thread/shci \
-I${TOP_DIR}/apps/tracker_application/middleware/ble/STM32_WPAN/utilities \
-I${TOP_DIR}/apps/tracker_application/middleware/ble/STM32_WPAN/ble/core \
-I${TOP_DIR}/apps/tracker_application/middleware/ble/STM32_WPAN/ble/core/auto \
-I${TOP_DIR}/apps/tracker_application/middleware/ble/STM32_WPAN/ble/core/template \
-I${TOP_DIR}/apps/tracker_application/middleware/ble/STM32_WPAN/ble/svc/Inc \
-I${TOP_DIR}/apps/tracker_application/middleware/ble/STM32_WPAN/ble/svc/Src \
-I${TOP_DIR}/apps/tracker_application/middleware/ble/STM32_WPAN/ble \
-I${TOP_DIR}/lora_basics_modem/lora_basics_modem/lbm_lib/smtc_modem_core/geolocation_services

#######################################
# include
#######################################

# LoRa Basics Modem
LORA_BASICS_MODEM = $(TOP_DIR)/lora_basics_modem/lora_basics_modem/lbm_lib/

include $(PROJECTS_COMMON_MAKEFILE)
include $(PLATFORM_BOARD_MAKEFILE)
# Use another LD script than the one in the host driver folder because of the bootloader
LDSCRIPT = ./stm32wb55xx_flash_cm4.ld
include $(TOOLCHAIN_MAKEFILE)


#######################################
# build the application
#######################################

.PHONY: all target

all: target

target: $(BUILD_DIR)/$(APP).elf $(BUILD_DIR)/$(APP).bin

.DEFAULT_GOAL:= target

## For the main application
# list of objects
OBJECTS = $(addprefix $(BUILD_DIR)/,$(notdir $(C_SOURCES:.c=.o)))
vpath %.c $(sort $(dir $(C_SOURCES)))

# list of ASM program objects
OBJECTS += $(addprefix $(BUILD_DIR)/,$(notdir $(ASM_SOURCES:.s=.o)))
vpath %.s $(sort $(dir $(ASM_SOURCES)))

$(BUILD_DIR)/%.o: %.c Makefile $(PLATFORM_MAKEFILE) | $(BUILD_DIR)
	$(CC) -c $(CFLAGS) -Wa,-a,-ad,-alms=$(BUILD_DIR)/$(notdir $(<:.c=.lst)) $< -o $@

$(BUILD_DIR)/%.o: %.s Makefile $(PLATFORM_MAKEFILE) | $(BUILD_DIR)
	$(AS) -c $(CFLAGS) $< -o $@

$(BUILD_DIR)/$(APP).elf: $(OBJECTS) $(LBM_LIB) Makefile | $(BUILD_DIR)
	$(CC) $(OBJECTS) $(LBM_LIB) $(LDFLAGS),--print-memory-usage -o $@
	$(SZ) $@

$(BUILD_DIR)/%.hex: $(BUILD_DIR)/%.elf | $(BUILD_DIR)
	$(HEX) $< $@

$(BUILD_DIR)/%.bin: $(BUILD_DIR)/%.elf | $(BUILD_DIR)
	$(BIN) $< $@

$(BUILD_DIR):
	mkdir $@

print-%  : ; @echo $* = $($*)

#######################################
# clean up
#######################################
clean: clean_lbm
	-rm -fR $(BUILD_DIR)

#######################################
# dependencies
#######################################
-include $(wildcard $(BUILD_DIR)/*.d)

# *** EOF ***
