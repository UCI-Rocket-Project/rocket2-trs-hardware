# TRS-GND — Overview

**Location:** Test Stand  
**Role:** Ground-side telemetry relay with battery management and dual-radio bridging

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

TRS-GND is mounted at the test stand and acts as the primary ground-side radio node for the rocket. It bridges the 915 MHz LoRa radio link from the rocket to the test stand Ethernet network. It also manages the test stand battery via a dedicated battery manager circuit.

TRS-GND runs two TRS_RADIO instances — one for uplink/downlink to the rocket, and a second for redundancy or range extension.

---

## System Context

![AV System Diagram](../assets/av-system-diagram.png)

TRS-GND sits in the **TRS-GND – Test Stand** subsection of the ground segment. It connects to:

- **Ethernet** → Router (Test Stand) → Network Switch (Bunker) → GSE Laptop, GUI PC
- **TRS_RADIO (x2)** → TRS-ARM (Rocket) via 915 MHz LoRa
- **5V Power Supply** → onboard regulator
- **Battery Manager** → barrel jack power input

---

## Key Responsibilities

- Relay telemetry from rocket (TRS-ARM) to ground network
- Forward commands from GSE laptop to rocket
- Monitor and manage test stand battery state
- Provide dual-radio link for redundancy
