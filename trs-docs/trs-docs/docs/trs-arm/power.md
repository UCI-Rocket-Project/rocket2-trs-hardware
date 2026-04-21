# TRS-ARM — Power

## Power Source

TRS-ARM is powered from the AV bay **8.4V LiPo battery pack**.

```
[8.4V AV Bay LiPo] ──► [AP63205WU Buck] ──► +5V ──► [AMS1117-3.3] ──► +3.3V
```

Refer to [TRS-GND Power](../trs-gnd/power.md) for full regulator specs and circuit details.

## TRS-ARM Power Notes

| Parameter | Value |
|-----------|-------|
| Input voltage | 8.4V (2S LiPo) |
| 5V rail | AP63205WU (switching buck) |
| 3.3V rail | AMS1117-3.3 (LDO) |
| Idle current draw | _TODO: measure_ |
| Radio TX peak current | _TODO: measure_ |
| FC switch current | _TODO: measure per channel_ |

## Battery Considerations

- TRS-ARM shares the AV bay 8.4V LiPo with other AV bay systems
- Ensure battery is fully charged before integration into airframe
- Verify voltage under load before flight — minimum input for AP63205WU is ~4.5V
- Battery capacity must support full flight duration plus pre-launch window

## Power-On Checklist (Pre-Flight)

- [ ] 8.4V battery connected and voltage confirmed ≥ 8.0V
- [ ] 3.3V LED (D3) illuminated
- [ ] Radio link to ground confirmed (telemetry received at GSE)
- [ ] FC switch in safe/disarmed state before transport
- [ ] USB-C disconnected before airframe close-out
