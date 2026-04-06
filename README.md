# Flipper Zero Toolkit

Custom apps, community SD card files, and a [ufbt](https://github.com/flipperdevices/flipperzero-ufbt) project scaffold for the [Flipper Zero](https://flipperzero.one/) multi-tool (STM32WB55RG + CC1101 + ST25R3916).

> **For AI agents**: This repo is the authoritative reference for Darrin's Flipper Zero SD card contents. Use the file inventory and category tables below to locate captures, recommend applications, and answer questions about what signals/protocols are available. Browse individual folders on GitHub to inspect `.sub`, `.ir`, `.nfc`, and `.txt` files directly.

---

## Repository Structure

```
flipper_zero/
├── .github/workflows/build.yml   # CI — builds stogs_rf_bridge.fap
├── application.fam                # ufbt app manifest
├── stogs_rf_bridge.c              # Custom app source (serial RF bridge)
├── stogs_rf_bridge.png            # App icon (10×10 1-bit)
├── images/                        # Additional icon assets
├── Micro_SD_Clone/                # ← Full SD card mirror (21,689 files)
│   ├── 00_Lab_Work/               # Personal captures & experiments
│   ├── 01_Radio_SubGHz/           # Sub-GHz signal files (.sub, .raw)
│   ├── 02_NFC_RFID/               # NFC dumps & RFID emulation
│   ├── 03_Infrared_Remotes/       # Curated IR remote files
│   ├── 03_Infrared_Remotes_IRDB/  # Flipper-IRDB community database
│   ├── 04_BadUSB_Payloads/        # DuckyScript HID payloads
│   ├── apps/                      # Pre-built .fap applications
│   ├── unirf/                     # UniRF Remix multi-signal configs
│   └── Wav_Player/                # WAV audio files
└── README.md                      # ← You are here
```

### Naming Convention
- All directories and filenames use **underscores** (no spaces)
- Top-level content folders have **numbered prefixes** (`00_`, `01_`, …) for sort order
- The `Micro_SD_Clone/` directory is a 1:1 mirror of the physical micro SD card (FAT32, inserted in the Flipper via USB adapter as drive `E:`)

---

## SD Card Contents — Detailed Inventory

### `01_Radio_SubGHz/` — 11,800+ files (11,500 `.sub` captures)

Sub-GHz radio signal captures at 300–928 MHz. Each `.sub` file is a Flipper-native capture that can be replayed via the Sub-GHz app. `.raw` files are raw signal recordings.

| Category | `.sub` files | Notes |
|----------|-------------|-------|
| **TouchTunes** | 8,199 | Jukebox remote commands (all codes) |
| **Gates** | 981 | Gate openers, barriers, bollards |
| **Ceiling_Fans** | 485 | Fan speed/light remotes |
| **LED** | 390 | LED strip controllers |
| **Restaurant_Pagers** | 287 | Paging systems |
| **Misc** | 198 | Uncategorized signals |
| **Remote_Outlet_Switches** | 179 | Smart outlet toggles |
| **Garages** | 169 | Garage door openers |
| **Vehicles** | 139 | Keyfob signals (15 brand folders) |
| **Multimedia** | 90 | A/V remotes |
| **Doorbells** | 83 | Wireless doorbells |
| **Training_Collars** | 66 | Pet training devices |
| **Weather_stations** | 39 | Weather sensor signals |
| Others | ~200+ | Cable boxes, gas signs, beds, sensors, sprinklers, smoke alarms, vacuums, etc. |

**Vehicle brands** (`Vehicles/`): Chrysler/Dodge/Jeep, Ford, GM/Chevy/GMC/Cadillac, Honda/Acura, Hyundai/Kia/Genesis, Isuzu, Lamborghini, LDV, Lexus/Toyota, Mazda, Nissan, Tesla, Mixed.

**Special folders**:
- `Settings/` — `setting_user` and `region_data_null` (Sub-GHz region config)
- `Sprinklers/` — includes HackRF `.complex16s` IQ captures (Hunter Roam)
- `Pocsag/` — pager protocol captures
- `DEFCON32_Bracelet_(FREE-WILi)/` — DEF CON 32 badge signals

### `02_NFC_RFID/` — 39 files

| Subfolder | Contents |
|-----------|----------|
| `Amiibo/` | Nintendo Amiibo `.nfc` dumps + converters (multiple collections) |
| `Fun_Files/` | Novelty NFC tags |
| `HID_iClass/` | HID access card formats |
| `NFC-Trolls/` | Troll/prank NFC payloads |
| `mf_classic_dict/` | MIFARE Classic dictionary files for brute-force |

### `03_Infrared_Remotes/` — 17 files (curated)

Hand-picked IR files in `IRDB/`, `Pronto_IR/`, and `ir_remote/` subfolders. These are select remotes for personal use.

### `03_Infrared_Remotes_IRDB/` — 8,943 files (community database)

Full clone of the [Flipper-IRDB](https://github.com/logickworkshop/Flipper-IRDB) project. **44 device categories** including:

ACs, Air Purifiers, Audio/Video Receivers, Blu-Ray, Cable Boxes, Cameras, CD Players, Consoles, Converters, DVD Players, Fans, Fireplaces, Heaters, Humidifiers, LED Lighting, Monitors, Multimedia, Projectors, SoundBars, Speakers, Streaming Devices, TVs, Universal TV Remotes, VCR, Vacuum Cleaners, and more.

> **Agent tip**: To find an IR file for a specific device brand/model, browse `03_Infrared_Remotes_IRDB/<Category>/` — files are organized by manufacturer.

### `04_BadUSB_Payloads/` — 764 files (445 `.txt` DuckyScript payloads)

HID attack scripts in DuckyScript format. Organized by author/collection:

| Collection | Platform | Description |
|------------|----------|-------------|
| **Aleff-BadUSB** | Win/Mac/Linux/iOS | Large curated library |
| **AbeNaws-BadUSB** | Win/iOS/Linux | Multi-platform payloads |
| **Jakoby_BadUSB** | Windows | Popular payload author |
| **emptythevoid-BadUSB** | Win/Linux | Advanced: exfil, serial, mass storage |
| **BadGPT** | — | AI-powered payload generation |
| **UNC0V3R3D** | Win/iPhone | Collection |
| **Bombs/** | Windows | Fork bomb, zip bomb, folder bomb, rickroll |
| **Kavitate / s4dic / atomiczsec** | Various | Misc authors |
| **InfoSecREDD / MarkCyber** | Windows | Security research payloads |
| Others | Various | chromeOS, macOS-specific, password grabs |

### `apps/` — Pre-built Flipper Applications

| App | Path | Purpose |
|-----|------|---------|
| **ProtoPirate** | `apps/Sub-GHz/proto_pirate.fap` | Sub-GHz protocol analyzer & replayer. Decodes/identifies protocols from captured signals. **Best for**: identifying unknown Sub-GHz signals, protocol reverse-engineering. |
| **RF Jammer** | `apps/Sub-GHz/jammer_app.fap` | Sub-GHz signal jammer (300–928 MHz). **Use with caution**: transmits noise on target frequency. |
| **ProtoView** | `apps/Tools/protoview.fap` | Real-time Sub-GHz signal protocol viewer by antirez. **Best for**: live signal analysis, visualizing modulation patterns, quick protocol ID. |
| **FlipperHTTP** | `apps/GPIO/flipper_http.fap` | WiFi dev board configuration UI. Requires ESP32/ESP8266 on GPIO header. **Best for**: setting up WiFi connectivity for the Flipper. |
| **Windows Exfil** | `apps/Scripts/Windows_Exfil-GSHD.js` | JavaScript exfiltration helper script (used with BadUSB payloads). |

> **Agent tip — choosing an app**:
> - "What protocol is this signal?" → **ProtoView** (real-time) or **ProtoPirate** (from captures)
> - "Replay/clone a Sub-GHz signal" → Use the built-in **Sub-GHz** app on the Flipper, or **ProtoPirate** for protocol-aware replay
> - "Jam a frequency" → **RF Jammer** (lab use only)
> - "Connect Flipper to WiFi" → **FlipperHTTP** (needs GPIO dev board)
> - "Run a BadUSB attack" → Load scripts from `04_BadUSB_Payloads/` via the built-in **Bad USB** app

### `unirf/` — UniRF Remix Configurations (21 files)

Multi-signal `.txt` files for the [UniRF Remix](https://github.com/ESurge/flern) app. Each file maps multiple Sub-GHz actions to a single menu. Notable configs:

- `Debruijn_Open-Sesame.txt` / `_EU.txt` — brute-force sequences for common fixed-code gates
- `TTbrute.txt` — TouchTunes brute force
- `Cop_Spotlight.txt`, `Ridin_Dirty1/2.txt` — vehicle-related
- `Gas_Sign_Edit.txt` — gas station LED sign
- `Doorbell_W727_A/B.txt` — wireless doorbell triggers

### `Wav_Player/` — 97 audio files

WAV files playable through the Flipper's speaker via the Wav Player app.

---

## Custom ufbt App — `stogs_rf_bridge`

A Flipper application that bridges RF data to the [stogsdill.net](https://stogsdill.net) dashboard via USB serial. This connects the Flipper Zero's CC1101 radio to the yard_service Python backend running on port 8800.

### Project Files

```
application.fam     # App manifest (appid, entry_point, icon, sources)
stogs_rf_bridge.c   # Main source — USB-CDC serial bridge
stogs_rf_bridge.png # 10×10 1-bit app icon
images/             # Additional icon assets compiled into .fap
```

### Build & Deploy

Requires [ufbt](https://github.com/flipperdevices/flipperzero-ufbt) (Flipper Zero micro build tool):

```bash
ufbt build          # Compile → dist/stogs_rf_bridge.fap
ufbt launch         # Build + install + run on connected Flipper
ufbt cli            # Open serial CLI to connected Flipper
```

**CI**: The `.github/workflows/build.yml` workflow builds automatically on push. It uses sparse checkout to skip `Micro_SD_Clone/` (the build only needs source files and `images/`).

### Integration with stogsdill.net

The `stogs_rf_bridge` app communicates over USB-CDC serial at 230400 baud. On the backend:
- **Python driver**: `server/rf_core/flipper_device.py` auto-detects VID:PID `0483:5740` on `/dev/ttyACM*`
- **FastAPI endpoints**: `/flipper/*` routes in `server/yard_service/main.py`
- **Flutter UI**: `lib/views/rf/flipper_zero_tab.dart` — 8-tab interface (Dashboard, Sub-GHz, NFC/RFID, IR, GPIO, Files, Apps, CLI Terminal)
- **WebSocket**: `/ws/flipper/telemetry` for live data streaming

---

## Hardware

| Device | VID:PID | Chip | Role | Frequency |
|--------|---------|------|------|-----------|
| Flipper Zero | `0483:5740` | STM32WB55RG + CC1101 + ST25R3916 | Multi-tool (Sub-GHz, NFC, RFID, IR, GPIO, BLE 5.4) | Sub-GHz: 300–928 MHz, NFC: 13.56 MHz, RFID: 125 kHz |
| RTL-SDR v4 | `0BDA:2838` | RTL2832U + R828D | Wideband receiver (RX only) | 24 MHz – 1.766 GHz |
| Yardstick One | `1D50:605B` | CC1111 | Sub-GHz TX/RX via rfcat | 300–928 MHz |

### Flipper Zero Specs
- **CPU**: ARM Cortex-M4F @ 64 MHz (STM32WB55RG)
- **Battery**: 2100 mAh Li-Po
- **GPIO**: 18-pin header (3.3V, 5V, UART, SPI, I2C, 1-Wire)
- **Storage**: micro SD (FAT32), currently ~2 GB used
- **Firmware**: Official + ufbt for custom `.fap` apps
- **Serial**: USB-CDC at 230400 baud, prompt `">: "`
- **Build SDK**: ufbt (Target 7, API 87.1), or full fbt from firmware repo

---

## Community Sources & Upstream Repos

These are the primary sources for the SD card files in this repo:

| Source | URL | What it provides |
|--------|-----|-----------------|
| **UberGuidoZ/Flipper** | [GitHub](https://github.com/UberGuidoZ/Flipper) | Comprehensive SD card pack (Sub-GHz, NFC, BadUSB, IR, etc.) — primary source for most files |
| **Flipper-IRDB** | [GitHub](https://github.com/logickworkshop/Flipper-IRDB) | 8,900+ IR remote files organized by device category |
| **RocketGod-git/ProtoPirate** | [GitHub](https://github.com/RocketGod-git/ProtoPirate) | Sub-GHz protocol analyzer `.fap` — decodes/IDs signals |
| **antirez/protoview** | [GitHub](https://github.com/antirez/protoview) | Real-time signal protocol viewer `.fap` |
| **jblanked/FlipperHTTP-App** | [GitHub](https://github.com/jblanked/FlipperHTTP-App) | WiFi dev board UI `.fap` |
| **ESurge/flern** | [GitHub](https://github.com/ESurge/flern) | UniRF Remix — multi-signal menu app |
| **Flipper Zero firmware** | [GitHub](https://github.com/flipperdevices/flipperzero-firmware) | Official firmware + fbt/ufbt build system |
| **Flipper Zero ufbt** | [GitHub](https://github.com/flipperdevices/flipperzero-ufbt) | Micro build tool for external `.fap` apps |
| **DuckyScript Cookbook** | [GitHub](https://github.com/hak5/usbrubberducky-payloads) | Hak5 payload reference (BadUSB format source) |

> **Agent tip**: To check for updates to any community source, compare the upstream repo's latest commit date with the files in `Micro_SD_Clone/`. If significantly newer content is available, recommend a refresh.

---

## File Format Reference

| Extension | Domain | Description | How to use on Flipper |
|-----------|--------|-------------|-----------------------|
| `.sub` | Sub-GHz | Captured/recorded signal (protocol + data) | Sub-GHz → Saved → select file → Send |
| `.raw` | Sub-GHz | Raw signal recording (no protocol decode) | Sub-GHz → Saved → select file → Send |
| `.ir` | Infrared | IR remote command(s) | Infrared → Saved Remotes → select |
| `.nfc` | NFC | NFC card dump (MIFARE, NTAG, etc.) | NFC → Saved → select → Emulate |
| `.rfid` | RFID | 125 kHz RFID tag dump | RFID → Saved → select → Emulate |
| `.fap` | Apps | Compiled Flipper application | Apps → select from category |
| `.txt` | BadUSB / UniRF | DuckyScript payload or UniRF config | Bad USB → select script → Run |
| `.wav` | Audio | Audio file for speaker playback | Wav Player → select file |
| `.complex16s` | IQ Data | HackRF IQ capture (not Flipper-native) | For analysis only (URH, GNU Radio) |
| `.js` | Scripts | JavaScript helper (BadUSB companion) | Run on host PC, not on Flipper |

---

## Quick Navigation Guide

**"I want to…"** → **Go to:**

| Goal | Path |
|------|------|
| Replay a garage door signal | `01_Radio_SubGHz/Garages/` |
| Control a TouchTunes jukebox | `01_Radio_SubGHz/TouchTunes/` |
| Open a gate | `01_Radio_SubGHz/Gates/` |
| Test vehicle keyfobs | `01_Radio_SubGHz/Vehicles/<Brand>/` |
| Control a ceiling fan | `01_Radio_SubGHz/Ceiling_Fans/` |
| Find a TV remote | `03_Infrared_Remotes_IRDB/TVs/<Brand>/` |
| Find an AC remote | `03_Infrared_Remotes_IRDB/ACs/<Brand>/` |
| Emulate an Amiibo | `02_NFC_RFID/Amiibo/` |
| Brute-force MIFARE Classic | `02_NFC_RFID/mf_classic_dict/` |
| Run a BadUSB payload | `04_BadUSB_Payloads/<Collection>/` |
| Brute-force a gate code | `unirf/Debruijn_Open-Sesame.txt` |
| Analyze an unknown signal | Install `apps/Tools/protoview.fap` or `apps/Sub-GHz/proto_pirate.fap` |
| Play audio on Flipper | `Wav_Player/` |
| Build the custom bridge app | `ufbt build` (root of repo) |

---

## License

Custom app code (`stogs_rf_bridge.c`, `application.fam`) is MIT. Community SD card files retain their original licenses — see upstream repos for details.
