# TRS-ECU — Comms

TRS-ECU uses the same hardware interfaces as TRS-GND. Refer to [TRS-GND Comms](../trs-gnd/comms.md) for full interface details on the RFM95W, Ethernet Xport, LoRa module, and level shifters.

## Interface Usage in ECU Role

| Interface | Role in TRS-ECU |
|-----------|-----------------|
| RFM95W (143 MHz LoRa) | Primary radio link to rocket |
| GC-XPORT-ENH (Ethernet) | Bridge to bunker network switch |
| SEEEDSTUDIOLORAERMINI | Secondary LoRa / redundancy |
| FC Switch | Not active |
| USB-C | Debug / flashing only |

## Network Topology

```
[TRS-ECU - Bunker] <── [RFM95W 143 MHz LoRa] ── [ECU Radio]
         ^
         │
      Ethernet
         │  
         v
[Network Switch - Bunker] <── Ethernet ──> [Router - Test Stand] <── Ethernet ──> [GSE Laptop / GUI PC]
                                                                                                                                                                     
```