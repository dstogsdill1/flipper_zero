# Flipper Zero Toolkit

Custom apps, community SD card files, and a ufbt project scaffold for the [Flipper Zero](https://flipperzero.one/) multi-tool.

## SD Card Layout

All directories and filenames use **underscores** (no spaces). Top-level content folders have numbered prefixes for sort order.

```
Micro_SD_Clone/
├── 00_Lab_Work/                # Personal captures, experiments, notes
├── 01_Radio_SubGHz/            # Sub-GHz signal captures & databases
├── 02_NFC_RFID/                # NFC card dumps & emulation files
├── 03_Infrared_Remotes/        # IR remote control files
├── 03_Infrared_Remotes_IRDB/   # Flipper-IRDB community IR database
├── 04_BadUSB_Payloads/         # DuckyScript HID payloads
├── apps/                       # Flipper applications (.fap)
│   ├── GPIO/flipper_http.fap   # WiFi config UI (FlipperHTTP)
│   ├── Sub-GHz/proto_pirate.fap
│   ├── Sub-GHz/jammer_app.fap
│   └── Tools/protoview.fap     # Signal protocol analyzer
├── unirf/                      # UniRF remix configurations
└── Wav_Player/                 # WAV audio files
```

## Custom ufbt App — `stogs_rf_bridge`

A Flipper application that bridges RF data to the [stogsdill.net](https://stogsdill.net) dashboard via serial.

```
application.fam     # App manifest
stogs_rf_bridge.c   # Main source
images/             # App icon assets
```

Build with [ufbt](https://github.com/flipperdevices/flipperzero-ufbt):

```bash
ufbt build
ufbt launch       # build + install + run
```

## Hardware

| Device | VID:PID | Role |
|--------|---------|------|
| Flipper Zero | `0483:5740` | Multi-tool (Sub-GHz, NFC, RFID, IR, GPIO, BLE) |
| RTL-SDR v4 | `0BDA:2838` | Wideband receiver (24 MHz – 1.766 GHz) |
| Yardstick One | `1D50:605B` | Sub-GHz TX/RX (300–928 MHz, rfcat) |

## Community Sources

- [UberGuidoZ/Flipper](https://github.com/UberGuidoZ/Flipper) — comprehensive SD card pack
- [Flipper-IRDB](https://github.com/logickworkshop/Flipper-IRDB) — IR remote database
- [RocketGod-git/ProtoPirate](https://github.com/RocketGod-git/ProtoPirate) — Sub-GHz protocol tool
- [jblanked/FlipperHTTP-App](https://github.com/jblanked/FlipperHTTP-App) — WiFi dev board UI
- [antirez/protoview](https://github.com/antirez/protoview) — signal protocol viewer

## License

Custom app code is MIT. Community SD card files retain their original licenses.
