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
SKY130_D2_SK1

How to define the width and height of core and Die (W&H calculation) ?
![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/71488e04-201c-4eb3-bce5-1c48af1be321)


	1. Start with basic netlist with launch and capture flipflop having combination circuit in between 
	2. Netlist defines the connectivity between the components

![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/00fd26e3-27f9-4662-8981-0b31a52fb3dd)

	3. Give proper length and width to gates and FF's

![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/3e7dd08f-9588-4368-9977-cf8128727aeb)

	4. To find dimensions of core and die, we will see dimensions of the std cells
	5. Let's give rough dimensions of all of them
Let the area of both FF's and gates(std cells) be 1 sq unit 
![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/ba77796f-0bcf-4ded-88ec-05a32b44a6d5)

	
	6. With help of this, first will remove wires and combine them to get the approx. are for all a a rough dimension ie 4 sq units, it will be min area acquired by the netlist.
![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/333a8a8c-a060-459f-8c32-b5b716e01b29)

	7. For core and die 

![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/e0f79973-78e6-49a4-a5d7-72451119934f)


If 4sq units  occupies full core area then it means core utilization is 100%
	8. Utilization factor is defined as are occupied by netlist / total area of the core
![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/dd64baf6-868b-4af0-901a-3288b2b9d694)

Utilization factor here is 1, means whole core is full and no place to put extra logic
![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/faf2115c-1dcb-49f3-ae11-77479cb7491c)

100% utilization factor is not practical, it is about ~0.5-0.6
	9. Aspect ration is heignt/width, 1 in this case, means chip is square shape othewice its rectangular
![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/cde15936-9ebf-41dc-a1c9-c43cc97fe08f)

	10. Lets take one more eg with different width and height
![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/49c88acd-e40d-4df7-96c4-1a10f5820797)

For the same logic this will give utilization factor of 0.5 and aspect ratio will be 2/4=0.5, 
![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/83af2ad3-beb8-4607-be3a-9d3ab5278859)


Other unused area can be used for routing.

SKY_L2
Preplaced call and defining locations for them

	1. Let's take eg of some combination logic, with 50K gates (say).
	2.  We did not implement this every time as part of main circuit, but we can take this peice and implement separately or granulize this circuit 
![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/5c7e4285-2c44-4aeb-855f-4ef45097a9c7)

Lets try to cut it in 2 parts, 
![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/0e53da9b-6252-47ea-b6e0-32dd23ce16b5)

	3. 2 different blocks will look like,
![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/ec2ed875-a177-4a6d-b821-1284691c4c37)

	4.  let's extend its input and output pins

	![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/422f9e5d-aeb7-4397-a752-24f19757c52e)

LHS has inputs(4) side, RHS has output(1) as per netlist.
	5. This circuitry can we invisible to top netlist and 2 boxes can be separated out, and each can be used separately reused multiple times.
	6. Eg memory, comparator, clock gating cell etc are few IP's where functionality is implemented  once and cells can be used multiple times, these are called preplaced cell as are placed in chip just need to define the location or arrangements of cells before placement and routing. Placement of these cells on top level chip is fixed before P&R so they are called pre placed cells.
	7. These cells are either macros or IPs, implemented once, can be part of any Hardware.
	8. To define location of these, let's say chip LHS is input and RHS is output and we have to place cells/block a,b,c accordingly such that location is well defined. If say we have  these blocks mostly interacting with inputs only so placement will look like below depending on design background and location of these cells can't be moved. 
![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/bd402098-008b-4bfa-a4e8-4b69a2221da8)

	9. We need to surround these cells with decoupling capacitors
DECOUPLING CAPACITORS-
		a. Let circuit below be the part of some block,
	![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/9adc7502-f845-4292-b4f5-b7a14eee1390)

		a. Whenever circuit switches, eg if any AND gate switches  from 0 to 1, some current it needs. As when transition occurs, these is always some capacitance exits which also need to be charged to represent logic 1. This is the derived from power supply to supply necessary current to all logic when switching from 0-->1. Similarly, when 1-->0  switching, Vss should also take that amount of charge due to capacitance discharge. 
		b. In reality, when power flow to circuit from wires, there is drop in wire as wires have physical dimensions so have R, L, C associated with them repeated throughout. So multiple V drops occurs. So 1V become ~0.7V, makes charging not to go beyond 0.7V and 0.7 should be within noise margin, have specific regions for logic 0 and 1 
	![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/532d3555-4bc0-425f-8042-3dc6a11f655e)

	
		c. Logic 1 is not guaranteed if have large distance from supply
		d. This problem is solved using decoupling capacitor.
		e. This capacitor is filled by charge and V across it is equivalent to power supply (1V in this case)
		![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/eac6d5b7-01c4-4eeb-bb44-e0b2fc655952)

		f. Whenever circuit switches Cd send charge to circuit.
		g. When switching activity happens it loses its some charge to circuit, when no switching, it gets charged from supply. It looks like, 
	![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/ef016b67-5d90-4022-83d5-ca9178eaccbb)

	i.e takes care of local communication. 
	
