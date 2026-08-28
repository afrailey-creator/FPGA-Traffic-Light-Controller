# FPGA Traffic Light Controller

## Overview

Designed and implemented a three-lane traffic metering controller
using digital logic and an Intel DE2-115 FPGA.

## Demo

![Design Board](images/board1.jpg)
![Design Process](images/board3.jpg)

## What It Does

The controller manages:
- Carpool lane
- Left lane
- Right lane

The carpool lane receives priority. When it is empty, the
controller uses a round-robin signal to alternate between
the left and right lanes.

![Logic Process](images/logic.jpg)


## System Inputs

| Input | Purpose |
|---|---|
| CS | Carpool vehicle sensor |
| LS | Left lane vehicle sensor |
| RS | Right lane vehicle sensor |
| RR | Round-robin selection |

## System Outputs

| Output | Purpose |
|---|---|
| CL | Carpool green light |
| LL | Left green light |
| RL | Right green light |

## Technologies

- Verilog
- Quartus Prime
- Intel DE2-115 FPGA
- Digital Logic
- Karnaugh Maps
- 7-Segment Display
- FPGA Simulation

## Design Process

![Design Process](images/design.jpg)

Problem Specification
↓
Truth Table
↓
Karnaugh Maps
↓
Boolean Logic
↓
Schematic
↓
Simulation
↓
FPGA Implementation
↓
Hardware Testing

## Simulation

![Waveform](images/waveform.jpg)

The circuit was tested against all 16 possible combinations
of the four inputs.

## Hardware Implementation

The design was implemented on an Intel/Altera DE2-115 FPGA,
using switches as inputs and LEDs as traffic-light outputs.

## 7-Segment Display

A 7-segment display was implemented to show the number of
vehicles detected, from 0–3.

## Lessons Learned

This project provided hands-on experience translating a
functional specification into digital logic, verifying the
design through simulation, and implementing the design on
physical FPGA hardware.

## Documentation

[Lab Report](documentation/Lab3_Report.pdf)
