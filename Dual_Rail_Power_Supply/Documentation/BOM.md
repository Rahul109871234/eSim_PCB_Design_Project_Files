# Bill of Materials (BOM)
## Project: Adjustable Dual-Rail Benchtop Power Supply
**FOSSEE eSim Winter Internship 2026 — Screening Task 7**

| Item | Reference Designator | Value / Part | Quantity | Footprint | Package / Description |
| :--- | :--- | :--- | :---: | :--- | :--- |
| 1 | **J1** | Vin 9V-24V DC | 1 | `TerminalBlock_Phoenix:MKDS-1,5-2-5.08` | 2-Pin Screw Terminal Block, 5.08mm Pitch |
| 2 | **F1** | 1.5A Slow-Blow | 1 | `Fuse:Fuseholder_Cylinder-5x20mm_Schurter` | 5x20mm Cartridge Fuse Holder |
| 3 | **D1** | 1N5819 | 1 | `Diode_THT:D_DO-41_SOD81_P10.16mm_Horizontal` | 1A 40V Schottky Barrier Diode (Reverse Protection) |
| 4 | **C1** | 1000µF / 35V | 1 | `Capacitor_THT:CP_Radial_D10.0mm_P5.00mm` | Radial Aluminum Electrolytic Bulk Filter Capacitor |
| 5 | **C2, C5** | 100nF (0.1µF) | 2 | `Capacitor_THT:C_Disc_D5.0mm_W2.5mm_P5.00mm` | High-Frequency Ceramic Disc Decoupling Capacitors |
| 6 | **U1** | LM317T | 1 | `Package_TO_SOT_THT:TO-220-3_Vertical` | 1.5A Adjustable Positive Linear Voltage Regulator |
| 7 | **R1** | 240 Ω, 1% | 1 | `Resistor_THT:R_Axial_DIN0207_P7.62mm_Horizontal` | 1/4W Metal Film Precision Setting Resistor |
| 8 | **RV1** | 5 kΩ | 1 | `Potentiometer_THT:Potentiometer_Bourns_3296W` | 25-Turn Precision Cermet Trimmer Potentiometer |
| 9 | **C3** | 10µF / 25V | 1 | `Capacitor_THT:CP_Radial_D6.3mm_P2.50mm` | Radial Electrolytic Capacitor (ADJ Ripple Rejection) |
| 10 | **D2, D3** | 1N4007 | 2 | `Diode_THT:D_DO-41_SOD81_P10.16mm_Horizontal` | 1A 1000V Silicon Rectifier Diodes (Back-EMF / Discharging Protection) |
| 11 | **C4** | 100µF / 25V | 1 | `Capacitor_THT:CP_Radial_D8.0mm_P3.50mm` | Radial Electrolytic Output Smoothing Capacitor |
| 12 | **J2** | VOUT_ADJ (1.25V-15V) | 1 | `TerminalBlock_Phoenix:MKDS-1,5-2-5.08` | 2-Pin Screw Terminal Output Block, 5.08mm Pitch |
| 13 | **R2** | 1.5 kΩ | 1 | `Resistor_THT:R_Axial_DIN0207_P7.62mm_Horizontal` | 1/4W Carbon Film LED Current Limiting Resistor |
| 14 | **D4** | LED Green (3mm) | 1 | `LED_THT:LED_D3.0mm` | Variable Rail Power Indicator LED |
| 15 | **U2** | L7805CV | 1 | `Package_TO_SOT_THT:TO-220-3_Vertical` | 1A Fixed +5.0V Positive Voltage Regulator |
| 16 | **C6** | 10µF / 25V | 1 | `Capacitor_THT:CP_Radial_D6.3mm_P2.50mm` | 7805 Input Filter Radial Capacitor |
| 17 | **C7** | 22µF / 16V | 1 | `Capacitor_THT:CP_Radial_D6.3mm_P2.50mm` | 7805 Output Filter Radial Capacitor |
| 18 | **R3** | 1 kΩ | 1 | `Resistor_THT:R_Axial_DIN0207_P7.62mm_Horizontal` | 1/4W 5V LED Current Limiting Resistor |
| 19 | **D5** | LED Blue (3mm) | 1 | `LED_THT:LED_D3.0mm` | Fixed +5V Rail Power Indicator LED |
| 20 | **J3** | +5V Logic Header | 1 | `Connector_PinHeader_2.54mm:PinHeader_1x02` | 2-Pin Male Header, 2.54mm Pitch |
| 21 | **H1-H4** | M3 Mounting Holes | 4 | `MountingHole:MountingHole_3.2mm_M3` | 3.2mm Plated Chassis Mechanical Mounting Holes |
