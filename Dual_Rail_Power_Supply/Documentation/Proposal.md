# Screening Task 7 Proposal Email Draft

**Recipient:** `contact-esim@fossee.in`  
**Subject Line:** `eSim Semester Long Internship - Autumn 2026 Submission Task 7 - Proposal`  

---

### Email Body:

Respected FOSSEE eSim Team,

I am writing to formally submit my proposal for **Screening Task 7: PCB Design using eSim** for the FOSSEE Winter Internship 2026.

**Project Title:**  
Design and Implementation of an Adjustable Dual-Rail Benchtop Power Supply (1.25V–15V Variable @ 1.5A & Fixed +5.0V Logic Rail)

**1. Project Overview & Motivation:**  
Electronic prototyping and testing require steady, low-noise DC power. This project implements a laboratory benchtop power supply PCB that converts an unregulated 9V–24V DC input into two independent, regulated output rails:
1. A continuously adjustable positive rail (+1.25V to +15V DC, up to 1.5A) driven by the LM317T adjustable linear regulator.
2. A fixed +5.0V logic rail (up to 1.0A) driven by the L7805CV regulator for powering microcontrollers and digital logic.

**2. Key Circuit Features:**  
- **Input Protection:** 1.5A cartridge fuse and 1N5819 Schottky diode for input overcurrent and reverse-polarity protection.
- **Ripple Rejection & Filtering:** Bulk 1000µF electrolytic capacitor, high-frequency ceramic bypass capacitors, and a 10µF bypass on the LM317 adjustment pin for 80 dB ripple suppression.
- **Safety Networks:** 1N4007 reverse-bias protection diodes across regulator terminals to safely discharge capacitors during power-down.
- **Diagnostics:** Independent Green and Blue LED indicators with current-limiting resistors for active power feedback.
- **Connectors:** Robust 5.08mm pitch Phoenix screw terminal blocks for high-current inputs/outputs and 2.54mm pin headers for breadboard logic interfacing.

**3. PCB Specifications & Methodology:**  
- **Layer Count:** 2 Copper Layers (Top Layer: Power routing & signals; Bottom Layer: Solid unbroken GND copper plane).
- **Design Environment:** eSim v2.3 / v2.5 / KiCad EDA Suite.
- **Design Workflow:** Complete schematic capture (`.kicad_sch`) -> Verified footprint assignment -> 2-layer manual routing with IPC-compliant trace widths (up to 1.2 mm for power) -> Full DRC validation (0 errors, 0 unconnected nets) -> 3D visualization and Gerber generation.

The complete eSim project files, schematic diagrams, DRC validation reports, and 3D renders have been prepared and organized for pull request submission to the official `FOSSEE/eSim_PCB_Design_Project_Files` repository.

Sincerely,  
[Your Name]  
[Your Degree & Department, e.g., B.Tech / B.E. Electronics Engineering]  
[Your Institute / University Name]  
[Contact Number]  
[GitHub Profile Link]  
