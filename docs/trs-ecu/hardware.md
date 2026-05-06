# TRS-ECU — Hardware

TRS-ECU uses the same `rocket2-trs-hardware` PCB as TRS-GND and TRS-ARM. See [Shared Hardware](../hardware.md) for a full explanation of every component and the reasoning behind each choice — all of that applies equally here.

The one meaningful difference in TRS-ECU is that the **FC switch is not used**. The TLP3553A optocouplers and NMOS transistors are populated on the board but held inactive in firmware. TRS-ECU has no need to arm anything — its job is purely to receive telemetry and put it on the network.

---

## Enclosure / Mounting

TRS-ECU is mounted in an enclosure in the bunker. The antenna is routed externally to maintain line-of-sight to the test stand. Ethernet connects directly to the bunker network switch.
