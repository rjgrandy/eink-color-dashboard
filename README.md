# Seeed Studio reTerminal E1002 Dashboard (ESPHome)

A custom ESPHome configuration for the **Seeed Studio reTerminal E1002**, a 7.3-inch color e-Paper display powered by an ESP32-S3.

This project turns the E1002 into a smart, battery-efficient dashboard that cycles between Home Assistant views, photo slideshows, and system statistics. It uses a "render-and-download" approach where a local server generates PNG images that the device downloads and displays.

## 🌟 Features
* **Hardware Support:** Designed specifically for the [Seeed Studio reTerminal E1002](https://www.seeedstudio.com/reTerminal-E1002-p-6533.html).
* **7-Color Display:** Supports the 7.3" ACeP/Spectra 6 color palette.
* **Multi-View Interface:** Toggle between 3 distinct screens (Dashboard, Photos, System) using the top buttons.
* **Smart Triggers:**
    * **Auto-Refresh:** Updates every 5 minutes.
    * **Media Trigger:** Updates immediately when specific media players change tracks (e.g., `media_player.amped_mb`).
    * **Manual Trigger:** Updates immediately on button press.
* **Power Management:** Optimized for battery life with Deep Sleep and PSRAM buffering enabled.

## 🛠 Hardware Specs
* **Device:** Seeed Studio reTerminal E1002
* **Display:** 7.3-inch Color e-Paper (800x480 resolution)
* **MCU:** ESP32-S3 (8MB PSRAM, 32MB Flash)
* **Sensors:** Built-in Temperature & Humidity (SHT40)
* **Battery:** 2000mAh Li-ion

## ⚙️ Pin Configuration
*Since the E1002 is a pre-assembled device, these pins are internal mappings used by the firmware.*

| Component | ESP32-S3 Pin | Function |
| :--- | :--- | :--- |
| **Display** | GPIO 7 | SPI Clock (CLK) |
| | GPIO 9 | SPI MOSI (DIN) |
| | GPIO 10 | Chip Select (CS) |
| | GPIO 11 | Data/Command (DC) |
| | GPIO 12 | Reset (RST) |
| | GPIO 13 | Busy |
| **Controls** | GPIO 3 | Left Button (Green) |
| | GPIO 4 | Middle Button (White) |
| | GPIO 5 | Right Button (White) |
| **Status** | GPIO 6 | LED Indicator |

## 🧩 Software Dependencies

This project relies on an external "Renderer" to convert web pages into images. The ESP32 expects to download a PNG from a local URL.

1.  **Home Assistant:** To host the dashboards.
2.  **Image Renderer / Dithering:** A middleware running on your local network that accepts a URL and returns a PNG. This provides further dithering services.

## 🎮 Usage

* **Green Button (GPIO 3):** Switch to **View 1** (Main Dashboard).
* **Middle Button (GPIO 4):** Switch to **View 2** (Photos/Immich).
* **Right Button (GPIO 5):** Switch to **View 3** (System Stats).
* **Auto-Update:** The screen refreshes every 5 minutes automatically.

## 📄 Credits
* Uses the [lublak/esphome](https://github.com/lublak/esphome) Waveshare component for 7-color support.
