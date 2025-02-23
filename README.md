<details>
<summary> <b>Task 1:</b> The task requires an in-depth review of lab videos on C programming and the RISC-V architecture to develop a strong understanding of both subjects. After completing the review, the  C program is compiled using two different compilers: the GCC compiler and the RISC-V compiler. This exercise will demonstrate the understanding of the compilation process by allowing the user to compare how each compiler converts the C code into machine code. Through this comparison, identification of differences in the compilation process and the unique characteristics of each architecture can be done..</summary> 
<br>
Task is to refer to C based and RISCV based lab videos and execute the task of compiling the C code using gcc and riscv compiler.

**C Language based LAB**

**C and RISC-V Based Labs**

This repository showcases the steps involved in compiling C programs and generating assembly code using both a standard GCC compiler and a RISC-V GCC compiler. It provides detailed instructions and explanations to guide users through each phase of the compilation and debugging process.

**C Language-Based Lab**

Steps to Compile a .c File on a Local Machine:

1. Open the Bash terminal and navigate to the desired directory.
2. Use the following command to create and edit a new .c file:
   ```sh
   leafpad sum1ton.c


**Steps to Compile a .c File on our Machine:**
 ```sh
 gcc sum1ton.c
 ./a.out
```

 
Compilation and execution complete.
 
![2](Task1/Cprogram.png)
RISC-V Based Lab

**Steps to Compile Using RISC-V GCC Compiler:**
1. Ensure the RISC-V GCC compiler is installed and accessible on the system.
2. Verify the .c file contents using the cat command:
   ```sh
   cat sum1ton.c


3. Compile the C program for RISC-V architecture using 01 option:
 ```sh
riscv64-unknown-elf-gcc -o1 -mabi=lp64 -march=rv64i -o sum1ton.o sum1ton.c
```
4. Disassemble the object file to view its assembly code using:
 ```sh
riscv64-unknown-elf-objdump -d sum1ton.o
```
5. Minimize the assembly by using following code:
```sh
riscv64-unknown-elf-objdump -d sum1ton.o | less
```
   a)Extract the main function's assembly code by using:
   ```sh
/main
```
6. Use /main in the terminal to locate the main function in the assembly output.
![4](Task1/Riscwitho1.png)

7.Compile the C program for RISC-V architecture using ofast option:
```sh
riscv64-unknown-elf-gcc -Ofast -mabi=lp64 -march=rv64i -o sum1ton.o sum1ton.c
```
8.Disassemble the object file to view its assembly code using:
```sh
riscv64-unknown-elf-objdump -d sum1ton.o
```
9.minimize the assembly by using following code:
```sh
riscv64-unknown-elf-objdump -d sum1ton.o | less
```
 a) Extract the assembly code **main** function using:
 ```sh
  /main
```
10. Use /main in the terminal to locate the main function in the assembly output.
![4](Task1/Riscwithofast.png)

Explanation of Key Commands and Options: 
1. -mabi=lp64: Specifies the Application Binary Interface (ABI) for 64-bit integers, pointers, and long data types, tailored for the 64-bit RISC-V architecture.

2. -march=rv64i: Defines the 64-bit RISC-V base integer instruction set architecture.

3. -O1: Enables basic optimization to improve performance without significantly increasing compilation time.

4. -Ofast: Applies extensive optimizations for maximum speed improvements.

5. riscv64-unknown-elf-objdump: A disassembly tool for analyzing RISC-V binaries and debugging code efficiently.
 
   </details>


---

<details>
<summary> <b>Task 2:</b> This task requires an analysis of lab videos on both C programming and the RISC-V architecture to develop a thorough understanding of compiling C code for different architectures. After completing the review, the process of compiling C code must be carried out using two distinct tools: the GCC compiler and the RISC-V compiler simulator. This will demonstrate the ability to work with both compilers while providing insights into how each translates C code into machine-readable instructions specific to its respective architecture.</summary> 
<br>

Task is to analyze the SPIKE simulation performance using RISC-V GCC with -O1 and -Ofast optimization levels.  

*SPIKE Simulation and Compiler Optimization*

This repository showcases the process of compiling a C program with RISC-V GCC, running it in the SPIKE simulator, and analyzing performance differences between optimization levels (`-O1` and `-Ofast`). It provides detailed instructions and explanations to enhance understanding. 

