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


># **DAY-1**
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


> PKD: *Process Desin Kit* is a collection of files used to model fabrication process by the EDA tools to design an IC. 
> >This is the interface between fabrication and designers 
> 
> The PDK includes:
> * PDRs: *process design rules* contained in DRC, LVS, PEX files.
> * Device Models.
> * Digital STD_Cell libs.
> * I/O libs.


   
      
  ## 2. SIMPLIFIED RLT2GDS FLOW
  ## 3. INTRODUCTION TO OPENLANE AND STRIVE CHIPSET
  ## 4. INTRODUCTION TO OPENLAEN DETAILED ASIC DESIGN FLOW
    
# PART-3 (GET FAMILIAR WITH OPEN SOURCE EDA)
  ## 1. OPENLADE DIRECTORY STRUCTURE IN DETAILS
  ## 2. DESIGN PREPARATION SETUP
  ## 3. RUN SYNTHESYS
  ## 4. OPENLANE PROJ GIT LINK DESCRIPTION
  ## 5. STEPS TO CHARACTERISE THE RESULT OF SYNTHESIS 


