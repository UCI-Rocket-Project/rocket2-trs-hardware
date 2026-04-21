# TRS-ECU — Pinout

TRS-ECU uses the same PCB and pin assignments as TRS-GND. Refer to the [TRS-GND Pinout](../trs-gnd/pinout.md) for the full STM32 pin table and connector definitions.

## Active Interfaces for TRS-ECU Role

| Interface | Pins | Used |
|-----------|------|------|
| RFM95W SPI Radio | RADIO_CS, RADIO_SCK, RADIO_MISO, RADIO_MOSI, RADIO_nRST | ✅ Yes |
| Ethernet UART (GC-XPORT-ENH) | PA2 (TX), PA3 (RX), ETH_RST | ✅ Yes |
| LoRa UART (SEEEDSTUDIOLORAERMINI) | PA9 (TX), PA10 (RX) | ✅ Yes |
| FC Switch (NMOS1/NMOS2) | PC14, PC15 | ❌ Not used |
| ARM Cortex Debug (J3) | SWDIO, SWCLK, NRST | ✅ For flashing |
| USB-C (J2) | USB_DP, USB_DM | ✅ Optional debug |
| ADC Voltage Sense (J1) | ADC1 | ❌ Not used |

## External Connectors (ECU)

| Connector | Function |
|-----------|----------|
| RJ45 | Ethernet to bunker network switch |
| J4 (Coaxial) | 915 MHz antenna |
| J3 (ARM Debug) | SWD programming |
| J2 (USB-C) | USB debug / DFU flash |
