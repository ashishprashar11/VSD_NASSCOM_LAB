SKY130_DY1_SK3:
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
