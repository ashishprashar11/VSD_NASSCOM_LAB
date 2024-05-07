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
	
