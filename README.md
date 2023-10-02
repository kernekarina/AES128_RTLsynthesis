# AES128_RTL Logical and Physical Synthesis
### Logical and physical synthesis of a 128-bit encryption core, AES128, starting from an RTL available on the OpenCores website and synthesis tools from the company Cadence.

The following steps were taken to perform the correct synthesis flow

#### Logical Synthesis

Logical synthesis is a critical step in digital design that translates a hardware description
high-level in a port-level netlist. At this stage, independent mapping is carried out
of the technology used, some optimizations that depend on the technology and the insertion of the chain
of Scan Chain.
A time analysis was carried out to verify whether the design complies with the requirements. 
At this point, the test chain of the Scan-chain type is inserted into the RTL file of the
AES128 module or input scan enable.

#### Physical Synthesis

In the physical synthesis stage, the logical synthesis is integrated with positioning. Uses-
if the flow with PLE and QoS prediction.
The first step to start the physical synthesis was adding the PADs to the datapath.v file
which is generated in the layout folder after the logical synthesis.

Then the creation of the IO file begins through Innovus. When importing the design, the import options open and in this
At this point, .lef files are added. These are the files that carry the information of the
libraries that will be used, in reference to the metal layers, core cells and models of the
PADs.
In the .io file it is possible to observe that each PADS instance presents offset values
automatically generated and that the file is divided into blocks (left, top, bottom and right). These
blocks define the positioning of the PADs on each side in the layout following the nomenclature of the
blocks [3].
To execute the physical synthesis, some parameters are defined, as shown in Figure 8, in the
physical syn.tcl file which is the file that contains the script for executing physical synthesis in
Innovus. These parameters limit the space of the circuit and with these conditions the tool
Menta performs the best possible positioning

#### LEC

Logical Equivalence Checking (LEC) is a formal verification technique used in
digital design and verification to ensure that two different representations of a design, nor-
Normally an RTL design and a port-level netlist are functionally equivalent.


### All files used in this synthesis are available in this repository
