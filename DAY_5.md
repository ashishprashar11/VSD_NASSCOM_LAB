RTL2GDS using tritonroute and openSTA
1.	Algorithm finds best possible path to connect A with B with minimum zig-zag
2.	It labels grids/checkboxes
3.	Label all adjacent grid as next number
   
![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/f4e31acf-a1c6-43d9-bf9c-30fa5944631b)
5.	Route will look like (final in global routing be)

![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/f2327f89-1d6c-4904-bcb1-9a091f18fcbf)

DESIGN RULE CHECK
There should be minimum width of the wire
Center to center distance between wire is also specified.
Minimum sepration between 2 wires is also defined 
DESIGN RULE CHECK
There should be minimum width of the wire
Center to center distance between wire is also specified.
Minimum sepration between 2 wires is also defined

![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/8f7d63d0-84d7-4d55-8686-47c382dfeee7)

Need to take care of signal short like situations 

![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/cb7c840a-6456-4d30-8b19-546a0aba606a)

To solve this we take another layer of metal eg if m+1, upper be wider than others. There are few more problems coming, need to check for
Via width: specified minimum value for this

![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/07bd7d4b-0752-4cd0-8ef8-92a077c29d56)

Another rule is via spacing: min spacing between via specified
All these things are controlled in lithography technique

![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/31ab39bc-8ad7-4f57-bf35-0e3f50296e4e)

We also extract the RC of net for parasitic extraction

![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/44fb8074-205d-4603-bf41-5d5e2de30a3c)

Start openlane again and load the design
![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/74087d80-604e-4a2f-b039-bf6c8becfb0d)
![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/0bc3e374-e9a6-4eff-9ae2-e9516e6c8b6e)

Now generate PDN using gen_pdn
![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/1ef0a509-75bc-435a-9313-51e3fb1ca51e)



![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/72f921f2-3f47-462a-8ba0-b3345bca7b5d)
Routing I sin 2 steps; fast/global routs where routing region is divided in rectangular sections and referred as 3D route and detailed routing which is done by triton
In detailed routing we use the global route to carry out detailed routing (trying to connect ABCD in best possible way)
Black dots are pins of std cell and need to be overlapped by route guides eg purple box M1 metal guide overlapping std cell pin. 
Route guide has tracks within it
![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/73c4a74a-eacf-4b17-b144-ba8a4856bbaf)
![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/0a6712b1-436e-4961-9e46-5fe56f0d25f6)
In fig e, Purple between M1 and M2 is non 0 vertical overlap area, needs Via
![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/b8688f8e-fcaa-4462-9292-678c48fb587c)
![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/47727920-fbc8-461a-8c08-2878d0d84eb4)
![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/55377131-552a-41a1-b076-0fc01abe3924)
Intra layer means within layer and interlayer means between layers
There are 4 layers each is M1,2,3,4.
Eg M2 we considered vertical   as vertical lines, these lines are called panels. Routing guide is assigned to atleast 1 panel.
First routing will happen for parallel for even index (say) and then for odd.
Routing in layer is in parallel but within layers is in sequence (grey arrow shows routing in m1 and m2 completed then only will go next m3 as shown in fig 2 for m1,2 greyed and m3 working ie called sequential)
 
For triton we need followings 
![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/113441f1-893b-4255-ad9a-8c63733712a7)
![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/b74899d8-f4bb-4006-ac20-f50568e6d614)
Access point : 
![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/e79ccdc1-4af7-4350-b43b-0fccbf870c93)
Dashed lines are tracks assigned for metal 2 
Solid line is completed routing for M1
In this (a) they are trying to comment the guides using VIA
Where to connect VIA ??
5points are there to connect via, 
![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/ca5f087b-3e77-4e7b-aabb-e6dfabe0d75b)
All 5 points where we can connect the upper layer with lower layer are Access points

![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/453903fc-6fda-4462-9923-65f422168e6e)
(a)-5 AP's
 (b)-if m1-m3 connection, then need to go for m1-m2-m3 so goal of MILP is to connect these APC's 
Collection of these points are called APC's
 
MILP: Mixed integer linear program equation
![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/afeab7b9-adfe-486b-8369-cc035e8eb5e0)
For each APC we need to find cost associated, then need to find the minimum and optimum point between APC's

Run routing using run_routing 

![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/72de2375-ba0c-4627-ad3f-460024d7ab6e)

We used triton 14 so 0 violations and more memory usage

![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/2e422147-6101-45ab-9539-be188be0b107)

You can fing routing guide in below location ie output of global routing 

![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/8152836a-a5c1-4016-8a91-0dc2cd6f6108)
![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/376d907d-d403-4448-b503-e3e2d73463cb)
![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/80da172d-e3b3-4cda-a861-ac0dec15f4ac)

Detailed routing make sure routing happens as per this only 
Further these guides are rectangular, in forms of 
Lower left x lower left y upper right x upper right y

![image](https://github.com/ashishprashar11/VSD_NASSCOM_LAB/assets/169080904/faf34fb3-815f-4190-837d-e77ab0af6c31)
