# Hardware architecture — Orion-1 Rev 1

This document describes **design intent and components present in the KiCad files**; it does not constitute a test report.

## Controller
- **U2: STM32F407VGTx** microcontroller, LQFP-100 footprint.
- The design includes **SWDIO / SWCLK** net labels and reset/clock circuitry for intended debugging and firmware development.
- Firmware, completed flash/programming verification, and a pin-to-function map have not been provided in this repository.

## Power
- **J2** is a USB-C USB 2.0 receptacle footprint (HRO TYPE-C-31-M-12).
- A polyfuse is included in the input design.
- **U1: AP2112K-3.3** is the 3.3 V LDO supplying intended logic power.
- **MOTOR_VCC** is identified separately for the motor supply. Do not assume the USB or 3.3 V path is suitable for motors or servo loads without checking actual nets and available current.
- Confirm that the selected power architecture, connector, ground returns, regulator dissipation, and any externally applied motor or servo power are electrically safe before turning on the board.

## Actuation
- **U3: TB6612FNG**, a dual motor-driver IC in an SSOP-24 footprint.
- Motor control net labels include **PWMA**; check the schematic for the rest of the interface and enable/standby wiring before writing firmware.
- **SERVO1–SERVO4** are represented as connector references in the schematic; validate each pin's signal, supply, and ground before connecting hardware.

## Interfaces and expansion
The project has named **UART1**, **I2C1**, **SPI1**, and **SEN1–SEN4** connections plus a header labeled **WIRELESS PORT**. These are intended expansion interfaces, not verified end-to-end sensor modules. All header pinouts should be checked against the schematic.

## Mechanical/layout
- 2 signal copper layers: `F.Cu` and `B.Cu`.
- Board outline: rectangle from (27.94, 27.94) mm to (129.54, 129.54) mm, giving **101.6 × 101.6 mm (4 × 4 in)**.
- Nominal PCB thickness set in project: **1.6 mm**.
- Editable KiCad files: `KiCad/orion-1.kicad_sch`, `KiCad/orion-1.kicad_pcb`, `KiCad/orion-1.kicad_pro`.

## Trade-offs and review points
1. **USB-C vs programming**: connector inclusion alone does not prove USB enumeration or firmware flashing. Verify boot modes and SWD before using USB for firmware.
2. **Motor noise**: inspect motor supply isolation, driver decoupling, and ground return routing.
3. **Current limits**: validate expected servo/motor loads against regulator, copper, connector, and driver ratings.
4. **Clock**: verify crystal part value/load capacitors and firmware clock configuration.
5. **Manufacturing**: review library footprints and produce a fresh DRC report, BOM, drill files, and fabrication package.

See [Bring-up checklist](BRING_UP_AND_VALIDATION.md) before physically powering or testing a board.
