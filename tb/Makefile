SYSTEMC_HOME = /usr/local/systemc232
PATH_PARA_O_ARQUIVO_SYSTEMC = ../SystemC

# IFS = ./sqrt_if.sv

# PKGS = ./pkg.sv

RTL = 	../rtl/Just_Pass.sv 

SYSTEMC_CPP = 	../SystemC/wrapper/just_pass_sc2sv.cpp \
		../SystemC/arch/just_pass_arch.cpp

# SYSTEMC_H = 	./ponte_sc2sv.h 


run: all

all:
	xrun -smartlib -uvm $(SYSTEMC_CPP) $(RTL) -smartorder -access +rwc -licqueue -64bit -sv \
	-SC_MAIN_STACKSIZE 0x4000000 -SC_THREAD_STACKSIZE 0x4000000 -sysc -v200x \
	-timescale 1ns/1ps -lic_used -errtcl_verbose -status -mccodegen -mcl -nxmbind -dpi -dpiheader \
	 dpi_header.txt -dpiimpheader dpi_imp_haeder.txt -format off -dumpstack -xceligen on \
	-I$(SYSTEMC_HOME)/include -L$(SYSTEMC_HOME)/lib-linux64 \
	-I$(PATH_PARA_O_ARQUIVO_SYSTEMC)/arch\
	-I$(PATH_PARA_O_ARQUIVO_SYSTEMC)/arch/just_pass_arch.cpp \
	-input shm.tcl Topo.sv  

create:
	@echo "database -open waves -shm" >> shm.tcl
	@echo "probe -create  Topo -depth all -all -memories -shm -database waves" >> shm.tcl
	@echo "run" >> shm.tcl
	@echo "exit" >> shm.tcl
	
waves: 
	simvision waves.shm	

simulate: all 

synthesize:
	rc -f rtl.tcl

clean_reports:
	rm -r reports*
clean:
	rm -rf xcelium.d INCA_libs xrun.* *.shm *.dsn *.trn *.ucm ncvlog_*.err imc.key .simvision
	rm -r  mapped* rc* fv libscore_work script
