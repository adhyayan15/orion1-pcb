# Fabrication and design-file notes

The repository contains an **editable KiCad 10.0 project** and exported Gerber layers. These files represent the Rev 1 design and should be reviewed for manufacturing suitability.

## Present files

| Purpose | Path |
| --- | --- |
| KiCad project | `KiCad/orion-1.kicad_pro` |
| Schematic | `KiCad/orion-1.kicad_sch` |
| PCB layout | `KiCad/orion-1.kicad_pcb` |
| Front/back copper | `KiCad/orion-1-F_Cu.gbr`, `KiCad/orion-1-B_Cu.gbr` |
| Front/back solder mask | `KiCad/orion-1-F_Mask.gbr`, `KiCad/orion-1-B_Mask.gbr` |
| Silkscreen | `KiCad/orion-1-F_Silkscreen.gbr`, `KiCad/orion-1-B_Silkscreen.gbr` |
| Paste layers | `KiCad/orion-1-F_Paste.gbr`, `KiCad/orion-1-B_Paste.gbr` |
| Board outline | `KiCad/orion-1-Edge_Cuts.gbr` |
| Job info | `KiCad/orion-1-job.gbrjob` |

## Mechanical information

The KiCad board outline is a **101.6 × 101.6 mm** rectangle; the project declares **1.6 mm** board thickness and **two copper layers**.

## Not established yet

- **NC drill file(s) are not included** in the repository tree reviewed; regenerate drill output before fabrication.
- There is no verified, dated ERC/DRC passing report.
- An exported assembly BOM, pick-and-place file, and populated-board inspection report have not been documented.
- Gerber presence does not mean the assembled board has been manufactured or functionally validated.

## Recommended order of operations

1. Open the KiCad project and verify component footprints, polarity and all external header pinouts.
2. Run schematic ERC and board DRC, fixing issues or explicitly documenting justified exceptions.
3. Export a fresh set of Gerbers **and NC drill files** from the same board revision.
4. View the exact exported output in KiCad's Gerber Viewer and check it against the PCB editor.
5. Check fabrication tolerances, solder-mask clearances, board thickness, and hole specifications with the intended manufacturer.
6. Order a small prototype quantity; execute [the bring-up plan](BRING_UP_AND_VALIDATION.md) before attaching expensive hardware or batteries.

The current outputs are **reference artifacts**, not a fabrication release certified for production.
