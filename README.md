# vsdworks
This repository contains all the information required for the physical design flow of your IPs or SOCs, using qflow and other open-source tools. It was created during the "Beginner Physical Design using Open-Source EDA Tools" .

## **TABLE OF CONTENT**
>**1. DAY-1**
___
* PART-1 (INTERACTION WITH COMPUTER)
  * INTRODUCTION TO QFN-48
  * INTRODUCTION TO RISC-V
  * FROM S/W TO H/W APPLICATIONS
    
* PART-2 (SOC DESIGN AND OPENLANE)
  * INTRODUCTION TO ALL OPEN SOURCE DEGITAL ASIC DESIGN
  * SIMPLIFIED RLT2GDS FLOW
  * INTRODUCTION TO OPENLANE AND STRIVE CHIPSET
  * INTRODUCTION TO OPENLAEN DETAILED ASIC DESIGN FLOW
    
* PART-3 (GET FAMILIAR WITH OPEN SOURCE EDA)
  * OPENLADE DIRECTORY STRUCTURE IN DETAILS
  * DESIGN PREPARATION SETUP
  * RUN SYNTHESYS
  * OPENLANE PROJ GIT LINK DESCRIPTION
  * STEPS TO CHARACTERISE THE RESULT OF SYNTHESIS 

___
>**DAY-2**

___


># DAY-1
# PART-1 (INTERACTION WITH COMPUTER)
  ## 1. INTRODUCTION TO QFN-48
  ### PACKAGE QFN-48
  The package are protective layer where ICs are put into to easy handing and assembling onto printed ciruite board to protect devices from damage. 

Here, QFN-48 means Quad Flat No-leads which have 48 pins and surface_mount. A wide variety of electronic packages exist, including through-hole packages, surface mount packages, chip carriers, pin grid arrays, flat packages, and ball grid arrays.
Using these small packages we can place IC to a circuit board.

These are used in various applications as follows,
1. Automotive
2. Consumer electronics
3. Industrial and powe applocations ...etc.

