# CMOS_Circuit_SPICE_Generator
The goal of this project is to implement a program that generates the part of a SPICE netlist (also 
known as a SPICE deck) that describes a CMOS circuit realizing an arbitrary Boolean function provided by the user. 

# A very brief description of SPICE decks:
A SPICE deck is a file starting with a title statement (one line) which is mostly ignored by SPICE simulators. It ends 
with the “.END” statement. In between, there are 3 parts which can appear in any order. For the purposes of this 
project, the most important part (usually appearing immediately after the title) is the data statements part which 
lists the circuit components including how they are interconnected and their models if needed. The SPICE deck also 
contains control statements which specify the type of analysis to perform on the circuit and output statements
which specify which signals should be monitored and displayed. Any line starting with an asterix “*” is considered 
a comment and ignored by the simulator. Long statements spanning more than one line should be split using the 
plus “+” symbol used in the beginning of a line to indicate that this line is a continuation of the previous one.

In the data statements part, each circuit component is given a label (just an identifying name). The same applies to 
each circuit node (also known as a wire or net). Each component is described by a single statement specifying its 
label, the labels of the nodes it is connected to, and any component specific parameters needed. Note that numbers 
can be used as node labels. The ground node is typically labelled as “0”. If two components are interconnected, a 
common node label will appear in both statements describing them. Note that statements order is not important 
as long as all the components are listed.

Since a resistor has two terminals, a basic resistor element statement will look as follows:
Rname net1 net2 value
where:
- Rname: is a label you pick for that resistor; however, it must start by an uppercase R to indicate that this is 
a resistor. 
- net1: is the label of the wire connected to the first resistor terminal 
- net2: is the label of the wire connected to the second resistor terminal 
- value: is the value of the resistor in Ohm

and a basic independent DC voltage source element statement will look as follows:
Vname net+ net- value
where:
- Vname: is a label you pick for that voltage source; however, it must start by an uppercase V to indicate that 
this is a voltage source. 
- net+: is the label of the wire connected to the positive terminal of the voltage source 
- net-: is the label of the wire connected to the negative terminal of the voltage source
- value: is the value of the voltage in Volt
