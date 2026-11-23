# 1.2V-Bandgap-Reference-Design
Design and simulation of a 1.2V Bandgap Reference with second-order temperature compensation and 4-bit digital trimming using Cadence Virtuoso. Includes circuit architecture, theoretical analysis, simulation results, process corner analysis, and performance verification.
# 1.2V Bandgap Reference Design with Temperature Compensation and Digital Trimming

## 1. Project Overview

This project focuses on the design and simulation of a 1.2V Bandgap Reference (BGR) circuit incorporating second-order temperature curvature compensation and a 4-bit digital trimming network.

The primary objective is to generate a stable reference voltage across process, voltage, and temperature (PVT) variations while improving output accuracy through temperature compensation and digital trimming.

The design incorporates a conventional bandgap reference core, startup circuit, curvature compensation branch, and programmable resistor-based trimming network.

## 2. Design Specifications

| Parameter | Target Specification |
|---|---|
| Bandgap Reference Voltage | 1.2 V |
| Pre-trim Variation | ±5% |
| Post-trim Variation | ±0.5% |
| Temperature Coefficient | <50 ppm/°C |
| Supply Voltage (VDD) | 1.62 V – 1.98 V |
| Temperature Range | −40°C to 125°C |

## 3. Design Architecture

The proposed bandgap reference consists of the following blocks:

1. Startup Circuit
2. Bandgap Core
3. PTAT Voltage Generation
4. CTAT Voltage Generation
5. Second-Order Curvature Compensation
6. 4-Bit Digital Trimming Network

## 4. Theoretical Background

### 4.1 Bandgap Reference Principle

A bandgap reference combines two voltages having opposite temperature coefficients:

- CTAT (Complementary to Absolute Temperature): Generated using the base-emitter voltage of a forward-biased BJT.
- PTAT (Proportional to Absolute Temperature): Generated using the difference between the base-emitter voltages of two BJTs operating at different current densities.

The combination of these components produces a temperature-compensated reference voltage.

### 4.2 Startup Circuit

The startup circuit prevents the self-biased bandgap core from remaining in its unwanted zero-current operating state.

It injects an initial current into the core during power-up and automatically disables itself once normal bias conditions are established.

### 4.3 Second-Order Curvature Compensation

Conventional first-order bandgap compensation cancels the linear temperature-dependent component but leaves residual nonlinear temperature curvature.

A curvature compensation branch is implemented to extract and inject a corrective nonlinear current, reducing the second-order temperature variation of the output reference voltage.

## 5. Digital Trimming Architecture

A 4-bit programmable resistor network is implemented to compensate for process-dependent output voltage variations.

- Number of digital bits: 4
- Number of available states: 16
- Trimming approach: Parallel resistor branches with digital switch control.
- Objective: Improve reference voltage accuracy across process corners.

The selected trimming codes reported in the project presentation are:

| Process Corner | Digital Code |
|---|---|
| Nominal | 1010 |
| SS | 1000 |
| FS | 1010 |
| SF | 1010 |
| FF | 0011 (alternative code 1010 also reported) |

The final FF code requires confirmation against the selected measurement condition.

## 6. Simulation and Design Results

### 6.1 Temperature Curvature Compensation

The following temperature drift results were reported during resistor optimization:

| Design Condition | Reported Voltage Drift |
|---|---:|
| Without curvature compensation | 2.7 mV |
| Compensation resistance = 80 kΩ | 1.7 mV |
| Compensation resistance = 66 kΩ | 1.6 mV |
| Compensation resistance = 64 kΩ | 1.2 mV |
| 64 kΩ with CTAT current variation | 759 µV |
| Unit-dimension resistor implementation | 837 µV |

The reported results demonstrate a reduction in temperature-dependent output voltage variation through curvature compensation and resistor optimization.

### 6.2 Process Corner Analysis

Process corner simulations include:

- FF – Fast-Fast
- FS – Fast-Slow
- SF – Slow-Fast
- SS – Slow-Slow
- Nominal / Typical

Detailed corner-wise output voltage measurements will be added with simulation waveforms.

### 6.3 Supply Voltage Analysis

Supply voltage variation was evaluated as part of the design validation.

Target supply range: 1.62 V – 1.98 V.

A reported 18 mV variation is included in the presentation; detailed sweep conditions and corresponding results will be documented separately.

### 6.4 Digital Trimming Results

The 4-bit trimming architecture provides 16 programmable states for output voltage adjustment.

The complete 16-state measurement table and final corner-wise voltage values will be added after verification.

## 7. Specification Verification

| Parameter | Target | Final Measured Result | Status |
|---|---|---|---|
| Reference Voltage | 1.2 V | To be documented | Pending |
| Pre-trim Accuracy | ±5% | To be documented | Pending |
| Post-trim Accuracy | ±0.5% | To be documented | Pending |
| Temperature Coefficient | <50 ppm/°C | To be calculated from temperature sweep | Pending |
| Supply Voltage Range | 1.62–1.98 V | To be documented | Pending |
| Temperature Range | −40°C to 125°C | Compensation evaluated over this range | To be verified |

## 8. Tools and Technologies

- Cadence Virtuoso
- Analog Circuit Design and Simulation
- PVT Corner Analysis
- Temperature Sweep Analysis
- Digital Trimming and Performance Verification

## 9. Project Documentation

The following materials will be included in this repository:

- Circuit schematics
- Design architecture diagrams
- Startup circuit implementation
- Curvature compensation implementation
- Digital trimming architecture
- Temperature simulation waveforms
- Process corner simulation results
- Supply variation results
- Pre-trim and post-trim performance comparison

## 10. Conclusion

The project investigates a temperature-compensated 1.2V bandgap reference with a programmable digital trimming architecture.

Second-order curvature compensation and resistor optimization were implemented to reduce temperature-dependent output voltage variation. A 4-bit trimming network was developed to improve output voltage accuracy across process variations.

Further detailed simulation results and specification verification will be documented as part of the project validation.

---

**Project:** Advanced Analog IC Design  
**Author:** Chetana Isunuri  
**Organization:** MOSart Labs