POWER PLANNING:
		a. Lets keep the circuitry as black box, say macro.
	![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/897e4b03-4837-4712-a77e-d17d1d4e131a)

		b. If this macro is repeated multiple times (4) and also some circuit exists at boundaries also.
	If have driver sending signal to load we need to make sure, that complete line maintains same signal so that load receives the same signal. 
	![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/df4cab2b-c2ab-44b9-a5c3-9e64a8b5c484)

	
		c. Assume Driver is connected to load by 16 bit bus
	![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/ae515e78-3c26-4338-8267-b1098c016800)

	If driver sends 0-->1 signal, it should maintain same level to make sure load receives the desired levels. As no decoupling capacitor is not feasible to be added everywhere, this has to be taken care from power supply. 
	1--> capacitor charged to VDD
	0--> capacitor discharged to GND
	![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/eb74d485-217e-497f-b5b0-cfa541a52c5f)

	
	Lets say all cap to be discharged 1-->0, GND will have some bump (GROUND BOUNCE) as we have single ground line for all 16 bits, and all have to be discharged at the same time, If bump size exceed Noise margin level it may be undefined sate, 1 or 0. Since all C's now discharging, 
	![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/547c7267-99a7-4f0a-b789-75bafb673e55)

	Similar is the case for charging as all need to be charged at the same time and as only single line, so voltage drop occurs.
	![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/30e209f9-d2a1-4844-bf83-32509e0bc87b)

	
		d. If multiple power supply exists, such problem can be resolved as it will look to nearest power source. As shown by multiple Vdd, Vss lines
	![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/79db7989-99d4-43ff-b5ed-2d52c86a7367)

	ie called mesh and process is called as power planning 
	![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/b6cf91a7-52aa-49c4-b534-69e9697d2e5a)

	
	SKY L5:
	
	PIN PLANNING
	1. Lets take 2 small circuits to implement derives by 2 different clocks sources also some preplaced cells (Block a, b), making 4 inputs (Din1, Din2, clk1, clk2) and 3 outputs(Dout1, Dout2, ClkOut).
![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/71c8ec58-5fa2-429f-8268-72feb12d104f)

	2. Lets say 2 more sections of same circuit of input Din3, Din4 output Dout3, Dout4 and clocks clk1 and clk2 present preplaced cell (Block c), making complete design looks like below

![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/9cd9a142-1206-4141-a95a-9dd822cd832a)

	3. Making proper netlist connectivity, it looks like below and is defined in verilog/VHDL and knows as netlist  
![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/48f4d078-8919-4391-9b3a-d004d4b22a0e)

	4. Lets place input on LHS and output RHS of chip we are planning to design 
![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/0c7b01f3-e47c-4365-9af6-325b5037ed2b)

-Pin information exists between core and die. 
-Ordering of inputs and output are random, depending on multiple reasons
-Handshaking between front and backend teams are required to finalize this.
-Clocks are more bigger then data as clock sends continues signals, and drive all chip so need least resistance path for clocks.
-No cell should be places in this areas. We block this area for P&R by logical cell placement blockage.
![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/80943a72-3baa-4eb7-87d4-b069bfd7bf24)

-Now after this its ready for placement and routing.
-Standard cell placement happens in placement stage.
SKY L6:

PIN PLANNING
	1. There are many switches for floor planning in OPENLANE
	2. Switches are in README.md file in directory ../o/configuration
	3. In readme file you will get variables required/set. Below shows the switches for Floorplan  
![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/06024a8e-2f21-4254-ac39-35a7c0a4491a)

	4. Below are placement switches 
![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/916ff875-147b-48dc-96a2-61bf8f2c6684)

	5. Here design/cells is/are spread as for P&R we need to start with congestion analysis. 
	6. To set these switches so to specific TCL files eg floorplan.tcl
