# SHIN_JAMMA FPGA board interface standard version 1

## Files

An FPGA based board named "board" will have three files associated with it:

- board.v: implements the actual adaptor component
- board.md: documents the different options available
- board.ucf, board.xdc, board.qsf: constraint file defining which FPGA pins are connected to which parts of the board

![file relationship](files.svg)

## System Pins

clock50MHz_o, resetn_o

## AV Pins

left_i[15:0], right_i[15:0], audioclk_i

green_i[9:0], red_i[9:0], vsync_i, hsync_i, blue_i[9:0], pixelclk_i

## Player Pins

p1select_o, p1start_o, p1up_o, p1down_o, p1left_o, p1right_o, p1button1_o, p1button2_o, p1button3_o, p1button4_o

p2select_o, p2start_o, p2up_o, p2down_o, p2left_o, p2right_o, p2button1_o, p2button2_o, p2button3_o, p2button4_o

For mouse or trackball up, down, left and right become Ydir, Yclk, Xdir and Xclk respectively.

## Keyboard Pins

strobe_o, key_d_o[7:0]

The strobe signal goes high to indicate an updated value on key_d and remains
high for at least 8 cycles of the 50MHz clock. key_d[7] is low to indicate a
key press and high for a key release, while key_d[6:0] is either the lower case
ASCII character associated with the key or a special code.

## Simple I/O Pins

switch_o[15:0], led_i[15:0], seg_i[63:0]

Up to eight 7 segment displays are supported, which are actually 8 segments
when the dot is included. The segment number plus 8 times the digit number
is the bit to be illuminated.

## External Memory Pins

mem_read_i, mem_write_i, mem_rdy_o, mem_addr_i[31:0], mem_d_i[31:0], mem_d_o[31:0]

Up to 4GB of external memory may be mapped to this interface. Any writes to
unmapped addresses are discarded while any reads from such regions return zero.

SDRAM controllers, specially for recent DDR variations, can be very complex and
even include whole microcontrollers. They might take up more FPGA resources than
the user's project.

## File System Pins

file_read_i, file_write_i, file_cmd_i, file_d_i[7:0], file_d_o[7:0]

When file_cmd is high data is written to the command register or read from
the status register. That signal is low for normal data transfers.

Bits 7:4 of the command register indicate the selected command to be executed
while bits 3:0 select between up to 16 different files.

| 7:3 | command | data | operation |
|-----|---------|---------|-----------|
| 0 | NOP | | does nothing, but will cancel any command in progress |
| 1 | OPEN | string0 | will open the named file |
| 2 | CLOSE | | closes the selected file |
| 3 | READ | | returns the next byte from the file |
| 4 | WRITE | byte | writes the byte at the next position in the file |
| 5 | SEEK | 4 bytes | positions the file at the indicated little endian number |

The READ and WRITE commands remain executing until another command is given.

Bit 7 of the status register is high if the last command caused an error.

Bit 6 of the status register is high if there is a command in progress.

Bits 5:0 indicate which error happened or how many bytes are available for
reading or how much space is available for writing. The maximum number of 63
means "63 or more".

This high level interface is not too different from what some late 1980s
microcomputers (like the Atari 800 or the Commodore Pet) did. This does require
considerable FPGA resources to implement compared to a simple SD Card interface.
By default this interface simply returns an error for all commands.

