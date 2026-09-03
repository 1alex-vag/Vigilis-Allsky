VIGILIS AllSky

Professional Raspberry Pi all-sky camera system for automated sky monitoring, image capture and processing.

Current release: VIGILIS AllSky 1.0.0 Beta 5.4
This project is currently in beta. Bugs and breaking changes may still occur.

Features

* Automated day and night image capture
* Automatic exposure and gain control
* Timelapse generation
* Star-trail images and videos
* Keogram generation
* Live camera preview and focus mode
* Gallery with image and sequence management
* Automatic lens-cover control with Hall sensors
* Dew-heater control
* Temperature and humidity monitoring
* Responsive web interface
* Support for Raspberry Pi CSI cameras

Requirements

* Raspberry Pi 4 or newer
* Raspberry Pi OS Bookworm 64-bit
* Compatible CSI camera
* Internet connection during installation
* Optional lens-cover motor, Hall sensors, heater and environmental sensors

Installation

Download the release ZIP file and copy it to the home directory of your Raspberry Pi.

Then run:

sudo systemctl stop vigilis
cd ~
unzip VIGILIS-AllSky-1.0.0-beta5.4-RaspberryPi.zip
cd VIGILIS-AllSky-1.0.0-beta5.4-RaspberryPi
chmod +x install.sh
./install.sh

Follow the instructions shown by the installer. After installation, open the VIGILIS AllSky web interface in your browser.

Updates

New versions and release notes are published in the GitHub Releases section.

Important

Back up your configuration and captured images before installing an update.

VIGILIS AllSky is currently beta software and is provided without warranty.

Author

Developed by Alexander Gschöpf

Instagram: @ag_astrophotography

License

This project is licensed under the MIT License.