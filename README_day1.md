Getting familiar to open source EDA TOOLS
![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/43011131-5ea9-4c11-8c77-625ed9b754b2)


	1. Open terminal in UBUNTU
	2. Change working directory to work/tools/openlane_working_directory/openlane
	3. There you will see flow.tcl file by using ls -ltr.
	4. Type "docker" in terminal,
	5. Source flow.tcl in interactive mode by typing ./flow.tcl -interactivep it will shows the above view.
	6. Use "package require openlane 0.9".
	7. You can see already build designs present in designs in directory work/tools/openlane_working_directory/openlane/designs.
	8. Before running the synthesis, need to setup data for design, as only few files are there 
	9. 
	![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/854bba13-4b6d-4924-95da-3fa7e2c9d348)

	10. To setup, use prep -design picorv32a
	11. It will merge files and we don’t need different files it will be shown like below in terminal 
	![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/afa94ca4-d5bb-4e44-8e8a-d3fdba481826)

	
	12. A new folder named Runs will come into the directory
![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/3a391d8f-858d-493b-85a4-e6376aaeffc0)

12. To view TLEF information, go to directory  work/tools/openlane_working_directory/openlane/designs/picorv32a/runs/<date>/tmp,  and open merge.lef. You will get layer and wire and cell level information.
	
![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/9e6f90cb-23d7-4d5d-8f40-3d5eb955fde9)


	2. Report and result will have information after runs.
	3. Conf.tcl tell info of parameters taken during the run.
![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/647cb2b5-2e53-45b7-b506-c4df13b8f22b)

	4. In open lane we can make changes in the run. Parameters like core utilization can be changed.
	5. Further run the synthesis by run_synthesis in Openlane prompt. It will run BIOS Synthesis and ABIS run (to get chip module area).
![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/fba2e462-5dea-4f0a-91fb-bf6d787f0372)

	6. STA has been done, synthesis and ABIS run also get completed, we can see chip module area
![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/da9d65e6-a293-4eec-92ee-7be2e23446d7)


	7. Flop ratio = No. of D Flip flop/total no. of cells
	8. So Fxtp= 1613
![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/35dc213c-27b9-45c6-a1d2-2d7f60c17f1b)

	And, total no. of cells=14876 

	![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/9b38e088-1495-43eb-aae5-a56a5a9c8a6f)

	Flop count = 1613/14876=0.1084*100= 10.8%
	
13. To see run result for synthesis, go to directory  work/tools/openlane_working_directory/openlane/designs/picorv32a/runs/<date>/results/synthesis. It contains synthesized netlist
14. You can view synthesized netlist.
15. ![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/1ab84956-bb32-4b9d-833b-7bb33d964b4e)



16. To see timing report go to reports folder, where all reports exists
![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/efe51ba4-49e9-4efb-b5bc-d1d96ecd2fe3)


DAY 2
PIN PLANNING
	1. There are many switches for floor planning in OPENLANE
	2. Switches are in README.md file in directory ../o/configuration
3. In readme file you will get variables required/set. Below shows the switches for Floorplan
![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/0b312735-8a63-41fd-95ff-e8559a35272f)
4. 
Below are placement switches 

![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/95b5a573-fe91-4c39-a476-b16294dc0a5d)
	5. Here design/cells is/are spread as for P&R we need to start with congestion analysis. 
6. To set these switches so to specific TCL files eg floorplan.tcl
![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/c0097eaf-c3d6-4fe1-8254-78fd20fc417a)
Here setting thses values
FP_IO_MODE shows how we want pin placements around the core and 1 --> pin placement is equidistant and 0--> pin placement is not equidistant.
These files shows the system default settings
In  ../openlane/designs/picrorc32, if you open config.tcl, you can see set parameters
![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/32652fd3-1d16-4395-8796-d98905985623)

	8. If core utilization is 65%, IO VERTICAL metal as 4 and horizontal metal is 3, in openlane its +1 ie Vertical metal is 5 and horizontal is 4.
	9. Priority is 
	system default < config.tcl < <variant>.tcl 
In <variant>.tcl, we can see core utilization is 35
![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/6829ecf3-e03b-4dfb-854b-155a736cdd0b)

10.  Run floorplan using command run_floorplan. After successful run you will see below snapshot.
![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/ba0908d1-18fd-4ec5-abe0-4fc048f28768)

Now we will check whether all set switches from config did not took over defaults from log in ../picorv32a/runs/<date_time>/logs/floorplan in file ioplacer.log
![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/3ae3900d-7693-4df4-9465-e74cb83aa1a2)

To view the floor plan, go to ../results/floorplan, open def file (design exchange format) where you can see all information. It also has die area,

