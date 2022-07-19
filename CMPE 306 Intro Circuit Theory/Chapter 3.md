# Chapter 3 Methods of Analysis
## Node-Voltage Method (based on KCL)
1. Pick a reference node (also called common or ground)
2. Define node voltages --- the voltage at non-reference node above the reference node
3. Express currents through resistors in terms of node voltages
	- i = (v<sub>higher</sub> - v<sub>lower</sub>) / R
	- Consistent with passive-sign convention
4. Apply KCL at each non-reference node
	- sum leaving currents to zero
- ### Super-node
	- When there is a voltage source (independent or dependent) ==directly== between two non-reference nodes.
	- To by-pass the issue of the current through the voltage source:
		- Form a super-node that contains the two involved nodes.
		- Write KCL at the super node
		- Write an equation that relates the voltage source to the node voltages.
	- When a voltage source is connected ==directly== between a non-reference node and the reference node, that node-voltage known from the voltage source
## Mesh Current Method (Based on KVL)
1. Define mesh currents around each mesh
2. Express voltages across resistors in terms of mesh currents (using Ohm's law)
3. Apply KVL around each mesh 
- ### Super-mesh
	- When there is a current source (independent or dependent) in a branch that is shared by two meshes.
	- To by-pass the issue of the voltage across the current source:
		- Form a super-mesh from the two involved meshes (ignore the branch with the current source).
		- Write KVL around the super-mesh (with originally defined mesh currents)
		- Write an equation that relates the current source to the two mesh currents.
	- When a current source is in a branch that is ==not shared== with another mesh, that mesh current is known for the current source