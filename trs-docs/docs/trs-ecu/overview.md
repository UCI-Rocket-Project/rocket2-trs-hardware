# TRS-ECU — Overview

**Location:** Bunker  
**Role:** Recieves live telemetry data from ECU

---

## Description

TRS-ECU is located in the bunker and serves as the bunker-side radio node in the telemetry chain. It receives telemetry data from ECU and forwards it back to the network.

TRS-ECU runs on the same shared PCB as TRS-GND and TRS-ARM, powered by an 8.4V LiPo supply.

---

## Key Responsibilities

- Relay rocket telemetry back to the bunker LAN
- Operate continuously from bunker power supply during test operations
