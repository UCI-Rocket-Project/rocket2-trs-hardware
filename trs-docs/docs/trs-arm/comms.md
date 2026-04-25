# TRS-ARM — Comms

TRS-ARM uses the same hardware interfaces as TRS-GND and TRS-ECU. 

## Interface Usage in TRS-ARM 

| Interface | Role in TRS-ARM |
|-----------|-----------------|
| RFM95W (915 MHz LoRa) | Arming radio link to TRS-GND |
| FC Switch (NMOS1/NMOS2) | **Active** — arms/disarms Easy Mini flight computer |
| GC-XPORT-ENH (Ethernet) | Not connected in flight |
| USB-C | Pre-flight debug/flash only |

## Radio Link

```
[TRS-ARM - Rocket AV Bay]
           ^
           │
  [RFM95W 915 MHz LoRa]
           │  
  [TRS-GND - Test Stand] <── Ethernet ──> [Network Switch - Bunker] <── Ethernet ──> [Router - Test Stand]
                                                                                               ^
                                                                                               │
                                                                                            Ethernet
                                                                                               │
                                                                                               v
                                                                                     [GSE Laptop / GUI PC]
```

TRS-ARM communicates **only via radio** during flight. There is no wired Ethernet connection once the rocket is integrated.

## FC Switch Protocol

The FC switch is controlled by the STM32 in response to arm/disarm commands received over the LoRa link from the ground.

| Command (from ground) | STM32 Action | FC Switch State |
|-----------------------|--------------|-----------------|
| ARM | Assert LOGICA1 / LOGICB1 | Closed — Easy Mini powered |
| DISARM | De-assert LOGICA1 / LOGICB1 | Open — Easy Mini unpowered |