![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/c24d3cd6-6055-435e-b1c6-d3f766f2e5d7)

Here setting thses values
FP_IO_MODE shows how we want pin placements around the core and 1 --> pin placement is equidistant and 0--> pin placement is not equidistant.
These files shows the system default settings
	7. In  ../openlane/designs/picrorc32, if you open config.tcl, you can see set parameters.
![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/326decb4-927c-45d7-93f3-82ee7434f670)

	8. If core utilization is 65%, IO VERTICAL metal as 4 and horizontal metal is 3, in openlane its +1 ie Vertical metal is 5 and horizontal is 4.
	9. Priority is 
	system default < config.tcl < <variant>.tcl 
	10. In <variant>.tcl, we can see core utilization is 35
	![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/56f3da36-f6d5-45f2-acb5-f235e7b07c2b)

11. Run floorplan using command run_floorplan. After successful run you will see below snapshot
![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/6b8da37f-9ba2-4c1f-bf45-bc12bd25fbfc)

	12. Now we will check whether all set switches from config did not took over defaults from log in ../picorv32a/runs/<date_time>/logs/floorplan in file ioplacer.log

	13. To view the floor plan, go to ../results/floorplan, open def file (design exchange format) where you can see all information. It also has die area, 

(0 0) lower left x value and lower left y value
(660685 671405) upper right x and upper right y value
Units =1000 Micron, 1 micron is 1000Database units so 660685/1000=660.685 mm is dimention
	14. To see layout use magic with command 

To see 
	


SKY130_D2_SK2:
P&R stage of PD flow
	1. Binding the netlist with the physical cell.
		a. NOT gate is triangle but in reality it has some width and height.
		

		b. Similar is the case for all the components of netlist, all have specific width and height.
		
			
		c. These things are present in shelves called library. Library also have the information of timings of these components in huge set
		d. Library is categorized as 2 subparts
			i. Of only shape and size
			ii. Of only timings
		e. So library has width info, delay info and required information like conditions of flip flop outputs. It also has various shapes of these gates. Ey showing biggersizes from LHS to RHS 
			
		f. After giving proper shape and sizes to all gates, next is to take them and place on floor plan.
	2. As per of now we have the proper floorplan with IO defines and placed, netlist, shape and size of all gates.
	3. Now we need to place this on floor plan
	4. Now we need to place the netlist on the floorplan
	
		
	5. As we have preplaced cells on floorplan, placement will make sure these locations are intact and no cell is placed in this area
	
	6. Need to take physical view of netlist and place on the floor plan.
	7. Logic one placed in straight line with some space, logic 2 is placed together with minimal delay between cells, 3rd is placed diagonally as din3 and din4 distance is higher. Similarly 4th is placed as shown in color codes of fig below
	
	8. Now after placement we have to solve for distance problem. So need to do some optimization. Before routing we need to estimate the capacitances. 
	9. Din 2 to FF1 (yellow) length is huge so resistance exists.
	10. So will try to place something in between so that signal go phase 1 phase and sent to FFI
	11. Its called signal integrity.
	12. It makes use of repeaters ie are buffers reconditions original signal and create new signal and send it forward.
	13. More repeaters more loss of area.
	14. Din 1 to FF1 SI is maintained, FF1 to 1 also OK, 1 to 2 also OK, 2 to FF2 also OK.
	15. Slew depends on capacitor value. If high cap value, high charge required to charge capacitor so slew will get impacted
	
	
	16. Din 2 is far from FF1, slew (signal transition goes beyond transition limit so signal got impacted) so need to break huge length using repeaters. 
	
	17. FF1 to FF2 circuited follows abutment as circuit works at very high speed so need to minimize delay. 
	18. Will try to optimize the placement of other 2.
		a. For circuit 3, Din 3 at sufficient distance from FF1, FF1-->1 also no buffer, 1-->2 also not required but based on slew analysys, distance between 2 and FF2 is high so need buffer.
		
		b. For circuit 3, its tricky, distances are high, so need to place buffers, but some logic is also there where we can't place buffer. Cross connection can be taken on the different layers.
		
		
	19. Now need to check for correctness. We have to check the data path considering clock is ideal.


