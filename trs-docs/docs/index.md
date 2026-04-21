# TRS Documentation

Welcome to the **Telemetry Radio System (TRS)** documentation. This site covers all three TRS units used across the ground and rocket avionics systems.

---

The TRS family of boards recieves radio telemetry, arms our flight computers, and command links between the rocket and the ground support equipment (GSE). All three units share the same PCB hardware but are configured differently based on their role in the system.

---

## Units

| Unit | Location | Role |
|------|----------|------|
| [TRS-GND](trs-gnd/overview.md) | Test Stand | Remote arming for TRS-ARM, ECU battery management |
| [TRS-ECU](trs-ecu/overview.md) | Bunker | Recieves live telemetry data from ECU |
| [TRS-ARM](trs-arm/overview.md) | Rocket AV Bay | Arms Easy Mini Flight Computer |

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


---

## TRS Schematic

All three units use the same rocket2-trs-hardware PCB (KiCad E.D.A. 9.0.6).

![PCB Schematic](assets/pcb-schematic.png)

