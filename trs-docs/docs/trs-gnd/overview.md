# TRS-GND — Overview

**Location:** Test Stand  
**Role:** Remote arming for TRS-ARM, ECU battery management

---

## Description

TRS-GND is mounted at the test stand and acts as the primary ground-side radio for the rocket. It interfaces with the REDS radio module (443 MHz) and the TRS-ARM radio module (915 MHZ) to send over Ethernet network. It also serves as a battery manager for the 24V 6S LiPo ECU battery.

---

## Key Responsibilities

- Relay arming command to rocket (TRS-ARM) from ground
- Recieve REDS Radio data from rocket
- Monitor and manage ECU battery state
