SYSTEMC_PATH = ../SystemC/
SYSTEMC_CPP = ../SystemC/wrapper/just_pass_sc2sv.cpp \
		       ../SystemC/arch/just_pass_arch.cpp

RTL = ../rtl/Just_Pass.sv
TOP = ./Topo.sv

sim:
	xrun -smartlib -uvm -I$(SYSTEMC_PATH) $(SYSTEMC_CPP) $(RTL) $(TOP) -smartorder -access +rwc -licqueue -64bit -sv \
	-SC_MAIN_STACKSIZE 0x4000000 -SC_THREAD_STACKSIZE 0x4000000 -sysc -v200x \
	-timescale 1ns/1ps -lic_used -errtcl_verbose -status -mccodegen -mcl -nxmbind -dpi -dpiheader \
	 dpi_header.txt -dpiimpheader dpi_imp_haeder.txt -dumpstack -xceligen on \
	-input shm.tcl

clean:
	rm -rf INCA_libs waves.shm cov_work/ *.history *.log *.key mdv.log imc.log imc.key ncvlog_*.err *.trn *.dsn .bpad/ .simvision/ simvision* xcelium.d .reinvoke.sim simv.daidir *.so *.o *.err