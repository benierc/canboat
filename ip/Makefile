#
# ip/Makefile
#
# (C) 2009-2015, Kees Verruijt, Harlingen, The Netherlands.
#
# This file is part of CANboat.
#
# CANboat is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.
#
# CANboat is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with CANboat.  If not, see <http://www.gnu.org/licenses/>.
#

PLATFORM=$(shell uname | tr '[A-Z]' '[a-z]')-$(shell uname -m)
TARGETDIR=../rel/$(PLATFORM)
TARGET1=../rel/$(PLATFORM)/iptee
TARGETLIST=$(TARGET1)

CFLAGS= -Wall -O2

all:	$(TARGETDIR) $(TARGETLIST)

$(TARGETDIR):	
	mkdir -p $(TARGETDIR)

clean:
	-rm -f $(TARGETLIST) *.elf *.gdb

$(TARGET1):	iptee.c ../common/common.c ../common/common.h
	$(CC) $(CPPFLAGS) $(CFLAGS) $(LDFLAGS) -o $(TARGET1) $(CFLAGS) -I../common iptee.c ../common/common.c
ifeq ($(notdir $(HELP2MAN)),help2man)
	-$(HELP2MAN) --no-discard-stderr --version-string=Unknown --output=../man/man1/iptee.1 --name='iptee' $@
endif
