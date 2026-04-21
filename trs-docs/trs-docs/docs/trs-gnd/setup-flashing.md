# TRS-GND — Setup & Flashing

## Requirements

- STM32CubeProgrammer or OpenOCD
- SWD debugger (ST-Link V2 or compatible)
- ARM Cortex Debug cable (J3 header)
- USB-C cable (optional, for USB DFU mode)

---

## SWD Flashing (Recommended)

Connect your SWD debugger to the **J3 ARM Cortex Debug** header:

| J3 Pin | Signal |
|--------|--------|
| 1 | VCC (3.3V) |
| 2 | SWDIO/TMS |
| 3 | GND |
| 4 | SWCLK/TCK |
| 5 | SWO/TDO |
| 6 | NC/TDI |
| 7 | SWDIO |
| 8 | SWCLK |
| Reset | NRST |

```bash
# Flash via OpenOCD (ST-Link)
openocd -f interface/stlink.cfg \
        -f target/stm32f1x.cfg \
        -c "program firmware.bin verify reset exit 0x08000000"
```

---

## USB DFU Mode

1. Hold **BOOT0** high (jumper or button) while applying power
2. Connect USB-C to host
3. STM32 will enumerate as a DFU device
4. Flash using `dfu-util`:

```bash
dfu-util -a 0 -s 0x08000000:leave -D firmware.bin
```

---

## First-Time Setup

1. Verify 3.3V LED (D3) is illuminated after power-on
2. Confirm `USB_DETECT` LED (D4) lights when USB-C is connected
3. Check Ethernet Xport link LED on RJ45 connector
4. Confirm radio is responding via serial debug output

---

## Configuration (TRS-GND Specific)

| Parameter | Value |
|-----------|-------|
| Role | Ground relay |
| Radio frequency | 915 MHz |
| Ethernet IP | Assigned by test stand router (DHCP or static) |
| UART baud (Ethernet Xport) | _TODO: confirm baud rate_ |
| UART baud (LoRa module) | _TODO: confirm baud rate_ |

---

## Troubleshooting

| Symptom | Check |
|---------|-------|
| No power LED | Verify barrel jack polarity and battery charge |
| No Ethernet link | Check RJ45 cable and router connection |
| Radio not responding | Verify antenna on J4, check SPI wiring |
| SWD not detected | Check J3 wiring, ensure NRST not held low |
| USB not enumerating | Confirm BOOT0 state, check USB-C cable |
