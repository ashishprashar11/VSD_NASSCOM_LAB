Timing model using delay table::
1.	Openlane is PnR tool
2.	P&R not requires is DR boundary, power and ground, input and outputs, no need to logic
3.	.lef file has all such info
4.	Objective : to extract lef file and will try to plug through picorv32a
5.	As layout is already completed
6.	You can see routes as below (metal traces)
![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/3b240b91-13da-4b56-89a9-e492d4645c3f)
7.	Every metal has X and Y direction
8.	Each apart 0.46 in x and 0.34 in y direction.
9.	Check grid command before execution
![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/6cc20ab3-034b-4b95-9c58-240e2b1a4eb6)
11.	Check if IO are at the intersection of the HZ and vertical tracks to ensure route reaches that position from both Hz and vertical direction.
12.	This shows IO are at the intersection
![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/cd69e92d-d3dd-4a23-853e-9d41b8d0c699)
13.	Width of std cell should be in odd multiples of the xpitch of that layer
14.	Its xpitch is 0.46
15.	PR boundary is 3 (2 full boxes and 3 as half on both sides )
![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/4e9bda9d-4f5a-4ccf-89ff-8e4ca4f6b938)
16.	Same rule is there for height of the std cell
17.	Height is along  Y and ensures std cell layout is done as per pnr requirements
18.	Save this design as new name.mag and create new lef file using below
![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/31eee77c-cf3d-407e-8aff-cfc4b74d07c8)
![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/12e94271-ab41-49a5-b45a-123516bb083b)
19.	Open this lef file
20.	It will look like below
![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/50851230-506c-4cfe-8e50-ba76581d3e5a)
We had selected a layer and declared that as port. It will create Pin . Pin A is input pin of signal class
21.	Now we need to plug this in picorv32a flow.
22.	Before this will move all files (new lef)to SRC location
23.	Now we need to custom cell in openlane flow
24.	Step ABC, we need to have library which has our cell definition for synthesis.
25.	We have all slow, fast and typical lib files. Typical meand pMOS&nMOS can be fast or slow
![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/89fa4923-d76b-4f73-9010-9abf2ef97890)
![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/df6a0884-edf8-4c24-8ee8-9161c6ed51a6)
![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/022bfc36-2305-4e36-9ed4-e52642eda7ec)
![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/c93710f7-33db-44b6-a460-3028b6775fd1)
![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/d85a0ff1-f893-4980-9492-d5439e03f0f1)

![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/db010e50-b20e-4b6b-8422-5c813677bdd1)

![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/7d7debcc-12a1-42ff-ae1c-a5f66a626ea7)

