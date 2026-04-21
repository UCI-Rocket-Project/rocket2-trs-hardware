# TRS-ECU — Overview

**Location:** Bunker  
**Role:** Bunker-side radio link bridging the network switch to the rocket via 915 MHz LoRa

---

## PCB 3D Model

<script type="module" src="https://ajax.googleapis.com/ajax/libs/model-viewer/3.5.0/model-viewer.min.js"></script>

<model-viewer
  src="../assets/rocket2-trs-hardware.glb"
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

## Description

TRS-ECU is located in the bunker and serves as the bunker-side radio node in the telemetry chain. It receives commands from the GSE laptop and GUI PC via the bunker network switch over Ethernet, and relays them wirelessly to the rocket (TRS-ARM) via the 915 MHz LoRa link. It also receives telemetry from the rocket and forwards it back to the network.

TRS-ECU runs on the same shared PCB as TRS-GND and TRS-ARM, powered by an 8.4V LiPo supply.

---

## System Context

![AV System Diagram](../assets/av-system-diagram.png)

TRS-ECU sits in the **TRS-ECU – Bunker** subsection. It connects to:

- **Ethernet** → Network Switch (Bunker) → GSE Laptop, GUI PC
- **TRS_RADIO (x1)** → TRS-ARM (Rocket) or TRS-GND (Test Stand) via 915 MHz LoRa
- **8.4V Power Supply** → onboard buck regulator

---

## Key Responsibilities

- Bridge bunker network to rocket radio link
- Forward operator commands from GUI PC / GSE laptop to rocket
- Relay rocket telemetry back to the bunker LAN
- Operate continuously from bunker power supply during test operations
