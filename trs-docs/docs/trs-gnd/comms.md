# TRS-GND — Comms

## Communication Interfaces

TRS-GND uses three primary communication interfaces: LoRa radio, Ethernet, and SPI.

---

## 915 MHz LoRa Radio (RFM95W)

| Parameter | Value |
|-----------|-------|
| Module | HopeRF RFM95W |
| Frequency | 915 MHz |
| Modulation | LoRa (Semtech SX1276) |
| Interface | SPI (RADIO_CS, RADIO_SCK, RADIO_MISO, RADIO_MOSI) |
| Reset | RADIO_nRST |
| Antenna | Coaxial connector J4 |

TRS-GND sends arming command to TRS-ARM.

---

## 433 MHz Secondary LoRa (SEEEDSTUDIOLORAERMINI)

| Parameter | Value |
|-----------|-------|
| Module | Seeed Studio LoRa (U6) |
| Interface | UART (STM_TX_LORA_TX / STM_RX_LORA_RX) |
| Pins | PA9/PA10 |

Used for REDS radio data.

---

## Ethernet (GC-XPORT-ENH)

| Parameter | Value |
|-----------|-------|
| Module | Grid Connect Ethernet Xport (U4) |
| Interface | UART bridge (STM_TX_ETH_TX / STM_RX_ETH_RX) |
| STM32 Pins | PA2 (TX), PA3 (RX) |
| Reset | ETH_RST (PB0) |
| Physical | RJ45 to test stand router |

The Ethernet Xport converts UART data to TCP/IP, connecting TRS-GND into the test stand network. This allows GSE laptops and the GUI PC in the bunker to receive data over the LAN.

---

## FC Switch (LOGICA / LOGICB)

| Signal | Description |
|--------|-------------|
| LOGICA1/LOGICB1 | FC switch channel A control |
| LOGICA2/LOGICB2 | FC switch channel B control |
| NMOS1/NMOS2 | MOSFET gate drive via TLP3553A optocoupler |

The FC switch allows the STM32 to switch flight computer power or signal lines via isolated NMOS logic.

---

## Level Shifters

Two SN74LVC1T45DCK single-bit level shifters (U9, U10) translate between 5V logic (Ethernet Xport, FC switch) and 3.3V logic (STM32).

---

## USB (USB-C)

Used for firmware flashing and serial debug. The `USB_DETECT` line signals the STM32 when USB is connected. Not used for live telemetry.
