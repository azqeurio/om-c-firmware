# db firmware

A user-made patch tool for adding extra features to Olympus / OM SYSTEM Micro Four Thirds cameras (**v0.4.5**, 24 bodies / 26 profiles).

[English](./README.md) | [한국어](./README.ko.md) | [Compatibility & Status](https://db-firmware-support.vercel.app/en) | [Overview Table](https://db-firmware-support.vercel.app/en/overview)

## Read before using

- **No firmware is included.** This program does not contain or redistribute any OM SYSTEM or Olympus firmware. It is simply a user-made tool that patches official stock firmware locally on your computer.
- **Hardware testing scope.** I only own **3 cameras (OM-1, OM-5 Mark II, and E-M10)**, so those are the ones I can test on real hardware before releasing. Everything for other models is checked through offline simulation. Please keep that in mind before flashing.
- **Use at your own risk.** I am not responsible if your camera breaks, bricks, or malfunctions after updating with this tool. Make sure your battery is fully charged, keep a backup of the stock firmware, and install at your own risk.
- **Please leave feedback after using it.** After trying a build, filling out the feedback form shown in the tool (or on the [compatibility site](https://db-firmware-support.vercel.app/en)) helps a lot. Since I don't own every camera, user reports are how everyone—including me—can see what actually works on each body.

---

## Desktop Tool

Available for **Windows (x64)** and **macOS (Apple Silicon, macOS 15.0+)** with both English and Korean UI.

- Downloads official stock firmware (or loads a local `.BIN` file) and lets you save an untouched stock backup with SHA-256 verification.
- Patches only the features you select and outputs an SD-card update folder (`DCOLYMP/`).
- Built-in **SD LUT Editor & Converter**: converts `.cube`, `.xmp`, `.lrtemplate`, and presets, previews them on RAW/photo files, and exports LUT files directly to your SD card.
- Built-in **Electronic Shutter Sound Editor**: imports `WAV / MP3 / FLAC / M4A / OGG` (up to 5 s), trims waveforms, previews burst rates (`12.5 / 16.7 / 25 / 50 fps`), and saves/loads sound bank presets.
- Built-in `?` window to check live compatibility stats and submit anonymous test reports (no firmware files or local file paths are ever uploaded).

---

## Features

### Firmware Ports (2 profiles)
- **OM-1 → OM-1 Mark II Port**
  Runs OM-1 Mark II (`FW 1.3`) firmware on the original OM-1 (Live GND, Human AF, Mk2 features) with an expanded Sequential burst buffer (**85 frames** / 93 physical RAW slots / +160 MiB). Supports Korean UI, Panasonic aperture ring, Wi-Fi 5 GHz, electronic shutter sound, Quasi LUT (with on-screen Q badge, selection bar, and wireless sync), and Hybrid shutter.
  *(Resets camera settings on first install and when reverting to stock OM-1 firmware.)*
- **OM-5 → OM-5 Mark II Port** *(Experimental)*
  Runs OM-5 Mark II (`FW 1.1`) firmware and its newer menu UI on the original OM-5. Supports Korean UI, Panasonic aperture ring, and IR Red-Blue channel swap.
  *(Resets camera settings on first install and when reverting to stock OM-5 firmware.)*

### Quasi LUT — SD Card & Mobile App (4 profiles: TruePic X)
*OM-1 (1.9), OM-1 Mk2 Port (1.9), OM-1 Mark II (1.3), OM-3 (1.1)*
- Adds channel mixing, shadow/highlight toning, 12-color HSL, black/white point, 257-point R/G/B/Master tone curves, 6-color hue/saturation, and RGB output gain (monochrome modes excluded).
- **Color Film Grain**: Applies OM-3's monochrome grain (Low / Medium / High) to color still photos (Art Filters excluded).
- Stores up to **8 LUT slots (`Q1`–`Q8`)** on the SD card, so you can swap looks without reflashing firmware.
- Assign `[Q-LUT]` to a button (short press = toggle on/off, hold + dial = switch slots) or change it in Wrench Menu → `Quasi LUT`. On/off state and active slot persist across power cycles.
  - OM-1 Mark II & OM-1 Mk2 Port show a live `Q1..Q8` badge and selection bar (up to 18-char names); OM-3 shows the selection bar while holding Q-LUT + dial; stock OM-1 uses button/dial and menu.
- Works with the [db_link Android app](https://play.google.com/store/apps/details?id=com.dblink) to edit, reorder, or delete SD card LUTs wirelessly from your phone.

### Hybrid Shutter (9 profiles)
*OM-1 (1.9), OM-1 Mk2 Port (1.9), OM-1 Mark II (1.3), OM-3 (1.1), OM-5 (1.2), OM-5 Mark II (1.1), E-M1X (2.4), E-M1 Mark III (1.6), E-P7 (1.1)*
- Adds a **Hybrid (`H□`)** drive mode next to Single shooting.
- Shoots with the mechanical shutter up to its limit (`1/8000 s`, or `1/4000 s` on E-P7) and automatically switches to the electronic shutter up to `1/32000 s` (`1/16000 s` on E-P7) when needed.
- Switches before Auto ISO drops into extended Low ISO in P/A, and opens the faster shutter speeds on the dial in S/M only while Hybrid is selected.
- Remembers the last drive mode across power cycles. Other drive modes, flash, Bulb/Live Time, video, High Res, Live ND, and Flicker Scan stay stock.

### Panasonic Aperture Ring Support (25 profiles)
*All supported profiles except E-M5 (2.3).*
- Lets Panasonic Leica / Lumix lenses with physical aperture rings work natively in **A and M modes**.
- Locked to A/M only so turning the ring in P/S won't affect exposure; lenses without an aperture ring keep normal body dial control.

### Infrared (IR) Red-Blue Channel Swap (22 profiles)
*All 22 non-TruePic-X profiles (everything except OM-1, OM-1 Mk2 Port, OM-1 Mark II, OM-3).*
- Swaps Red and Blue channels in the hardware 3×3 color matrix for IR-converted cameras.
- Applies to Live View, JPEGs, video, and in-camera RAW conversion without touching raw ORF sensor data or MakerNotes.
- Monotone, Monochrome profiles (`MONO 1/2/3`), and B&W/Sepia Art Filters stay stock.

### Korean Menu & Font Localization (7 profiles)
*OM-1 (1.9), OM-1 Mk2 Port (1.9), OM-1 Mark II (1.3), OM-3 (1.1), OM-5 (1.2), OM-5 Mk2 Port (1.2), OM-5 Mark II (1.1)*
- Translates camera menus (and help text where available) into Korean.
- Stock OM-1 also allows adjusting font, size, weight, and letter spacing. OM-5 Mk2 Port lets you choose which slot (Japanese, Traditional Chinese, or Simplified Chinese) to replace.

### Electronic Shutter Sound (4 profiles: TruePic X)
*OM-1 (1.9), OM-1 Mk2 Port (1.9), OM-1 Mark II (1.3), OM-3 (1.1)*
- Adds 3 custom electronic shutter sound slots (`Off / 1 / 2 / 3`) and 6 volume steps (`0–5`: `0%`–`100%`) under Wrench Menu → `Shutter Sound` / `Shutter Volume`.
- Works in both AF and MF/PreMF modes (excluded in SH1 / ProCap SH1; does not change capture speed).

### Wi-Fi 5 GHz Hotspot (6 profiles)
*OM-1 (1.9), OM-1 Mk2 Port (1.9), OM-1 Mark II (1.3), OM-5 (1.2), E-M1X (2.4), E-M1 Mark III (1.6)*
- Switches standard camera AP mode to 5 GHz (channel 36) while keeping the camera's stock country code.

### Auto ISO Minimum Shutter Speed (6 profiles + E-P7)
*E-M5 (2.3), E-M5 Mark II (4.1), E-M10 (1.4), E-M10 Mark II (1.4), E-M10 Mark III (1.2), E-M10 Mark IV (1.1), plus E-P7 (1.1) inside E-P7 Controls*
- Adds P/A Auto ISO minimum shutter speed menu, saved setting, and exposure control to bodies that didn't come with it.

### Camera-Specific Features
- **OM-1 (`1.9`) — SH2 / ProCap SH2 Extra Rates**: Adds `12.5 / 16.7 / 25 / 50 fps` and allows non-50fps lenses to select `12.5` and `16.7 fps`.
- **E-M1X (`2.4`) — Auto ISO Limit 25600**: Raises the Auto ISO upper limit and internal AE clamps from ISO 6400 to ISO 25600.
- **E-P7 (`1.1`) — Controls, Exposure & Menu Pack**: Top Shortcut and body button remapping, arrow-pad customization (ISO/WB/AF/Drive default or per-direction), AF Set Home recall (with center-target fallback), M + Auto ISO exposure compensation (button + dial), dial direction settings, Auto ISO minimum shutter speed menu, and expanded Korean menu font (569 Hangul glyphs).

---

## Supported Cameras (26 Profiles)

| Camera | Base FW | Korean | Aperture Ring | IR R↔B Swap | Hybrid Shutter | Wi-Fi 5 GHz | Quasi LUT | Shutter Sound | Extra / Notes |
| :--- | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :--- |
| OM-1 | `1.9` | O | O | - | O | O | O | O | SH2 Extra Rates (`12.5/16.7/25/50 fps`) |
| OM-1 (Mk2 Port) | `1.9` *(Mk2 1.3)* | O | O | - | O | O | O | O | OM-1 Mk2 Port, 85-frame burst buffer (+160 MiB) |
| OM-1 Mark II | `1.3` | O | O | - | O | O | O | O | - |
| OM-3 | `1.1` | O | O | - | O | - | O | O | - |
| OM-5 | `1.2` | O | O | O | O | O | - | - | - |
| OM-5 (Mk2 Port) | `1.2` *(Mk2 1.1)* | O | O | O | - | - | - | - | OM-5 Mk2 New UI Port *(Exp.)* |
| OM-5 Mark II | `1.1` | O | O | O | O | - | - | - | - |
| E-M1X | `2.4` | - | O | O | O | O | - | - | Auto ISO Limit `25600` |
| E-M1 Mark III | `1.6` | - | O | O | O | O | - | - | - |
| E-M1 Mark II | `3.7` | - | O | O | - | - | - | - | - |
| E-M1 Mark I | `4.6` | - | O | O | - | - | - | - | - |
| E-M5 Mark III | `1.7` | - | O | O | - | - | - | - | - |
| E-M5 Mark II | `4.1` | - | O | O | - | - | - | - | Auto ISO Min Shutter |
| E-M5 | `2.3` | - | - | O | - | - | - | - | Auto ISO Min Shutter |
| E-M10 Mark IV | `1.1` | - | O | O | - | - | - | - | Auto ISO Min Shutter |
| E-M10 Mark III | `1.2` | - | O | O | - | - | - | - | Auto ISO Min Shutter |
| E-M10 Mark II | `1.4` | - | O | O | - | - | - | - | Auto ISO Min Shutter |
| E-M10 Mark I | `1.4` | - | O | O | - | - | - | - | Auto ISO Min Shutter |
| PEN-F | `3.1` | - | O | O | - | - | - | - | - |
| E-P7 | `1.1` | *(569 glyphs)* | O | O | O | - | - | - | E-P7 Controls Pack (Remap, AF Home, M+AutoISO EC, Min Shutter) |
| E-P5 | `1.8` | - | O | O | - | - | - | - | - |
| E-PL9 | `1.1` | - | O | O | - | - | - | - | - |
| E-PL8 | `1.1` | - | O | O | - | - | - | - | - |
| E-PL7 | `1.4` | - | O | O | - | - | - | - | - |
| E-PL6 | `1.4` | - | O | O | - | - | - | - | - |
| E-PL5 | `1.6` | - | O | O | - | - | - | - | - |

---

## How to use

1. Download `db firmware 0.4.5` from [Releases](../../releases):
   - Windows (x64): `db firmware 0.4.5.exe`
   - macOS (Apple Silicon, macOS 15.0+): `DBFirmware-macOS-AppleSilicon-0.4.5.zip` *(unsigned build — right-click → Open if Gatekeeper blocks it)*
2. Pick your camera profile and download/load the matching stock firmware. Save a backup of the stock file just in case.
3. Check the features you want and configure any optional editors (SD LUT / shutter sound / font).
4. Build the patched file and copy the `DCOLYMP/` folder to the root of a formatted SD card.
5. Update the camera with a full battery and do not power it off until the update finishes.
6. After testing on your camera, please submit your results through the tool's feedback window (`?`) or on [db-firmware-support.vercel.app](https://db-firmware-support.vercel.app/en).

## Links

- Compatibility & Release Notes: https://db-firmware-support.vercel.app/en
- Full Camera × Feature Table: https://db-firmware-support.vercel.app/en/overview
- `db_link` Android App: https://play.google.com/store/apps/details?id=com.dblink
