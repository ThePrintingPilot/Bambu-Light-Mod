# Bambu Light Mod

**A smart lighting addon that keeps your secondary LED lights in perfect sync with your Bambu Lab printer's chamber light — locally, instantly, no cloud required..**

Built by [The Printing Pilot](https://theprintingpilot.com) · [YouTube](https://www.youtube.com/@ThePrintingPilot) · [GitHub](https://github.com/ThePrintingPilot/Bambu-Light-Mod)

---

## What Is It?

Bambu Light Mod is a smart lighting addon for Bambu Lab 3D printers. It adds a secondary LED light strip to your printer enclosure that automatically syncs with the printer's built-in chamber light — when the chamber light turns on, your addon lights turn on too, and when it turns off, they follow.
The system runs entirely on your local network with no cloud connection required. A small ESP32-C3 module sits inside your enclosure and connects directly to your printer's local MQTT broker — the same local API Bambu Lab exposes for developer use. It listens for chamber light state changes in real time and drives a custom PCB that controls the additional LED lights.
There is no polling, no delays, and no dependency on Bambu Cloud or any external service. Everything happens on your local network between the ESP32 and the printer, making it fast, reliable, and private.
The whole system is built around a custom PCB that draws power directly from the printer's AMS connector — no separate power supply, no extra cables. Just plug it in and it works.


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

Tested on the **P2S**. Should work on any Bambu Lab printer with Developer Mode enabled.

| Series | Models |
|---|---|
| X1 | X1, X1 Carbon, X1E |
| P1 | P1P, P1S, P2S |
| A1 | A1, A1 Mini |
| H2 | H2D, H2D Pro |

To enable Developer Mode on your printer: **Settings → Network → Developer Mode → Enable**


---

Made with ❤️ by [The Printing Pilot](https://theprintingpilot.com)
