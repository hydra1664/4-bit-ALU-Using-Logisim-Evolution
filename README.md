# 4-Bit ALU Design (Logisim Evolution)

## Introduction
This project is a 4-bit Arithmetic Logic Unit (ALU) built in Logisim Evolution.  
It is capable of performing six fundamental arithmetic and logical operations:  
- ADD, SUB, AND, OR, XOR, and NOT(A)  

The ALU is controlled using a 3-bit ALUControl input signal that selects the desired operation through a multiplexer-based logic structure. The design emphasizes modularity, clarity, and testability.

---

## Architecture Overview
The design is modular and structured with the following components:

### Inputs
- A[3:0] → First operand  
- B[3:0] → Second operand  
- ALUControl[2:0] → 3-bit control signal for operation selection  

### Core Functional Units
- Arithmetic Block:  
  - A 4-bit adder/subtractor  
  - Subtraction is achieved by inverting B and adding 1 (via carry-in) using 2’s complement logic  

- Logic Gates:  
  - Bitwise AND, OR, XOR, and NOT(A)  

- Selector (MUX):  
  - A 6-input multiplexer selects the output of the required operation based on ALUControl  

### Outputs
- ALUResult[3:0] → Final selected output  
- Gate Outputs: Individual 4-bit outputs after each operation block (Adder, AND, OR, XOR, NOT)  
  - These were used for internal verification during simulation  

---

## Control Logic
The ALU operation is determined by a 3-bit ALUControl signal.  

| ALUControl | Operation |
|------------|-----------|
| 000 | ADD |
| 001 | SUB |
| 010 | AND |
| 011 | OR  |
| 100 | XOR |
| 101 | NOT(A) |

The control signals directly drive the multiplexer, routing the correct output to the ALU’s main output pin. This makes the design easily expandable for future operations.

---

## Design Decisions
- A single multiplexer was used as the final output selector to keep the design modular and simple  
- Subtraction was handled by inverting B and adding 1, avoiding the need for a dedicated subtractor unit  
- Probes were placed at each block output to verify correctness during simulation  
- Internal verification made debugging and validation easier  

---

## Verification
The ALU was tested with different input combinations:  
- Binary values were applied to A and B while toggling ALUControl  
- Outputs were verified against expected results using probes  
- Edge cases like A < B in subtraction, resulting in negative values in 2’s complement, were also tested  
- Screenshots of simulation outputs were taken for all operations  

---

## Simulation Results
Figures below show the ALU’s behavior for each operation.  

- ![ADD Operation](images/add.png)<img width="1920" height="1079" alt="ADD" src="https://github.com/user-attachments/assets/69989e43-9512-4572-840c-8308b8646c36" />

- ![SUB Operation](images/sub.png)  
- ![SUB Operation (Negative)](images/sub_negative.png)  
- ![AND Operation](images/and.png)  
- ![OR Operation](images/or.png)  
- ![XOR Operation](images/xor.png)  
- ![NOT(A) Operation](images/not.png)  

(Screenshots are stored in the /images/ folder of this repository.)

---

## Repository Contents
- 4_Bit_ALU.circ → Logisim Evolution circuit file of the ALU  
- /images/ → Screenshots of ALU operations (ADD, SUB, AND, OR, XOR, NOT)  
- README.md → Project documentation  

---

## Conclusion
The ALU design demonstrates correct implementation of 4-bit arithmetic and logic operations using a clean and modular approach.  
It is easy to extend with additional operations and was verified through simulation and internal probes.  
This project was a good way to explore digital design principles and practice hardware logic design using Logisim Evolution.