NEED TO CHARACTERIZATION:
	1. Logic synthesis is first step to do this-Functionality coded in RTL converted first to Legal hardware is called logic synthesis. Output is representation. in form of logic gates and flipflops.
	2. Import netlist and decide the size of core and die depending on the output of logic synthesis.
	3. After floor planning we place the logic cells and place on chip making sure initial timing is met.
	4. Next is CTS. If need clock to be spread throughout we need clock tree synthesis.
	5. Routing, if want to rout 2 cells, it depends on cell properties taken care into.
	6. STA tells of max achievable frequency of circuit, setup and hold time violations.
	7. One thing common among all stages is GATE/CELLS, where are library Characterization is important. 
	8. Gate has to be represented in Understandable form to EDA tool.
	9. In openlane placement occurs in 2 steps, one is global placement other is detailed placement.
	10. Legalization only happens in detail placement
	11. Legalization is important for timings. It means standard cells are placed in std cell rows and abutted with each other. 
	12. Global placement reduces the wire length.
	13. Run placement by using run_placement.
	14. Objective is to converge overflow value. Ie happens when overflow value reduces.
	15. HPWL: Half parameter wave length.
	16. You can see placement data like below

	17. Placement of standard cell in std cell rows are shown as below

	18. Let the placement and routed design be 

	19. Library is a place where we keep all macros and Ips
	20. CELL DESIGN FLOW

	21. We get inputs from foundry.
	22. User defined specifications:
	-cell width
	-supply voltage
	-metal layers
	-pin locations
	23. Designs step
	-Circuit design: involves 2 steps 1. Implement function 2. model PMOS & NMOS with specific W/L ratios. Are based on spice simulations. It will give CDL file.
	-Layout design: Implement circuit as per PMOS and NMOS connections. Includes PMOS AND NOMS network graph. After network path we need Euler's Path 
	
	After euler path needs stick diagram as shown below
	
	Convert this stick diagram into layout while adhere to foundry DRC rules and user rules.
	-Characterization : extract parasitic and characterize in in term of timing , before characterization we have GDSII (layout file), LEF is having width and height of cell and extracted spice netlist has L &R values of each element in layout.
	
	After this last step is characterization, where we get timing noise and power information & output of this is timing,noise ,power .libs files
	
	
	
	
	
	CHARACTERIZATION FLOW:: 
	a. The layout of buffer be
	
	b.  we have description of buffer and spice extracted netlist 
	

	c. 
	d. Flow be:
		a. Model file reading
		b. Reading extracted spice netlist
		c. Recognize behavior of buffer
		d. Read subcircuit of invertor
			
				
			
			
			
		e. Attach necessary power supplies
		f. Apply stimulus 
		g. Provide necessary output capacitances
		h. Provide necessary simulation steps
	e. Feed all (a-h) in form of characteristics file to GUNA which will give timing noise and power model




SKY130_D2_SK4::
	1. TIMING CHARACTERIZATION:
	a. Will see syntax for GUNA software, will see according to below diagram
	

	b. We plotted waveforms at U1 & U2.
		a. Red is first invertor, blue is second
		
		Slew low defined lower side values colsed to 0 power supply. Typical value is 20-30%
		Slew_high_rise_thr also required with this to get sleits 20%power from max power supplyw
		
		Similar definitions also applies for falling waveforms
		
		
		
		To calculate slew we need these
		b. Let red be input, blue be output and stimulus is applied. Output is taken from buffer.
		In_rise_thr is threshold of delay is 50% of slew waveform 
		
		Similarly out rise threshold 
		
		Similar is the case for fall waveforms.
		
		
		
		Any input has 2 delays, rise and fall delays.
		Based on these 8 terms, slews and propogation etc are calculated.
		
		PROPOGATION DELAY::
		a. It may lead to unexpected results
		b. Will see wrt this waveform 
			
			
		c. Way to calculated is shown in diagram below
			
			
		d. If input waveform and output waveform be below with 50% threshold with mentioned values
			
			3.23-3.207=0.023  
		e. Delay is 23micro sec. here thresholds are 50%. If somehow threhold pont moves down, time in rise be 3.263 and fall threshold be 3.221ns. So we get negative delay. If poor choice made for threshold selection we get negative thresholds
			
			
		f. If we have correct threshold values then also possibility is there of negative threshold. If 2 invertors/buffers are far apart, then as per input waveform we can slew is very high.
			
			Output come before input, we get negative delays. This is problem with circuit design.
			
	c. Transition time:
		a. Slew of waveform of rising wave, 
		
Similar slew fall wave, 
		
		b. 20% of VDD is general value for low rise and fall
		c. 80% of VDD is general value for high rise and fall
			
		d. Slew be high - low, will give below values
			
	

