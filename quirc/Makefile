# PS Vita Custom Makefile - Only builds library, and builds with Vita Toolchain

# quirc -- QR-code recognition library
# Copyright (C) 2010-2012 Daniel Beer <dlbeer@gmail.com>
#
# Permission to use, copy, modify, and/or distribute this software for any
# purpose with or without fee is hereby granted, provided that the above
# copyright notice and this permission notice appear in all copies.
#
# THE SOFTWARE IS PROVIDED "AS IS" AND THE AUTHOR DISCLAIMS ALL WARRANTIES
# WITH REGARD TO THIS SOFTWARE INCLUDING ALL IMPLIED WARRANTIES OF
# MERCHANTABILITY AND FITNESS. IN NO EVENT SHALL THE AUTHOR BE LIABLE FOR
# ANY SPECIAL, DIRECT, INDIRECT, OR CONSEQUENTIAL DAMAGES OR ANY DAMAGES
# WHATSOEVER RESULTING FROM LOSS OF USE, DATA OR PROFITS, WHETHER IN AN
# ACTION OF CONTRACT, NEGLIGENCE OR OTHER TORTIOUS ACTION, ARISING OUT OF
# OR IN CONNECTION WITH THE USE OR PERFORMANCE OF THIS SOFTWARE.

TARGET_LIB = libquirc.a
LIB_OBJ = \
    ../decode.o \
    ../identify.o \
    ../quirc.o \
    ../version_db.o
INCLUDES = ../lib

CC      = arm-vita-eabi-gcc
AR      = arm-vita-eabi-ar
PREFIX  ?= ${VITASDK}/arm-vita-eabi
CFLAGS ?= -Wl,-q -Wall -O3 -I$(INCLUDES) -ffat-lto-objects -flto
ASFLAGS = $(CFLAGS)

all: $(TARGET_LIB)

debug: CFLAGS += -DDEBUG_BUILD
debug: all

$(TARGET_LIB): $(LIB_OBJ)
	$(AR) -rc $@ $^
	
clean:
	rm -rf $(TARGET_LIB) $(LIB_OBJ)
	
install:
	@mkdir -p $(DESTDIR)$(PREFIX)/lib/
	cp $(TARGET_LIB) $(DESTDIR)$(PREFIX)/lib/
	@mkdir -p $(DESTDIR)$(PREFIX)/include/
	cp ../lib/quirc.h $(DESTDIR)$(PREFIX)/include/
