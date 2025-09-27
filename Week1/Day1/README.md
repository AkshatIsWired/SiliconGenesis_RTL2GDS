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
1. [Core Simulation Concepts](#-1-core-simulation-concepts)  
2. [Lab 1: RTL Simulation of a 2x1 MUX](#-2-lab-1-rtl-simulation-of-a-2x1-mux)  
3. [Core Synthesis Concepts](#-3-core-synthesis-concepts)  
4. [Lab 2: Logic Synthesis of a 2x1 MUX](#-4-lab-2-logic-synthesis-of-a-2x1-mux)  
5. [Day 1 Learning Summary](#-5-day-1-learning-summary)

---

## 🧠 1. Core Simulation Concepts

Before running the labs, I learned the fundamental building blocks of RTL verification:

- **Design**: The Verilog code that describes the intended hardware functionality to meet specific requirements.  
- **Simulator**: A software tool (e.g., **iverilog**) that checks functional correctness by applying test inputs and observing outputs.  
- **Testbench**: A self-contained Verilog module with **no primary I/Os** that generates stimulus for the design and validates its behavior.

The simulation flow is:

Design + Testbench → iverilog → a.out → VCD file → GTKWave (waveform viewer)

The simulator only evaluates outputs when inputs change—no input toggle means no output update.

---

## 🧪 2. Lab 1: RTL Simulation of a 2x1 MUX

I simulated a 2-to-1 multiplexer to verify its logical behavior using **iverilog** and **GTKWave**.

🔹 Click to view Lab 1 Details: Verilog Code, Commands, and Results

### 🔹 MUX Design: `good_mux.v`
```verilog
module good_mux(input i0, input i1, input sel, output reg y);
always@(*)
begin
    if(sel)
        y <= i1;
    else
        y <= i0;
end
endmodule

```

🔹 MUX Testbench: 
```verilog
`timescale 1ns/1ps
module tb_good_mux;
    // Inputs
    reg i0, i1, sel;
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
        $dumpvars(0, tb_good_mux);
        // Initialize Inputs
        sel = 0;
        i0 = 0;
        i1 = 0;
        #300 $finish;
    end

    always #75 sel = ~sel;
    always #10 i0 = ~i0;
    always #55 i1 = ~i1;
endmodule
```

🔹 Simulation Commands
```
# Compile design + testbench
iverilog good_mux.v tb_good_mux.v

# Run simulation (generates tb_good_mux.vcd)
./a.out

# View waveform
gtkwave tb_good_mux.vcd
```

🔹 Waveform Analysis
✅ The output y correctly follows:
```

i0 when sel = 0
i1 when sel = 1
(See gtkwave_good_mux_simulation.png in repo for visual confirmation)
</details>
```

⚙️ 3. Core Synthesis Concepts
```
After functional verification, the next step is logic synthesis—converting abstract RTL into a physical implementation.

Synthesis: Translates RTL Verilog into a gate-level netlist using standard cells from a technology library.
.lib (Liberty) File: Contains definitions of all available standard cells (AND, OR, MUX, FFs, etc.) in the target process (e.g., Sky130).

Gate Flavors: Multiple variants of the same logic function exist to balance performance, power, and area:

    Fast Cells: Wider transistors → low delay, but higher power & area → used to meet setup time.
    Slow Cells: Narrower transistors → higher delay, but lower power & area → used to avoid hold time violations.
💡 Key Insight: Synthesis isn’t just mapping—it’s optimization under constraints. Too many fast cells cause hold violations; too many slow cells hurt performance.
```

🔬 4. Lab 2: Logic Synthesis of a 2x1 MUX
I synthesized good_mux.v using Yosys and the Sky130 HD standard cell library.


🔹 Lab 2 Details: Yosys Commands and Results.

🔹 Yosys Command Flow
```
yosys
read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
read_verilog good_mux.v
synth -top good_mux
abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
show
write_verilog -noattr good_mux_netlist.v
```

🔹 Synthesis Results
Yosys mapped the entire MUX to a single standard cell:
```
sky130_fd_sc_hd__mux2_1
Verified via show command (see synthesized_netlist.png in repo).
Clean netlist generated with -noattr to remove synthesis metadata.
```
🔹 Netlist Verification
```
Reused the same testbench (tb_good_mux.v) with the synthesized netlist:
iverilog good_mux_netlist.v tb_good_mux.v
./a.out
gtkwave tb_good_mux.vcd
```

✅ Waveform matched RTL simulation exactly—proving functional equivalence.

🔑 Why this works: Primary I/Os are unchanged by synthesis, so the same testbench validates both RTL and gate-level. 


✅ 5. Day 1 Learning Summary
RTL Functional Verification
iverilog
✅ Mastered
Waveform Analysis & Debugging
GTKWave
✅ Mastered
Logic Synthesis Fundamentals
Theory
✅ Understood
RTL-to-Gate-Level Conversion
Yosys
✅ Mastered
Liberty Libraries & Gate Flavors
Sky130
.lib
✅ Understood

🌟 Final Takeaway:
From behavioral Verilog to a technology-mapped netlist—Day 1 laid the groundwork for the entire RTL-to-GDS flow. The environment is ready, and the core concepts are clear. On to Day 2! 💎 
