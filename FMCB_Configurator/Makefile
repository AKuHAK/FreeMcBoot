EE_BIN = BOOT.ELF
EE_OBJS = main.o pad.o config.o elf.o draw.o loader.o  filer.o\
	icon_sys.o icon_icn.o \
	timer.o \
	font_uLE.o

EE_INCS := -I$(PS2DEV)/gsKit/include -I$(PS2DEV)/libjpg/include\
	-I$(PS2SDK)/sbv/include -I$(PS2DEV)/libcdvd/ee

EE_LDFLAGS := -L$(PS2DEV)/gsKit/lib -L$(PS2DEV)/libjpg\
	-L$(PS2SDK)/sbv/lib -L$(PS2DEV)/libcdvd/lib -s
EE_LIBS = -lpad -lgskit -ldmakit -lmc -lmf -lpatches -ldebug -lc

all:	$(EE_BIN)

run: comp
	ps2client -h 192.168.1.4 -t 1 execee host:FMCB_CFG.ELF
reset: clean
	ps2client -h 192.168.1.4 reset
comp: all
	ps2-packer BOOT.ELF FMCB_CFG.ELF

loader.s:
	$(MAKE) -C loader
	bin2s loader/loader.elf loader.s loader_elf

icon_sys.s:
	bin2s icons/icon.sys icon_sys.s icon_sys
icon_icn.s:
	bin2s icons/FMCB.icn icon_icn.s icon_icn

clean:
	$(MAKE) -C loader clean
	rm -f *.o *.a *.s BOOT.ELF BOOTc.ELF

include $(PS2SDK)/samples/Makefile.pref
include $(PS2SDK)/samples/Makefile.eeglobal
