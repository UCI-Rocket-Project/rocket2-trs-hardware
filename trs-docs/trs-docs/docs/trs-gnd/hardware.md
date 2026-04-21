# TRS-GND — Hardware

## PCB

TRS-GND uses the shared `rocket2-trs-hardware` PCB.

![PCB Schematic](../assets/pcb-schematic.png)

## Key Components

| Component | Part | Description |
|-----------|------|-------------|
| MCU | STM32F103C8Tx (U2) | Main microcontroller |
| Radio | HopeRF RFM95W (U5) | 915 MHz LoRa transceiver |
| LoRa Module | SEEEDSTUDIOLORAERMINI (U6) | Secondary LoRa interface |
| Ethernet | GC-XPORT-ENH (U4) | Ethernet-to-serial bridge |
| 5V Regulator | AP63205WU (U1) | Buck regulator, 8V → 5V |
| 3.3V Regulator | AMS1117-3.3 (U3) | LDO, 5V → 3.3V |
| USB | USB-C Receptacle J2 | Programming / debug |
| FC Switch | TLP3553A (U7, U8) | Optocoupler-based switch logic |
| Level Shifters | SN74LVC1T45DCK (U9, U10) | Logic level translation |
| Crystal | Y1 16 MHz | MCU clock source |

## Additional Hardware (TRS-GND Specific)

| Item | Description |
|------|-------------|
| Battery Manager | Barrel jack input, manages test stand battery charging and output |
| 5V Power Supply | External 5V supply input to the board |
| Dual TRS_RADIO | Two RFM95W-based radio modules for redundant link |

## Mechanical

- Mounting holes: H1–H4 (MountingHole_Pad footprints)
- PCB size: A4 format (KiCad layout)
- Connector: Screw terminal J7, ARM Cortex Debug J3, Coaxial antenna J4