**Steps to Complete the Task**  

1.Write a Simple C Program  

2.The following program calculates the sum of numbers from 1 to 100:  

3.Compile Using RISC-V GCC

4.Compile with -O1 Optimization.

*Use the following command to compile the program with the -O1 optimization flag:*
```sh
riscv64-unknown-elf-gcc -O1 -mabi=lp64 -march=rv64i -o sum1ton.o sum1ton.c
```
**Disassemble Object Files to View Assembly Code(in new terminal)**
*Generate Dump for -O1 Optimization*
```sh
riscv64-unknown-elf-objdump -d sum1ton.o
```
*Minimize the assembly by using following code:*
```sh
riscv64-unknown-elf-objdump -d sum1ton.o | less
```
![main program for O1 option](Task2/objdump_o1.png)


**Run SPIKE Simulation**
*Run a compiled RISC-V program on the SPIKE simulator in non-debug mode.*
```sh
spike pk sum1ton.o
```
*Invoke the debug mode of the SPIKE RISC-V simulator.*
```sh
spike -d pk sum1ton.o
```
![compiling with O1 option](Task2/o1_debug.png)


**Compile with -Ofast Optimization.**
*Use the following command to compile the program with the -Ofast optimization flag:*
```sh
riscv64-unknown-elf-gcc -Ofast -mabi=lp64 -march=rv64i -o sum1ton.o sum1ton.c
```
**Disassemble Object Files to View Assembly Code(in new terminal)**
*Generate Dump for -Ofast Optimization*
```sh
riscv64-unknown-elf-objdump -d sum1ton.o
```
*Minimize the assembly by using following code:*
```sh
riscv64-unknown-elf-objdump -d sum1ton.o | less
```
![main program for ofast option](Task2/objdump_ofast.png)


**Run SPIKE Simulation**
*Run -O1 Binary in SPIKE*
```sh
spike pk sum1ton.o
```
*Invoke the debug mode of the SPIKE RISC-V simulator*
```sh
spike -d pk sum1ton.o
```
![compiling with Ofast option](Task2/ofast_debug.png)


**After(spike -d pk swift.o) Observe the Instructions:**

1)After loading, SPIKE initializes and displays the Program Counter (PC) and Stack Pointer (SP).

2)Press Enter repeatedly to step through the execution.

3)Each press displays the next instruction executed by the program.

4)The displayed instructions directly correspond to the C code of the main program, providing insights into the program's execution flow.
**Explanation of Key Commands and Options:**

1. spike:RISC-V simulator that runs RISC-V programs on a virtual machine.

2. pk:Proxy kernel that acts as a minimal runtime environment for RISC-V programs, handling system calls like I/O and memory management.

3. sum1ton.o:The compiled RISC-V binary of your program (created using a RISC-V GCC compiler).

4. -d (for debugging):Debugging mode in SPIKE, allows stepping through the instructions and inspecting the program's behavior.

5. riscv64-unknown-elf-gcc:RISC-V GCC compiler used to compile the C program into a RISC-V object file (.o).

6. -O1, -Ofast: Compiler optimization flags:
      a.-O1: Basic optimizations for performance.
      b.-Ofast: Extensive optimizations for maximum speed.

7. riscv64-unknown-elf-objdump:Disassembles RISC-V binaries to examine assembly code.

These tools together enable compiling, running, and debugging RISC-V programs on a simulated environment.

</details>

---

<details>
<summary><b>Task 3:</b> The objective is to examine and classify each given instruction according to its type—whether it belongs to the R-type, I-type, or J-type category. After categorization, each instruction must be converted into its corresponding 32-bit machine code while adhering to the specific encoding format and opcode structure of the target architecture. The final output should present a comprehensive mapping of the instructions along with their correctly formatted binary representations.</summary>

This repository contains a list of 15 unique RISC-V instructions extracted from the assembly code along with their corresponding 32-bit instruction codes. These instructions cover different instruction formats, such as **U-type**, **I-type**, **J-type**, **B-type**, and **R-type**.


# RISC-V Instructions

This README contains a table of 15 unique RISC-V instructions, their machine codes, opcodes, formats, and instruction binaries for my assembly codes.

