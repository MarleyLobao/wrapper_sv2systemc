SYSTEMC_PATH = ../systemc/
SYSTEMC_CPP  = ../systemc/wrapper/just_pass_sc2sv.cpp \
               ../systemc/arch/just_pass_arch.cpp

SYSTEMC_SC2SV = ../systemc/wrapper/just_pass_sc2sv.sv
RTL = ../rtl/Just_Pass.sv
TOP = ./top.sv

sim:
	xrun -smartlib -uvm -I$(SYSTEMC_PATH) $(SYSTEMC_CPP) $(SYSTEMC_SC2SV) $(RTL) $(TOP) \
	-smartorder -access +rwc -licqueue -64bit -sv \
	-SC_MAIN_STACKSIZE 0x4000000 -SC_THREAD_STACKSIZE 0x4000000 -sysc -v200x \
	-timescale 1ns/1ps -lic_used -errtcl_verbose -status -mccodegen -mcl -nxmbind -dpi -dpiheader \
	 dpi_header.txt -dpiimpheader dpi_imp_haeder.txt -dumpstack -xceligen on \
	-input shm.tcl

clean:
	rm -rf INCA_libs waves.shm *.so *.o *.history *.log *.key *.err *.trn *.dsn .bpad/ .simvision/ simvision* xcelium.d .reinvoke.sim simv.daidir