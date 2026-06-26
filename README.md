# digital-logic-calculator
Simulation of an automated BCD calculator using Deed software. Features hardware-level logic including demultiplexers, registers, and 7-segment displays for real-time processing.
## 🛠️ Components & Technologies Used
* **Software:** Deed (Digital Electronics Education and Design Suite) 
* **Logic Types:** Binary Coded Decimal (BCD), Combinational & Sequential Logic 
* **Key Components:**
  * Priority Encoders & Demultiplexers 
  * D Flip-Flops & grouped shift registers 
  * 4-Bit Adders 
  * 4-to-1 Multiplexers 
  * 7-Segment Displays 
  * Basic Logic Gates (AND, OR, NAND) 

## ⚙️ Hardware Architecture & Workflow

### 1. Input Stage
The calculator features a 10-button keypad (0-9). Pressing a number triggers a priority encoder which converts the decimal input into a 4-bit BCD output. 

### 2. Registration & Storage
The system uses two main groups of registers (3 registers each) to memorize the input digits
*]As digits are entered, they are stored and shifted sequentially within the first register group
* When the `PLUS` button is triggered, logic `1` is supplied to a multiplexer, routing subsequent keypad presses into the second group of registers. 

### 3. Calculation (The Adder)
The core arithmetic unit uses cascaded 4-bit adders to compute the 1st, 10th, and 100th decimal places simultaneously. 
* **BCD Correction Measure:** The circuit includes a custom correction logic block. [cite_start]If an addition results in an overflow (greater than 9 in base 10, or `1001` in binary), the circuit automatically adds 6 (`0110` in binary) to the sum and carries `1` over to the next adder stage to ensure accurate BCD formatting.

### 4. Control Flow & Display
The system states are managed by five functional buttons: `ON/OFF`, `PLUS`, `EQUAL`, `DELETE`, and `CLEAR`. 
* `CLEAR` resets the clock (CL) on all flip-flops and registers to 0, wiping all stored data. 
* `DELETE` clears only the second input's registers. 
* Pressing `EQUAL` shifts the multiplexer control bits (to `01`), routing the computed sum from the 4-bit adders directly to the three 7-segment displays.
