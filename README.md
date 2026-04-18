<div align="center">
  <img src="https://raw.githubusercontent.com/ThePrintingPilot/Bambu-Light-Mod/refs/heads/main/images/TPP-Mono.png" width="160" />
  <h1>Bambu Light Mod</h1>
  <p><strong>A smart lighting addon that keeps your secondary LED lights in perfect sync with your Bambu Lab printer's chamber light — locally, instantly, no cloud required.</strong></p>
  <p>
    <a href="https://theprintingpilot.com"><img src="https://img.shields.io/badge/Website-ThePrintingPilot-00e5a0?logo=googlechrome&logoColor=white" alt="Website" /></a> 
    <a href="https://www.youtube.com/@ThePrintingPilot"><img src="https://img.shields.io/badge/YouTube-ThePrintingPilot-FF0000?logo=youtube&logoColor=white" alt="YouTube" /></a> 
    <a href="https://github.com/ThePrintingPilot"><img src="https://img.shields.io/badge/GitHub-ThePrintingPilot-181717?logo=github&logoColor=white" alt="GitHub" /></a>
  </p>
  <p>
    <img src="https://img.shields.io/endpoint?url=https://bambu-light-mod.tomernassi.workers.dev/badge&style=flat-square" alt="Active Devices" />
  </p>
</div>

---

## What Is It? 



Bambu Light Mod is a smart lighting addon for Bambu Lab 3D printers. It adds a secondary LED strip inside your enclosure that automatically syncs with the printer's chamber light in real time — when the chamber light turns on, your addon lights follow, and when it turns off, they do too.

Everything runs locally on your network. The ESP32 connects directly to the printer's local MQTT broker — no cloud, no polling, no delays. State changes are instant and nothing ever leaves your network.



---

## Get One


<img src="https://raw.githubusercontent.com/ThePrintingPilot/Bambu-Light-Mod/refs/heads/main/images/TPP-Mono.png" width="85" align="right" />

Bambu Light Mod is fully open source — all the firmware, PCB files, and enclosure designs are available here for you to build yourself.

That said, because we manufacture these in volume, **buying directly from our store is almost always cheaper than sourcing the parts and assembling it yourself** — and you get a fully assembled, tested board ready to plug in.

More importantly, every purchase directly supports The Printing Pilot. It allows us to keep improving this product, push firmware updates, and continue designing new tools for the Bambu Lab community.

> ### 🛒 [Buy from The Printing Pilot Store](https://theprintingpilot.com)
> Fully assembled · Tested · Ready to plug in


---

## Hardware


Bambu Light Mod is built around a fully custom hardware stack — everything from the PCB to the enclosure was designed specifically for this project.

### Custom PCB

The heart of the project is a custom-designed PCB built around the ESP32-C3. It handles the WiFi connection to the printer, drives the LED lights, and manages all the onboard electronics. There are no off-the-shelf modules or loose wiring — everything is integrated onto a single compact board.

<img src="https://raw.githubusercontent.com/ThePrintingPilot/Bambu-Light-Mod/refs/heads/main/images/PCB.png" width="430" height="260" />

### Power via AMS Connector

The PCB draws power directly from the printer's AMS connector. No external power supply, no USB cable, no extra wiring. Plug it into the AMS port and the board powers up immediately.

<img src="https://raw.githubusercontent.com/ThePrintingPilot/Bambu-Light-Mod/refs/heads/main/images/3.jpg" width="430" height="250" />

### Custom 3D Printed Enclosure

The electronics sit inside a custom 3D printed enclosure with embedded magnets that attach directly to the outside of the printer. The enclosure was designed with the Bambu Light Mod logo embossed on the front and is printed directly on the Bambu Lab printer it controls.

<img src="https://raw.githubusercontent.com/ThePrintingPilot/Bambu-Light-Mod/refs/heads/main/images/1.jpg" width="430" height="250" />

### Physical Toggle Switch

A mechanical keyboard switch is mounted on the enclosure for offline manual control. Press it at any time to toggle the lights on or off independently of the printer — useful when you want to control the lights without opening the web interface or when the printer is idle.

<img src="https://raw.githubusercontent.com/ThePrintingPilot/Bambu-Light-Mod/refs/heads/main/images/2.jpg" width="430" height="250" />

---

## Getting Started

1. Flash the firmware to your ESP32-C3
2. Connect to the **`BambuLightMod-Setup`** WiFi hotspot from your phone or laptop
3. Open **`http://192.168.4.1`** and fill in your WiFi and printer details
4. Hit **Save & Connect** — the ESP joins your network and starts syncing within seconds

> The printer serial number is detected automatically — just enter the IP and access code.

---

## Web Interfaces


The ESP hosts three pages you can access from any browser on your network. 


---

### `http://ESP_IP` — Config

<img src="https://raw.githubusercontent.com/ThePrintingPilot/Bambu-Light-Mod/refs/heads/main/images/ui_config.png" width="400" height="650" />

The main setup page. Enter your WiFi credentials, printer IP address, and local access code. The serial number is auto-detected from the printer — no need to look it up manually.

The two status indicators at the bottom show the current state of the printer's chamber light and the ESP's GPIO output in real time.

If a newer firmware version is available on GitHub, the version badge in the top right turns red and links directly to the release page.

---

### `http://ESP_IP/webserial` — Live Logs

<img src="https://raw.githubusercontent.com/ThePrintingPilot/Bambu-Light-Mod/refs/heads/main/images/ui_webserial.png" width="400" height="550" />

A live log viewer — no USB cable or Arduino IDE needed. See exactly what the ESP is doing in real time, colour coded by module. Useful for debugging connection issues or just confirming everything is working.

---

### `http://ESP_IP/ota` — Firmware Update

<img src="https://raw.githubusercontent.com/ThePrintingPilot/Bambu-Light-Mod/refs/heads/main/images/ui_ota.png" width="400" height="650" />

Update the firmware wirelessly without connecting a USB cable. Download the latest `.bin` from the [releases page](https://github.com/ThePrintingPilot/Bambu-Light-Mod/releases), select it on this page, and hit **Flash Firmware**. The ESP updates and reboots automatically.

---

## Supported Printers


Tested on the **P2S**. Software should work on any Bambu Lab printer with Developer Mode enabled, but for now the PCB comes with a 6 pin AMS/AMS Pro connector.

**For AMS Lite Users**
For now, the PCB does not come with the 4 pin AMS Lite connector. The board will still work with external power. A future update will add a PCB variant with the 4 pin AMS Lite connector.

| Series | Models |
|---|---|
| X1 | X1, X1 Carbon, X1E |
| P1 | P1P, P1S, P2S |
| A1 | A1, A1 Mini |
| H2 | H2D, H2D Pro |

To enable Developer Mode on your printer: **Settings → Network → Developer Mode → Enable**

---

<div align="center">
  <img src="https://raw.githubusercontent.com/ThePrintingPilot/Bambu-Light-Mod/refs/heads/main/images/TPP-Mono.png" width="80" />
  <br>
  Made with ❤️ by <a href="https://theprintingpilot.com">The Printing Pilot</a>
</div>
