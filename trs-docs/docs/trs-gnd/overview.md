# TRS-GND — Overview

**Location:** Test Stand  
**Role:** Remote arming for TRS-ARM, ECU battery management

---

## Description

TRS-GND is mounted at the test stand, physically adjacent to the rocket on the pad. It is the ground-side endpoint of both the 915 MHz arming link to TRS-ARM and the 433 MHz REDS radio link from the rocket. 

In addition to radio duties, TRS-GND monitors the 24V 6S LiPo ECU battery at the test stand throughout the test campaign.

---

## Key Responsibilities

- Send arm/disarm commands to TRS-ARM over 915 MHz LoRa
- Receive REDS radio data from the rocket over 433 MHz
- Bridge both radio links to the test stand Ethernet network
- Monitor the ECU battery at the test stand
