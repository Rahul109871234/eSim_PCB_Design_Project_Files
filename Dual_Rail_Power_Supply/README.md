# Dual-Rail Precision Benchtop Power Supply
### FOSSEE Winter Internship 2026 — Screening Task 7: PCB Design using eSim

An open-source, dual-layer PCB design of an adjustable laboratory benchtop power supply created using **eSim / KiCad**.

---

## 📌 Project Overview
This project provides a clean, regulated dual-output DC power supply:
* **Adjustable Output:** +1.25V to +15.0V DC (up to 1.5A) via **LM317T** with a 25-turn precision potentiometer.
* **Fixed Output:** +5.0V DC (up to 1.0A) via **L7805CV** for microcontrollers, sensors, and digital logic.
* **Input Voltage:** 9V to 24V DC (via 2-pin screw terminal or external DC adapter).

---

## 🛠 Features & Design Highlights
- **Input Protection:** 1.5A cartridge fuse (`F1`) and 1N5819 Schottky diode (`D1`) for reverse-polarity protection.
- **Low Noise & Ripple Rejection:** Bulk 1000µF smoothing capacitor (`C1`), 100nF ceramic decoupling (`C2`, `C5`), and a 10µF bypass on the LM317 `ADJ` pin for 80 dB ripple suppression.
- **Safety Diodes:** 1N4007 diodes (`D2`, `D3`) to prevent capacitor discharge damage to regulators on power-down.
- **Indicators:** Dedicated Green LED (Variable output) and Blue LED (+5V output).
- **PCB Stackup:** 2 Copper Layers:
  - Top Layer (`F.Cu`): Power tracks ($1.0\text{ mm} - 1.2\text{ mm}$) and signal routing.
  - Bottom Layer (`B.Cu`): Continuous low-impedance **Ground Plane** with thermal relief pads.
  - Mounting: 4x M3 chassis mounting holes at board corners.

---

## 📁 Repository Structure
```text
Dual_Rail_Power_Supply/
├── Dual_Rail_Power_Supply.kicad_pro    # KiCad / eSim project file
├── Dual_Rail_Power_Supply.kicad_sch    # Schematic diagram
├── Dual_Rail_Power_Supply.kicad_pcb    # 2-layer PCB layout
├── Dual_Rail_Power_Supply.kicad_prl    # Project local settings
├── sym-lib-table                       # Symbol library mapping
├── fp-lib-table                        # Footprint library mapping
│
├── Documentation/
│   ├── Project_Report.md               # Detailed engineering report
│   ├── BOM.md                          # Bill of Materials
│   ├── Proposal.md                     # Screening task proposal draft
│   ├── Schematic_Diagram.pdf           # Plotted schematic diagram
│   ├── PCB_Layout_Layers.pdf           # Plotted copper and silkscreen layers
│   ├── drc_report.txt                  # DRC verification report
│   ├── 3D_Isometric_View.png           # 3D render (Isometric)
│   ├── 3D_Top_View.png                 # 3D render (Top)
│   └── 3D_Bottom_View.png              # 3D render (Bottom Ground Plane)
│
└── Gerbers/                            # Production-ready manufacturing files
    ├── Dual_Rail_Power_Supply-F_Cu.gtl  # Top Copper
    ├── Dual_Rail_Power_Supply-B_Cu.gbl  # Bottom Copper
    ├── Dual_Rail_Power_Supply-F_Mask.gts# Top Solder Mask
    ├── Dual_Rail_Power_Supply-B_Mask.gbs# Bottom Solder Mask
    ├── Dual_Rail_Power_Supply-F_Silkscreen.gto
    ├── Dual_Rail_Power_Supply-Edge_Cuts.gm1
    └── Dual_Rail_Power_Supply.drl       # Excellon NC Drill File
```

---

## 🚀 How to Open in eSim / KiCad
1. Launch **eSim** (or **KiCad**).
2. Click **Open Project** and navigate to this folder:
   `c:\Users\Rahul\Downloads\fossee\Dual_Rail_Power_Supply\Dual_Rail_Power_Supply.kicad_pro`
3. Click **Open Schematic** to view the circuit in eSchema.
4. Click **PCB Layout** to inspect the 2-layer board layout in PCBnew.
5. Press `Alt + 3` (or click `View -> 3D Viewer`) to view the interactive 3D board render.

---

## 📋 Evaluation Compliance Checklist
- [x] Functional 2-layer PCB designed in eSim/KiCad environment.
- [x] Standard footprint assignments from verified KiCad libraries.
- [x] IPC-compliant track widths ($1.0\text{ mm} - 1.2\text{ mm}$ for power rails).
- [x] Continuous Ground plane on bottom copper layer.
- [x] Complete Design Rule Check (DRC) run with zero critical errors.
- [x] Photorealistic 3D renders generated.
- [x] Plotted PDF schematics and Gerber manufacturing files exported.
- [x] Detailed Design Report and Bill of Materials provided.