| Instruction                | Opcode  | Format | Machine Code | Instruction Binary                          |
|----------------------------|---------|--------|--------------|----------------------------------------------|
| lui a0, 0x21              | 0110111 | U-type | 0x00021537   | 00000000000000100001010100110111            |
| addi sp, sp, -16          | 0010011 | I-type | 0xff010113   | 11111111000000010000000000010011            |
| li a2, 720                | 0010011 | I-type | 0x2d000613   | 00000010110100000000011000010011            |
| addi a0, a0, 384          | 0010011 | I-type | 0x18050513   | 00000001100001010000010100010011            |
| sd ra, 8(sp)              | 0100011 | S-type | 0x00113423   | 00000000000100011010010000100011            |
| jal ra, 10408             | 1101111 | J-type | 0x340000ef   | 00000011010000000000000011101111            |
| ld ra, 8(sp)              | 0000011 | I-type | 0x00813083   | 00000000100000011000000010000011            |
| ret                       | 1100111 | I-type | 0x00008067   | 00000000000000001000000001100111            |
| auipc a5, 0xffff0         | 0010111 | U-type | 0xffff0797   | 11111111111111110000011110010111            |
| beqz a5, 100f4            | 1100011 | B-type | 0x00078863   | 00000000000001111000100001100011            |
| j 101b0                   | 1101111 | J-type | 0x0c00006f   | 00000011000000000000000001101111            |
| lw a0, 0(sp)              | 0000011 | I-type | 0x00012503   | 00000000000000010010010100000011            |
| srai s1, a5, 0x3          | 0110011 | R-type | 0x4037d493   | 01000000001101111010010010010011            |

         

</details>


---
<details>
<summary> <b>Task 4:</b>This task involves simulating the RISC-V Core using the provided Verilog netlist and testbench. You will set up a simulation environment using tools like Icarus Verilog and GTKWave, run the simulation to verify the functional correctness of the core, and analyze output signals. Waveform snapshots of the executed instructions must be captured and uploaded to your GitHub repository along with a brief description, demonstrating your understanding of RISC-V functional simulation and verification.</summary> 
<br>

