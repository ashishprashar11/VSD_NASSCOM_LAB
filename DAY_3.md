SKY130_D3_SK

	1. Will see wrt invertor as a cell.
	2. Download .magic file from github.
	3. If want change how IO pins are aligned in the core,ie pin configuration , use 

![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/722f9353-de43-4469-98d7-aca03eec6c19)
	
As seen below, all pins are equidistant
![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/f86f1fc7-6ecb-48a1-9cac-7de884421d73)
5.	If want to change for some other IO pin strategy, IO places supports 4  IO strategy.
6.	So we will take the variable that selects mode for IO
7.	Navigate to openlane/configuration folder
8.	FP_IO switch is there to select this, it will be in floorplaning file. 
![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/6977ce23-79d4-4367-90ac-f996b0e06040)
9.	Set it to 2 and rerun floorplan to change the spacing between the pins.
 
Now will see rise propagation, fall propagation delay etc
 
SPICE SIMULATIONS ON MOSFETs::
 
1.	Will create spice deck: ie connectivity info of the netlist.
2.	pMOS arrow is inside, nMOS is outside 
![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/eb78f80b-6c6b-4338-ba23-4e593c9e1b46)
3.	PMOS source to Vdd, NMOS source to Vss.
4.	Define components values, channel length is 0.25u and with be .375u for both.
5.	Ideally pmos should be 2x or 3x of nmos
6.	Will define all values as below
 ![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/35f4619e-e9d5-4a4b-8c4b-3e814170bacd)

7.	Now will start writing the spice deck
8.	** specify comments
9.	Drain gate substre source is the format for specifying as below to define connectivity
 ![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/0066c2b0-bc5e-401c-bc01-925b29916ec5)

M1 is drain connected to out, gate to in node and substrate and source both to vdd
10.	cload os between out and node 0 of value 10fF
11.	Supply voltage vdd between vdd and 0 of 2.5v
12.	Input voltage Vin Between and 0 of 2.5v
![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/5e728669-b0fb-427f-94f7-0fd31597e369)
13.	Sweeping the gate input of nmos from certain voltage 
14.	i.e sweeped gate input voltage from 0 to 2.5 of steps of 0.05v
15.	Final steps is to describe he modelfile have complete info of nmos and pmos
![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/7df7e845-8616-4c75-a757-1391f2a5e1c7)
![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/430a8ed3-3cd5-4291-9804-540eb528c7e1)
![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/d92e7a7e-c12d-42ac-a76a-4c635418e5a3)
 
18.	Netlist is like below
![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/4989a981-30df-4843-8863-4cde122c06ad)
19.	Will do spice simulation on this
20.	VI characterstics will like below
![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/00650a5f-d8cf-422a-b4e5-59bb48b2d7c0)
21. Switching threshold is a point where vin = vout
![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/6c11017b-7097-47ba-b7de-208166badaf2)
21.	In this point both are turned on so high possibility of leakage current.
22.	These are the switching thresholds are ~0.98v and ~1.2V
![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/8aca6e8d-c303-4bd5-9f35-6a2d1b697238)
23.	Both pMOS and nMOS are in saturation.
![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/4c32b9a4-d45b-4470-8ccf-9ca67fb43107)
![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/ca1a3d4f-466e-41f3-8240-1c00b35c8ae9)
24.	The pulse is defined as below
![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/22f9ad8c-1f24-4860-bcb7-f21a555191b0)

25.	25.	Pulse: starts from 0 end at 2.5 shift is 0 starts at 0, rise and fall time of 10ps, pulse width is 1ns and complete cycle of 2ns, will use this as input to CMOS.
26.	We will do transient analysis.
![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/683f50a6-433d-4463-a456-3e70e6b48fea)
27.	Zoomed in rise wave be below
![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/503aab69-6c20-4120-809d-e38be7706f1b)
Rise delay will be 0.14831 or 148 ps
28.	For fall delay will do same 
![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/28aeaa09-f04d-4c3f-9c96-e89fd5c846fb)
fall delay 71ns
![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/e78d05b4-bf03-4268-8dc7-f4868f94ac93)
Vm=0.99
![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/28dabf2d-061d-4b38-b0d6-2560d35f596a)
30.	Clone the git
![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/6b7c7534-1c8a-4695-910c-896f251a869a)

