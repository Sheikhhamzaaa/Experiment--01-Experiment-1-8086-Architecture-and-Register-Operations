# Experiment--01-Experiment-1-8086-Architecture-and-Register-Operations
 
## Aim

To study the architecture of the 8086 microprocessor and write assembly
language programs for register-to-register data transfer, memory
storage, and exchanging two 16-bit memory values.

## Learning Outcomes

After completing this experiment, students will be able to: - Explain
the main functional units of the 8086 microprocessor. - Describe the
roles of the Bus Interface Unit (BIU) and Execution Unit (EU). - Write
8086 assembly instructions for 16-bit data transfer. - Exchange data
between two memory locations using registers.

## Software Required

-   An 8086 assembly emulator, such as emu8086 or an equivalent
    8086-compatible emulator.
-   A text editor for writing the assembly programs.

------------------------------------------------------------------------

## Part (a): 8086 Architecture and Functional Units

### Question

Explain the architecture of the 8086 microprocessor with a neat block
diagram, describing the functions of the BIU and EU.

###Answer

The 8086 microprocessor has two main parts called the BIU (Bus Interface Unit) and the EU (Execution Unit). Both units work together to make the processor work faster. The BIU fetches instructions from memory and stores them in a 6-byte queue, which acts like a waiting area for instructions. The EU takes these instructions from the queue and executes them. While the EU is busy executing one instruction, the BIU can fetch the next instructions from memory and keep them ready in the queue. When the EU needs to read or write data from memory or perform an input/output operation, it asks the BIU to do the required work. If a jump instruction changes the normal flow of the program, the instructions already waiting in the queue are cleared, and the BIU fetches new instructions from the new location. In this way, the BIU and EU work together instead of waiting for each other, which helps the 8086 microprocessor execute instructions faster.

### Simplified Block Diagram

          +-------------------------------------------+
          |           8086 MICROPROCESSOR             |
          |                                           |
          |  +-------------------+----------------+   |
          |  | BUS INTERFACE UNIT| EXECUTION UNIT |   |
          |  |      (BIU)        |     (EU)       |   |
          |  |                   |                |   |
          |  | +---------------+ | +------------+ |   |
          |  | | Segment       | | | Instruction| |   |
          |  | | Registers     | | | Decoder &  | |   |
          |  | | CS, DS, SS, ES| | | Control    | |   |
          |  | +---------------+ | | Logic      | |   |
          |  |                   | +------------+ |   |
          |  | +---------------+ |                |   |
          |  | | Instruction   | | +------------+ |   |
          |  | | Pointer (IP)  | | |    ALU     | |   |
          |  | +---------------+ | +------------+ |   |
          |  |                   |                |   |
          |  | +---------------+ | +------------+ |   |
          |  | | 6-Byte        | | | General    | |   |
          |  | | Instruction   | | | Purpose    | |   |
          |  | | Queue         | | | Registers  | |   |
          |  | +---------------+ | | AX, BX, CX,| |   |
          |  |                   | | DX         | |   |
          |  | +---------------+ | | SP, BP, SI,| |   |
          |  | | Address       | | | DI         | |   |
          |  | | Generation &  | | +------------+ |   |
          |  | | Bus Control   | |                |   |
          |  | +---------------+ | +------------+ |   |
          |  |                   | | Flag       | |   |
          |  |                   | | Register   | |   |
          |  |                   | +------------+ |   |
          |  +---------+---------+----------------+   |
          |            |                              |
          +------------|------------------------------+
                       |
                 SYSTEM BUS
          (Address, Data & Control)
                       |
                +--------------+
                | Memory & I/O |
                |   Devices    |
                +--------------+

### Working Principle

### Working Principle

The BIU (Bus Interface Unit) fetches instructions from memory and stores them in its 6-byte instruction queue. Meanwhile, the EU (Execution Unit) takes instructions from the queue, decodes them, and executes them. While the EU is executing instructions, the BIU can fetch the next instructions from memory, allowing both units to work simultaneously. When the EU needs to read or write data from memory or access an I/O device, it requests the BIU to perform the required bus operation. If a jump instruction changes the flow of the program, the existing instructions in the queue are cleared, and the BIU fetches new instructions from the updated location. This process reduces waiting time and improves the overall speed of the 8086 microprocessor.

------------------------------------------------------------------------

## Part (b): Transfer a 16-bit Value Between Registers and Store It in Memory

### Question

Write an 8086 assembly language program to transfer a 16-bit data value
from one register to another and store the result in memory.

### Algorithm

1. Initialize the data segment register.
2. Load the 16-bit value 1234H into register AX.
3. Copy the contents of AX into register BX.
4. Store the contents of BX in the memory variable RESULT.
5. Terminate the program


### Assembly Program

<img width="1150" height="628" alt="image" src="https://github.com/user-attachments/assets/dfeafb44-1d54-40d5-8b8c-3dfdbb0631e8" />
### Expected Result

<img width="415" height="340" alt="image" src="https://github.com/user-attachments/assets/b426b02f-0b9d-4059-b26c-92f48b02e773" />

### Explanation

Explanation
First, the program initializes the data segment register. The instruction MOV AX, 1234H loads the 16-bit value 1234H into AX. Next, MOV BX, AX copies the value from AX into BX without changing AX. Then, MOV RESULT, BX stores the value in BX into the memory variable RESULT. Finally, MOV AH, 4CH and INT 21H terminate the program.


------------------------------------------------------------------------

## Part (c): Exchange Two 16-bit Memory Locations Using Registers

### Question

Write an 8086 assembly language program to exchange the contents of two
16-bit memory locations using registers.

### Algorithm

1)Initialize the data segment register.
2)Load the first memory value into register AX.
3)Load the second memory value into register BX.
4)Store the value in BX at the first memory location.
5)Store the value in AX at the second memory location.
6)Terminate the program.

### Assembly Program

<img width="1160" height="710" alt="image" src="https://github.com/user-attachments/assets/f3e19822-7598-4997-a136-a5360f2f7ace" />

 

### Expected Result

<img width="426" height="436" alt="image" src="https://github.com/user-attachments/assets/73a8980f-f335-43b1-ae7b-da4ac0a85c8a" />

### Explanation

First, the data segment register is initialized to access the data stored in memory. The first memory value is loaded into the AX register, and the second memory value is loaded into the BX register. Next, the value in BX is stored in the first memory location, and the value in AX is stored in the second memory location. In this way, the two memory values are exchanged using the AX and BX registers. Finally, the program is terminated.

## Procedure

1)Open an 8086-compatible assembler or emulator.
2)Create a new assembly language file.
3)Type the given 8086 assembly language program.
4)Assemble the program and correct any errors if present.
5)Execute the program using the emulator.
6)Check the register values and memory contents after execution.
7)Record the output and verify that it matches the expected result.
## Screenshot of the results 

<img width="426" height="436" alt="image" src="https://github.com/user-attachments/assets/73a8980f-f335-43b1-ae7b-da4ac0a85c8a" />

## Result

The architecture of the 8086 microprocessor and the functions of the BIU and EU were studied. The 8086 assembly language programs were executed to understand the transfer of 16-bit data between registers and memory, as well as the exchange of two 16-bit values stored in memory.


## Viva Voce Questions

1.  What is the function of the BIU in the 8086?
2.  What is the role of the EU?
3.  Why does the 8086 use a 6-byte instruction queue?
4.  What is the maximum physical memory address space of the 8086?
5.  What is the difference between a register and a memory variable?
6.  Does the `MOV` instruction change the source operand?
7.  Why are registers used when exchanging two memory values?
8.  What is the purpose of the DS segment register?

 
` 
