# Orion-1

Version 1 of Orion, a custom robotics controller PCB designed in KiCad. This project was developed to explore PCB design, power management, and embedded hardware development while creating a compact controller for future robotics applications. Orion-1 integrates an STM32 microcontroller, USB-C programming interface, regulated power supply, motor and servo connections, and expansion headers for sensors. The project emphasizes practical PCB design practices, component selection, schematic development, routing, and hardware organization. As the first iteration, the design serves as a functional prototype and provides a foundation for future revisions with improved performance and additional features.

---

# Project Report

## Overview

Orion-1 is a custom-designed robotics controller PCB intended for small to medium-scale robotic systems. The objective of this project was to gain hands-on experience in professional PCB design while developing hardware capable of supporting embedded robotics applications. Every stage of the project, from schematic creation to PCB layout, was completed in KiCad.

## Objectives

- Design a complete custom PCB from scratch.
- Learn professional schematic capture and PCB layout practices.
- Develop a reusable robotics controller platform.
- Improve understanding of power distribution and embedded hardware design.
- Create a foundation for future robotics projects.

## Hardware Features

- STM32 microcontroller
- USB Type-C programming interface
- 3.3V voltage regulation
- Servo output headers
- DC motor interface
- Sensor expansion headers
- Decoupling capacitors for power stability
- Reset circuitry
- Crystal oscillator for precise clock generation

## Software & Tools

- KiCad 10.0
- STM32CubeIDE (planned firmware development)

## Design Process

The project began with component selection and system planning, followed by schematic development. Components were connected according to their datasheets, with particular attention given to power integrity and signal routing. Electrical rule checks were performed throughout development to identify and resolve schematic issues before PCB routing. The PCB layout was then created with careful component placement, efficient routing, and consideration of manufacturability.

## Challenges

During development several issues were encountered, including:

- Power flag and ERC errors
- USB power routing
- Crystal oscillator connections
- Ground connectivity
- Component placement optimization
- Trace routing improvements

Each issue required reviewing datasheets, understanding KiCad's electrical rules, and making iterative improvements to the design.

## Project Status

**Current Version:** Orion-1 (Prototype)

This represents the first revision of the Orion robotics controller. While the board is complete from a design perspective, but still have some functional problems. The future revisions will focus on optimization, testing, and expanding its capabilities.

---

*Designed by Adhyayan Tiwari*
