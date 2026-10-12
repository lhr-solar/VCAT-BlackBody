# VCAT-BlackBody

Blackbody sensor boards for the LHR solar car top shell (VCAT / Telemetry).

Measures **solar irradiance** and **solar-module temperature** at locations across the top shell and reports them over CAN.

## Boards

| Board | Folder | Purpose |
|---|---|---|
| Main board | `hardware/` (`BlackBodyBoard.kicad_pro`) | Collects sensor data from the breakout(s), does the math, sends CAN messages |
| Breakout board | `hardware/IrradianceBreakout` | Holds the irradiance and temperature sensors on the top shell |

Baseline quantity: 3 (final count and placement TBD).

## CAN data (planned)

| Message | Rate |
|---|---|
| Solar irradiance (W/m²) | 10 Hz |
| Solar-module temperature (°C) | 2 Hz |
| Board status / faults | 1 Hz |

## Repo layout

Same layout as VCAT-StrainGaugeBoard:

```
CubeMX/CubeMX.ioc               STM32G473 pin/clock config (started from strain gauge; re-pin for Blackbody)
hardware/BlackBodyBoard.*        main board project (root sheet)
hardware/<Block>.kicad_sch       design blocks: PowerProtection, 12VBuck, Power_Mux, LDO,
                                 USB-C_Connector, 48PinMCU, CAN_Transceiver,
                                 Irradiance, Thermocouple, TC_Channel
hardware/IrradianceBreakout/     sensor breakout project
lib/KiCAD-Sharepoint/            shared LHRS symbols, footprints, design blocks (submodule)
lib/footprints/, lib/3dmodels/   board-specific parts
```

Conventions: power symbols + local labels on the root sheet, hierarchical labels inside sub-sheets, inputs on the left / outputs on the right, passive values without units (`10k`, `0.1u`).

## Getting started

```sh
git clone https://github.com/lhr-solar/VCAT-BlackBody.git
cd VCAT-BlackBody
git submodule update --init --recursive
```

## Documentation

Requirements: VCAT Board Tracker → Blackbody Board (Notion).
