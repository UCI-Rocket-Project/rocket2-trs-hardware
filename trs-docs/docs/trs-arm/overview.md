# TRS-ARM — Overview

**Location:** Rocket AV Bay  
**Role:** Arms Easy Mini Flight Computer

---

## Description

TRS-ARM is mounted inside the rocket's avionics bay. It is the rocket-side endpoint of the 915 MHz LoRa telemetry link, communicating with TRS-GND at the test stand to arm the flight computers. In addition, TRS-ARM controls the **FC Switch** — the flight computer power/arming relay that turns on/arms the Easy Mini flight computer.

TRS-ARM is powered by an 8.4V LiPo battery inside the AV bay.

---

## Key Responsibilities

- Receive commands from ground (arm[ON]/disarm[OFF]) over 915 MHz LoRa
- Transmit REDS radio data  back to ground
- Control FC Switch to arm/disarm the Easy Mini flight computer
- Operate reliably from battery power throughout flight
