include $(top_srcdir)/config/Rules.am

VPATH = \
	$(top_srcdir)/module/nvpair \
	$(top_srcdir)/lib/libnvpair

# Required CFLAGS for libtirpc
AM_CFLAGS += $(LIBTIRPC_CFLAGS)

# Includes kernel code, generate warnings for large stack frames
AM_CFLAGS += $(FRAME_LARGER_THAN)

DEFAULT_INCLUDES += \
	-I$(top_srcdir)/include \
	-I$(top_srcdir)/lib/libspl/include

lib_LTLIBRARIES = libnvpair.la

USER_C = \
	libnvpair.c \
	libnvpair_json.c \
	nvpair_alloc_system.c

KERNEL_C = \
	nvpair_alloc_fixed.c \
	nvpair.c \
	fnvpair.c

nodist_libnvpair_la_SOURCES = \
	$(USER_C) \
	$(KERNEL_C)

libnvpair_la_LIBADD = $(LIBTIRPC)
libnvpair_la_LDFLAGS = -version-info 1:1:0

EXTRA_DIST = $(USER_C)
