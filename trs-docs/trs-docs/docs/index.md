# TRS Documentation

Welcome to the **Telemetry Radio System (TRS)** documentation. This site covers all three TRS units used across the ground and rocket avionics systems.

---

## System Overview

![AV System Diagram](assets/av-system-diagram.png)

The TRS family of boards provides radio telemetry and command links between the rocket and the ground support equipment (GSE). All three units share the same PCB hardware — a custom STM32F103C8Tx-based board with a HopeRF RFM95W 915 MHz LoRa radio — but are configured differently based on their role in the system.

---

## Units

| Unit | Location | Role |
|------|----------|------|
| [TRS-GND](trs-gnd/overview.md) | Test Stand | Ground-side radio relay, battery management, dual-radio bridging |
| [TRS-ECU](trs-ecu/overview.md) | Bunker | Bunker-side radio link to ECU network switch |
| [TRS-ARM](trs-arm/overview.md) | Rocket AV Bay | Rocket-side radio, FC switch control, arming relay |

---

## Shared PCB

All three units use the same `rocket2-trs-hardware` PCB (KiCad E.D.A. 9.0.6).

<script type="module" src="https://ajax.googleapis.com/ajax/libs/model-viewer/3.5.0/model-viewer.min.js"></script>

<model-viewer
  src="assets/rocket2-trs-hardware.glb"
  alt="TRS Hardware PCB 3D Model"
  auto-rotate
  camera-controls
  shadow-intensity="1"
  style="width: 100%; height: 500px; background: #1a1a2e; border-radius: 8px; margin-bottom: 1.5rem;"
  exposure="1.2"
  environment-image="neutral">
</model-viewer>

> **Tip:** Click and drag to rotate · Scroll to zoom · Right-click drag to pan

![PCB Schematic](assets/pcb-schematic.png)

Key ICs on the shared board:

- **MCU:** STM32F103C8Tx
- **Radio:** HopeRF RFM95W (915 MHz LoRa)
- **LoRa Transceiver:** Seeed Studio LoRa / SEEEDSTUDIOLORAERMINI (U6)
- **Ethernet:** Grid Connect GC-XPORT-ENH
- **5V Regulator:** AP63205WU (from 8V battery input)
- **3.3V Regulator:** AMS1117-3.3
- **USB:** USB-C receptacle (USB2.0, 16P)
- **FC Switch Logic:** TLP3553A optocouplers + NMOS logic
- **Level Shifters:** SN74LVC1T45DCK (x2)

---

## Communication Architecture

```
  [GSE Laptop] ──Ethernet── [Network Switch]
                                  │
                    ┌─────────────┼─────────────┐
                    │             │              │
               [TRS-ECU]    [GUI PC]      [Steady Blue GS]
                    │
               (915 MHz LoRa)
                    │
               [TRS-GND] ──── [TRS-ARM (Rocket)]
```

Refer to each unit's **Comms** page for protocol and frequency details.
