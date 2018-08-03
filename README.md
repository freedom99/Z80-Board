# Z80-Board
Z80 computer wirewrapped on perfboard

![Image](NKZ80montage-small.png)

This Z80 board was inspired by Grant Searle's "9-chip" design, but using a GAL for most of the glue logic takes the chip count to 6! This board does not yet have the compact flash/IDE interface fitted. For more details of what the board can do, see Grant's original documentation:

Original inspiration: http://searle.hostei.com/grant/cpm/index.html

# Schematic

![Image](schematic.png)

The glue logic in the original design has been replaced with a Lattice GAL20V8; the WINCUPL .PLD source file and ,JED file for the programmer of your choice are provided.

The unit in the photo is powered via the USB-to-TTL adapter, drawing a current of about 170mA with the following components:

Mostek MK3880N (4Mhz Z80 CPU)
Zilog Z80SIO/0 (Z8440AB1)
TMS27C128 EPROM
HM628128 64K SRAM
74HCT00 Quad NAND gate - this MUST be an 74HCT part; the clock circuit is not likely to work with anything else (74LS, HC etc.)
Lattice GAL20V8

Subtituting CMOS parts for the CPU and SIO would reduce supply current. If you choose to use a separate 5V support for the board, remember to keep the GND/0V line of the USB-TTL adapter connect, but disconnect its 5V line - do not try to use two poer sources at the same time.

You may find that the USB-TTL adapter resets when plugged into the board; this seems to be due to the inrush current. 

Because 4MHz parts were used to test the design, this board is fitted with a 3.6864Mhz crystal and the serial interface runs at 57600BPS. If faster spec parts are used then the board should run at the original clock speed of 7.3728Mhz, with a serial speed of 115200BPS. You might get away with overclocking a 4Mhz Z80 CPU (for a while at least!), but the SIO chips are more fussy. 

