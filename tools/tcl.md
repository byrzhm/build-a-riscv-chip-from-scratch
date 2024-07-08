# Tcl

## Set up

Add `<install_path>/Vivado/<version>/bin` directory to the PATH.
Suppose the vivado is installed in linux at directory `/tools/Xilinx/Vivado/2024.1`, append the following line to `~/.bashrc` and then run `source ~/.bashrc`.

```sh
export PATH="/tools/Xilinx/Vivado/2024.1/bin:$PATH"
```

Now, when you enter `vivado` at the command prompt, it will automatically runs `vivado -mode gui` to launch the Vivado IDE.

Now, enter `vivado -mode tcl`. It will launch an interactive Tcl command shell. You can enter `start_gui` at the tcl prompt to launch the Vivado IDE and open the Vivado tool GUI.

## Elaborate

```tcl
source ./target.tcl -notrace

# Read Verilog source files
if {[string trim ${RTL}] ne ""} {read_verilog -v ${RTL}}

# Read user constraints
if {[string trim ${CONSTRAINTS}] ne ""} {read_xdc ${CONSTRAINTS}}

# Read memory initialization files
if {[string trim ${MIFS}] ne ""} {read_mem ${MIFS}}

# Only elaborate RTL (don't synthesize to netlist)
synth_design -top ${TOP} -part ${FPGA_PART} -rtl

# write_checkpoint doesn't work:
# Vivado% write_checkpoint -force z1top_post_elab.dcp
# ERROR: [Common 17-69] Command failed: Checkpoints are not supported for RTL designs

# Open the schematic visualization
start_gui
```

## Synthesis

```tcl
source ../target.tcl -notrace

# Read Verilog source files
if {[string trim ${RTL}] ne ""} {read_verilog -v ${RTL}}

# Read user constraints
if {[string trim ${CONSTRAINTS}] ne ""} {read_xdc ${CONSTRAINTS}}

# Read memory initialization files
if {[string trim ${MIFS}] ne ""} {read_mem ${MIFS}}

synth_design -top ${TOP} -part ${FPGA_PART}

write_checkpoint -force ${TOP}.dcp
report_timing_summary -file post_synth_timing_summary.rpt
report_drc -file post_synth_drc.rpt
report_utilization -file post_synth_utilization.rpt
write_verilog -force -file post_synth.v
write_xdc -force -file post_synth.xdc
```

## Implementation

```tcl
source ../target.tcl -notrace

open_checkpoint ${ABS_TOP}/build/synth/${TOP}.dcp

if {[string trim ${CONSTRAINTS}] ne ""} {read_xdc ${CONSTRAINTS}}

opt_design
place_design
write_checkpoint -force ${TOP}_placed.dcp
report_utilization -file post_place_utilization.rpt
phys_opt_design
route_design

write_checkpoint -force ${TOP}_routed.dcp
write_verilog -force post_route.v
write_xdc -force post_route.xdc
report_drc -file post_route_drc.rpt
report_timing_summary -warn_on_violation -file post_route_timing_summary.rpt

write_bitstream -force ${TOP}.bit
```

## Program

```tcl
source ../target.tcl -notrace
open_hw_manager

connect_hw_server -url localhost:3121 -allow_non_jtag
current_hw_target [get_hw_targets */xilinx_tcf/Digilent/*]
set_property PARAM.FREQUENCY 15000000 [get_hw_targets */xilinx_tcf/Digilent/*]
open_hw_target

current_hw_device [get_hw_devices xc7z*]
refresh_hw_device -update_hw_probes false [lindex [get_hw_devices xc7z*] 0]
set_property PROBES.FILE {} [get_hw_devices xc7z020_1]
set_property FULL_PROBES.FILE {} [get_hw_devices xc7z020_1]

# Hack to expand ${ABS_TOP} and ${TOP} properly, running set_property directly doesn't expand these variables
set set_cmd "set_property PROGRAM.FILE \{${ABS_TOP}/build/impl/${TOP}.bit\} \[get_hw_devices xc7z*\]"
eval ${set_cmd}
program_hw_devices [get_hw_devices xc7z*]
refresh_hw_device [lindex [get_hw_devices xc7z*] 0]

close_hw_manager
```

## References

* [Vivado Design Suite Tcl Command Reference Guide](https://docs.amd.com/viewer/book-attachment/a2qiEEk26YWwT25rSFVbmg/NprkEJ~T_~hEobkp7CgVRA)