31. Copy this file below to
![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/0eb392dc-9c88-48b3-a2b3-c8a133319178)
![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/c1f0976d-3523-4d39-92b1-31484cf35b2b)
32. To see the layout use magic,
![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/2727a077-209e-4d69-9f51-225ccadc0e5c)
![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/8c40d47d-7153-4fc5-941c-b163e5c52446)
16-MASK CMOS PROCESS ::
1.	Select the substrate (P)
2.	Creating active region for transistors
3.	N-well and P-well formations
Well diffusion by using dry furnace to get wells.
As per from threshold voltage equation, which depends on body effect, we will try to maintain body effect parameters. 
4.	For formation of gate will maintain doping concentration and masking.
5.	Open the lightly doped drain (LDD)for P+(SD), P-(LDD), N(substarte)) (N+ (SD), N-(LDD), P (substrate)). Its P+P-and N in this order only becoz of hot electron effect and short chennel efffect
a.	When device size reduces, high energy carriers can break Si-SI bonds- hot electron effect
b.	When we move to shorter channel length drain voltage penetrate to channel area and tough to control voltage- short channel effect 
6.	Source and drain formation
7.	Creating metal contacts
8.	Higher metal level formation
9.	Chemical mechanical polishing.

BASIC CMOS INVERTOR
  ![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/d0264e71-0d95-4fda-8fc1-4decf3fefa62)
2.	Take cursor to block and type what, you can see what is what 
![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/ca95cc80-eb84-4bbe-9f10-aa2b08c676ac)
4.	You can also see parasitic capacitances value by creating a file using ext2spice which looks like
5.	Press G to see the blocks.
![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/a735e2bd-7932-4fae-8022-50b1ce682afa)


LOOKING INTO SPICEDECK::
a.	Type extract all to create sky130_inv.ext
b.	Use ext2spice ctresh 0 rthresh 0 command next
c.	Use ext2spice
d.	Open file sky130_inv.spice and make below changes for more details see step 1-6
e.	Install ngspice model and run, you will see the below window
![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/882812f6-2e05-4ce5-acf9-bbcb53ef3d0d)
g.	Now will see for characterization of cell (finding 4 parameters), will see rise time ie time taken by the output to transient from 20% to 80% of max value ( VDD), fall time be time taken by output waveform to fall from 80% to   20%, similarly fall and rise cell delays ie propagation delays ie 50% of input and 50% of output
h.	You will get rise time from below figure 
![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/cd313d74-4bdf-4c89-8f13-d27e08973249)
![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/a0174627-067d-4e62-b82f-fb6d393dedf8)



MAGIC TOOL ::
See magic basics from magic webpage. 
http://opencircuitdesign.com/magic
 
1.	Technology file : It is one signal file whch contains everything of process it has all layers in colors, connectivity, rules for wiring etc
Tech file list technology of fab process
Google opensource skywater 130 nm
Sources of information are there:
PDK can be found here:
Pdk : https://github.com/google/skywater-pdk
Documantation : https://skwater-pdk--136.org.readthedocs.build
2.	For lab exercise take layout from http://opencircuitdesign.com/open_pdks/archieve/drc_test.tgz
3.	Unzip the zipped firl you can get below files 
![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/c3ce9213-a938-4769-888f-c766137550e2)
4.	.mag is layout files
5.	.magicrc is script for starting magic.
6.	Start magic by using magic -D XR
7.	Load file met3.mag, you will see below layout. Here there are number of independent example layouts showing some kind of DRC errors
8.	Each example is labeled with name.
9.	You can see rows listed correspond to each name in document. 
![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/46f96461-56be-4871-a161-823adf04df66)
10.	Select any and type :drc why
11.	You will see below details
![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/fa2df504-c5c9-4b45-955e-3abd436fb208)
12.	Draw box near box3.3c type cif see VIA2, will shows contact cuts
13.	Load the file poly.mag, you will see below view
![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/9c55e647-dcdd-4030-ae4c-9f72983af1dd)
14.	Check poly 9 
15.	Select a poly and type what,you will see below 
![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/834bbe18-3c31-4e67-b53e-c0963642eb70)
16.	The box measurements between poly be below
![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/79c352f3-c16b-460b-807c-993b9f9c3e78)
17.	If 0.22 micron then rule violations
18.	To fix poly9 error, open file sky130A.tech
19.	Search for poly and add one more line with with allpolynonres
![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/c74ddd0d-042a-498c-a624-382575be729c)

![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/05c8941d-dfee-468d-a947-22cb2abd221a)

L8: exercise to describe DRC error in geometrical construct
1.	Need to use the Boolean operators in sequence
2.	After all operators are applied, whatever left is an error
3.	Open sky130A.tech and search for DRC
4.	Check for cifmaxwidth value
![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/ef663100-9409-4855-b641-18ba6aff1514)
1.	PMOS Drain connected to node Y gate to node A, source and substrate to node Vpwr.
2.	NMOS drain connected to Y, gate to A and source and substrate to node Vgnd.
3.	Need node  0 with vdd  3.3V
4.	Pulse voltage needed between A nad Vgnd of voltage Va
5.	Any voltage is measured wrt one box dimention i.e. 0.01micron
6.	Make below changes for including pmos, nmos library files, supply and pulse voltages.
![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/797819ec-aaee-4709-8f4e-ba859352e7b2)
7.	Add .tran from 1ns to 20ns for transient analysis
8.	Run this in ngspice
