#  _____     ___ ____
#   ____|   |    ____|      PS2 Open Source Project
#  |     ___|   |____
#
#--------------------------------------------------------------------------
#
#    Copyright (C) 2008 - Neme & jimmikaelkael (www.psx-scene.com)
#
#    This program is free software; you can redistribute it and/or modify
#    it under the terms of the Free McBoot License.
#
#	 This program and any related documentation is provided "as is"
#	 WITHOUT ANY WARRANTIES, either express or implied, including, but not
# 	 limited to, implied warranties of fitness for a particular purpose. The
# 	 entire risk arising out of use or performance of the software remains
# 	 with you.
#    In no event shall the author be liable for any damages whatsoever
# 	 (including, without limitation, damages to your hardware or equipment,
# 	 environmental damage, loss of health, or any kind of pecuniary loss)
# 	 arising out of the use of or inability to use this software or
# 	 documentation, even if the author has been advised of the possibility
# 	 of such damages.
#
#    You should have received a copy of the Free McBoot License along with
#    this program; if not, please report at psx-scene :
#    http://psx-scene.com/forums/freevast/
#
#--------------------------------------------------------------------------
#
# MakeFile
#
# ------------------------------------------------------------------------

EE_BIN = launcher2.elf

EE_INCS = -I$(PS2SDK)/ee/include -I$(PS2SDK)/common/include -I$(PS2SDK)/sbv/include
EE_LDFLAGS = -nostartfiles -Tlinkfile -L$(PS2SDK)/sbv/lib -L. -s
EE_LIBS = -ldebug -lcdvd -lpad -lpatches -lc -lkernel

EE_OBJS = launcher2.o gs.o chkesr_rpc.o chkesr.o pad.o timer.o iomanx.o init.o dma_asm.o gs_asm.o ps2_asm.o elf_loader.o #usbhdfsd.o usbd.o


all:
	$(MAKE) $(EE_BIN)

clean:
	$(MAKE) -C init clean
	$(MAKE) -C chkesr clean
	$(MAKE) -C elf_loader clean
	rm -f crt0.o
	rm -f *.elf *.irx *.o init.s chkesr.s elf_loader.s


iomanx.s:
	iomanx.s iomanx_irx
#filexio.s:
#	filexio.s filexio_irx
#usbd.s:
#	usbd.s usbd_irx
#usbhdfsd.s:
#	usbhdfsd.s usb_mass_irx
init.s:
	$(MAKE) -C init
	bin2s init.irx init.s init_irx
chkesr.s:
	$(MAKE) -C chkesr
	bin2s chkesr.irx chkesr.s chkesr_irx
elf_loader.s:
	$(MAKE) -C elf_loader
	bin2s elf_loader/elf_loader.elf elf_loader.s elf_loader

include Makefile.pref
include Makefile.eeglobal


