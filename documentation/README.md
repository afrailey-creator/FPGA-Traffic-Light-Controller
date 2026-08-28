# FPGA Traffic Light Controller

## Overview

This project implements a traffic metering controller for a three-lane highway entrance ramp using digital logic and an Intel FPGA.

The controller manages three lanes:

* **Carpool lane (CL)**
* **Left lane (LL)**
* **Right lane (RL)**

Each lane has a vehicle sensor, and the controller determines which lane receives a green light based on the sensor inputs and a round-robin signal.

## Project Objectives

The project involved:

* Translating a functional specification into a truth table
* Simplifying Boolean logic using Karnaugh maps
* Designing minimized SOP logic
* Implementing the circuit using AND/OR gates
* Simulating all possible input combinations
* Creating a 7-segment display controller
* Implementing the design on an Intel FPGA
* Testing the circuit on physical hardware

## System Behavior

The controller uses four inputs:

| Input | Description                 |
| ----- | --------------------------- |
| `CS`  | Carpool lane vehicle sensor |
| `LS`  | Left lane vehicle sensor    |
| `RS`  | Right lane vehicle sensor   |
| `RR`  | Round-robin lane selection  |

The outputs are:

| Output | Description              |
| ------ | ------------------------ |
| `CL`   | Carpool lane green light |
| `LL`   | Left lane green light    |
| `RL`   | Right lane green light   |

### Traffic Logic

1. The carpool lane receives priority whenever a vehicle is detected.
2. If the carpool lane is empty, the controller selects between the left and right lanes.
3. When both regular lanes have vehicles waiting, the `RR` signal determines which lane receives the green light.
4. If no vehicles are waiting, the right lane remains green.

## 7-Segment Display

A 7-segment display was added to indicate the number of vehicles detected by the three sensors.

The display represents:

```text
000 → 0 cars
001 → 1 car
010 → 2 cars
011 → 3 cars
```

The maximum possible number of detected vehicles is three.

## Simulation

The design was tested against all **16 possible combinations** of the four inputs.

Testing every combination allowed the logic to be compared against the truth table before programming the FPGA.

![Simulation Results](results/simulation.png)

## FPGA Implementation

The circuit was implemented on an **Altera/Intel DE2-115 FPGA development board**.

The switches were used as circuit inputs and the board LEDs represented the traffic light outputs.

![FPGA Implementation](results/fpga_board.jpg)

## Error Handling

An additional error output was considered that would activate if two or more traffic lights were simultaneously green:

```text
ERR1 = (CL · LL) + (CL · RL) + (LL · RL)
```

This provides a simple way to detect an invalid traffic-light state.

## Lessons Learned

This project gave me hands-on experience translating a real-world problem into digital logic, simplifying Boolean functions, testing logic through simulation, and implementing the final design on physical FPGA hardware.

One of the most useful parts of the project was comparing simulation results with physical FPGA behavior. Simulation can verify the logical design, but hardware testing can reveal implementation issues such as incorrect pin assignments or physical connections.

## Technologies

* Digital Logic Design
* Boolean Algebra
* Karnaugh Maps
* SOP Logic
* AND/OR Gates
* Verilog
* Quartus Prime
* FPGA
* 7-Segment Displays
* Hardware Simulation

## Documentation

The complete lab report and supporting documentation are available in the [`documentation`](documentation/) folder.
