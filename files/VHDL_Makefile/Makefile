VHDFILE =          <+VHDFILE+>
TBFILE  =          <+TBFILE+>

all : compile

compile : $(VHDFILE).vhd
	ghdl -a $(VHDFILE).vhd

compileall : $(VHDFILE).vhd $(TBFILE).vhd
	ghdl -a $(VHDFILE).vhd
	ghdl -a $(TBFILE).vhd
	ghdl -e $(TBFILE)
	ghdl -r $(TBFILE) --vcd=$(TBFILE).vcd

sim : compileall
	gtkwave $(TBFILE).vcd
