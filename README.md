
# 🛠️ Geeetech M1 Klipperization & Upgrade Project

Welcome to the build guide for transforming your humble Geeetech M1 into a lean, mean, Klipper-powered printing machine. This README outlines the upgrades, installation steps, and configuration notes for replicating or understanding this custom setup.

## 🧰 Overview

This project includes the following enhancements:
- **Mainboard Upgrade**: BTT SKR Pico running *Simple AF Klipper*
- **Controller**: Raspberry Pi Zero 2W
- **Power Supply**: Internal 100W unit for cleaner, more compact power delivery
- **Custom Printhead Assembly**:
  - A1 Mini hotend for improved thermal performance
  - Creality K1 Extruder for smoother filament feed
  - Microprobe sensor for reliable bed leveling
- **Streaming Camera**: Live monitoring via connected camera

## 🚀 Goals

- Increase printing speed and precision using Klipper firmware
- Modernize printer hardware while maintaining affordability
- Enable wireless control and remote monitoring
- Create a clean internal layout with minimal external clutter

## 📦 Hardware List

| Component             | Model/Description                    |
|----------------------|--------------------------------------|
| Mainboard            | BTT SKR Pico                         |
| Firmware             | Simple AF Klipper                    |
| Controller           | Raspberry Pi Zero 2W                 |
| Power Supply         | Internal 100W                        |
| Hotend               | A1 Mini                              |
| Extruder             | Creality K1                          |
| Bed Leveling         | Microprobe sensor                    |
| Streaming Camera     | USB/CSI compatible                   |

## 🛠️ Installation Highlights

1. **Mainboard & Pi Setup**
   - Flash Klipper on the Pi Zero 2W using the Simple AF config.
   - Connect Pi via USB to SKR Pico.
   - Wire up power and communication lines carefully; use ferrules!

2. **Printhead Upgrade**
   - Replace stock hotend with A1 Mini.
   - Mount Creality K1 extruder and calibrate steps/mm in Klipper.
   - Install Microprobe and configure bed leveling mesh.

3. **Power Integration**
   - Mount and wire internal 100W PSU.
   - Ensure safe cable management and cooling clearance.

4. **Camera Streaming**
   - Connect camera to Pi.
   - Configure MJPG-streamer or Moonraker for live feed.

## 🧠 Configuration Notes

- Use `printer.cfg` tailored for SKR Pico & Microprobe.
- PID tune hotend and bed after install.
- Enable Input Shaping via accelerometer (optional).
- Camera stream viewable via OctoDash, Fluidd, or Mainsail.

## 🎨 Bonus Mods & Ideas

- LED lighting for the enclosure
- Custom magnetic toolhead plate
- Enclosure with sound dampening foam

## ✨ Acknowledgments

Thanks to the open-source Klipper community, BTT engineers, and DIYers who turn retro machines into futuristic wonders.

---

Print smarter, not harder. 💡

Yes I generated this readme with AI. Don't worry I'm just gonna use it as a guide. BOM to follow.