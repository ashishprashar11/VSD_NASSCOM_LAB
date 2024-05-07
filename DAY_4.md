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
