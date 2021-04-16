# Rsume(English)
## List
-| Field | Timing | Company |
   |: --------- |: --------- |: --------- |
   | Robotics | 2020-2021 | [Re-al] (#anchor 1) |
   | AI | 2019 ~ 2020 | [Recruit Dispatch 1: XXXXX] (#anchor 2) |
   | AI-Robotics | 2019 | [XXXXX] (#anchor 3) |
   | Robotics | 2018-2019 | [Recruit Dispatch 2: XXXXX] (#anchor 4) |
   | FA | 2018 | [Recruit Dispatch 3: XXXXX] (#anchor 5) |
   | 3D / AI | 2017-2018 | [Recruit Dispatch 4: XXXXX] (#anchor 6) |
   | CMOS Image Sensor Test | 2016-2017 | [Intelligence Dispatch: XXXXX] (#anchor 7) |
   | Part-time job | 2015-2016 | [Day labor etc] (#anchor Z) |
   | DRAM | 2008-2014 | [Elpida Memory] (#anchor 8) |
   | Software | 2005-2008 | [XXXXX] (#anchor 9) |
   | CAE | 2003-2005 | [XXXXX] (#anchor 10) |
   | CAE | 2002-2003 | [XXXXX] (#anchor 11) |

 <div id = "anchor 1"> </a>

## Development of remote fishing robot system
### Development and introduction of fishing robot system for Tokyo events
--Compatible technology
  --Development of robot status transition display tool using web application
  --Development of fishing history / images data playback tool using web application
  --Building a data server
  --Remote (VPN wide) network design, device IP configuration and inspection
  --Reference: https://www.youtube.com/watch?v=rJ-qyWjQkr0
  --Network study IpV6 optical communication, 5G, AWS
### Development of virtual fishing robot system
--Compatible technology
  --Unity3D, PUN2
  --Unity <-> Robot device communication

 <div id = "anchor 2"> </a>

## AI-NLP
### Text annotation environment
--Compatible technology
  --Improved based on the text annotation tool brat. javascript / python / Git (auto commit)
  --Create an original DataSet
### Linking text tagging environment with DNN forecasting
--Compatible technology
  --transformer / pytorch, NFS, Japanese BERT Model (Kyoto Univ.)
  --This technology enables automatic text annotation (sentence analysis)

 <div id = "anchor 3"> </a>

## AI solution
### Development of automatic picking robot
--Used arm
  --Denso Wave arm
    ――Although it can be operated with 6-axis tating, there are many singular points depending on the posture, and it was inconvenient to set the target position automatically by AI (image recognition).
--Compatible technology
  --Hand design support. Designed a work contact rotation control mechanism (belt gear) with 1-axis control using a motor. Uses FreeCAD.
  --Support to make Mask-RCNN, an AI program, a resident program. Since tensor-flow is used, it is started for the first time, and when an input image is given, only inference is performed.
### Pharmaceutical process automation robot
--Used arm
  --Denso Wave arm
    --The cause of the demonstration experiment being stopped due to the overload of the motor was identified as overweight of the hand part.
--Compatible technology
  -Supports hand weight reduction. The heavy hand made of SUS is made of aluminum (titanium). Difficult because there are only partial drawings.

<div id = "anchor 4"> </a>

## Development of robot hand
--Technology used
& ensp; & ensp; A certain university haptics laboratory
--Corresponding area
  --Software (Small PC: raspberry pi): Program Python / C Connection: GPIO / UART / USB
  --Software (microcomputer: esp32, stm32): Program C / C ++ Connection: GPIO / UART / SPI
  --Hardware (control board): Connection wiring with the microcomputer
  --Network (for IoT): Internet connection of small devices UDP, TCP network measures
    Short-range Wifi connection or long-range Global IP (IP limit) connection
--Supported functions
  --Master / slave bilateral control
    --Connect the general-purpose board to the Raspberry Pi (3B +) via USB (UART) to communicate between the Raspberry Pi.
      I used Python for the program, but I gave up because it was too late to get it at the communication interval of 1msec. After that, the C language version is diverted.
  --Gravity guarantee with multi-axis arm configuration
    --For axes whose motor rotation axis is different from that in the vertical direction. For a medical 7-axis robot, the angle components for 2 axes are combined with 1 axis that has a vertical angle component, and A * Cos (θ1-θ2) cancel input implementation: A is the measured value at a specific angle.
  --Route planning
    --Manually check the range of motion of each axis when making each setting for a medical 7-axis robot. Program control was possible, but there is a real stopper.
  --Moment of inertia setting, gain tuning (position, speed)
    --Basic gain tuning is auto-tuning by setting the motor with the software attached to a certain company's motor driver. Manually set from there where the position fixing does not overshoot. The moment of inertia cannot be set with the design value, and it will be in a violent seesaw state, so manually set the place where the sensitivity settles down with a low setting.
  --Verification of communication in general-purpose board (including confirmation of control cycle)
    --Use an oscilloscope (voltage confirmation and timing analysis) or protocol analyzer (SPI).
    --Use FTDI High Speed ​​for UART conversion.
    --The internal UART / SPI protocol is unique and uses the SDK (partially modified).
  --UI (Potato Chip Grab Hand)
    --Create a UI + demo control program that programs with PySide using the touch panel display for Raspberry Pi (3B +) to start, stop, record, and play back latte.

 <div id = "anchor 5"> </a>

## FA
### LCD TV inspection
--Technology used
  --Image processing (using a library dedicated to a certain company)
--Compatible technology
  --C #, MELSEC-Q, CC-Link, modbus (rewriting from pymodbus to C #), Giga-E

 <div id = "anchor 6"> </a>

## A certain company Yokohama Research Institute
### Development of reliability evaluation method for AI system
--Tools used
  --TensorFlow / Keras / Chainer, OpenCV, Python, SKLearn, Numpy
--Compatible technology
  --Adversarial Examples
--Sample used
  --mnist, traffic road sign
### Development of accuracy verification technology for 3D sensors
--Tools used
  --FreeCAD, Python, Gocator
--Compatible technology
  --FreeCAD improvement

 <div id = "anchor 7"> </a>

## Semiconductor chip test process
### Software development for CMOS image sensor verification
--Technology used
  --Image processing (point defects, line defects, use of convolution in Bayer array, etc.)
--Compatible technology
  --Development of test automation software for TeraDyne semiconductor testers
  --ExcelVBA, .NET basic, C #, IG-XL

 <div id = "anchor 6"> </a>

## DRAM development (semiconductor manufacturer)
### Development of verification software for 10-year warranty (in-house only)
--Technology used
  --Hpsice, Hsim, SmartSpice, BSIM4, degraded model
--Compatible technology
  --Development of a system that can verify the circuit operation after 10 years by transient analysis (SPICE) of transistor hot carrier aging deterioration. The conversion formula based on the actual measurement (DC life) is directly implemented in the Tr model code such as BSIM4.
  --Co-developed with members of USA, the developer of C ++, Spice vendor, Exceed, Red Hat Enterprise Linux

### Development of circuit layout (wiring) verification software (in-house software)
--Technology used
  --Virtuoso System Design Platform, Star-RCXT, CalibreDRC
--Compatible technology
  --Development of tungsten transfer wiring checker. Tool name WINET. Large-scale data analysis that searches by regarding the wiring branch of the circuit in the chip as a tree structure. Wiring resistance is extracted by the actual load tool. GUI is the result display on Virtuoso. In 2014, this system was ported to Micron's design environment through integration with Micron. Work with managers in Texas and Idaho.
  --C ++, multi-CPU (2CPUjob * 32), GPGPU (unused for recursive processing), Exceed, Red Hat Enterprise Linux

### Development of circuit layout (wiring) verification software (in-house software)
--Technology used
  --Virtuoso System Design Platform, Star-RCXT, CalibreDRC
--Compatible technology
  --Development of current density layout verification system for electromigration, which is a factor of deterioration of semiconductor wiring.
  --C ++, multi-CPU (2CPUjob * 32), GPGPU (unused for recursive processing), Exceed, Red Hat Enterprise Linux

### TCAD software operation
--Technology used
  --Sentaurus (Process Simulator / Device Simulator)
--Compatible technology
  --In-house deployment and support of cases that can be newly analyzed due to new devices (PRAM) and new functions (quantum effect related).
  --Design of experiments
--Patent application
  --Japanese Patent Laid-Open No. 2012-164038

<div id = "anchor 9"> </a>

## Software Development
### CAE Seismic Intensity Analysis System GUI Development
--Compatible technology
  --GiD (CAD, CAE), Tcl / Tk and CAE solver compatible parts are C ++
### Development of C language-based high-level synthesis tool for ASIC / FPGA design
--Development tools
  --CyberWorkBench (C-based)
--Compatible technology
  --The development language of high-level logic synthesis tools is also C language
  --Qt, veilogHDL / VHDL

<div id = "anchor 10"> </a>

## CAE
### Collision safety performance evaluated by CAE
--Development model
  --2006 release Move
--Compatible technology
  --LS-DYNA, Toyota in-house CAD, strength of materials, collision safety body, finite element method, NEC SX ,, Octane2 WS

<div id = "anchor 11"> </a>

## CAE
### 3DCAD / CAE
--Compatible technology
  --3D modeling for collision / strength ,, Toyota in-house CAD, ANSA

<div id = "anchor Z"> </a>

## Part-time job (day labor etc)
--Picking in Amazon warehouse (clothes), picking in drugstore warehouse (drinks, detergent), picking in frozen warehouse (winter, kneaded products), ground improvement work (design, construction assistance), Tochu tea (cultivation, using industrial equipment) Drying process), TEPCO call center, caterer (Tokyo warehouse, French)

## Education
Shinshu University
Bachelor's degree, Physics, 