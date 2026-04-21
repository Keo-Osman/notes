---
tags:
  - CS
---
# Von Neumann Architecture
1. Uses one memory location for both data and instructions.
2. *Requests* next instruction/data from memory with unidirectional address bus.
3. Data or instructions are sent to the CPU via the data bisectional bus. The SPU can send data to be stored in memory via this.
# Harvard Architecture
1. Memory and data are stored/treated separately. Can also have different caches for instructions and data - generally only split on L1 level. L2 is for both.
***
# The CPU
1. ALU
	1. Performs calculations.
2. Control Unit (CU)
	1. Fetches and decodes instructions.
	2. Issue control signals to hardware.
	3. Regulate timing using clock.
3. Clock
	1. Rapidly alternate between 1 and 0 to sync all CPU operations.
4. Registers
	1. Program Counter - Stores memory address of next instruction.
	2. Memory Address Register - contains address of memory that is to be read or written.
	3. Current Instruction Register - stores the current instruction whilst executing.
	4. Memory Data Register - stores the data which is fetched from memory.
	5. Accumulator - stores results from ALU.
	6. CPU also has general purpose registers - typically 8.
5. Bus - Collection of parallel wires to pass data between components.
	1. Address bus
		1. Connects CPU *specifically the MAR* to RAM to fetch memory.
	2. Data bus
		1. Where memory is transferred to and from RAM on.
	3. Control bus
		1. Sends different control signals to various components. 
		2. Sends read/write signal to RAM.
***
# Fetch, Decode, Execute Cycle
1. Fetch
	1. The PC is copied to the MAR.
	2. A read signal is sent across the control bus and the data in the MAR is sent across the address bus.
	3. The program counter is incremented by 1 to point to the next instruction.
	4. Instruction from RAM returns to CPU via the data bus arriving at the MDR.
	5. The MDR is copied into CIR.
2. Decode
	1. The instruction in the CIR is decoded by the decoder in the CU.
3. Execute
	1. The instruction is then executed - either by the ALU and/or will fetch memory.
***
# Memory and Storage
## SSD
1. Uses flash memory consisting of parallelly wired NOR gates or serially wired NAND gates.
2. Comprised of floating gate transistors.
3. Current is passed along the bit and word line to activate flow of electrons from source to drain.
## Magnetic
1. Contains platters/discs.
2. Coated in a special magnetic coating.
3. Binary data represented by changing magnetic orientation.
4. Read write head for each side of the plater.
## Optical
1. Data is stored on a single spiral track.
2. Disk rotates at a high speed.
3. Laser head moves across the radius of disc.
4. Made of pits and land.
5. Change form pit to land or vice versa is a 1 as light is reflected differently.
***
# CISC vs. RISC
**CISC** - complex instruction set computer. It is an architecture of CPU with many 


***
***
# Flashcards

What are the components of the CPU and their role?
?
1. ALU
	1. Performs calculations.
2. Control Unit (CU)
	1. Fetches and decodes instructions.
	2. Issue control signals to hardware.
	3. Regulate timing using clock.
3. Clock
	1. Rapidly alternate between 1 and 0 to sync all CPU operations.
4. Registers
	1. Used to store small amounts of data that are needed during processing such as
		1. The address of the next instruction.
		2. The current instruction.
		3. Result of calculations.
	2. Special registers include:
		1. Program Counter.
		2. Memory Address Register.
		3. Current Instruction Register.
		4. Memory Buffer Register.
		5. Status Register.
		6. Accumulator.
5. Bus
	1. Collection of parallel wires to pass data between components.

What is the difference von Neumann and Havard architecture?
?
1. Von Neumann Architecture
	1. Uses one memory location for both data and instructions.
	2. *Requests* next instruction/data from memory with unidirectional address bus.
	3. Data or instructions are sent to the CPU via the data bisectional bus. The SPU can send data to be stored in memory via this.
2. Harvard Architecture
	1. Memory and data are stored/treated separately. Can also have different caches for instructions and data - generally only split on L1 level. L2 is for both.

What is the fetch execute decode cycle?
?
1. Fetch
	1. The PC is copied to the MAR.
	2. A read signal is sent across the control bus and the data in the MAR is sent across the address bus.
	3. The program counter is incremented by 1 to point to the next instruction.
	4. Instruction from RAM returns to CPU via the data bus arriving at the MDR.
	5. The MDR is copied into CIR.
2. Decode
	1. The instruction in the CIR is decoded by the decoder in the CU.
3. Execute
	1. The instruction is then executed - either by the ALU and/or will fetch memory.