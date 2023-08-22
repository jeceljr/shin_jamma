# SHIN_JAMMA FPGA board interface standard version 1

## Files

An FPGA based board named "board" will have three files associated with it:

- board.v: implements the actual adaptor component
- board.md: documents the different options available
- board.ucf, board.xdc, board.qsf: constraint file defining which FPGA pins are connected to which parts of the board

[file relationship](files.svg)

## System Pins

clock50MHz, resetn

## AV Pins

left[15:0], right[15:0], audioclk

green[9:0], red[9:0], vsync, hsync, blue[9:0], pixelclk

## Player Pins

p1select, p1start, p1up, p1down, p1left, p1right, p1button1, p1button2, p1button3, p1button4

p2select, p2start, p2up, p2down, p2left, p2right, p2button1, p2button2, p2button3, p2button4

For mouse or trackball up, down, left and right become Ydir, Yclk, Xdir and Xclk respectively.

## Keyboard Pins

strobe, key_din[7:0]

## Simple I/O Pins

switch[15:0], led[15:0], seg[63:0]

## External Memory Pins

mem_read, mem_write, mem_rdy, mem_addr[31:0], mem_din[31:0], mem_dout[31:0]

## File System Pins

file_read, file_write, file_cmd, file_din[7:0], file_dout[7:0]