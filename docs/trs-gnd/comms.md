# TRS-GND — Comms

## Communication Interfaces

TRS-GND uses three primary communication interfaces: LoRa radio, Ethernet, and SPI.

---

## Interface Usage in TRS-GND 

| Interface | Role in TRS-ARM |
|-----------|-----------------|
| RFM95W (915 MHz LoRa) | Arming radio link to the rocket (TRS-ARM) |
| SEEEDSTUDIOLORAERMINI (433 MHz) | REDS radio link |
| GC-XPORT-ENH (Ethernet) | Recieve radio data to push to GSE laptop |
| USB-C | Power Supply |

## Radio Link

```
[TRS-ARM - Rocket AV Bay]
           │
  [RFM95W 915 MHz LoRa]
           │ 
           v 
  [TRS-GND - Test Stand] <── Ethernet ──> [Network Switch - Bunker] <── Ethernet ──> [Router - Test Stand]
           ^                                                                                  ^
           |                                                                                  │
  [SEEEDSTUDIO 433 MHz]                                                                    Ethernet
           |                                                                                  │
[REDS Radio - Rocket AV Bay]                                                                  v
                                                                                     [GSE Laptop / GUI PC]
```