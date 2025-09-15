🛠️ Geeetech M1 Klipperization & Upgrade Project

Welcome to the build guide for transforming your humble Geeetech M1 into a lean, mean, Klipper-powered printing machine. This README outlines the upgrades, installation steps, and configuration notes for replicating or understanding this custom setup.

💡 Help me fund a 3D scanner so I can stop squeezing magic out of Polycam and a Razor phone.
ko-fi.com/0dysseusrex

🧰 Project Overview
This upgrade journey includes:
- Mainboard: BTT SKR Pico running Simple AF Klipper
- Controller: Raspberry Pi Zero 2W
- Power Supply: Internal 100W unit for compact, clean power delivery
- Custom Printhead Assembly:
- A1 Mini hotend for improved thermal performance
- Creality K1 extruder for smoother filament feed
- Microprobe sensor for reliable bed leveling
- Streaming Camera: Live monitoring via USB/CSI camera

🚀 Goals
- Boost speed and precision with Klipper firmware
- Modernize hardware while keeping costs low
- Enable wireless control and remote monitoring
- Achieve a clean internal layout with minimal external clutter

📦 Hardware List
| Component         | Model/Description         |
|------------------|---------------------------|
| Mainboard        | BTT SKR Pico              |
| Firmware         | Simple AF Klipper         |
| Controller       | Raspberry Pi Zero 2W      |
| Power Supply     | Internal 100W             |
| Hotend           | A1 Mini                   |
| Extruder         | Creality K1               |
| Bed Leveling     | Microprobe sensor         |
| Streaming Camera | USB/CSI compatible        |

🛠️ Installation Highlights
- Mainboard & Pi Setup
- Flash Klipper on the Pi Zero 2W using the Simple AF config
- Connect Pi to SKR Pico via USB
- Wire power and comms with care—use ferrules for safety and reliability
- Printhead Upgrade
- Swap stock hotend for A1 Mini
- Mount Creality K1 extruder and calibrate steps/mm in Klipper
- Install Microprobe and configure mesh leveling
- Power Integration
- Mount internal 100W PSU
- Ensure tidy cable management and proper airflow
- Camera Streaming
- Connect camera to Pi
- Configure MJPG-streamer or Moonraker for live feed access

🧠 Configuration Notes
- Use a printer.cfg tailored for SKR Pico + Microprobe
- Run PID tuning for hotend and bed
- Enable Input Shaping with accelerometer (optional but recommended)
- View camera stream via OctoDash, Fluidd, or Mainsail

🎨 Bonus Mods & Ideas
- LED lighting for enclosure ambiance
- Custom magnetic toolhead plate for quick swaps
- Sound-dampened enclosure for stealthy prints

<details><summary>📊 <strong>Project Completion Tracker</strong> — Click to expand</summary>
🔧 Printhead Re-design — 90%
█████████░
✅ Completed:
- A1 Mini Hotend
- Probe mounting location
- Microprobe mount
- Fan mounts
- Cable guides
📝 To Do:
- Redesign bottom screw mounts to point forwards

🏗️ Gantry Re-design — 100%
██████████
- Universal screw holes for custom MCU mounts ✅

🧩 MCU / Breakout Board Mount — 100%
██████████
- Fully installed ✅

⚙️ Electronics Mount — 0%
░░░░░░░░░░
- SKR Pico Mount ❌
- Pi Zero 2W Mount ❌
- Breakout Board Mount ❌
- Knomi Mount ❌
- E-stop Mount ❌

🔌 PSU Mount — 0%
░░░░░░░░░░
- Not yet started ❌

💻 Software — 0%
░░░░░░░░░░
- Clone Simple AF Repo ❌
- Custom printer.cfg ❌
- Automate setup via Simple AF ❌
- Test functionality ❌

🧪 Testing — 0%
░░░░░░░░░░
- Initial printer function tests ❌
- PID tuning ❌
- Input shaper graphs ❌
- First test prints ❌
- Speed tests ❌
- Dial-in settings ❌

🎬 Video Editing — 0%
░░░░░░░░░░
- Not yet started ❌

🌐 Publish & Go Live — 0%
░░░░░░░░░░
- Awaiting completion ❌
</details>

✨ Acknowledgments
Big thanks to the Klipper community, BTT engineers, and all the DIYers who turn retro machines into futuristic wonders.

🧠 Print smarter, not harder.
🤖 Yes, this README was AI-generated—but only as a launchpad. BOM coming soon.


