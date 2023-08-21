# The shin_jamma interface for FPGA projects

Porting a Verilog project that is working on a specific FPGA board to a different
board can be very time consuming. One solution is to define a standard interface
and implement an adaptator component for each board between the user's project and the actual interfaces implemented by that particular board.

This is similar in spirit to the JAMMA (Japanese Arcade Machine Manufacturers Association) standard interface between cabinets and game boards, which is why
Mario Gazziro suggested the name shin (new) JAMMA. The 56 pin JAMMA connector includes power, analog video and speaker signals as well as button interfaces while this standard just has digital signals, but the functionality is very similar.

## Current Boards

## Planned Boards

- Terasic DE0
- Xess XSA100
- Xilinx ML401
