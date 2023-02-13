# Hardware Description Language
- Used to simply descibe hardware, not similar to c++ (don't think that way)
- A high level of abstraction to define the function of a circuit
- Implement a verilog test bench to input stimulus, time and control to verify function of design
- Verilog -> Logic synthesis -> gate netlist -> place and route -> mask
## VHDL
- ADA-like verbose syntax, lots of redundancy (which can be good)
- Very rigid
- Has different types, have to write functions to mix multiple types
- Harder to learn
## Verilog
- C-like concise syntax
- Built-in types and logic representations. Oddly this led to slightly incompatible simulators from different vendors
- Design is composed of ==modules==
### Structural
- Structural models: basically a hierarchical netlist with "primitives" (built-in verilog logic gates, or instances of library modules)
- Instantiation of modules
- Use of gate level primitives
# Language Structure
```Verilog
module <name> (port list);

<parameters>
<port direction>
<internal variables/signals>
```
## Port Direction
- input
- ouput
- inout
## Single net or a bus
- single net: `input siga;`
- 4 bit bus: `input[3:0] busa;`
# Signal
## Types
- `wire`
- `reg` - variable that represents a register or a data storage element, typically used for outptuts of precedural statements
- `int` - integer value, is a 32-bit wide data type
- `real` - values with decimal or in scientific notion
	- Used in test benches
	- not synthesizable
## Values
- 1
- 0
- Z - high impedance state that is neither 0 or 1
- X - unknown state
# Parameters
- Variables that can defined at instantiation of a module
- Facilities reuse of a module for multiple applications
- Defines common variables for consistency in code
# Internal 
## Variables/Signals
- Variables used within the module
- Signals that connect gates within the module
- Signals that represent outputs of operations
- Same data types as ports
## Functions
- Describes the functions of the circuit
- Two types of function statements that can be synthesized
- Assign statement
	- Continuous assignment
	- Asynch logic
	- Can be used for a single bit or bus
- Procedural statment
	- Implemented with an "always" block
	- Sensitivity list - list of signals that will "trigger" execution of the "always" block
	- Combinational or sequential
# Operators
- Unary - one operand
- Binary - two operands
- Ternary - 3 operands
# Blocking vs. Non-Blocking
## Blocking
- Blocks execution of next statement until current statement completes