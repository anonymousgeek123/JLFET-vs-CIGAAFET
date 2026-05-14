# CIGAAFET Modelling with Self-Heating Effects

Sentaurus TCAD simulation study of 8 nm nanowire Gate-All-Around FETs 
in Core-Insulator GAAFET (CIGAAFET) configuration.  
Course project for BEVD206L Semiconductor Device Modelling, VIT Chennai (2026).

## Overview

Models a novel CIGAAFET architecture where a coaxial SiO₂ core is embedded 
within the silicon channel, suppressing off-state leakage while preserving 
on-current. DC parameters are extracted with and without Self-Heating Effects 
(SHEs) and benchmarked against a standard GAAFET.

## Key Results

| Parameter     | GAAFET      | CIGAAFET (RCI=5nm) |
|---------------|-------------|---------------------|
| Vth_lin (V)   | 0.39        | 0.40                |
| DIBL (mV/V)   | 20.61       | 16.34               |
| SS (mV/dec)   | 59.61       | 59.59               |
| Ion/Ioff      | 4.64 × 10⁸  | 7.37 × 10⁸          |
| go (µS)       | 0.84        | 0.45                |

- Ion/Ioff reaches 1.68 × 10⁹ at RCI = 7 nm
- CIGAAFET retains performance advantage even with SHEs included
- 82 K temperature rise observed in channel during saturation

## Device Structure

- 8 nm radius cylindrical Si nanowire, 200 nm channel length
- SiO₂ core insulator (RCI swept 1–7 nm)
- HfO₂ gate dielectric, gate work function = 4.55 eV
- n⁺–p–n⁺ doping: As at 1×10¹⁹ cm⁻³ (S/D), B at 1×10¹⁶ cm⁻³ (channel)

## Tools Used

- Synopsys Sentaurus TCAD (W-2024.09)
- Sentaurus Structure Editor (SDE) — device geometry
- SDEVICE — drift-diffusion + hydrodynamic transport simulation
- Inspect — DC parameter extraction (Vth, DIBL, SS, Ion/Ioff, go)
- MATLAB — polynomial fitting and verification

## Simulation Files

- `sde_code.tcl` — structure definition and mesh refinement
- `sdevice_code.tcl` — physics models and bias sweep setup
- `report.pdf` — full methodology, results, and discussion

## Acknowledgements

SDEVICE simulation code adapted from:  
[akdimitri/Advanced-Electronic-Devices](https://github.com/akdimitri/Advanced-Electronic-Devices)  
(Imperial College London coursework)

Modifications made in this work:
- Core insulator radius fixed at RCI = 5 nm
- Self-heating effects enabled via Hydrodynamic transport model
- Gate work function tuned to 4.55 eV
- Parameter extraction scripts written independently in Inspect
- Junctionless FinFET added as comparison architecture

## Team

Sonakshi Agrawal, Sanjana Chejeti, Katakam Shrihita, Vyshnavi E  
VIT Chennai — April 2026
