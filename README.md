# VIGILIS AllSky

<p align="center">
  <strong>Professional Raspberry Pi all-sky camera system</strong><br>
  Automated sky monitoring, image capture and processing.
</p>

<p align="center">
  <img src="https://img.shields.io/badge/License-MIT-green.svg" alt="MIT License">
  <img src="https://img.shields.io/badge/Python-3.11-blue" alt="Python 3.11">
  <img src="https://img.shields.io/badge/Raspberry%20Pi-Supported-red" alt="Raspberry Pi">
  <a href="https://github.com/1alex-vag/Vigilis-AllSky/releases/latest">
  <img src="https://img.shields.io/github/v/release/1alex-vag/Vigilis-AllSky?include_prereleases&label=Release&color=orange" alt="Latest Release">
</a>
  <img src="https://img.shields.io/badge/Open%20Source-Yes-success" alt="Open Source">
</p>

## ✨ Features

- 🌌 Automated all-sky image capture
- ☀️ Automatic day and night operation
- 📷 Automatic exposure and gain control
- 🎞️ Timelapse generation
- 🌠 Star-trail images and videos
- 📊 Automatic keogram generation
- 🔭 Live camera preview and focus mode
- 🖼️ Integrated gallery and sequence management
- 🛡️ Automatic lens-cover control
- 🔥 Intelligent dew-heater control
- 🌡️ Temperature and humidity monitoring
- 🌐 Responsive web interface
- 🔄 Automatic update system
- 💾 Configurable image storage

## 📥 Download

[![Latest Release](https://img.shields.io/github/v/release/1alex-vag/Vigilis-AllSky?include_prereleases&label=Release&color=orange)](https://github.com/1alex-vag/Vigilis-AllSky/releases/latest)

➡️ [Download latest VIGILIS AllSky release](https://github.com/1alex-vag/Vigilis-AllSky/releases/latest)

> VIGILIS AllSky is currently beta software. Bugs and breaking changes may still occur.

## 🛠️ Installation

1. Install Raspberry Pi OS Bookworm (64-bit)
2. Download the latest VIGILIS AllSky release
3. Copy the ZIP file to the home directory
4. Open the terminal and run:

```bash
sudo systemctl stop vigilis
cd ~
unzip VIGILIS-AllSky-1.0.0-beta5.4-RaspberryPi.zip
cd VIGILIS-AllSky-1.0.0-beta5.4-RaspberryPi
chmod +x install.sh
./install.sh
```

5. Follow the instructions shown by the installer
6. Open the VIGILIS AllSky web interface
7. Enjoy the sky 🙂 

## 🔌 Hardware & GPIO Wiring

Complete GPIO assignments, wiring instructions and safety information:

➡️ [VIGILIS AllSky Hardware Guide](./HARDWARE.md)

## 🔧 Supported Hardware

### Raspberry Pi

- Raspberry Pi 4 with 4 GB RAM recommended
- Raspberry Pi 5 support planned and under evaluation
- Raspberry Pi OS Bookworm 64-bit

### Cameras

- Raspberry Pi HQ Camera / Sony IMX477
- Compatible Raspberry Pi CSI cameras
- ZWO ASI cameras

### Optional Hardware

- Motorized lens cover
- Hall-effect sensors
- Dew heater
- Temperature and humidity sensors
- External SSD or HDD

## 🌌 About VIGILIS AllSky

VIGILIS AllSky is an open-source all-sky camera platform designed for reliable automated sky monitoring.

It captures and manages day and night images, automatically creates timelapses, star trails, star-trail videos and keograms, and provides complete control through a modern responsive web interface.

The project focuses on reliability, image quality, easy operation and expandability.

## ⚠️ Important

Back up your configuration and captured images before installing an update.

This software is provided without warranty. Hardware connected to GPIO pins should always be checked carefully before operation.

## 👨‍💻 Author

Developed by **Alexander Gschöpf**

📷 Instagram: [@ag_astrophotography](https://www.instagram.com/ag_astrophotography/)

## 📄 License

This project is licensed under the [MIT License](LICENSE).
