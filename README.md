# DE0 Nano SoC - Golden Hardware Reference Design
This is from the system CF contents provided by Terasic. This is provided in the Demonstrations->SoC_FPGA->DE0_NANO_SOC_GHRD.
This can be downloaded from: http://www.terasic.com.tw/cgi-bin/page/archive.pl?Language=English&CategoryNo=163&No=941&PartNo=4

## Building the project

Quartus Prime has been used to build this system. It will produce a .sof file for programming the FPGA.


## Converting programming files

In Quartus, select File -> Convert programming files:
	Select the appropriate output format and supply the generated .sof file. Generating will produce the desired file.
	In our case, the .rbf is preferred.


## Generating the device tree

In the SoC Embedded design console, run the following command to convert the .sopcinfo into a .dts
	sopc2dts --input soc_system.sopcinfo --output soc_system.dts --type dts --board soc_system_board_info.xml --board hps_common_board_info.xml --bridge-removal all --clocks

Compile the device tree into a .dtc with the dtc compiler by running:
	dtc -I dts -O dtb -o soc_system.dtb soc_system.dts


## Copy to SD Card or TFTP server
The two files, soc_system.rbf and soc_system.dtb, are required to program the FPGA when booting.
