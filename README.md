# 🛠️ Geeetech M1 Klipperization & Upgrade Project

Welcome to the build guide for transforming your humble Geeetech M1 into a lean, mean, Klipper-powered printing machine. This README outlines the upgrades, installation steps, and configuration notes for the project.

> 💡 Help me fund a 3D scanner so I can stop squeezing magic out of Polycam and a Razor phone.  
> [![Support Me on Ko-fi](https://img.shields.io/badge/Support%20Me%20on-Ko--fi-ff5f5f?logo=ko-fi&logoColor=white&style=flat-square)](https://ko-fi.com/0dysseusrex)

---

<details>
<summary>📊 <strong>Project Completion Tracker</strong> — 40% Overall (Weighted by Major Milestones) — Click to expand</summary>

> **Note:** Project completion is calculated by assigning weights to major milestones as follows:
> - Printhead Re-design: 30%
> - Gantry Re-design: 30%
> - Electronics Mount: 20%
> - Software: 20%
> Weighted progress is shown below. All other tasks are tracked for transparency but do not affect the overall percentage.

### 🔧 Printhead Re-design — 90% (27% of total)
`█████████░`  
**✅ Completed:**  
- A1 Mini Hotend ✔️  
- Probe mounting location ✔️  
- Microprobe mount ✔️  
- Fan mounts ✔️  
- Cable guides ✔️  

**📝 To Do:**  
- Redesign bottom screw mounts to point forwards ❌  

---

### 🏗️ Gantry Re-design — 100% (30% of total)
`██████████`  
- Universal screw holes for custom MCU mounts ✔️  

---

### ⚙️ Electronics Mount — 60% (12% of total)
`██████░░░░`  
**✅ Completed:**  
- SKR Pico Mount ✔️  
**📝 To Do:**  
- Fly Lite 2.1 mount ❌  
- Knomi Mount ❌  
- E-stop Mount ❌  

The finished `STL Files/Electronics Mount/Pi Mount.stl` fits the previous Raspberry Pi Zero 2W host. It is not a verified Mellow Fly Lite 2.1 mount, so that STL is unchanged. The 60% figure above still counts that Pi mount.  

---

### 💻 Software — 0% (0% of total)
`░░░░░░░░░░`  
- Flash the Fly-bian 1.0 Simple-AF image on the Fly Lite 2.1 ❌  
- Draft `printer.cfg` written, not tested on the machine ❌  
- Run the Simple-AF install command in the installation section ❌  
- Test functionality ❌  

---

### 🔌 PSU Mount — 0%
`░░░░░░░░░░`  
- Not yet started ❌  

---

### 🧪 Testing — 0%
`░░░░░░░░░░`  
- Initial printer function tests ❌  
- PID tuning ❌  
- Input shaper graphs ❌  
- First test prints ❌  
- Speed tests ❌  
- Dial-in settings ❌  

---

### 🎬 Video Editing — 0%
`░░░░░░░░░░`  
- Not yet started ❌  

---

### 🌐 Publish & Go Live — 0%
`░░░░░░░░░░`  
- Awaiting completion ❌  

</details>

---

## 🧰 Project Overview

This upgrade journey includes:

- **Mainboard**: BTT SKR Pico (Klipper MCU)
- **Controller**: [Mellow Fly-Pi-lite2.1](https://mellow.klipper.cn/en/docs/ProductDoc/SBC/fly-lite/lite2.1/) (Fly Lite 2.1), the Klipper host
- **Host image**: [Fly-bian 1.0 Simple-AF](https://github.com/0dysseusRex/fly-bian/releases/tag/v1.0) — `Fly-bian-1.0_Fly-Lite-2.1_Simple-AF-0d21afe.img.xz`. This is unofficial Armbian/Debian from [fly-bian](https://github.com/0dysseusRex/fly-bian), not Mellow FlyOS
- **Power Supply**: Internal 100W unit for compact, clean power delivery
- **Custom Printhead Assembly**:
  - A1 Mini hotend for improved thermal performance  
  - Creality K1 extruder for smoother filament feed  
  - Microprobe sensor for reliable bed leveling
- **Streaming Camera**: Live monitoring via a USB camera on the Fly Lite

---

## 📦 Hardware List

| Component         | Model/Description         |
|------------------|---------------------------|
| Mainboard        | BTT SKR Pico (Klipper MCU) |
| Controller       | Mellow Fly-Pi-lite2.1 (Fly Lite 2.1) |
| Host image       | Fly-bian 1.0 Simple-AF (`Fly-bian-1.0_Fly-Lite-2.1_Simple-AF-0d21afe.img.xz`) |
| Power Supply     | Internal 100W             |
| Hotend           | A1 Mini                   |
| Extruder         | Creality K1               |
| Bed Leveling     | Microprobe sensor         |
| Streaming Camera | USB (Fly Lite USB-A; no CSI connector on this host) |

---

## 🛠️ Installation Highlights

- **Controller (Fly Lite 2.1)**  
  - Flash only the Simple-AF card: [Fly-bian-1.0_Fly-Lite-2.1_Simple-AF-0d21afe.img.xz](https://github.com/0dysseusRex/fly-bian/releases/download/v1.0/Fly-bian-1.0_Fly-Lite-2.1_Simple-AF-0d21afe.img.xz) (SHA256 `3523ba04239469a7654b9d3b5ce8d07d9bf0d138a92ea3c833cd38d0f7c9e470`). Do not flash the Base or KIAUH image, FlyOS, or Raspberry Pi OS
  - Mellow specifies a MicroSD of 16–128 GB, speed class C10 or higher. The board has no eMMC
  - Before the first power-on, edit `fly-start.txt` on the `FLY-SETUP` volume (2.4 GHz Wi-Fi, locale, root password, sudo user). Steps: [Fly-bian Simple-AF how-to](https://github.com/0dysseusRex/fly-bian/blob/main/docs/howto-simpleaf.md)
  - Power the host from its own 5 V supply. Mellow says the Fly-Pi-lite2.1 must not be powered from the printer mainboard
  - Fit the IPEX antenna. Onboard Wi-Fi is 2.4 GHz only
  - After SSH login, `~/pellcorp` is already on the card. [Simple-AF for RPi](https://pellcorp.github.io/creality-wiki/rpi/) accepts a custom printer file as `--printer` (a GitHub file URL or a local path) and the probe as `--probe`. This machine is not one of the predefined printers, so there is no `--mount`. The draft [`printer.cfg`](printer.cfg) is that file. Run:

    ```
    ~/pellcorp/installer.sh --install --printer https://github.com/0dysseusRex/Geeetech-M1-Upgrade/blob/cursor/fly-lite-21-controller-0fcf/printer.cfg --probe microprobe
    ```

    The same line can be `INSTALL_CMD=` in `fly-start.txt` on the `FLY-SETUP` volume before the first boot. That is the hook in the [Fly-bian Simple-AF how-to](https://github.com/0dysseusRex/fly-bian/blob/main/docs/howto-simpleaf.md). The installer rewrites the GitHub URL to the raw file. `printer.cfg` is still a draft
  - The SKR Pico stays the MCU and still connects over USB. No Fly Lite GPIO pinout is added here
  - Wire power and comms with care—use ferrules for safety and reliability

- **Printhead Upgrade**  
  - Swap stock hotend for A1 Mini  
  - Mount Creality K1 extruder and calibrate steps/mm in Klipper  
  - Install Microprobe and configure mesh leveling

- **Power Integration**  
  - Mount internal 100W PSU  
  - Ensure tidy cable management and proper airflow

- **Camera Streaming**  
  - Connect a USB camera to a Fly Lite USB-A port. A CSI camera connector is not listed on the Fly-Pi-lite2.1
  - After Crowsnest is installed, `fly-crowsnest-add-cams` adds the camera. Fluidd and Mainsail are the web UIs on this image

---

## 🧠 Configuration Notes

- [`printer.cfg`](printer.cfg) is the Simple-AF `--printer` file for the SKR Pico MCU. Probe and mesh values are in its `-- microprobe.cfg` section so the installer keeps the SKR Pico probe pins. Simple-AF's own `START_PRINT` homes with `G28` on the mechanical endstops, then meshes. The Fly Lite 2.1 is the host. Its only documented Klipper GPIO is the KPPM pin, and this config does not load that pin. [`adxl345.cfg`](adxl345.cfg) is not part of that install; include it only while the USB accelerometer is plugged in
- Run PID tuning for hotend and bed  
- Enable Input Shaping with accelerometer (optional but recommended)  
- View the camera stream in Fluidd or Mainsail on the Fly Lite

---

## ✨ Acknowledgments

Big thanks to the Klipper community, BTT engineers, Pellcorp ([Simple AF](https://pellcorp.github.io/creality-wiki/)), Mellow for the [Fly-Pi-lite2.1](https://mellow.klipper.cn/en/docs/ProductDoc/SBC/fly-lite/lite2.1/), the [Fly-bian](https://github.com/0dysseusRex/fly-bian) image, and [adamrodgers/geeetech-m1s-klipper](https://github.com/adamrodgers/geeetech-m1s-klipper) for the stock M1S X/Y/Z motor steps, travel, homing direction, and cartesian kinematics in `printer.cfg`. That project keeps the original M1S board, so only those motion numbers were used here. And thanks to all the DIYers who turn retro machines into futuristic wonders.

## Credits

X/Y/Z steps, travel, and homing direction in `printer.cfg` come from the stock M1S Marlin dump published by [adamrodgers/geeetech-m1s-klipper](https://github.com/adamrodgers/geeetech-m1s-klipper). That project keeps the original M1S board. This one uses a Fly Lite 2.1 host and an SKR Pico, so only the motion numbers were taken, not their pin map.

---

> 🧠 Print smarter, not harder.  
> 🤖 Yes, this README was AI-generated—but only as a launchpad. BOM coming soon.
