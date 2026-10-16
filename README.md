# Orion-1

### My first attempt at designing a robotics controller from scratch

![Orion-1 board render](Images/PCB_3D_Front.png)

I wanted a controller I could eventually use in my own robots instead of building every project around a development board and a mess of jumper wires. That's where Orion-1 started.

The plan was to put the essentials on one PCB: an STM32, motor control, servo connections, power regulation, and enough headers to plug in sensors later. I built the schematic and laid out the board in KiCad. It's a 4 × 4-inch, two-layer design based around the **STM32F407VGTx**.

This is **revision one**, not a finished commercial controller. Some functional issues are still unresolved, and I haven't documented a successful full hardware bring-up. I'm keeping it here because the design process itself taught me a lot.

## What's on the board?

| Part | Why it's there |
| --- | --- |
| STM32F407VGTx | Main microcontroller; an Arm Cortex-M4 |
| TB6612FNG | Dual DC-motor driver |
| AP2112K-3.3 | 3.3 V regulation for the logic side |
| USB-C connector + polyfuse | Part of the input/power interface |
| Four servo headers | Connections for future actuators |
| UART, I²C, SPI and sensor headers | Room to add peripherals |
| SWD signals, reset, oscillator, LEDs | Bring-up, debugging and basic feedback |

The KiCad project uses a **101.6 × 101.6 mm**, two-copper-layer board outline, with 1.6 mm nominal thickness.

## A closer look

| PCB layout | Schematic |
| :---: | :---: |
| ![PCB top view](Images/PCB_Top.png) | ![Circuit schematic](Images/Schematic.png) |

## What I learned building it

The parts list was the easy part. Getting all those parts to make sense together was harder.

I spent time sorting out KiCad's power flags and ERC messages, thinking through the USB supply path, checking crystal connections, and fixing grounding and routing issues. A robotics board also forces you to think about things you can mostly ignore on a breadboard: motor current, where the return paths go, and whether your connectors will actually be usable after assembly.

One thing I would do differently is plan the bring-up process earlier, before worrying so much about making the layout look finished. A routed board isn't the same thing as a tested board.

## Current state

The repository includes the [editable KiCad project](KiCad/), exported Gerber layers, and the images above. **It's still a design-stage prototype.** I haven't included firmware, measured rail voltages, or a verified motor/servo demo. The current repository also doesn't have NC drill output, so the manufacturing package needs to be regenerated before ordering.

If you're looking through the design, the most useful files are:

- [Schematic](KiCad/orion-1.kicad_sch) and [PCB layout](KiCad/orion-1.kicad_pcb)
- [Hardware notes](docs/HARDWARE_ARCHITECTURE.md)
- [Bring-up checklist](docs/BRING_UP_AND_VALIDATION.md)
- [Fabrication notes](docs/FABRICATION_NOTES.md)

Open `KiCad/orion-1.kicad_pro` in **KiCad 10.0**. Re-run ERC and DRC and check footprints and power nets before treating this revision as fabrication-ready.

## What's next

I want to resolve the electrical issues, verify the 3.3 V supply and SWD connection, flash a basic LED test, and then move on to peripherals and motor control. Once I can show actual measurements and a running board, I'll add them here rather than just calling the design “working.”

---

Built by **Adhyayan Tiwari** · [MIT License](LICENSE)
