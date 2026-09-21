<div align="center">

# VIGILIS AllSky

**Automated Raspberry Pi AllSky imaging, environmental monitoring and night-sky processing.**

[![Release](https://img.shields.io/badge/release-1.0.0--beta9.9-5f9f8f?style=for-the-badge)](https://github.com/1alex-vag/Vigilis-Allsky/releases/tag/v1.0.0-beta9.9)
[![Platform](https://img.shields.io/badge/platform-Raspberry%20Pi-a22846?style=for-the-badge&logo=raspberrypi&logoColor=white)](https://www.raspberrypi.com/)
[![Python](https://img.shields.io/badge/Python-3-3776ab?style=for-the-badge&logo=python&logoColor=white)](https://www.python.org/)

**Current public test release:** [VIGILIS AllSky 1.0.0-beta9.9 — Final Release Candidate](https://github.com/1alex-vag/Vigilis-Allsky/releases/tag/v1.0.0-beta9.9)

</div>

![VIGILIS AllSky startrail](Vigilis-hero.png)

VIGILIS AllSky is a self-hosted AllSky platform for Raspberry Pi. It controls the camera, adapts exposure and gain across day, twilight and night, archives the original frames, creates night-sky products automatically, monitors environmental hardware and provides a responsive web interface for operation, diagnostics and updates.

> [!IMPORTANT]
> **beta9.9 is the final pre-V1.0 release candidate.** It is intended for real Raspberry Pi and overnight validation before promotion to V1.0. See the [beta9.9 release](https://github.com/1alex-vag/Vigilis-Allsky/releases/tag/v1.0.0-beta9.9) and `RELEASE_NOTES_BETA9_9_ALLSKY.md` for the latest audit results and upgrade notes.

## Highlights

- **CSI and ZWO ASI camera paths** with VIGILIS-controlled exposure and gain
- **Day → Transition → Night** capture with continuous, non-blocking twilight regulation
- **Automatic night products:** Timelapse, Keogram, Clean Startrail, Full Startrail, Startrail Video and Starogram
- **Advanced Processing** with sample-point glare rejection, masking circle and hard/soft edge blending
- **Day and Night archives** with reprocessing directly from the Gallery
- **Lens-cover automation** with stepper motor and Hall-sensor feedback
- **Dew-point-based heater control** with indoor/outdoor environmental monitoring
- **SHT31 + SAMD21 + AS3935 integration** for outdoor climate and lightning data
- **Telegram integration** for station messages and image delivery
- **SSD storage support** and archive management
- **Built-in Diagnostics** for environment history, lightning, focus and hardware status
- **OTA updates from GitHub** with Beta/Stable channels and package verification
- **Responsive Liquid Glass interface** designed for phone, tablet and desktop use

## Interface

### Home

Live station state, current AllSky image, sun altitude, capture timing, exposure/gain and environmental telemetry in one view.

<p align="center">
  <img src="docs/images/ui-home.jpeg" alt="VIGILIS AllSky Home" width="360">
</p>

### Gallery

Browse Day and Night archives, inspect source images and create or reprocess generated products.

![VIGILIS AllSky Gallery](docs/images/ui-gallery.jpeg)

### Diagnostics

Rolling environmental history, outdoor telemetry, lightning diagnostics, Focus Mode and hardware diagnostics.

![VIGILIS AllSky Diagnostics](docs/images/ui-diagnostics.jpeg)

### Settings

Compact grouped configuration for Camera & Capture, Processing, Archive, Overlay, Lens Cover, Environment, Telegram and system updates.

![VIGILIS AllSky Settings](docs/images/ui-settings.jpeg)

## Processing products

| Product | Description |
| --- | --- |
| **Timelapse** | Night or day image sequence rendered as video |
| **Keogram** | Time-compressed sky strip generated from the configured sky position |
| **Clean Startrail** | Startrail stack with frame rejection for transient glare and unusable frames |
| **Full Startrail** | Full-frame startrail accumulation |
| **Clean Startrail Video** | Progressive startrail build-up as a video |
| **Hybrid Startrail** | Startrail accumulation inside the configured mask while the normal video continues outside it |
| **Starogram** | Combined hybrid Startrail video, static time axis and animated Keogram |

Advanced Processing can use multiple sample regions to detect short brightness spikes such as passing headlights without deleting or modifying the original archive frames.

## Camera and capture

VIGILIS supports the Raspberry Pi CSI camera path and ZWO ASI cameras. The capture controller manages:

- automatic exposure and gain
- maximum exposure and gain limits
- Day / Transition / Night states
- configurable solar-altitude thresholds
- day and transition capture intervals
- night delay
- focus mode
- persistent exposure state for safer restart behavior
- automatic recovery from strong underexposure or clipping

Normal Transition and Night capture uses continuous feedback; it does not pause for the old multi-step twilight calibration sequence.

## Optional hardware

VIGILIS is designed so optional hardware can be enabled only when installed.

| Hardware | Integration |
| --- | --- |
| Raspberry Pi CSI camera | Native Picamera2 / libcamera path |
| ZWO ASI camera | USB camera path through `zwoasi` |
| Motorized lens cover | Stepper + open/closed Hall sensors |
| Lens heater | Automatic dew-point-based control |
| Indoor climate | SHT31 / configured local sensor path |
| Outdoor node | XIAO SAMD21 serial bridge |
| Outdoor climate | SHT31 through the outdoor node |
| Lightning | AS3935 through the outdoor node |
| External storage | USB SSD archive support |

Pin assignments and hardware options are configurable in VIGILIS and should be checked against your own station before connecting hardware.

## Installation

### Recommended: beta9.9 release

Download the current Raspberry Pi package from:

**[VIGILIS AllSky 1.0.0-beta9.9 — Final Release Candidate](https://github.com/1alex-vag/Vigilis-Allsky/releases/tag/v1.0.0-beta9.9)**

Extract the release ZIP on the Raspberry Pi, then run:

```bash
chmod +x install.sh
./install.sh
```

> [!NOTE]
> Run the installer as your normal Raspberry Pi user — **do not run `install.sh` with `sudo`**. The installer requests elevated privileges only for the system operations that require them.

The installer creates/updates the VIGILIS environment, installs system and Python dependencies, installs the systemd service and performs a local health check.

After installation, open:

```text
http://<RASPBERRY-PI-IP>:5000
```

### Updating an existing station

Open:

**Settings → System → Software Update**

Choose the **Beta** channel while testing beta9.9, press **Check for updates**, then **Install update** when the release is offered.

The OTA package filename must end in `-RaspberryPi.zip`, and VIGILIS validates the package structure and internal version before deployment.

## First setup

After the first installation:

1. Open **Settings → General** and configure location/time settings.
2. Open **Camera & Capture** and select/detect the camera.
3. Configure exposure/gain limits and Day/Night solar-altitude thresholds.
4. Enable only the hardware modules physically installed on the station.
5. Configure Processing products and resolutions.
6. Verify the camera in **Diagnostics → Focus Mode**.
7. Confirm a normal Day → Transition → Night cycle before leaving the station unattended.

## Storage and preservation

VIGILIS keeps captured source frames separate from generated processing products. Reprocessing does not intentionally modify the original archive images.

The installer preserves the standard persistent VIGILIS data, archive, logs, backups and user configuration locations during upgrades. If you use a custom archive directory inside the application tree, read the beta9.9 release notes before upgrading from older beta versions.

## Release status

### Current beta

**1.0.0-beta9.9 — Final Release Candidate**  
[Release page →](https://github.com/1alex-vag/Vigilis-Allsky/releases/tag/v1.0.0-beta9.9)

beta9.9 completed the pre-V1.0 audit and automated regression suite and is intended for controlled Raspberry Pi / overnight testing before V1.0.

Planned final validation includes:

- real Day → Transition → Night → Transition → Day operation
- restart behavior during different capture states
- CSI and ZWO hardware checks
- lens cover / heater / environmental hardware checks
- real OTA update and rollback validation
- Safari/iPhone UI verification
- multi-night storage and resource monitoring

## Security note

VIGILIS is currently intended for use on a **trusted local network**. Management endpoints are not designed as a hardened public Internet interface. Do not expose the station directly to the Internet without an appropriate authenticated reverse proxy or equivalent network protection.

## Project structure

```text
VIGILIS-AllSky/
├── install.sh
├── run.py
├── config.example.yaml
├── requirements.txt
├── systemd/
├── tools/
└── vigilis/
    ├── app.py
    ├── core/
    ├── modules/
    ├── static/
    ├── templates/
    └── tuning/
```

## Development and testing

The beta9.9 release includes regression/self-test tooling for:

- exposure and continuous exposure regulation
- Day/Transition handover
- Advanced Processing
- Starogram
- updater/package validation
- UI behavior and responsive layouts
- configuration, storage and hardware failure paths

Automated tests complement — but do not replace — real camera, GPIO, storage and overnight sky testing on the Raspberry Pi.

## Credits

**VIGILIS AllSky** is designed and developed by **Alexander Gschöpf**.

Built for a real AllSky station, with an emphasis on reliability, image quality, automated processing and a clean local-first interface.

---

<div align="center">

**[Download beta9.9](https://github.com/1alex-vag/Vigilis-Allsky/releases/tag/v1.0.0-beta9.9)** · **[All releases](https://github.com/1alex-vag/Vigilis-Allsky/releases)**

</div>
