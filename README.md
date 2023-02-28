# KARSTGEN1.0
<img align="left" src="img/LogoKG.png" width="30%" /> 

- KarstGen was developped in HydroSciences Montpellier (http://www.hydrosciences.org/).
- Part of the tool was developped within the framework of KARMA Project (http://karma-project.org/).

<img src="img/LogoKARMA.jpg" width="10%" />   <img src="img/LogoHSM.png" width="6%" />   <img src="img/LogoUM.png" width="5%" />

## Correspondance:
Mohammed Aliouache (mohammed.aliouache@umontpellier.fr), 
Hervé Jourde (herve.jourde@umontpellier.fr)

## To cite:
Aliouache M., Jourde H. and Wang X., (2023) KARSTGEN : Incipient karst genesis in fractured carbonate rocks, Github: https://www.github.com/maliouache/KARSTGEN

## Description:
This code simulate incipient karst genesis in 2D discrete fracture networks for limestone. 
It couples fluid flow and reactive solute transport in fractures using a two parrallel plates model.
	1. One dimensional discretization (segments) for flow and transport models
	2. Mass conservation at intersections
	3. Model only advective flux in network; complete mixing of solute at nodes
	4. It considers laminar flow (Simulations stop automatically when the Reynolds number exceeds 2100 in one fracture segment)
The code will automatically extract the backbone of the discrete fracture network, thus, please make sure to have a well connected DFN.
	
## Assumptions:
- Quasi-stationary approximation (Ortleva et al. 1987; Lichtner 1988)
- Instant mixing from the fracture wall to the middle of the fracture (high flow velocity location) – Advection limited reaction
- Linear reaction kinetics
- Fully saturated medium
	
## Installation
Install matlab Runtime from Install/ folder

## To use:
The code requieres matlab core to be installed to work (a standalone application with requiered installable programs is found in Install/ folder)
		
### Step 1: Prepare the initial DFN to use in the simulation by respecting the following format,
the DFN is defined by a descritized fractures into segments(please, make sure that all the intersections are defined as a node)
the segments are then provided in the segments.txt input file as below:

	X1		Y1		X2		Y2		Aperture
	.		.		.		.		.
	.		.		.		.		.
	.		.		.		.		.

X1,Y1,X2 and Y2 are the coordinates of the two points defining each line segment. The tool can read .txt and .mat formats
	
### Step 2: 
Save the segments defining the DFN in .txt or .mat format and launch KarstGen program in Use/ folder
	
### Step 3: 
Load the segments file then define the different input parameter (default values are already provided):

	#output folder
	Output			--> defines the name of the folder containing the segments.txt file
	#flow direction
	x-direction	--> defines the flow boundary direction type (can be: x-direction, y-direction or concentrated recharge points). Note that rnd-direction will randomly defines nodes in the model as input and output (10 input points and one output point)
	# constant head or constant flow
	cst-rate		--> defines the type of flow boundary condition (can be: cst-head or cst-rate)
	#Hin or Qin
	4e-5			--> defines the input value for flow (in case of constant head boundary condition, please provide the hydraulic head at the input nodes in meters, else, in case of constant rate boundary condition, please provide the flow rate for the input points in m3/s)
	#Hout
	0				--> defines the hydraulic head at the boundary condition (default set to 0 m)
	#dt timestep (in seconds)
	315360000		--> defines the dissolution timestep  in seconds
	#Kinetics of the reaction
	2.5e-7			--> defines the kinetics of limestone dissolution
	#max number of iterations
	250				--> defines the maximum number of iteration as a stop condition. Note that the simulation will automatically stop if the Reynolds number exceeds Re>2100
	#Water dynamic viscosity (in Pa.s)
	0.001				--> defines the water dynamic viscosity and displays the equivalent temperature
	#Equilibrium concentration (in Mole/m3)
	2				--> defines the calcium (Ca2+) equilibrium concentration
		
		
### Step 4: 
Launch the simulation by clicking on Run button

### Step 5: 
The results are saved inside the defined ooutput folder (default: ./Output)
	
## Applications:
Aliouache, M., Wang, X., Jourde, H., Huang, Z., & Yao, J. (2019). Incipient karst formation in carbonate rocks: Influence of fracture network topology. Journal of Hydrology, 575, 824-837. Doi: https://doi.org/10.1016/j.jhydrol.2019.05.082 
	
