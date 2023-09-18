
- Produce documentation that allows design to be manufactured and assembled
- Needs to evidence performance of design to client 
	- Also to show design performs like i have claimed
- Golden level is to allow another party to completely reproduce my design
- If design is reproduced it needs to be able to prove to them that their reproduction performs similar to my original design
- Capturing design intend. Rationale for why i selected a certain value or type of component to have in my circuit

Audience
---
- other engineers
	- Might be working with as part of a team reviewing my work
	- Design reviews of a schematic, simulation 
	- Assessing design against technical standards
	- Electrical circuit will have to be housed, so mechanical engineers aswel

* Manufacturers
	- Document parts
	- Printed circuitboard
	- Assembled with the parts and components

- Customers
	- Functional specifications of your design
	- More interested in external performance
	- Evidence that my design does what it says it does

- Others
	- Marketing or sales groups
	- People ordering the parts and budgets
	- People servicing and repairing design


Design Intent
--

HOW you document your design matters
- The way you draw your schematic 
	- Choice of symbols - using conventional symbols
	- Placement of components/ subcircuits
		- Points towards design intend implicitly, showing how you meant subcircuits to work together 
-  The way you annotate your documentation 
	- Descriptions, comments, captions, scales etc

Drawing a schematic
---
- Use meaningful component prefixes and net names (resistor = R(resistor number), C - capacitor, U for subcircuits)
- Group sections of your circuit together in functional subsections
- Keep component orientation consistent 
- Use graphical layout of circuit to convey function
	- Power supplies at top, ground at bottom, signal flow left to right
- Name important nets using net labels
- Use power ports for power rails
- Annotate circuit with comments, labels to show important design intent
- Use net labels instead of wires where you can


Presenting a PCB layout
--

- Has a number of layers
	- Only show necessary levels
	- For example to show connectivity only show copper, pads and silkscreen
	- For multi layer designs show both sides
	- A legend might be needed for complex boards
- Print to scale, use dimensions to indicate scale (0.5 scale for example)
- For complex, multilayer boards you need to document your pcb stackup (layers, thickness etc)
- Inverting colours to be more readable
Validation
Print design on paper on 1:1 scale and compare to physical components

2nd vid - EAGLE demonstration


Documenting a simulation circuit
---
To reproduce circuit you need
- Circuit
- Model details
- simulation command
- signals to plot
Most of these details are captured in the netlist

LTSpice tips and tricks
- use the .EMF format to export circuits and plots
	- Vector file format
	- Imports best into microsoft word
	- Size of window when importing effects font scaling
- You can add comments to your circuit
	- * or ; to change directive into comment
- You can scale plots manually
- Add second plot plane, change trace colours


Presenting oscilloscope captures
--
- Ensure scaling is appropriate (voltage and time)
	- Should be consistent across multiple captures
	- Consistency with simulation plots allows comparison (AND oscilloscope, compare the two)
- Figure captions should include details of channels, scaling and pertinent measurements
	- Oscilliscope
		- Details of channels and probes
		- Horizontal scale
		- What channel shows what graph
		- what the trace shows and name values
- Scope measurements can be used to annotate traces
- Inverting colours for improved readability

NEED to validate claims and behaviours