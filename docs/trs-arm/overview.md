# TRS-ARM — Overview

**Location:** Rocket AV Bay  
**Role:** Arms Easy Mini Flight Computer

---

## Description

TRS-ARM is mounted inside the rocket's avionics bay and arms the Easy Mini flight computer. It receives arm and disarm commands from TRS-GND over the 915 MHz LoRa link and asserts the FC switch in response — physically gating power to the Easy Mini.

TRS-ARM boots in a safe, disarmed state. The Easy Mini only receives power after an explicit ARM command is received and verified over the radio link, which means the flight computer cannot accidentally activate e-matches during transport, integration, or handling on the pad.

TRS-ARM is also the return path for REDS radio data — it relays it from the rocket back to TRS-GND at the test stand, which then forwards it over Ethernet to the bunker.

---

## Key Responsibilities

- Receive arm/disarm commands from TRS-GND over 915 MHz LoRa
- Assert FC switch to arm the Easy Mini flight computer
- Default to disarmed state on every boot — arming requires an explicit command
- Relay REDS radio data back to TRS-GND at the test stand
- Operate from AV bay LiPo battery through the full flight profile
