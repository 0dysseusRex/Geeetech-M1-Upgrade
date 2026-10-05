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
- Custom `printer.cfg` ❌  
- Finish host setup with `fly-start` ❌  
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
  - After SSH login, run `fly-start`. Printer and probe choices follow [Simple-AF for RPi](https://pellcorp.github.io/creality-wiki/rpi/); this repo does not ship a Geeetech M1 `printer.cfg`
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

- Use a `printer.cfg` tailored for SKR Pico + Microprobe. The Fly Lite is the host; it does not replace the SKR Pico pinout
- Run PID tuning for hotend and bed  
- Enable Input Shaping with accelerometer (optional but recommended)  
- View the camera stream in Fluidd or Mainsail on the Fly Lite

---

## ✨ Acknowledgments

Big thanks to the Klipper community, BTT engineers, Pellcorp ([Simple AF](https://pellcorp.github.io/creality-wiki/)), Mellow for the [Fly-Pi-lite2.1](https://mellow.klipper.cn/en/docs/ProductDoc/SBC/fly-lite/lite2.1/), the [Fly-bian](https://github.com/0dysseusRex/fly-bian) image, and all the DIYers who turn retro machines into futuristic wonders.

---

> 🧠 Print smarter, not harder.  
> 🤖 Yes, this README was AI-generated—but only as a launchpad. BOM coming soon.