![Screenshot 2024-04-26 084350](https://github.com/arungithub007/vsdworks/assets/95173376/681fcbb6-6838-4b4e-bda4-6b341f610083)

The core is placed in the middle of the quad flat package. Here below is how the chip placed in the middle of the package looks like


**IC** is the **intergrated circuit** which consist of millions of transistors, cpacitors, resigtors inside a semiconductor chip. 
They comes in veriety of size and pakages. 

**SOC - System on Chip** is kind of IC which has the capability of combining functional elemnts of many electronic device on a single chip. It may constist of CPU, Memeory, inputs, outputs, ICs, IPs and other functional elements integrated init. SOC is used in multiple computing task, we can widely see in mobiles, laptops, tablets, AI devices etc. 

The chip is madeup of **core** and **die** area.

**Die** is the semiconductin_material(specimen) on which caore(fundamental logic circuit) is fabricated.

**Core** is the section of chip where the fundamental logic of the design is placed.


The fabrication of the chip is done on the **silicon wafer** which are usually of 9 inch to 12 inch in diameter. Then, this wafer is cutted into pieces. Each piece has similar funtionality of the fundamental logic called **Die**.


![Screenshot 2024-04-26 091121](https://github.com/arungithub007/vsdworks/assets/95173376/16c96f7f-fb9e-4a51-8065-ea4c76d7cd79)

We can make external connection by placing Pads on the rectangualer metal patches as in above fig.

  ## 2. INTRODUCTION TO RISC-V
  RISC-V stands as a public, open-source specification for an Instruction Set Architecture (ISA) based on Reduced Instruction Set Computer prinnciples, setting it apart from the proprietary ISAs such as x86, typically found in personal computers, and ARM, commonly used in mobile devices. 
  Unlike many ISAs that are bound by proprietary standards, RISC-V is accessible under licenses that are free of charge, giving it a significant advantage over its commercial counterparts. It’s characterized by its simplicity, stability, and compact standard base, while offering extendable ISA support. This has been instrumental in enhancing the adaptability, scalability, extensibility, and modular nature of chip designs.

  ## 3. FROM S/W TO H/W APPLICATIONS
  **Assembly language** is the bridge betweeen s/w and h/w. 
  Different software and applications runs in different language programs(ex:- C, C++, Java, pyhton ...etc). Hardware cannot understand these lanuguages therefore we use special program like comiler and assembler to convert the instuctions in different languages to the targeted assembly language. 

# PART-2 (SOC DESIGN AND OPENLANE)
  ## 1. INTRODUCTION TO ALL OPEN SOURCE DEGITAL ASIC DESIGN
  Some of the open sources we can use for,
  1. RTL Designs
       * libracores.org
       * opencores.org
       * github.com   

  2. EDA tools 
       * Qflow
       * OpenRoad
       * OpenLane
  
  3. PDK data
      * [Google + skywater](https://github.com/google/skywater-pdk) = foss 130nm PDK


> PKD: *Process Desin Kit* is a collection of files used to model fabrication process by the EDA tools to design an IC. 
> >This is the interface between fabrication and designers 
> 
> The PDK includes:
> * PDRs: *process design rules* contained in DRC, LVS, PEX files.
> * Device Models.
> * Digital STD_Cell libs.
> * I/O libs.


   
      
  ## 2. SIMPLIFIED RLT2GDS FLOW
### Logic Synthesis
| no.  | Description              | tool    |
| :--- | :----------------------- | :------ |
| i    | RTL synthesis using      | yosys   |
| ii   | Technology mapping using | abc     |
| iii  | STA reports using        | OpenSTA |


### Floor Plan
| no.  | Description                                            | tool     |
| :--- | :----------------------------------------------------- | :------- |
| i    | To implement core area                                 | init_fp  |
| ii   | To place input,output ports and macros                 | ioplacer |
| iii  | To geerate the power description n/w                   | pdn      |
| iv   | To insert welltap and Decap cells(physical only cells) | tapcell  |


### Placement
| no.  | Description                    | tool       |
| :--- | :----------------------------- | :--------- |
| i    | To perform Global Placement    | RePlace    |
| ii   | To Perform Design Optimization | Resizer    |
| iii  | To perform Timing Optimization | OpenPhySyn |
| iv   | To Perfrom Detailed Placement  | OpenDP     |


### CTS
| no.  | Description                            | tool       |
| :--- | :------------------------------------- | :--------- |
| i    | To synthesize the CLK distribution n/w | Triton CTS |


### Routing
| no.  | Description                 | tool            |
| :--- | :-------------------------- | :-------------- |
| i    | To perform Global rouitng   | FastRoute       |
| ii   | To perform detailed routing | TritonRoute     |
| iii  | To Perform SPEF extraction  | SPEF-Extraction |


### STA
| no.  | Description        | tool    |
| :--- | :----------------- | :------ |
| i    | To get STA reports | OpenSTA |


### GDSII Generation
| no.  | Description                                        | tool  |
| :--- | :------------------------------------------------- | :---- |
| i    | to perform final GDSII layout file from routed def | magic |


### Checks
| no.  | Description                              | tool   |
| :--- | :--------------------------------------- | :----- |
| i    | To perform DRC checks and Antenna Checks | Magic  |
| ii   | To perform LVS checks                    | NetGen |

  ## 3. INTRODUCTION TO OPENLANE AND STRIVE CHIPSET
  ## 4. INTRODUCTION TO OPENLAEN DETAILED ASIC DESIGN FLOW
    
# PART-3 (GET FAMILIAR WITH OPEN SOURCE EDA)
  ## 1. OPENLANE DIRECTORY STRUCTURE IN DETAILS
  ### Importent file in openlane_working_dir
  1. pdk file
  2. openlane 
   ![Screenshot 2024-04-27 092126](https://github.com/arungithub007/vsdworks/assets/95173376/9f6a5290-4f74-4230-86f4-3a3fb2ad841f)

   The PDK we are usign here is Skywater130nm which is recently made as opensource. Openlane is built arround this pdk.

### Firest lets see PDK file:

![Screenshot 2024-04-27 092816](https://github.com/arungithub007/vsdworks/assets/95173376/57f428aa-6cf2-4ff8-bc27-61c9c9006de8)

ALL the files present in these pdk files are shown in the above directory structure.


The silicon foundry files i.e.,skywater130nm or any of the foundry files made to use in the commerrtial eda tools(Paid version) rather than opensource eda tools. This open_pdks used to avoid this problem by converting the files from commertial levl to opensource tool(for example like magic, netgen...etc) usable.

Sky130A is the foundry file that made opensource eda compatible.
| file      | description                                                            | contents                                                                                                                        |
| :-------- | :--------------------------------------------------------------------- | :------------------------------------------------------------------------------------------------------------------------------ |
| libs.ref  | it is specific to tecchnology. Here we are focusing on Sky130_fd_sc_hd | ![Screenshot 2024-04-27 094803](https://github.com/arungithub007/vsdworks/assets/95173376/031f4959-abeb-467f-897b-8d0f4550173b) |
| libs.tech | it is specific to tool                                                 | ![Screenshot 2024-04-27 095010](https://github.com/arungithub007/vsdworks/assets/95173376/622a8665-cc4f-4160-8636-abb461289bbd) |

#### sky130_fd_sc_hd :
The file name abrivates as follows,
* fd --> foundry
* sc --> std_cells
* hd --> high dencity
  

![Screenshot 2024-04-27 100040](https://github.com/arungithub007/vsdworks/assets/95173376/9f4622c9-b51b-4deb-b470-b0715a7a606c)
these are the files we can find inside the sky130_fd_sc_hd

  ## 2. DESIGN PREPARATION SETUP 
### openlane 
openlane is a silicon implimtntation platform that supports open-source tools such as yosys, Openroad, Macgic, Klayout along with other opensource and proprietary utilities.

These are the files present in openlane
![Screenshot 2024-04-27 123538](https://github.com/arungithub007/vsdworks/assets/95173376/872d75aa-2580-4ff9-86ab-a6ddae667a71)

#### The list of main commands we use here are:
![Screenshot 2024-04-27 125606](https://github.com/arungithub007/vsdworks/assets/95173376/2b95a6e6-bca6-4508-b511-bf80859fb186)

> note:- the commads from 3 to 14 can be put into a <file_name> and we can pass it to "flow.tcl" i.e, > ./flow.tcl -interactive -file <file_name>

#### Design file
**picorv32a** is the Design we are using here. we can also create other desig aswell in the design folder of openlane.

Some list of designs we will get in design is shown in below:
![Screenshot 2024-04-27 130713](https://github.com/arungithub007/vsdworks/assets/95173376/037bb8a5-5b14-4e97-b681-fe44f2d3d6eb)

The files included in the **picorv32a** is as follows:
![Screenshot 2024-04-27 131531](https://github.com/arungithub007/vsdworks/assets/95173376/21fb00d8-8258-4135-a3de-8f0a0d57bdcd)

> note:- here config.tcl contains information about:
>* design name
>* path to sdc and .v
>* clock_period, cloc_port, clock_net

#### DOCKER
**First** we need to get inside docker_build using command ***docker*** And get the docker into interactive mode.
> 1. we should be in interactive mode ohter wise it will excicute full flow. 
> 
> `./flow.tcl -interactive`
>
> 2. we need to include all the files required to run the flow
> 
> `package require openlane 0.9`

![Screenshot 2024-04-27 134121](https://github.com/arungithub007/vsdworks/assets/95173376/9f5426cc-f717-42ca-aef4-a7130047b3d9)




#### Design setup stage:

![Screenshot 2024-04-27 134420](https://github.com/arungithub007/vsdworks/assets/95173376/7fdbac9d-f76a-43a6-bc24-10b7a4d9f124)

When we run  `prep -design picorv32a` a run file with todays date will be created inside the `Picorv32a>runs>dd/mm/yy`
![image](https://github.com/arungithub007/vsdworks/assets/95173376/3fa75454-414d-4a52-8206-2da2465e6024) 

At this point we  can see multiple folders and files are created inside the **27-04_08-06** file. But most of them are empty.
![image](https://github.com/arungithub007/vsdworks/assets/95173376/5b4fa439-607e-465b-b036-a4a658fe12a6)
Step by step each files will generated with report files inside these files.

Next we will start our synthesis

  ## 3. RUN SYNTHESIS
`run_synthesis`This will run the `yosys` and `abc` synthesis.
![image](https://github.com/arungithub007/vsdworks/assets/95173376/25808d53-92b1-47e0-ae37-1025d423bf26)


  ## 4. OPENLANE PROJ GIT LINK DESCRIPTION
https://github.com.efabless/openlane 


  ## 5. STEPS TO CHARACTERISE THE RESULT OF SYNTHESIS 
  After synthesis report files are generated inside the synthesis folder present in runs. we can see the report mentioned above in these folders, as shown below.
 ![image](https://github.com/arungithub007/vsdworks/assets/95173376/aada7452-7d7c-404d-b2bf-fad8a1449cf4)

---
---

># DAY-2
# PART 1. Chip floor planning considerations
## 1. Utilization factor and Aspect ratio
## 6. STEPS TO RUN FLOORPLAN
Before sunning the floor plan just have a glan on README.md file in openlane/configuration directory.
![image](https://github.com/arungithub007/vsdworks/assets/95173376/93cd1ed4-352a-477e-8ccc-7f46b4587f70)

>open openlane/configuration/floorplan.tcl where we can see default parameter set for floorplan by openlane.

here we need to give more preority to  these files.
![image](https://github.com/arungithub007/vsdworks/assets/95173376/cca85fdd-6a5a-46ed-92e5-13d97ad39e5d)![image](https://github.com/arungithub007/vsdworks/assets/95173376/1c654540-3197-4686-8111-e7fa03c96d0d)

## 7. steps to view floorplan
![image](https://github.com/arungithub007/vsdworks/assets/95173376/dc8e3dad-8167-440d-80ab-04531988d4d8)
## 8. Review Floorplan in magic
![image](https://github.com/arungithub007/vsdworks/assets/95173376/91e8a1c5-88a2-4564-b5ae-d9fae72aae26)

we can get info of an object by selecting it and asking **>what** in ***teckon*** as shown below.
![image](https://github.com/arungithub007/vsdworks/assets/95173376/94555fe4-9b67-43b6-a1ef-30549fad7ce8)
![image](https://github.com/arungithub007/vsdworks/assets/95173376/4fb989cb-7256-45c3-968b-2954a49a82f7)


# PART 2. Library Binding and Placement
## Congestion aware placement
The next stage after the floorplan is ***placement***
to see placement in magic tools:
![image](https://github.com/arungithub007/vsdworks/assets/95173376/c58e86e9-a04d-492a-9da4-c59e67e6d332)

![image](https://github.com/arungithub007/vsdworks/assets/95173376/ad44a51c-79f1-410b-a77d-07d528922e7b)
We can see All the std_cells placed in std_cells rows. All the physical only cells also place.

# PART 3. Cell design and characterization flow
# PART 4. General timing charactorization parameters

# Steps to Disply std_cells Uisng Magic tool
1. first we need to get the technology file from `sky130A` pdk folder, to the `vsdstdcelldesign` folder.
   ![image](https://github.com/arungithub007/vsdworks/assets/95173376/ae2bc165-50b5-4130-be8f-383255e7f72e)

2. now give magic tool command to display the cell
    > magic -T sky130A.tech sky130_inv.mag

3. The inevertor std_cell will be displayed as below.
   ![image](https://github.com/arungithub007/vsdworks/assets/95173376/6cacb50b-a174-4bb2-90ad-5367cdb8331e)

# Introduction to sky130 basic layers and Lef using inerter
![image](https://github.com/arungithub007/vsdworks/assets/95173376/0ff7899a-60e8-4fb8-a28d-0b0c45ac701f)
we can use tkcon to get the infrmation about the cell layers by giving command `what`.

# Creat std cell layout and extract SPICE netlist