![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/314026f2-2592-4566-8d0c-3dddc62f6f7b)
Have skew of 0 (x9'+y15) same for delay as well.
If either if 2 are 1 then non 0 skew will come
It may leadd to setup-hold voilations
POWER ARE CLOCK TREE SYNTHESIS

CONSIDERATIONS:
FOR CERATAIN PERIOD OF TIME, CERTAIN PART OF CIRCUIT IS NOT ACTIVE, SO CAN STOP CLOCK THERE. THAT IS CALLED POWER AWARE CTS

![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/6a394b02-b700-47a3-aeca-927acf30bc09)
1.	Open README.md file in configuration folder this file will have variable information

 ![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/c9616699-7556-45d3-86f7-57fe8d91eb7a)

2.	Synthesis has already reported the delays


![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/d531e603-8335-4dba-8d1c-7e091d7e94f6)
5.	Enable buffering and sizing as below


![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/9949bcfd-79cd-45a7-afad-82168e21d537)
6.	To check driving strength follow below steps


![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/62ebfb90-744a-41fa-b384-668f5d8c85d9)

![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/d44f4b7e-a34f-413d-937e-8f68a4afbbc5)
8.	Run floorplan to check whether changes are taken in p&r flow
9.	It ended with error

![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/4be04ec5-0a46-4f30-90a8-703e72b8e016)

![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/0d154a66-020d-49b9-8563-2b4b8a043ad1)

![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/7068af06-c348-4c79-84a7-cc9d3bd703a0)

![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/61984298-6c2c-42d2-9284-a28a467e4b64)
Run_placement

![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/1980dae5-43c9-4fd0-815f-b2cab6c56e10)

![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/49981afd-21f7-40f0-bada-0f47089f84de)
17.	Find cell vsdnew by zooming in. it will look like below

![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/1a204ce3-7333-4fe9-b07b-59c062774d41)

18.	To know how it is connected type expand in terminal, you will get its connections

![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/b278c00b-d64c-4423-9640-5d01137d2703)
	
STATIC TIMIG ANALYSIS: 
Will take ideal clock first (Clock tree not build yet) to check for basic structure and parameters to check timing considerations.
Lets start with signle clock of 1GHz of period 1ns, ideal clock network (no clock tree built yet)
1.	On 0 th time one clock edge reaches flop, on Tth second edge reaches capture flop
2.	Let combinational delay is thetha and should be less then T, if it is more than T then clock period also need to be shifted to RHS and frequency will decrease. It can be allowed as system is designed to work in specific frequency.

![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/95d43bf0-2981-4775-883d-5544844de138)
3.	Now will see practical scenario
4.	Lets open capture flop which have several gates, R's,C's etc. lets take be MUX then when clk at 0, D input reaches from 1 pt to other after some delay. That finite delay is taken when clock 0. So output is fixed, not changes
5.	When clock switches from 0-->1 then change happens. Qm moves from Qm to Q. so MUX2 delay also comes.
6.	The MUX1 or MUX2 delay when logic 0 or 1 will restrict combinational circuit delay 

![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/fcde1bb3-91ee-469c-b328-bb153bf578ca)
That amount of time has to be subtract from complete time period T. As it got reduces as some time before T has to be required for mux 1 to settle. That is setup delay.

![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/46eddfb8-9a46-4aa7-be6c-d442ef07b497)
Combinational delay should be less than that (T-S) (clockperiod - setup)

![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/1232870f-b966-4b68-bca6-d60e78f4cd32)

![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/588837d7-ba1f-45ed-9bf9-212bffec8a19)
 
8.	Lets identify timing path in existing design with single clock to FF1 and FF2.
9.	Will see for set of logic with ideal and single clock
10.	We need to identify combinational path

![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/8353c8d6-f46d-4c44-94eb-166463949dd0)

![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/7e0dcdc1-a14a-499d-a554-e0f0f7e7a98d)
12.	To make sure no slack, we will do timing analysis on openSTA
13.	Min analysis is hold analysis
14.	Create a file named pre_Sta.conf

![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/2fc07303-69a5-45aa-b056-a4a7fb3a105f)
15.	It reads max and slow libraries, verilog from read verilog., link designs, SDC from specified location
16.	Create sdc file named my_base.sdc

![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/cb2b8275-4dd3-4a7d-a8a8-f13d373d9bca)
17.	It defines clockport, sets time period
18.	Its same file but with specific charges for STA (…./src/base.sdc)
19.	As it is continuous flow from previous steps, you will get 0 slack

![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/9b5dd5e2-3022-4523-930b-345c0e1607dc)
20.	Old default design will have non zero slack values

![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/8d61e7f4-f3bf-47dc-a51b-45060194cf3e)
Will see for steup analysis, 
Delay of cell is function of input slew and output load.

![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/a90ee0ca-4085-4abb-b61b-7d8e76cbb7a7)
Hold doesnot signifies anything as cts not done and clock is ideal.

![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/b85505bc-9152-4cb5-8e64-87844781b882)

![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/e1fb31ad-1380-4e6d-a3a3-0d7fb7e8ecf4)

![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/fcd734a7-95ef-49ae-b3e8-04112ed0f0dd)
24.	The further slack will be as shown below

![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/a60bab03-66f4-4cf4-9679-b22e8cf0d351)
25.	We will optimize the fanout using openlane as well
Set ::env(SYNTH_MAX_FANOUT) 4
Run_synthesis
BASIC TIMING ECO::
1.	TRITONCTS AND SIGNAL INEGRITY

![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/f1827469-4644-43a5-a1ea-d917c6ecf343)

![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/f04ab577-3f5f-419b-afd0-fbf94ef99d32)


![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/07e2f026-17a8-4f27-8745-990af43d5c4c)
It takes this clock route and calculate distance to all point, it check for midpoints. But following midpoint strategy, we do like  as shown below

![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/fb169ba3-175c-4200-9ce5-30627a1fe4ed)
Similar for second

![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/d14bf713-9f0e-42ca-8b57-abba986a01af)
2.	Clock tree buffering:
All clock trees are wires and each wire has R, C. There will be huge capacitances so there exists signal integrity problem
Lets say below be clock path shown experiences c's

![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/2f00d841-cdff-4ee4-bece-cf8ef347bf1f)
When this waveform is fed more problematic / non ideal waveform come
So best solution is to add buffers/repeaters
Repeaters for clock and Data path difference is that for clock repeaters has same rise and fall time. Will now add chain of buffers

![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/51c61807-327f-44bd-bd1e-b2ada1857cc8)
It makes sure clock waveform is successfully recovered at the output
Will try to check for NET SHIELDING
Clock tree maintains 0 skew between launch and capture flop
Clock nets are critical nets. It some crosstalk happens on these lines can detriate the clocking. 
Shielding means encapsulating clock tree nets 

![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/89de646f-23d0-4300-856a-97276716949f)
So any signal/net/wire inside shield have some activity occurring and it may cause if coupling capacitance happens between this and shielding, glitch and delta problems come

![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/3dc62e70-4002-446c-8440-9c0f09035667)
It shows glitch
If A is aggressor going under switching and coupling capacitor is there between A and V victim that is without shielding we can see glitch here as it got inverted we can get incorrect logic high which may reset memory for eg. 
Shielding protects this victim
Shields are either connected to VDD or ground.
The shield donot switch
 
WHAT if victim itself switching and aggressor also

![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/80a2b3c5-7a20-4c1a-8d00-f4f92e8b9fb1)
 Clock tree be like it give 0 clock skew (l1=l2)
In of v line 0-->1 and a line be 1-->0  switches. Then due to glitch it impact 1-->0 with some delta delay as it ceased  the aggressor. So skew will be l1-l2+delta
So SHEILDING is one technique to avoid crosstalk in critical clock and data nets.
