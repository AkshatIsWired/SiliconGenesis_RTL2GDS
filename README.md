# 🎨 Open-Source VLSI Design Journey: RTL-to-GDSII 🚀

This repository chronicles my dedicated journey learning the **Digital ASIC Design Flow** from start to finish, leveraging the power of **fully open-source EDA tools** and Process Design Kits (PDKs).

The primary objective is to create a robust, end-to-end log detailing every step from the initial **RTL (Register Transfer Level) code** down to the final **GDSII** layout, using community-driven tools.

---

## 🎯 Project Goals

- **Master the Flow:** Achieve deep, practical understanding of the complete RTL-to-GDSII process.  
- **Tool Proficiency:** Gain hands-on expertise with the core open-source EDA tools (Yosys, OpenROAD, Magic, etc.).  
- **Comprehensive Documentation:** Provide a detailed, step-by-step learning log for each stage, serving as a future reference and community resource.  
- **PDK Implementation:** Successfully implement a design using the **Skywater 130nm (sky130)** open-source PDK.

---

## 🛠️ Open-Source Toolchain & Design Stages

We are building a functional digital ASIC flow using the following powerful open-source tools:

| Design Stage                 | Primary Tool(s)           | Key Function                                               | Module Log |
|------------------------------|---------------------------|------------------------------------------------------------|------------|
| **RTL & Simulation**         | Icarus Verilog, GTKWave   | Functional verification of the Verilog design.             | **02**     |
| **Logic Synthesis**          | Yosys                     | Translates RTL into a gate-level netlist using standard cells. | **03**     |
| **Static Timing Analysis (STA)** | OpenSTA                | Verifies timing constraints and identifies critical paths. | **04**     |
| **Physical Design**          | OpenROAD                  | Executes automated floorplanning, placement, CTS, and routing. | **05**     |
| **Physical Verification**    | Magic, Netgen             | Performs **DRC** (Design Rule Check) and **LVS** (Layout vs. Schematic). | **06**     |
| **Integrated Flow**          | OpenLane                  | High-level automation wrapper for the entire flow using the **sky130 PDK**. | **07**     |

---

## 📚 Learning Path & Detailed Modules

The entire journey is broken down into eight sequential learning modules. Each module has a dedicated markdown file serving as the **detailed learning log, tutorial, and command reference**.

| # | Module Title                          | Status       | Log File                                      |
|---|---------------------------------------|--------------|-----------------------------------------------|
| 1 | Linux & Ubuntu Basics                 | ⬜ Pending    | [01_linux_basics.md](01_linux_basics.md)      |
| 2 | RTL Design with Verilog               | ⬜ Pending    | [02_rtl_verilog.md](02_rtl_verilog.md)        |
| 3 | Logic Synthesis                       | ⬜ Pending    | [03_synthesis_yosys.md](03_synthesis_yosys.md)|
| 4 | Static Timing Analysis (STA)          | ⬜ Pending    | [04_sta_opensta.md](04_sta_opensta.md)        |
| 5 | Physical Design (P&R)                 | ⬜ Pending    | [05_openroad_flow.md](05_openroad_flow.md)    |
| 6 | Physical Verification (DRC/LVS)       | ⬜ Pending    | [06_magic_netgen.md](06_magic_netgen.md)      |
| 7 | Integrated ASIC Flow (OpenLane)       | ⬜ Pending    | [07_openlane_sky130.md](07_openlane_sky130.md)|
| 8 | Final Project Implementation          | ⬜ Pending    | [08_final_project.md](08_final_project.md)    |

> **💡 Tip:** Update the `Status` column to `✅ Complete` or `➡️ In Progress` as you finish each module!

---

## 📂 Repository Structure
open-vlsi-journey/
├── README.md # Project entry point and navigator
├── 01_linux_basics.md # Module 1: Environment Setup
├── 02_rtl_verilog.md # Module 2: Verilog, Icarus Verilog, GTKWave
├── 03_synthesis_yosys.md # Module 3: Yosys synthesis & scripting
├── 04_sta_opensta.md # Module 4: OpenSTA & SDC constraints
├── 05_openroad_flow.md # Module 5: OpenROAD Place-and-Route
├── 06_magic_netgen.md # Module 6: Magic (DRC) & Netgen (LVS)
├── 07_openlane_sky130.md # Module 7: OpenLane + sky130 PDK automation
├── 08_final_project.md # Module 8: End-to-end design implementation
└── resources/ # Scripts, configs, and reference materials 

✨ **Join me as I explore the fascinating world of open-source chip design!** Contributions, suggestions, and collaborative learning are always welcome.
