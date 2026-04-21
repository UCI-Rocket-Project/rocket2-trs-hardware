# TRS-ARM — Comms

TRS-ARM uses the same hardware interfaces as TRS-GND and TRS-ECU. Refer to [TRS-GND Comms](../trs-gnd/comms.md) for full interface details on the RFM95W, LoRa module, and level shifters.

## Interface Usage in ARM Role

| Interface | Role in TRS-ARM |
|-----------|-----------------|
| RFM95W (915 MHz LoRa) | Primary radio link to ground (TRS-GND / TRS-ECU) |
| SEEEDSTUDIOLORAERMINI | Secondary LoRa / redundancy |
| FC Switch (NMOS1/NMOS2) | **Active** — arms/disarms Easy Mini flight computer |
| GC-XPORT-ENH (Ethernet) | Not connected in flight |
| USB-C | Pre-flight debug/flash only |

## Radio Link

```
[TRS-ARM - Rocket AV Bay]
        │
  [RFM95W 915 MHz LoRa]
        │  (wireless)
   [TRS-GND - Test Stand]  ──Ethernet──► [Network Switch]
        │                                       │
   [TRS-ECU - Bunker]  ──────────────────────► [GSE Laptop / GUI PC]
```

TRS-ARM communicates **only via radio** during flight. There is no wired Ethernet connection once the rocket is integrated.

## FC Switch Protocol

The FC switch is controlled by the STM32 in response to arm/disarm commands received over the LoRa link from the ground.

| Command (from ground) | STM32 Action | FC Switch State |
|-----------------------|--------------|-----------------|
| ARM | Assert LOGICA1 / LOGICB1 | Closed — Easy Mini powered |
| DISARM | De-assert LOGICA1 / LOGICB1 | Open — Easy Mini unpowered |

The optocoupler (TLP3553A) provides galvanic isolation between the STM32 logic and the FC switch power rail.

## LoRa Link Parameters

| Parameter | Value |
|-----------|-------|
| Frequency | 915 MHz |
| Modulation | LoRa (SX1276) |
| Spreading factor | _TODO: confirm_ |
| Bandwidth | _TODO: confirm_ |
| TX power | _TODO: confirm (dBm)_ |
| Expected range | > 1 km line-of-sight |
