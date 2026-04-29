# TRS-GND — Hardware

The TRS hardware is built around a small set of components, each chosen for a specific reason. This page explains what each part does and why it is on the board.

The TRS hardware is built around a small set of components, each chosen for a specific reason. This page explains what each part does and why it is on the board.

---

## STM32F103C8Tx — Main Microcontroller

The STM32F103C8Tx is the brain of the board. It was chosen because it is a well-supported, low-cost ARM Cortex-M3 that has enough GPIO, SPI, UART, and USB peripherals to talk to every other chip on the board simultaneously. It runs the radio link state machine, processes arm/disarm commands, manages the Ethernet bridge, and controls the FC switch — all from a single device. The "Blue Pill" form factor also means it is widely available and has extensive community firmware support.

## HopeRF RFM95W — 915/143 MHz LoRa Radio

The RFM95W is the primary radio link between TRS-GND and TRS-ARM on the rocket. LoRa (Long Range) modulation was chosen because it provides kilometre-scale range at low transmit power, which is critical for maintaining a link to the rocket at altitude or during a drift under parachute. The 915 MHz ISM band was selected because it is licence-free in the US and offers good penetration through airframe materials. The RFM95W talks to the STM32 over SPI, keeping the interface simple and the latency low for time-sensitive arm commands.

## Seeed Studio LoRa Module (SEEEDSTUDIOLORAERMINI) — 433 MHz Secondary Radio

This module handles the REDS radio data coming from the rocket. It operates on 433 MHz separately from the 915 MHz arming link, so REDS telemetry reception and arming commands do not interfere with each other. Using a dedicated module for this keeps the two radio links electrically independent.

## Grid Connect GC-XPORT-ENH — Ethernet Bridge

The Ethernet Xport converts UART serial data from the STM32 into TCP/IP packets on the wired network. This means the STM32 does not need to implement a full TCP/IP stack — it just sends and receives bytes over UART, and the Xport handles everything on the network side. TRS-GND uses this to feed data from the radio links into the test stand LAN, where the GSE laptop and GUI PC can receive it without any special drivers or direct serial connections.

## AP63205WU — 5V Buck Regulator

The board is powered at 5V from the Seeed Studio port. The AP63205WU is a synchronous buck converter that efficiently steps the input voltage down to a stable 5V rail. A switching regulator was used here rather than a linear regulator because it wastes far less power as heat, which matters for a board that may run for extended periods during a test campaign.

## AMS1117-3.3 — 3.3V LDO Regulator

The STM32, RFM95W, and the LoRa module all run at 3.3V. The AMS1117 takes the 5V rail and produces a clean 3.3V supply. An LDO was chosen at this stage because the voltage drop from 5V to 3.3V is small enough that the heat dissipation is manageable, and the LDO gives a quieter output than a second switcher would, which is important for the radio and ADC circuits.

## TLP3553A Optocouplers + NMOS — FC Switch

The Easy Mini and E-matches require a low-resistance firing path — anything over roughly one ohm in series and the e-match will not receive enough current to fire. MOSFETs are used as the switching element because their on-state resistance (R_DS(on)) is extremely low, keeping the total series resistance in the firing circuit well within limits.

The logic level shifter drives the MOSFET gates at a voltage high enough to fully saturate them. An under-driven gate leaves the MOSFET partially on with much higher resistance, which would undermine the whole point of using a MOSFET in the first place.

The TRS board and the Easy Mini run on separate ground references. Connecting them directly would create a transient path between the two grounds, causing noise and current spikes to couple back into the STM32 and radio circuitry at the moment of firing. The TLP3553A optocouplers drive the MOSFET gates optically, so the two ground domains are never conductively linked and transients on the firing side stay isolated from the rest of the board.

## SN74LVC1T45DCK — Level Shifters

The Ethernet Xport operates at 5V logic, while the STM32 operates at 3.3V. The SN74LVC1T45 single-bit level shifters sit between them, translating signals in both directions without needing separate power domains or resistor dividers. Two are used — one per UART direction — to keep the interface clean.

## USB-C Receptacle

USB-C is included primarily for firmware flashing in DFU mode and for serial debug output and as a power supply for TRS-GND ONLY. It is not used during live operations. The USB_DETECT signal lets the STM32 know when a host is connected, which can be used to suppress radio transmissions or trigger a bootloader entry.

## 16 MHz Crystal (Y1)

The STM32's internal RC oscillator is not accurate enough for USB enumeration or UART timing at high baud rates. The external 16 MHz crystal provides the precise clock reference that both the USB peripheral and the UART baud rate generators require.

## TRS-GND Specific Hardware

TRS-GND also includes a **Battery Manager** circuit that monitors the 24V 6S LiPo ECU battery at the test stand. This keeps the ECU battery in a known state during test operations and prevents over-discharge.