![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/bbd847e2-57e4-4ae1-9b12-a2eb8fe04055)
![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/8990525d-66f6-499b-aa61-f22a61f75fd1)


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
You can see placement data like below!
![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/2d5f99ff-2fe0-44ee-93ac-31724435b7a9)
Placement of standard cell in std cell rows are shown as below![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/56ed4972-be2d-4f52-93bf-2cf7a85e2ab7)
![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/90756745-dc90-4438-aa99-7a0e005e45a1)
Library is a place where we keep all macros and Ips


CELL DESIGN FLOW

![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/61aff43e-3296-4b1d-a42e-bb0e9b44f6aa)
	21. We get inputs from foundry.
	22. User defined specifications:
	-cell width
	-supply voltage
	-metal layers
	-pin locations
	23. Designs step
	-Circuit design: involves 2 steps 1. Implement function 2. model PMOS & NMOS with specific W/L ratios. Are based on spice simulations. It will give CDL file.
-Layout design: Implement circuit as per PMOS and NMOS connections. Includes PMOS AND NOMS network graph. After network path we need Euler's Path 

	CHARACTERIZATION FLOW:: 
The layout of buffer be!
![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/a89b102d-8b9c-4af1-8195-195956ad7715)
 we have description of buffer and spice extracted netlist 
 ![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/4a610763-de32-49cc-86cd-5b27c05e7f90)
	d. Flow be:
		a. Model file reading
		b. Reading extracted spice netlist
		c. Recognize behavior of buffer
		d. Read subcircuit of invertor
		e. Attach necessary power supplies
		f. Apply stimulus 
		g. Provide necessary output capacitances
		h. Provide necessary simulation steps
Feed all (a-h) in form of characteristics file to GUNA which will give timing noise and power model

	1. TIMING CHARACTERIZATION:
Will see syntax for GUNA software, will see according to below diagram![image]![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/09f0ba2b-e2af-4bc2-a1d3-8175d90b5141)

	b. We plotted waveforms at U1 & U2.
		a. Red is first invertor, blue is second
		![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/5c0fc9f8-d253-41d7-890b-6ffc371ec85d)

		Slew low defined lower side values colsed to 0 power supply. Typical value is 20-30%
		Slew_high_rise_thr also required with this to get sleits 20%power from max power supply
  ![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/478200f5-d3a7-4688-912f-f9231c29e713)

		
		Similar definitions also applies for falling waveforms
		![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/81af503e-04fc-497f-a77b-6394b328102b)

		![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/531968e4-7649-4255-b047-8a87d9b0a7cd)

		
		To calculate slew we need these
		b. Let red be input, blue be output and stimulus is applied. Output is taken from buffer.
		In_rise_thr is threshold of delay is 50% of slew waveform 
		![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/109fb82c-e1c0-4a24-81a7-6c14dd30b977)

		Similarly out rise threshold 
		![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/52cc40fa-a7b5-4596-8b8b-317325d7d5fe)

		Similar is the case for fall waveforms.
		![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/83ea2ec3-7c2d-4fb0-a32e-442fe4ef70b4)

		![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/94464548-a1d0-455d-8a69-d1a106caed13)

		
		Any input has 2 delays, rise and fall delays.
		Based on these 8 terms, slews and propogation etc are calculated.
		
		PROPOGATION DELAY::
		a. It may lead to unexpected results
		b. Will see wrt this waveform 
			![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/e3d548ad-748e-4e35-a7cf-af464345e60f)

			
		c. Way to calculated is shown in diagram below
			
			![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/8de0988f-0cc6-4bcd-8047-9be5c2608f29)

		d. If input waveform and output waveform be below with 50% threshold with mentioned values
			![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/8ca220ad-8a57-4745-bccc-3c8fcc145c50)

			3.23-3.207=0.023  
		e. Delay is 23micro sec. here thresholds are 50%. If somehow threhold pont moves down, time in rise be 3.263 and fall threshold be 3.221ns. So we get negative delay. If poor choice made for threshold selection we get negative thresholds
			![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/552f16fa-ec8a-477d-8ccb-f056b0cd40a2)

			
		f. If we have correct threshold values then also possibility is there of negative threshold. If 2 invertors/buffers are far apart, then as per input waveform we can slew is very high.
			![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/4a1340d6-8749-498a-bbc1-102513828a94)

			Output come before input, we get negative delays. This is problem with circuit design.
			
	c. Transition time:
		a. Slew of waveform of rising wave, 
		![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/08e3f52f-a7bf-47c1-890f-9da9fa84ee3a)

Similar slew fall wave, 
		![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/0f0da18a-cfa9-44ba-9b43-de545b8269ff)

		b. 20% of VDD is general value for low rise and fall
		c. 80% of VDD is general value for high rise and fall
			![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/7ba071de-2450-43f4-bda1-3ac458033291)

		d. Slew be high - low, will give below values
			![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/cb9d11ff-08eb-4bfc-8057-a034f179ee95)

	

