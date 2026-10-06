# Experimental Board

A KiCad 8 hardware project for a general-purpose electronics experimentation / breakout board: a large prototyping platform with indicators, switches, sensors, sound, and power distribution blocks that can be wired up for bench experiments.

Repository: [Enerzinc/experimentall-board](https://github.com/Enerzinc/experimentall-board)

## Repository layout

```
experimental_board/
├── ExperimentalBoard/                 # Original (v1) design — schematic only
│   ├── ExperimentalBoard.kicad_pro
│   ├── ExperimentalBoard.kicad_sch
│   ├── ExperimentalBoard.kicad_pcb     # empty stub (no board layout yet)
│   ├── ExperimentalBoard-backups/      # KiCad auto-backups (.zip)
│   └── new_exp_board/                  # Current revision (v2)
│       ├── new_exp_board.kicad_pro
│       ├── new_exp_board.kicad_sch
│       ├── new_exp_board.kicad_pcb     # board outline + placement
│       └── new_exp_board-backups/      # KiCad auto-backups (.zip)
└── README.md
```

- **`ExperimentalBoard/`** — first iteration. Contains the full schematic (114 symbols) including the power-supply section, but the PCB file is still empty.
- **`ExperimentalBoard/new_exp_board/`** — current iteration. Schematic (93 symbols) plus a laid-out PCB.

## Features

### Power (v1 schematic)
- DC barrel jack input (12 V)
- TBU-CA-025-500 transient-blocking protection and 1N5819 Schottky diodes
- Linear regulators: LM7809 (9 V), LM7805 (5 V), LD1117 (12 V)
- Labeled distribution headers/rails: `12vin`, `9volts`, `5volts`, `3.3volts`
- Indicator LEDs for the supply rails

### I/O and experiment blocks (both revisions)
- 8 × indicator LEDs (D2–D9 with series resistors)
- 8-bit DIP switch (plus a 4-bit DIP switch in v1)
- Tactile push buttons (MEC 5E / 5G family) and 6 × external switch terminals (`PINSW1`–`PINSW6`)
- 4 × LDR07 light-dependent resistors (light sensing)
- Potentiometers: 10 kΩ, 50 kΩ, 100 kΩ, 5 kΩ + a trimmer (`RV`)
- 2 × buzzers driven by BC547 NPN transistors
- Interfacing: 2.54 mm pin headers, 1.00 mm pin headers, 3-pin pot/sensor headers, 8-bit parallel header, and screw terminals for external wiring
- `5V` / `GND` test points

## Board specifications (new_exp_board)

| Item | Value |
|---|---|
| PCB size | ~276.4 × 169.7 mm |
| Layers | 2 (F.Cu, B.Cu) |
| Thickness | 1.6 mm |
| Footprints placed | 77 |
| Track segments | 0 (unrouted) |
| Mounting holes | none |

## Project status

| Stage | v1 (`ExperimentalBoard`) | v2 (`new_exp_board`) |
|---|---|---|
| Schematic | Complete | Complete |
| Board outline | — | Done (276 × 170 mm) |
| Footprint placement | — | Partial / in progress |
| Routing | — | Not started |
| DRC / fab outputs | — | Not started |

The board is currently in the **placement phase** — the outline and most components are positioned, but no traces have been routed and no gerbers have been generated.

## Getting started

1. Install [KiCad 8.0](https://www.kicad.org/) or newer (files use KiCad 8 file formats, `kicad_sch` v20231120 / `kicad_pcb` v20240108).
2. Open the project file:
   - Current revision: `ExperimentalBoard/new_exp_board/new_exp_board.kicad_pro`
   - Original schematic: `ExperimentalBoard/ExperimentalBoard.kicad_pro`
3. Schematic Editor to review/edit the circuit, PCB Editor to continue placement and routing.

All symbols and footprints come from the standard KiCad 8 libraries — no custom libraries are required.

## Backups

Each design has a `-backups/` folder containing timestamped `.zip` archives written by KiCad's auto-backup. These are safe to keep under version control, but large; trim them if repository size becomes an issue.
