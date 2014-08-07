#
# Makefile for the kernel mobicore drivers
#

GUD_ROOT_FOLDER := drivers/gud
# add our modules to kernel.
obj-$(CONFIG_MOBICORE_API) += mcKernelApi.o
obj-$(CONFIG_MOBICORE_DRIVER) += mcDrvModule.o

mcDrvModule-objs := MobiCoreDriver/logging.o \
		MobiCoreDriver/ops.o \
		MobiCoreDriver/mem.o \
		MobiCoreDriver/api.o \
		MobiCoreDriver/pm.o \
		MobiCoreDriver/main.o

mcKernelApi-objs := MobiCoreKernelApi/main.o \
		MobiCoreKernelApi/clientlib.o \
		MobiCoreKernelApi/device.o \
		MobiCoreKernelApi/session.o \
		MobiCoreKernelApi/connection.o

# Release mode by default
ccflags-y := -DNDEBUG 
ccflags-y += -include $(srctree)/$(GUD_ROOT_FOLDER)/build_tag.h
ccflags-y += -Wno-declaration-after-statement

subdir-ccflags-y += -Wno-declaration-after-statement -DNDEBUG
subdir-ccflags-$(CONFIG_MOBICORE_DEBUG) += -DDEBUG
subdir-ccflags-$(CONFIG_MOBICORE_VERBOSE) += -DDEBUG_VERBOSE

# The original makefile used ls | tail -1 to pick a random folder for the
# platform configuration!!!
#
# For kicks, let's make a stand and pick one.  It doesn't matter right now
# anyway because they are the same.
MOBICORE_PLATFORM := EXYNOS_5_STD

# Include platform folder
ccflags-y += -I$(GUD_ROOT_FOLDER)/MobiCoreDriver/platforms/EXYNOS_5420_STD
# MobiCore Driver includes
subdir-ccflags-y += -I$(GUD_ROOT_FOLDER)/MobiCoreDriver/public
# MobiCore KernelApi required incldes

ccflags-y += -I$(GUD_ROOT_FOLDER)/MobiCoreKernelApi/include
ccflags-y += -I$(GUD_ROOT_FOLDER)/MobiCoreKernelApi/public
