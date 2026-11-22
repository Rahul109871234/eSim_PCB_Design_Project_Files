# Design Report: Dual-Rail Precision Benchtop Power Supply

**FOSSEE Winter Internship 2026 — Screening Task 7: PCB Design using eSim**  
**Author:** Candidate for eSim Winter Internship  
**Design Environment:** eSim v2.3 / v2.5 / KiCad EDA Suite  
**Date:** November 2026  

---

## 1. Project Overview

The objective of this project is to design, route, verify, and document a robust, production-ready, dual-layer Printed Circuit Board (PCB) for an **Adjustable Dual-Rail Benchtop Laboratory Power Supply**. 

Electronic prototyping benches and research labs require clean, ripple-free DC power rails. This board converts an unregulated DC input (9V to 24V DC from a standard DC wall adapter or transformer) into:
1. **Variable Precision Output:** Continuously adjustable from **+1.25V to +15V DC** at up to **1.5A** load current, powered by the industry-standard **LM317T** positive adjustable linear regulator.
2. **Fixed Logic Output:** Stable, regulated **+5.0V DC** at up to **1.0A**, driven by the **L7805CV** positive linear regulator, dedicated for microcontrollers, sensors, and digital logic circuits.

The board incorporates comprehensive input fault protection, ripple rejection networks, reverse-voltage discharge paths, status LED indicators, and a solid low-impedance ground plane on the bottom copper layer.

---

## 2. Circuit Architecture & Theoretical Calculations

### 2.1 Block Diagram

```text
[DC Input: 9V–24V]
       │
       ▼
 [Protection Stage] ──► 1.5A Fuse (F1) + 1N5819 Schottky Diode (D1)
       │
       ├─────────────────────────────────────────┐
       ▼                                         ▼
[Adjustable Regulator: LM317T]           [Fixed 5V Regulator: 7805]
  • Formula: Vout = 1.25V * (1 + RV1/R1)    • Output: Stable +5.0V
  • 5kΩ 25-turn precision trimmer          • Dedicated decoupling (C6, C7)
  • Decoupling (C1, C2, C3, C4, C5)         • Output Indicator: Blue LED (D5)
  • Protection Diodes (D2, D3)              • Header Pinout (J3)
  • Output Indicator: Green LED (D4)
       │                                         │
       ▼                                         ▼
[Output Terminal J2: 1.25V - 15V]         [Output Header J3: +5.0V]
```

### 2.2 Mathematical Equations & Component Calculations

#### 1. Output Voltage Equation (LM317T):
The LM317 develops a nominal 1.25V reference voltage ($V_{\text{ref}}$) between the output and adjustment terminals:
$$V_{\text{out}} = V_{\text{ref}} \left(1 + \frac{R_{V1}}{R_1}\right) + I_{\text{adj}} \cdot R_{V1}$$

Since $I_{\text{adj}}$ is small ($\approx 50\mu\text{A}$) and controlled, the second term is negligible with $R_1 = 240\,\Omega$:
* At minimum resistance ($R_{V1} = 0\,\Omega$):
  $$V_{\text{out, min}} = 1.25\text{ V}$$
* At nominal setting ($R_{V1} \approx 2.64\text{ k}\Omega$):
  $$V_{\text{out}} = 1.25\left(1 + \frac{2640}{240}\right) = 15.0\text{ V}$$

#### 2. Ripple Rejection:
Capacitor $C_3$ ($10\,\mu\text{F}$) bypassed from the `ADJ` pin to ground prevents ripple from being amplified as the output voltage increases, achieving an 80 dB ripple rejection ratio.

#### 3. Power Dissipation & Thermal Considerations:
Maximum power dissipation in the LM317 pass transistor occurs at maximum output current and minimum output voltage:
$$P_D = (V_{\text{in}} - V_{\text{out}}) \times I_{\text{load}}$$
For $V_{\text{in}} = 15\text{ V}$, $V_{\text{out}} = 5\text{ V}$, and $I_{\text{load}} = 0.8\text{ A}$:
$$P_D = (15 - 5) \times 0.8 = 8.0\text{ W}$$
The TO-220 footprint is vertically placed with adequate clearance to attach a standard aluminum clip-on or bolt-on heatsink.

---

## 3. Footprint Assignment Details

Every component was strictly mapped to verified, standard KiCad / eSim libraries:

| RefDes | Part Name | Assigned KiCad Footprint | Pitch / Package |
| :--- | :--- | :--- | :--- |
| **J1, J2** | 2-Pin Terminal Blocks | `TerminalBlock_Phoenix:MKDS-1,5-2-5.08_Horizontal` | 5.08mm Pitch |
| **F1** | 1.5A Cartridge Fuse | `Fuse:Fuseholder_Cylinder-5x20mm_Schurter` | 5x20mm Cylinder |
| **D1, D2, D3** | 1N5819 / 1N4007 | `Diode_THT:D_DO-41_SOD81_P10.16mm_Horizontal` | DO-41 Axial, 10.16mm Pitch |
| **U1** | LM317T Regulator | `Package_TO_SOT_THT:TO-220-3_Vertical` | TO-220-3 (Heatsink compatible) |
| **U2** | L7805CV Regulator | `Package_TO_SOT_THT:TO-220-3_Vertical` | TO-220-3 |
| **C1** | 1000µF / 35V | `Capacitor_THT:CP_Radial_D10.0mm_P5.00mm` | 10mm Dia, 5mm Lead Pitch |
| **C2, C5** | 100nF Ceramic | `Capacitor_THT:C_Disc_D5.0mm_W2.5mm_P5.00mm` | Disc 5.0mm Dia, 5mm Pitch |
| **C3, C6, C7** | 10µF, 22µF Radial | `Capacitor_THT:CP_Radial_D6.3mm_P2.50mm` | 6.3mm Dia, 2.5mm Pitch |
| **C4** | 100µF / 25V | `Capacitor_THT:CP_Radial_D8.0mm_P3.50mm` | 8.0mm Dia, 3.5mm Pitch |
| **R1, R2, R3** | Metal / Carbon Film Resistors | `Resistor_THT:R_Axial_DIN0207_P7.62mm_Horizontal` | DIN 0207, 7.62mm Pitch |
| **RV1** | 5k Trimmer | `Potentiometer_THT:Potentiometer_Bourns_3296W` | 3-pin Inline 2.54mm |
| **D4, D5** | 3mm LEDs | `LED_THT:LED_D3.0mm` | 3.0mm Round, 2.54mm Pitch |
| **J3** | 2-Pin Pin Header | `Connector_PinHeader_2.54mm:PinHeader_1x02_Vertical` | 2.54mm Pitch |
| **H1–H4** | M3 Mounting Holes | `MountingHole:MountingHole_3.2mm_M3` | 3.2mm Plated Through-Hole |

---

## 4. PCB Layout & Routing Methodology

### 4.1 Layer Stackup
* **Layer Count:** 2 Copper Layers (FR-4 Dielectric, 1.6 mm Board Thickness, 1 oz / 35 µm copper).
* **Top Copper Layer (`F.Cu`):** Primary signal routing, low-dropout linear regulation stages, power distribution rails, and component solder pads.
* **Bottom Copper Layer (`B.Cu`):** Continuous, unbroken **Ground Plane (`GND`)** copper pour. This provides a low-impedance return path for currents, shields analog signals from EMI, and improves thermal dissipation.

### 4.2 Track Width Strategy (IPC-2152 Compliant)
* **High-Current Power Traces (`+VIN_RAW`, `+VIN`, `+VOUT_ADJ`):** Track widths set to **$1.0\text{ mm} - 1.2\text{ mm}$** ($40 - 48\text{ mils}$), capable of carrying $> 2.0\text{ A}$ with $< 10^\circ\text{C}$ temperature rise.
* **Medium Power Traces (`+5V` Logic Rail):** Track width **$0.8\text{ mm}$** ($32\text{ mils}$).
* **Feedback & Signal Traces (`V_ADJ_PIN`, LED Anodes):** Track width **$0.5\text{ mm}$** ($20\text{ mils}$) for clean routing and impedance consistency.

### 4.3 Clearance & Design Rule Specifications
* Trace-to-Trace Clearance: $\ge 0.25\text{ mm}$ ($10\text{ mils}$)
* Trace-to-Pad Clearance: $\ge 0.25\text{ mm}$
* Copper-to-Edge Clearance: $\ge 0.8\text{ mm}$
* Minimum Via Size: $0.8\text{ mm}$ diameter / $0.4\text{ mm}$ drill hole

---

## 5. Verification & DRC Results

The complete design was validated using the KiCad / eSim Design Rules Check (DRC) engine.

### Verification Metrics:
* **Unconnected Nets:** 0 (All 9 electrical nets fully routed and verified)
* **Shorting Violations:** 0
* **Clearance Violations:** 0
* **Footprint / Courtyard Overlaps:** 0
* **Electrical Connectivity:** Complete continuity across all through-hole pins and ground zones.

The formal DRC log is archived at `Documentation/drc_report.txt`.

---

## 6. Manufacturing & 3D Visualization Deliverables

The project deliverables include full manufacturing outputs:
1. **Gerber Files (`Gerbers/`):** Standard RS-274X format for all copper layers (`.gtl`, `.gbl`), solder masks (`.gts`, `.gbs`), silkscreens (`.gto`, `.gbo`), paste, and board outline (`.gm1`).
2. **Excellon Drill File:** `Gerbers/Dual_Rail_Power_Supply.drl` with complete tool definitions.
3. **Schematic PDF:** `Documentation/Schematic_Diagram.pdf`
4. **Layout Layers PDF:** `Documentation/PCB_Layout_Layers.pdf`
5. **Photorealistic 3D Renders:**
   - Isometric View: `Documentation/3D_Isometric_View.png`
   - Top Orthographic View: `Documentation/3D_Top_View.png`
   - Bottom Ground Plane View: `Documentation/3D_Bottom_View.png`

---

## 7. Conclusion

The **Dual-Rail Precision Benchtop Power Supply** fulfills every mandatory requirement stipulated under Screening Task 7 of the FOSSEE Winter Internship 2026. The workflow demonstrates rigorous schematic engineering, proper component footprint mapping, strict adherence to IPC PCB layout rules, and complete project portability within eSim and KiCad EDA environments.
