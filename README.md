![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/4c078719-4a26-4775-92e7-5957d03b9edc)SKY130D1SK1
Package : The outer 256 pin package(for eg), pin locations are driven by board
Pads : Package is connected to chip through pads, any signal go too and fro the chip is through the PADS only.
Core: Has all the logic ( RISC V SOC, Foundry Ips etc )in it
![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/fb62c485-c93c-49dd-af67-274bad5b8af4)

Die is manufactured on Si wafer.
Foundry IP : IP need some specific technique to be ready.
Macro : Pure digital logic.
Interface files are used to communicate with Foundry.

SKY L1
![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/1e8a2727-7485-4e0d-b055-4db11738bd27)


ISA : Instruction set architecture, used to interact with computer.
For C Program to run on HW with shown layout(chip interior), it  required to be first compiled in  assembly language program(RISC V assembly language program) which is then converted in  machine language (binary). Finally these bits gets executed in this layout.

Interface between the RISC V arch and layout is HDL. We need to implement this RISC V specs using some RTL.

From RLT to layout it is RTL2GDS Flow.
![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/720ce3c8-311e-4080-ad80-50f5a184c9fb)



SKY_L2 : 

How applications like Firefox runs on hardware ?
Application software enters into system software which converts it to binary language.
Major components of system software are OS, compiler, assembler.
OS handles IO operations and memories and take app to assembly language program and then to Machine language, that can be handled by HW. 

C/C++/java --> Compiler --> RISCv Format (.exe file) (depends on instruction set)-->Assembler takes this and converts to binary numbers.
![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/348ff31d-c19c-42e3-8e95-720f692ac13a)


Instruction set arch is interface between compiler and assembler
Assembler output  is in Binary.

SKY130_D1_SK2:
![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/f177d963-60b9-4f7c-b414-cb3cdaea97fc)


PDK: it is a process design kit & is a interface between fab and design.
![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/1b1fe13e-e82e-4eba-9e78-5c19c0c3064d)

For open source ASICS we need below tools 
![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/8ffecf0b-caf2-476d-90f0-afd0dcc36ccc)

SKY_L2:
![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/c33a8684-cf48-40b2-8410-b267422eaa02)

These are some major implementation steps.
![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/d8a79890-ae77-4cba-816d-13bf3f180753)

![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/f0470e74-ea7d-4964-a09c-badc19f442f1)
![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/549119e9-589c-424f-b7d2-0dc8f673265d)






SKY130_DY1_SK3:
Getting familiar to open source EDA TOOLS

![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/32d3ee71-90f7-462f-b162-9352acf62c07)

	1. Open terminal in UBUNTU
	2. Change working directory to work/tools/openlane_working_directory/openlane
	3. There you will see flow.tcl file by using ls -ltr.
	4. Type "docker" in terminal,
	5. Source flow.tcl in interactive mode by typing ./flow.tcl -interactivep it will shows the above view.
	6. Use "package require openlane 0.9".
	7. You can see already build designs present in designs in directory work/tools/openlane_working_directory/openlane/designs.
	8. Before running the synthesis, need to setup data for design, as only few files are there 
	9. ![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/e1dbc7a2-b8af-4ff3-9f83-ed2da05ba986)

	
	10. To setup, use prep -design picorv32a
	11. It will merge files and we don’t need different files it will be shown like below in terminal 
	
	![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/1f4093fd-3523-4019-a61c-dd17f37ffb6b)

	12. A new folder named Runs will come into the directory
![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/d855d17d-96d1-4a3a-97fb-a52bcc3cd2f6)

12. To view TLEF information, go to directory  work/tools/openlane_working_directory/openlane/designs/picorv32a/runs/<date>/tmp,  and open merge.lef. You will get layer and wire and cell level information.
	![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/39eb9505-8f70-49f1-95a4-04d6a0f7ec71)



	2. Report and result will have information after runs.
	3. Conf.tcl tell info of parameters taken during the run.
![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/d908fce0-fe82-4925-90e2-781f0e8fcf58)

	4. In open lane we can make changes in the run. Parameters like core utilization can be changed.
	5. Further run the synthesis by run_synthesis in Openlane prompt. It will run BIOS Synthesis and ABIS run (to get chip module area).
![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/9a7083bc-a2c5-47a8-9f04-f703380dc799)

	6. STA has been done, synthesis and ABIS run also get completed, we can see chip module area
![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/477474d7-72d8-40ce-9723-39a63fc41d68)


	7. Flop ratio = No. of D Flip flop/total no. of cells
	8. So Fxtp= 1613
![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/5ab4af56-9a88-4999-96f5-3702bdad1b06)

	And, total no. of cells=14876 
![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/46ef3c39-866a-4c9e-8428-442e7f617375)

	
	Flop count = 1613/14876=0.1084*100= 10.8%
	
13. To see run result for synthesis, go to directory  work/tools/openlane_working_directory/openlane/designs/picorv32a/runs/<date>/results/synthesis. It contains synthesized netlist
14. You can view synthesized netlist. 
![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/db525aa7-045e-4efc-b2c6-5622dd122c95)


15. To see timing report go to reports folder, where all reports exists

DAY2
