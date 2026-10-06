# VCAT-BlackBody

Blackbody sensor boards for the LHR solar car top shell (VCAT / Telemetry).

Measures **solar irradiance** and **solar-module temperature** at locations across the top shell and reports them over CAN.

## Boards

| Board | Folder | Purpose |
|---|---|---|
| Main board | `hardware/BlackbodyMain` | Collects sensor data from the breakout(s), does the math, sends CAN messages |
| Breakout board | `hardware/BlackbodyBreakout` | Holds the irradiance and temperature sensors on the top shell |

Baseline quantity: 3 (final count and placement TBD).

## CAN data (planned)

| Message | Rate |
|---|---|
| Solar irradiance (W/m²) | 10 Hz |
| Solar-module temperature (°C) | 2 Hz |
| Board status / faults | 1 Hz |

## Repo layout

```
hardware/BlackbodyMain/       KiCad project: main board
hardware/BlackbodyBreakout/   KiCad project: sensor breakout
lib/KiCAD-Sharepoint/         Shared LHRS symbols, footprints, design blocks (submodule)
lib/footprints/, lib/3dmodels/  Board-specific parts
```

Symbol, footprint, and design-block tables use `${KIPRJMOD}` paths into `lib/KiCAD-Sharepoint`, so they work on any machine.

## Getting started

```sh
git clone https://github.com/lhr-solar/VCAT-BlackBody.git
cd VCAT-BlackBody
git submodule update --init --recursive
```

## Documentation

Requirements: VCAT Board Tracker → Blackbody Board (Notion).
