# 🎨 Open-Source VLSI Design Journey: RTL-to-GDSII 🚀

This repository chronicles my dedicated journey learning the **Digital ASIC Design Flow** from start to finish, leveraging the power of **fully open-source EDA tools** and Process Design Kits (PDKs).

The primary objective is to create a robust, end-to-end log detailing every step from the initial **RTL (Register Transfer Level) code** down to the final **GDSII** layout, using community-driven tools.

---

## 🎯 Project Goals

* **Master the Flow:** Achieve deep, practical understanding of the complete RTL-to-GDSII process.
* **Tool Proficiency:** Gain hands-on expertise with the core open-source EDA tools (Yosys, OpenROAD, Magic, etc.).
* **Comprehensive Documentation:** Provide a detailed, step-by-step learning log for each stage, serving as a future reference and community resource.
* **PDK Implementation:** Successfully implement a design using the **Skywater 130nm (sky130)** open-source PDK.

---

## 🛠️ Open-Source Toolchain & Design Stages

We are building a functional digital ASIC flow using the following powerful open-source tools:

| Design Stage | Primary Tool(s) | Key Function | Module Log |
| :--- | :--- | :--- | :--- |
| **RTL & Simulation** | **Icarus Verilog**, **GTKWave** | Functional verification of the Verilog design. | **02** |
| **Logic Synthesis** | **Yosys** | Translates RTL into a gate-level netlist using standard cells. | **03** |
| **Static Timing Analysis (STA)** | **OpenSTA** | Verifies timing constraints and identifies critical paths. | **04** |
| **Physical Design** | **OpenROAD** | Executes automated floorplanning, placement, Clock Tree Synthesis (CTS), and routing. | **05** |
| **Physical Verification** | **Magic**, **Netgen** | Performs **DRC** (Design Rule Check) and **LVS** (Layout Versus Schematic). | **06** |
| **Integrated Flow** | **OpenLane** | High-level automation wrapper for the entire flow using the **sky130 PDK**. | **07** |

---

## 📚 Learning Path & Detailed Modules

The entire journey is broken down into eight sequential learning modules. Each module has a dedicated markdown file serving as the **detailed learning log, tutorial, and command reference**.

| # | Module Title | Status | Log File |
| :--- | :--- | :--- | :--- |
| **1** | **Linux & Ubuntu Basics** | ⬜ Pending | [01\_linux\_basics.md](01_linux_basics.md) |
| **2** | **RTL Design with Verilog** | ⬜ Pending | [02\_rtl\_verilog.md](02_rtl_verilog.md) |
| **3** | **Logic Synthesis** | ⬜ Pending | [03\_synthesis\_yosys.md](03_synthesis_yosys.md) |
| **4** | **Static Timing Analysis (STA)** | ⬜ Pending | [04\_sta\_opensta.md](04_sta_opensta.md) |
| **5** | **Physical Design (P&R)** | ⬜ Pending | [05\_openroad\_flow.md](05_openroad_flow.md) |
| **6** | **Physical Verification (DRC/LVS)** | ⬜ Pending | [06\_magic\_netgen.md](06_magic_netgen.md) |
| **7** | **Integrated ASIC Flow (OpenLane)**| ⬜ Pending | [07\_openlane\_sky130.md](07_openlane_sky130.md) |
| **8** | **Final Project Implementation** | ⬜ Pending | [08\_final\_project.md](08_final_project.md) |

> **Update the `Status` column to `✅ Complete` or `➡️ In Progress` as you finish each module!**

---

## 📂 Repository Structure

open-vlsi-journey/ ├── README.md (The project entry point and navigator) ├── 01_linux_basics.md (Module 1 Log: Environment Setup) ├── 02_rtl_verilog.md (Module 2 Log: Verilog, Icarus Verilog, GTKWave) ├── 03_synthesis_yosys.md (Module 3 Log: Yosys scripting and synthesis) ├── 04_sta_opensta.md (Module 4 Log: OpenSTA and SDC constraints) ├── 05_openroad_flow.md (Module 5 Log: OpenROAD Place and Route) ├── 06_magic_netgen.md (Module 6 Log: DRC and LVS) ├── 07_openlane_sky130.md (Module 7 Log: OpenLane flow automation) ├── 08_final_project.md (Module 8 Log: Application and final design) └── resources/ (Scripts, documentation, and external reference files)
