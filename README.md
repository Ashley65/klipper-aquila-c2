
# Voxelab Aquila C2 Klipper Configuration

This repository contains the Klipper configuration files for my Voxelab Aquila C2. It serves as a backup and a reference for running Klipper on an upgraded Creality V4/F407 board.

## 🛠️ Hardware Specifications

* **Printer Model:** Voxelab Aquila C2
* **Mainboard:** Creality V4 / F407
* **MCU:** STM32F407 *(Note: This configuration is NOT for the H32, N32, or GD32 boards)*
* **Build Volume:** 220mm (X) x 220mm (Y) x 250mm (Z)
* **Z-Axis:** Belted Z-Axis Mod 
  * *Configured with a 40mm rotation distance and an 80:16 gear ratio (yielding 8mm per rotation).*
* **Thermistors:** EPCOS 100K B57560G104F (Both Hotend and Heated Bed)

## Kinematics & Performance Limits

* **Max Velocity:** 500 mm/s
* **Max Acceleration:** 3000 mm/s²
* **Square Corner Velocity:** 5.0
* **Firmware Retraction:** Enabled (0.5mm @ 35mm/s)

## Key Features Enabled

* **[KAMP](https://github.com/kyleisah/Klipper-Adaptive-Meshing-Purging):** Adaptive bed meshing and purging. Only probes the area of the bed being printed on for faster start times.
* **Exclude Object:** Allows cancelling individual failed parts on the build plate without stopping the entire multi-part print.
* **GCode Arcs:** Enabled (`resolution: 0.1`) to process standard G2/G3 arc commands, allowing for smoother curves and reduced G-code file sizes.
* **Screws Tilt Adjust:** Automated calculation for manual bed tramming. Moves the nozzle directly over the four bed screws and provides exact turn adjustments (CW-M3).
* **Automated Backups:** Integrated script for automatically pushing config changes to this GitHub repository.

## Repository Structure

* `printer.cfg` - The main Klipper configuration file handling pin mappings and core limits.
* `macros.cfg` - Custom print start, print end, and utility macros.
* `KAMP_Settings.cfg` - Parameters governing adaptive meshing behavior.
* `mainsail.cfg` - Variables and settings required by the Mainsail web interface.
* `timelapse.cfg` - Moonraker timelapse component settings.
* `config_backup.cfg` - Macro to trigger the automated GitHub push script.

## Current Status & To-Do

- [x] Tune PID for Hotend and Bed
- [x] Configure Firmware Retraction
- [x] Calibrate X, Y, and Z endstops
- [ ] Install and configure BLTouch *(Currently disabled/commented out in `printer.cfg`)*

---

### ⚠️ Disclaimer
*This configuration uses exact USB serial IDs (`/dev/serial/by-id/usb-1a86_USB_Serial-if00-port0`) and PID tuning values specific to my physical hardware environment. If you are copying this to your own Voxelab Aquila C2, you must update the MCU serial path and run your own PID tuning for safety.*
