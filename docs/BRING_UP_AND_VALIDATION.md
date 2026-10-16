# Orion-1 hardware bring-up and validation plan

> **Status:** This is a **proposed test plan**, not evidence that these steps have been completed. The original project notes mention unresolved functional problems without documenting their causes. Do not assume the board is safe to power until its design has been reviewed.

## A. Design review before fabrication

- [ ] Re-run KiCad **ERC** and review every reported item.
- [ ] Re-run **DRC** against chosen fabrication rules; capture dated outputs.
- [ ] Audit MCU voltage, decoupling, BOOT0, NRST, SWD, crystal and grounding nets.
- [ ] Confirm USB-C CC and VBUS wiring, data-line routing, and protection against the intended use case.
- [ ] Review the AP2112K input/output capacitor selection and thermal budget.
- [ ] Check motor-driver supply/current limits, standby control and load return paths.
- [ ] Check servo and peripheral connector pinouts, voltage domains and orientation.
- [ ] Confirm all footprints using actual component datasheets and mechanical drawings.
- [ ] Export fresh fabrication outputs including **NC drill files** and BOM.

## B. Bench equipment

Regulated current-limited power supply, multimeter, SWD/ST-LINK debugger, oscilloscope (recommended), USB-C cable/USB power meter (as appropriate), and simple low-current test loads.

## C. Initial power checks

- [ ] Inspect assembly for polarity/orientation, solder bridges, missing parts and shorts.
- [ ] Measure resistance between each supply rail and GND **before applying power**.
- [ ] Isolate motors, servos and sensor loads.
- [ ] Apply a current-limited supply only after verifying the correct input source and intended voltage.
- [ ] Measure **3.3 V**, input rail voltage, idle current, regulator temperature, and unexpected heating.
- [ ] Document photographs, measurement conditions and pass/fail results.

## D. MCU and firmware

- [ ] Verify NRST/BOOT0 behavior.
- [ ] Connect an SWD debugger and read the MCU identification.
- [ ] Flash a minimal LED-blink example and verify the user LED.
- [ ] Validate oscillator selection and clock frequency.
- [ ] Test UART with a loopback or external serial adapter.
- [ ] Test I²C/SPI with known-working peripheral devices at the intended logic voltage.

## E. Actuation and integration

- [ ] Validate TB6612FNG control and direction with a safe, low-current load, separate appropriate motor power and current limiting.
- [ ] Verify standby and stop behavior.
- [ ] Validate each servo signal and **its external/load power supply assumptions** before attaching servos.
- [ ] Add connectors and loads one at a time, observing supply sag and motor-induced resets.
- [ ] Record each failure and revision note with a clear reproduction procedure.

## Suggested report table

| Test | Expected | Measured | Result | Notes |
| --- | --- | --- | --- | --- |
| 3.3 V logic rail | Near nominal under allowed load | Not measured | Pending | |
| MCU SWD identification | Read device ID | Not measured | Pending | |
| LED firmware | Deterministic blink | Not measured | Pending | |
| UART / I²C / SPI | Functional transfers | Not measured | Pending | |
| Motor output | Controlled direction and stop | Not measured | Pending | |
| Servo outputs | Valid PWM and safe rail | Not measured | Pending | |

Once tests are performed, replace **Pending** entries with measured data and link instrument screenshots / firmware commits.
