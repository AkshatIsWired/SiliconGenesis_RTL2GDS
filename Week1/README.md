# 🗓️ Week 1, Day 1: Intro to Verilog RTL Design & Synthesis

[← Back to Main Page](../README.md)

<p align="center">
  <img src="https://img.shields.io/badge/Week-1-blue?style=for-the-badge" />
  <img src="https://img.shields.io/badge/Day-1-blueviolet?style=for-the-badge" />
  <img src="https://img.shields.io/badge/Status-Complete-brightgreen?style=for-the-badge" />
  <img src="https://img.shields.io/badge/Tools-iverilog_&_Yosys-orange?style=for-the-badge" />
</p>

> 🚀 **Today's Goal**: To build a foundational understanding of digital design by learning to write Verilog RTL, simulate it using the open-source **iverilog**, and synthesize it into a gate-level netlist with **Yosys**.

---

## 📚 Table of Contents
1.  [Core Simulation Concepts](#-1-core-simulation-concepts)
2.  [Lab 1: RTL Simulation of a 2x1 MUX](#-2-lab-1-rtl-simulation-of-a-2x1-mux)
3.  [Core Synthesis Concepts](#-3-core-synthesis-concepts)
4.  [Lab 2: Logic Synthesis of a 2x1 MUX](#-4-lab-2-logic-synthesis-of-a-2x1-mux)
5.  [Day 1 Learning Summary](#-5-day-1-learning-summary)

---

## 🧠 1. Core Simulation Concepts

Before running the labs, I learned the fundamental building blocks of RTL verification.

* [cite_start]**Design**: The Verilog code that describes the intended hardware functionality to meet specific requirements[cite: 350].
* [cite_start]**Simulator**: A software tool, like **iverilog**, that checks the functional correctness of a design by applying test inputs and observing outputs[cite: 347, 348].
* [cite_start]**Testbench**: A simulation-specific Verilog module used to generate stimulus (inputs) for the design and verify its behavior[cite: 352].

[cite_start]The simulation flow is a straightforward process: the design and testbench are compiled by iverilog, which produces a VCD (Value Change Dump) file[cite: 361, 363]. [cite_start]This VCD file can then be viewed as a waveform using a tool like GTKWave[cite: 364].

---

## 🧪 2. Lab 1: RTL Simulation of a 2x1 MUX

In this lab, I simulated a 2-to-1 multiplexer to verify its logical behavior.

<details>
<summary>🔹 **Click to view Lab 1 Details: Verilog Code, Commands, and Results**</summary>

### Verilog Code

Here are the two Verilog files used for this simulation.

<details>
  <summary> MUX Design: `good_mux.v` </summary>
  
  ``verilog
  module good_mux (input i0, input i1, input sel, output reg y);
    always @ (*)
    begin
      if(sel)
        y<=i1;
      else
        y<=i0;
    end
  endmodule


</details>

<details>
<summary> MUX Testbench: tb_good_mux.v </summary>

Verilog

`timescale 1ns / 1ps
module tb_good_mux;
  // Inputs
  reg i0,i1,sel;
  // Outputs
  wire y;
  // Instantiate the Unit Under Test (UUT)
  good_mux uut (
    .sel(sel),
    .i0(i0),
    .i1(i1),
    .y(y)
  );
  initial begin
    $dumpfile("tb_good_mux.vcd");
    $dumpvars(0,tb_good_mux);
    // Initialize Inputs
    sel = 0;
    i0=0;
    i1=0;
    #300 $finish;
  end
  always #75 sel = ~sel;
  always #10 i0 = ~i0;
  always #55 i1 = ~i1;
endmodule


</details>

Simulation Commands
The following commands were used to compile the Verilog files, run the simulation, and open the waveform viewer.

Bash

# Compile the design and testbench together
iverilog good_mux.v tb_good_mux.v

# Execute the compiled output file (a.out)
./a.out

# Open the generated VCD waveform file with GTKWave
gtkwave tb_good_mux.vcd




📸 Waveform Analysis
(Insert your screenshot of the GTKWave simulation output here. It should show the i0, i1, sel, and y signals over time.)

</details>

⚙️ 3. Core Synthesis Concepts
After simulation, the next step is synthesis: converting the abstract RTL code into a physical gate-level implementation.


Synthesis: The process of translating RTL code into a gate-level netlist, which is a representation of the design using standard cells from a technology library.



Liberty (.lib) File: A technology library file that contains a collection of standard cells (like AND, OR, NOT, flip-flops) available for synthesis.


Gate Flavors: A single logic function (e.g., a 2-input AND gate) can have multiple "flavors" (slow, medium, fast) in the library. This is crucial for balancing performance, power, and area.

Fast Cells: Use wider transistors, resulting in low delay but higher power and area consumption. They are needed to meet performance targets (

setup time).



Slow Cells: Use narrower transistors, resulting in higher delay but lower power and area. They are often needed to prevent race conditions (

hold time violations).


🔬 4. Lab 2: Logic Synthesis of a 2x1 MUX
In this lab, I used Yosys to synthesize the good_mux.v design into a gate-level netlist using the sky130 standard cell library.

<details>
<summary>🔹 Click to view Lab 2 Details: Yosys Commands and Results</summary>

Yosys Command-Line Flow
The following commands were executed sequentially inside the Yosys prompt to perform synthesis.

Tcl

# 1. Read the standard cell library (.lib file)
yosys> read_liberty -lib lib/sky130_fd_sc_hd_tt_025C_1v80.lib

# 2. Read the Verilog design file
yosys> read_verilog verilog_files/good_mux.v

# 3. Synthesize the design for the top module 'good_mux'
yosys> synth -top good_mux

# 4. Map the synthesized design to the standard cells
yosys> abc -liberty lib/sky130_fd_sc_hd_tt_025C_1v80.lib

# 5. Show the graphical representation of the synthesized netlist
yosys> show

# 6. Write the final gate-level netlist to a Verilog file
yosys> write_verilog -noattr good_mux_netlist.v






📸 Synthesized Netlist Visualization
(Insert your screenshot of the graphical netlist generated by the show command here.)

Generated Netlist
(Insert a screenshot or code block of the final good_mux_netlist.v file here.)

</details>

✅ 5. Day 1 Learning Summary
Concept / Skill Learned	Tool(s) Used	Status
RTL Functional Verification	iverilog	✅ Mastered
Waveform Analysis & Debugging	GTKWave	✅ Mastered
Understanding of Synthesis Flow	Yosys	✅ Mastered
RTL-to-Gate-Level Netlist Conversion	Yosys	✅ Mastered
Liberty Library & Gate Flavors	Theory	✅ Understood

Export to Sheets
The environment is set, and the foundational concepts are clear. Ready for the next challenge!