## 2. BLOCK DIAGRAM OF RISC-V RV32I
![image](https://user-images.githubusercontent.com/110079631/181293948-beb8622c-7696-4b06-b6c9-eeab9b8ab9d3.png)

## 3. INSTRUCTION SET OF RISC-V RV32I
![image](https://user-images.githubusercontent.com/110079631/181298133-60269bc2-01da-4b5c-8b42-69057b8dc15c.png)

# RISC-V Core Functional Simulation 
## 4. FUNCTIONAL SIMULATION

### 4.1 About iverilog and gtkwave
- Icarus Verilog is an implementation of the Verilog hardware description language.
- GTKWave is a fully featured GTK+ v1. 2 based wave viewer for Unix and Win32 which reads Ver Structural Verilog Compiler generated AET files as well as standard Verilog VCD/EVCD files and allows their viewing.

### 4.2 Installing iverilog and gtkwave

- **For Ubuntu**

 Open your terminal and type the following to install iverilog and GTKWave
 ```
 $   sudo apt get update
 $   sudo apt get install iverilog gtkwave
 ```

- **To clone the repository and download the netlist files for simulation , enter the following commands in your terminal.**

 ```
 $ git clone https://github.com/vinayrayapati/iiitb_rv32i
 $ cd iiitb_rv32i
 ```
- **To simulate and run the verilog code , enter the following commands in your terminal.**

```
$ iverilog -o iiitb_rv32i iiitb_rv32i.v iiitb_rv32i_tb.v
$ ./iiitb_rv32i
```
- **To see the output waveform in gtkwave, enter the following commands in your terminal.**

`$ gtkwave iiitb_rv32i.vcd`

### 4.3 The output waveform

 The output waveform showing the instructions performed in a 5-stage pipelined architecture.

## Instructions and Pipeline Details  

Below are the 15 instructions and their corresponding pipeline details:  

---

### 1. `add r6, r2, r1`  
**Purpose:** Add `r2` and `r1`, store the result in `r6`.  
```markdown
Fetch Stage:
  - IF_ID_IR: Holds the `add` instruction.
  - IF_ID_NPC: Holds the next program counter value.
Decode Stage:
  - ID_EX_IR: Ensures the instruction is decoded.
  - ID_EX_A: Value of register `r2`.
  - ID_EX_B: Value of register `r1`.
Execute Stage:
  - EX_MEM_ALUOUT: Result of `r2 + r1`.
  - EX_MEM_IR: Holds the `add` instruction.
Write-Back Stage:
  - WB_OUT: Verifies the result is written to `r6`.
```

---

### 2. `sub r7, r1, r2`  
**Purpose:** Subtract `r2` from `r1`, store the result in `r7`.  
```markdown
Fetch Stage:
  - IF_ID_IR: Holds the `sub` instruction.
Decode Stage:
  - ID_EX_A: Value of register `r1`.
  - ID_EX_B: Value of register `r2`.
Execute Stage:
  - EX_MEM_ALUOUT: Result of `r1 - r2`.
Write-Back Stage:
  - WB_OUT: Verifies the result is written to `r7`.
```

---

### 3. `and r8, r1, r3`  
**Purpose:** Perform bitwise AND between `r1` and `r3`, store the result in `r8`.  
```markdown
Fetch Stage:
  - IF_ID_IR: Holds the `and` instruction.
Decode Stage:
  - ID_EX_A: Value of register `r1`.
  - ID_EX_B: Value of register `r3`.
Execute Stage:
  - EX_MEM_ALUOUT: Result of `r1 & r3`.
Write-Back Stage:
  - WB_OUT: Verifies the result is written to `r8`.
```

---

### 4. `or r9, r2, r5`  
**Purpose:** Perform bitwise OR between `r2` and `r5`, store the result in `r9`.  
```markdown
Fetch Stage:
  - IF_ID_IR: Holds the `or` instruction.
Decode Stage:
  - ID_EX_A: Value of register `r2`.
  - ID_EX_B: Value of register `r5`.
Execute Stage:
  - EX_MEM_ALUOUT: Result of `r2 | r5`.
Write-Back Stage:
  - WB_OUT: Verifies the result is written to `r9`.
```

---

### 5. `xor r10, r1, r4`  
**Purpose:** Perform bitwise XOR between `r1` and `r4`, store the result in `r10`.  
```markdown
Fetch Stage:
  - IF_ID_IR: Holds the `xor` instruction.
Decode Stage:
  - ID_EX_A: Value of register `r1`.
  - ID_EX_B: Value of register `r4`.
Execute Stage:
  - EX_MEM_ALUOUT: Result of `r1 ^ r4`.
Write-Back Stage:
  - WB_OUT: Verifies the result is written to `r10`.
```

---

### 6. `addi r12, r4, 5`  
**Purpose:** Add immediate value `5` to `r4`, store the result in `r12`.  
```markdown
Fetch Stage:
  - IF_ID_IR: Holds the `addi` instruction.
Decode Stage:
  - ID_EX_A: Value of register `r4`.
  - ID_EX_IMMEDIATE: Immediate value `5`.
Execute Stage:
  - EX_MEM_ALUOUT: Result of `r4 + 5`.
Write-Back Stage:
  - WB_OUT: Verifies the result is written to `r12`.
```

---

### 7. `sw r3, r1, 2`  
**Purpose:** Store the value of `r3` into memory address `r1 + 2`.  
```markdown
Memory Access Stage:
  - EX_MEM_ALUOUT: Computed memory address (`r1 + 2`).
  - EX_MEM_B: Value of `r3` to store.
```

---

### 8. `lw r13, r1, 2`  
**Purpose:** Load word from memory address `r1 + 2` into `r13`.  
```markdown
Memory Access Stage:
  - MEM_WB_LMD: Value loaded from memory.
Write-Back Stage:
  - WB_OUT: Verifies the value is written to `r13`.
```

---

### 9. `beq r0, r0, 15`  
**Purpose:** Branch to PC + 15 if `r0 == r0` (always true).  
```markdown
Decode Stage:
  - BR_EN: High (branch taken).
Fetch Stage:
  - IF_ID_NPC: Updated program counter.
```

---

### 10. `add r14, r2, r2`  
**Purpose:** Add `r2` to itself, store the result in `r14`.  
```markdown
Fetch Stage:
  - IF_ID_IR: Holds the `add` instruction.
Decode Stage:
  - ID_EX_A: Value of register `r2`.
  - ID_EX_B: Value of register `r2`.
Execute Stage:
  - EX_MEM_ALUOUT: Result of `r2 + r2`.
Write-Back Stage:
  - WB_OUT: Verifies the result is written to `r14`.
```

---

### 11. `bne r0, r1, 20`  
**Purpose:** Branch to PC + 20 if `r0 != r1`.  
```markdown
Decode Stage:
  - BR_EN: High if `r0 != r1`.
Fetch Stage:
  - IF_ID_NPC: Updated program counter.
```

---

### 12. `addi r12, r4, 5`  
**Purpose:** Add immediate value `5` to `r4`, store the result in `r12`.  
```markdown
Fetch Stage:
  - IF_ID_IR: Holds the `addi` instruction.
Decode Stage:
  - ID_EX_A: Value of register `r4`.
  - ID_EX_IMMEDIATE: Immediate value `5`.
Execute Stage:
  - EX_MEM_ALUOUT: Result of `r4 + 5`.
Write-Back Stage:
  - WB_OUT: Verifies the result is written to `r12`.
```

---

### 13. `sll r15, r1, r2 (2)`  
**Purpose:** Perform logical left shift of `r1` by 2 (specified in `r2`), store the result in `r15`.  
```markdown
Fetch Stage:
  - IF_ID_IR: Holds the `sll` instruction.
Decode Stage:
  - ID_EX_A: Value of register `r1`.
  - ID_EX_SHAMT: Immediate shift value `2`.
Execute Stage:
  - EX_MEM_ALUOUT: Result of `r1 << 2`.
Write-Back Stage:
  - WB_OUT: Verifies the result is written to `r15`.
```

---

### 14. `srl r16, r14, r2 (2)`  
**Purpose:** Perform logical right shift of `r14` by 2 (specified in `r2`), store the result in `r16`.  
```markdown
Fetch Stage:
  - IF_ID_IR: Holds the `srl` instruction.
Decode Stage:
  - ID_EX_A: Value of register `r14`.
  - ID_EX_SHAMT: Immediate shift value `2`.
Execute Stage:
  - EX_MEM_ALUOUT: Result of `r14 >> 2`.
Write-Back Stage:
  - WB_OUT: Verifies the result is written to `r16`.
```


#### *Analysing the Output Waveform of various instructions*  
**```Instruction 1: ADD R6, R2, R1```**  
  
![add](https://github.com/user-attachments/assets/44851b1c-806a-4182-81ab-47af3cf725be)


**```Instruction 2: SUB R7, R1, R2```**  
  
![sub](https://github.com/user-attachments/assets/1104fc06-491a-4e9c-971c-8b51387bd2d6)


**```Instruction 3: AND R8, R1, R3```**  

![and](https://github.com/user-attachments/assets/ddeb5386-04ac-4ea7-a4ee-1e4d2968d2c9)


**```Instruction 4: OR R9, R2, R5```**  

![or](https://github.com/user-attachments/assets/c10ba03d-4f25-49f6-a1c4-b68dde3c1383)


**```Instruction 5: XOR R10, R1, R4```**  

![xor](https://github.com/user-attachments/assets/ed7a6299-92a0-4ed5-b812-97050af83c54)


**```Instruction 6: SLT R1, R2, R4```**  

![slt](https://github.com/user-attachments/assets/d463ee88-c39f-41c3-a4b3-31ee670da5e3)


**```Instruction 7: ADDI R12, R4, 5```**  

![addi](https://github.com/user-attachments/assets/4581b98f-e445-4776-8700-68b03f26131f)


**```Instruction 8: BEQ R0, R0, 15```**  
  
![BEQ](https://github.com/user-attachments/assets/02bbbd72-6d84-4595-a0af-5157524ccdf8)

 
**```Instruction 9:sw r3,r1,2```**

![sw](https://github.com/user-attachments/assets/65fd8529-9b5e-4572-a796-c370ab6b7051)

  
**```Instruction 10:lw r13,r1,2```**  

![lw](https://github.com/user-attachments/assets/58c72387-6ca2-4e15-a7c3-ca68f906ee3f)

**``` Full 5-stage instruction pipeline and pc-increment description Waveform```**

![5-stage instruction pipeline and pc-increment description Waveform](https://github.com/user-attachments/assets/2bce01e3-3405-432d-a1d6-ec359d45d560)



</details>

---

<details>
<summary> <b>Task 5:</b>This smart light system is an intelligent setup designed to control lighting based on the presence or absence of daylight and motion within its detection range. The system utilizes a LDR sensor and an IR sensor to continuously monitor its surroundings for any daylight or movement. When daylight is detected, the system automatically turns OFF the LED. If no daylight is detected, the LED turns ON at 50% brightness. Then the IR sensor comes into use, it detects motion and signals the system to operate the LEDs at full power. This system is widely used in smart street lights for energy conservation and smart city applications.</summary> 
<br>

# Automatic Light System using VSDSquadron Mini RISC-V Board

## Project Overview
An **Smart light system** is a setup designed to automatically control the lighting based on the presence or absence of daylight or motion within its detection range.
### Features:
✅ **Smart Light Control**: Switches light ON oe OFF based on daylight conditions  
✅ **Motion Detected**: LED brightness increases to 100% from it's default 50%   
✅ **Energy Conservation**: Saves energy on street lights    

---

## Required Components  
| Component | Quantity | Description |
|-----------|----------|-------------|
| **VSDSquadron Mini Board** | 1 | RISC-V SoC-based development board |
| **IR Sensor** | 1 | Detects motion based on infrared radiation |
| **LDR Sensor**| 1 | Detects daylight condition | 
| **LEDs** | 5 | Represents street light |
| **Breadboard** | 1 | For circuit connections |
| **USB Cable** | 1 | Power and programming |
| **Jumper Wires** | - | For making connections |

---

## Pin Connections  

| **Component** | **Board Pin** | **Purpose** |
|--------------|-------------|-------------|
| **VCC of IR Sensor** | **3.2V** | Power supply |
| **GND of IR/LDR Sensor** | **GND** | Ground connection |
| **OUT of IR Sensor** | **Pin 4** | Motion detection signal |
| **OUT of LDR Sensor**| **Pin 5**| Light detection signal|
| **LED** | **Pins 0-4** | Indicates motion detected |


---
## Working 
- The **LDR sensor** id placed in a location where it can detect light within its range.
- The **IR sensor** is placed in a location where it can detect motion within its range.
- It continuously monitors light for any changes caused by environmental changes.
- When the LDR gives a false signal, LEDs light up at 50%.
- When an individual enters the detection range, the IR sensor sends a signal to the microcontroller.
- Upon detecting motion, the system turns the LED brightness to 100% by usinf PWM signals.
---
</details>

---


<details>
<summary> <b>Task 6:</b>The Smart Street Light System uses the VSDSquadron Mini RISC-V Board, a LDR sensor, an IR sensor, and LEDs for daylight and motion-based lighting control. The LDR detects light and IR sensor detects movement, respectively switching the LED ON/OFF and regulating the brightness. If no motion is detected, the LEDs stay at 50% brightness. This system is ideal for smart street light, sustainable energy usage, smart city developement.</summary> 
<br>

## Project Implementation  

### Steps to Implement:  
1. **Hardware Setup:**  
   - Connect the **LDR and IR sensor** to the board's GPIO pins.  
   - Wire an **LEDs** to indicate motion detection.  
   - Use a **breadboard** for easy prototyping and secure connections.  

2. **Software Development:**  
   - Write the **C firmware** to read the IR sensor output.  
   - Configure the GPIO pins for input (LDR and IR sensor) and output (LEDs).  
   - Implement logic to **Switch LEDs on/off and increse/decrease brightness** upon detecting motion.  
   - Keep the LED **OFF** as long as light is detected.  
   - Turn the LED brightness **100%** when movement is present.  

3. **Compilation & Upload:**  
   - Compile the code using a **RISC-V compatible toolchain**.  
   - Flash the program onto the **VSDSquadron Mini Board**.  

4. **Testing & Debugging:**  
   - Test the system in different lighting conditions.  
   - Adjust sensor sensitivity if needed.   

### Expected Output:  
- If light is detected for a certain period, the LED automatically **turns OFF**. 
- If no light is detected for, the LED automatically **turns ON**.
- If no motion is detected, LEDs are at 50% brightness.
- If motion detected brightness is incresed to 100%  

This implementation ensures **automatic lighting control**, **indicate the proper process**, and **security enhancements** for various applications.
---

## Code Implementation  
```c
#include "debug.h"

#define LED_COUNT 5

// Define LED GPIO pins (PC0 - PC4)
#define LED1_PIN GPIO_Pin_0  // Brightest
#define LED2_PIN GPIO_Pin_1  
#define LED3_PIN GPIO_Pin_2  
#define LED4_PIN GPIO_Pin_3  
#define LED5_PIN GPIO_Pin_4  // Least bright

#define LDR_PIN GPIO_Pin_4  // LDR sensor on PD4
#define IR_SENSOR_PIN GPIO_Pin_5  // IR sensor on PD5

uint16_t brightness_levels[] = {100, 60, 30, 15, 5}; // Simulated PWM duty cycle

void GPIO_Config(void);
void Control_LED_Brightness(uint8_t duty);

int main(void)
{
    NVIC_PriorityGroupConfig(NVIC_PriorityGroup_1);
    SystemCoreClockUpdate();
    Delay_Init();
    GPIO_Config();

    while (1)
    {
        uint8_t ldr_state = GPIO_ReadInputDataBit(GPIOD, LDR_PIN);
        uint8_t ir_state = GPIO_ReadInputDataBit(GPIOD, IR_SENSOR_PIN);

        if (ldr_state == 0) // Dark condition
        {
            if (ir_state == 1) // IR sensor detects object (Active)
                Control_LED_Brightness(100); // Full brightness
            else
                Control_LED_Brightness(30); // Dim light
        }
        else
        {
            Control_LED_Brightness(0); // Light detected, LEDs OFF
        }
    }
}

void GPIO_Config(void)
{
    GPIO_InitTypeDef GPIO_InitStructure = {0};

    // Enable GPIO clocks
    RCC_APB2PeriphClockCmd(RCC_APB2Periph_GPIOC | RCC_APB2Periph_GPIOD, ENABLE);

    // Configure LDR and IR sensor as input (PD4, PD5)
    GPIO_InitStructure.GPIO_Pin = LDR_PIN | IR_SENSOR_PIN;
    GPIO_InitStructure.GPIO_Mode = GPIO_Mode_IPU;
    GPIO_Init(GPIOD, &GPIO_InitStructure);

    // Configure LED pins (PC0 - PC4) as output
    GPIO_InitStructure.GPIO_Pin = LED1_PIN | LED2_PIN | LED3_PIN | LED4_PIN | LED5_PIN;
    GPIO_InitStructure.GPIO_Mode = GPIO_Mode_Out_PP;
    GPIO_InitStructure.GPIO_Speed = GPIO_Speed_50MHz;
    GPIO_Init(GPIOC, &GPIO_InitStructure);
}

// Function to simulate PWM brightness control
void Control_LED_Brightness(uint8_t duty)
{
    uint16_t pwm_levels[LED_COUNT];

    // Scale brightness based on duty cycle
    for (int i = 0; i < LED_COUNT; i++)
    {
        pwm_levels[i] = (brightness_levels[i] * duty) / 100;
    }

    // Simulate PWM by toggling LEDs
    for (int t = 0; t < 100; t++)
    {
        GPIO_WriteBit(GPIOC, LED1_PIN, (t < pwm_levels[0]) ? Bit_SET : Bit_RESET);
        GPIO_WriteBit(GPIOC, LED2_PIN, (t < pwm_levels[1]) ? Bit_SET : Bit_RESET);
        GPIO_WriteBit(GPIOC, LED3_PIN, (t < pwm_levels[2]) ? Bit_SET : Bit_RESET);
        GPIO_WriteBit(GPIOC, LED4_PIN, (t < pwm_levels[3]) ? Bit_SET : Bit_RESET);
        GPIO_WriteBit(GPIOC, LED5_PIN, (t < pwm_levels[4]) ? Bit_SET : Bit_RESET);
        Delay_Ms(1);
    }
}

```
</details>
---
